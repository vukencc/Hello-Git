execute as @s at @s store result score @s healthfixp1 run attribute @s generic.max_health get
$scoreboard players remove @s healthfixp1 $(count)
execute as @s if score @s Health >= @s healthfixp1 as @s run tag @s add regeneration3
execute as @s if score @s Health >= @s healthfixp1 as @s run scoreboard players set @s PlayerHealth 20
execute as @s if score @s Health >= @s healthfixp1 as @s run effect give @s instant_health 1 200 true
$scoreboard players add @s healthfixp1 $(count)
scoreboard players operation @s PlayerHealth = @s healthfixp1
$scoreboard players set @s MaxHealthFix $(count)
execute as @s if entity @s[tag=!regeneration3] at @s run function respawn:enchant/regeneration3
tag @s[tag=!regeneration3] add regeneration2
tag @s remove regeneration3
kill @e[tag=healthfix,type=marker]