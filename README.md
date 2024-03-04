-- Define the list of whitelisted user IDs with expiration time
local WhitelistedUserIds = {
    ["470784963"] = os.time() + 4200, -- Add an hour to the current time
    -- Add more whitelisted user IDs here if needed
}

-- Function to check if a player's ID is whitelisted and not expired
local function isWhitelisted(player)
    local playerId = tostring(player.UserId)
    local currentTime = os.time()
    if WhitelistedUserIds[playerId] and WhitelistedUserIds[playerId] > currentTime then
        return true
    else
        WhitelistedUserIds[playerId] = nil -- Remove expired user ID from whitelist
        return false
    end
end

-- Check if the player's ID is whitelisted
if isWhitelisted(game.Players.LocalPlayer) then
   loadstring(game:HttpGet("https://raw.githubusercontent.com/therealzeek/Nara.cc/main/script1.lua"))()
else
    -- Code for non-whitelisted players
    print("Sorry, you are not whitelisted or your whitelist has expired.")
    -- You can kick or restrict access for non-whitelisted players here
end
