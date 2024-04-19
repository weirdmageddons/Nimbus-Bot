
#### Methods
* `getLocal()` : Returns bot local information
* `getWorld()` : Returns bot world information
* `getInventory()` : Returns bot's inventory list
* `connect()` : Connects bot to server
* `disconnect()` : Disconnects bot from server
* `hasAccess(x: [number], y: [number])` : Returns true if bot has access in spesific tile
* `sendRaw(packet: [TankPacket])` | `sendPacketRaw(packet: [TankPacket])` | `sendRawPacket(packet: [TankPacket])` : Sends tank packet
* `sendPacketRaw(packet: [TankPacket])` : Sends tank packet
* `sendPacket(packet: [text])` : Sends text packet
* `warp(world_name: [text])` : Warps world
* `say(message: [text])` : Sends a message to world
* `wear(itemID: [number])` : Wears an item if bot isn't wearing
* `unwear(itemID: [number])` : Unwears an item if bot is wearing
* `drop(itemID: [number], count: [number])` : Drops item (count is optional)
* `trash(itemID: [number], count: [number])` : Trashs item (count is optional)
* `buy(storeID: [text])` : Buys item from store with storeID
* `sleep(millisecond: [number])` : Delay
* `print(log: [text])` : Log to application console
* `place(x: [number], y: [number, itemID: [number])` : Places block if its valid
* `punch(x: [number], y: [number)` : Hits to tile
* `wrenchPlayer(netid: [number])` : Wrenchs to player by netid
* `enter()` : Enters the door, if there is door
* `findPath(x: [number], y: [number)` : Finds tile path and moves to destination
* `collect(range: [number])` : Collect all objects by range
* `isInWorld(world_name: [text])` : Returns true if bot is in a world (world_name is optional)
* `isInTile(x: [number], y: [number])` : Returns true if the bot is in the tile
* `setSkin(skinID: [text])` : Sets skin by skinID: Example: `setSkin("3370516479")`
* `isWearing(itemID: [number])` : Returns true if bot wears item
* `getInfo(itemID: [number])` : Returns item info by itemID


## Local Info
* `name`
* `status`
* `country`
* `netid`
* `userid`
* `x`
* `y`
* `mac`
* `rid`

#### Example 1
```lua
while getLocal().status ~= "online" do
    connect()
    sleep(15000)
    print("Waiting bot to return online...")
end
print("Bot online!")
```

#### Example 2
```lua
bot_x = math.floor(getLocal().x / 32)
bot_y = math.floor(getLocal().y / 32)
print("Bot position: (" .. bot_x .. "," .. bot_y .. ")")
```

## Inventory
* `name` | `id` | `amount`

#### Example
```lua
for _, item in pairs(getInventory()) do
  print("Item Id: " .. item.id)
  print("Item Amount: " .. item.amount)
  print("Item Name: " .. item.name)
end
```

## Players
* `name` | `country` | `netid` | `userid` | `x` | `y`

#### Example
```lua
for _, player in pairs(getPlayers()) do
  print("Player Name: " .. player.name)
end
```

### World
* `name` | `width` | `height` | `tilecount`
* `isJammed` 

#### Example
```lua
if (getWorld().name == "NIMBUS") then
    print("World tile count: " .. getWorld().tilecount)
    if (getWorld().isJammed == false) then
        print("World is public")
    else
        print("World is jammed")
    end
end
```

## Item Info
* `name` | `editable_type` | `item_category` | `action_type` | `collision_type` | `rarity` | `grow_time` | `clothing_type`

#### Example
```lua
item_id = 818

if (getInfo(item_id).clothing_type ~= 6) then
    print("Item ID: " .. item_id)
    print("Item Name:  " .. getInfo(item_id).name)
    print("Item Cloth Type: Wing")
end
```

## Tank Update Packet | Raw Packet

Represents a packet that updates the state of an object in the game.

- `type` : The type of packet.
- `object_type` : The type of object change type.
- `count1` : A count variable used in certain types of packets.
- `count2` : A count variable used in certain types of packets.
- `netid` : The network ID of the object/player... being updated.
- `item` : The item being updated.
- `flags` : A set of flags used in certain types of packets.
- `float_var` : A floating point variable used in certain types of update packets.
- `int_data` : An integer variable used in certain types of update packets.
- `vec_x` | `pos_x` : The x position of a component being updated.
- `vec_y` | `pos_y` : The y position of a component being updated.
- `vec2_x` | `pos2_x` : The velocity x of a component being updated.
- `vec2_y` | `pos2_y` : The velocity y of a component being updated.
- `particle_rotation` : The rotation of a particle being updated.
- `int_x` : An integer variable used in certain types of update packets. (Ex Tile Position)
- `int_y` : An integer variable used in certain types of update packets. (Ex Tile Position)

## Example
```lua
packet = {}

packet.type = 3
packet.vec_x = 1239
packet.vec_y = 2304

sendRaw(packet)
```

## Events

SOON!



## Enums

```lua
"online"
"offline"
"account_banned"
"wrong_password"
"location_banned"
"version_update"
"advanced_account_protection"
"server_overload"
"too_many_login"
"maintenance"
"server_busy"
"guest_limit"
"http_block"
"bad_name_length"
"invalid_account"
"error_connecting"
"logon_fail"
"captcha_requested"
"high_load"
"temporary_ban"
"changing_subserver"
"refresh_item_data"
"getting_server_data"
```
