---
title: "Conky Xoap"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by Apv507 on 2011-02-04
What is up with conky? I can never get the weather to work, I have tried 5 times over the last 3 years on 5 separate installations of Ubuntu. Where in the world do I find my XOAP Partner ID and Licence Key? I am a member on weather.com and I can't find anything about XOAP. Please Help this is so frustrating!

---

### Post by Quackers on 2011-02-04
You get your Partner ID and Licence Key from the weather site, then enter them into your conkyforecast.config file.
See the conkyweather thread
[http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)

---

### Post by Apv507 on 2011-02-04
I found the part of the site where they email you the ID and Licence, but it still fails to work and I have to have my resolution jacked all the way up to see everything. Here is the text file:


##################################
## VinDSL | rev. 11-02-02 03:08 ##
##################################
##   Screen res: 1280x1024x24   ##
##################################

####
## Use XFT? Required to Force UTF8 (see below).
#
use_xft yes
xftfont DroidSans:size=8.75
xftalpha 0.1
text_buffer_size 2048

####
## Force UTF8? Requires XFT (see above).
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## Daemonize Conky, aka 'fork to background'.
#
background yes

####
## Update interval in seconds.
#
update_interval 1.5

####
## This is the number of times Conky will update before quitting.
## Set to zero to run forever.
#
total_run_times 0

####
## Create own window instead of using desktop (required in nautilus)?
#
own_window yes
own_window_type override
own_window_transparent yes

####
## Force images to redraw when they change.
#
imlib_cache_size 0

####
## Use double buffering? Reduces flicker.
#
double_buffer yes

####
## Draw shades?
#
draw_shades no

####
## Draw outlines?
#
draw_outline no

####
## Draw borders around text?
#
draw_borders no

####
## Draw borders around graphs?
#
draw_graph_borders no

####
## Print text to stdout?
## Print text in console?
#
out_to_ncurses no
out_to_console no

####
## Text alignment.
#
alignment top_right

####
## Minimum size of text area.
#
minimum_size 238 0

####
## Gap between text and screen borders.
#
gap_x 8
gap_y 33

####
## Shorten MiB/GiB to M/G in stats.
#
short_units yes

####
## Pad % symbol spacing after numbers.
#
pad_percents 0

####
## Pad spacing between text and borders.
#
border_inner_margin 4

####
## Limit the length of names in "Top Processes".
#
top_name_width 10

####
## Subtract file system -/+buffers/cache from used memory?
## Set to yes, to produce meaningful physical memory stats.
#
no_buffers yes

####
## Set to yes, if you want all text to be in UPPERCASE.
#
uppercase no

####
## Number of cpu samples to average.
## Set to 1 to disable averaging.
#
cpu_avg_samples 2

####
## Number of net samples to average.
## Set to 1 to disable averaging.
#
net_avg_samples 2

####
## Add spaces to keep things from moving around?
## Only affects certain objects.
#
use_spacer right

####
## My colors (suit yourself).
#
color0 White
color1 Ivory
color2 Ivory2
color3 Ivory3
color4 Tan1
color5 Tan2
color6 Gray
color7 AntiqueWhite4
color8 DarkSlateGray
color9 Black

####
## Load Lua for shading (optional).
## Set the path to your script here.
#
lua_load ~/.conky/draw_bg.lua
lua_draw_hook_pre draw_bg

####
## Load Lua for bargraphs (required).
## Set the path to your script here.
#
lua_load ~/.conky/bargraph_small.lua
lua_draw_hook_post main_bars

####
## Installed fonts (required).
#
# ConkyWeather (Stanko Metodiev)
# ConkyWindNESW (Stanko Metodiev)
# Cut Outs for 3D FX (Fonts & Things)
# Droid Font Family (Google Android SDK)
# Liberation Mono (Ascender Corp)
# Liberation Sans (Ascender Corp)
# Moon Phases (Curtis Clark)
# OpenLogos (Icoma)
# PizzaDude Bullets (Jakob Fischer)
# Radio Space (Iconian Fonts)
# StyleBats (Vinterstille)
# Ubuntu (Canonical Ltd)
# Ubuntu Title Bold (Paulo Silva)
# Weather (Jonathan Macagba)

TEXT
##################
##     LOGO     ##
##################
${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 178}${font UbuntuTitleBold:size=20}${color4}10.10${font}
##################
##    SYSTEM    ##
##################
${voffset 20}${font DroidSans:bold:size=8.25}${color4}SYSTEM${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font OpenLogos:size=10}${color2}u${voffset -4}${font DroidSans:size=8.65}${color3}${offset 5}${sysname}${offset 5}${kernel}${alignr}${font DroidSans:size=8.75}${machine}${font}
${voffset 2}${font StyleBats:size=10}${color2}A${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}Intel${offset 3}P4${offset 3}Extreme${offset 3}Edition${alignr}${font DroidSans:size=8.4}${freq_g cpu0}${offset 1}GHz${font}
${voffset 2}${font StyleBats:size=10}${color2}q${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}System${offset 3}Uptime${alignr}${font DroidSans:size=8.4}${uptime_short}${font}
${voffset 2}${font StyleBats:size=10}${color2}o${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}File${offset 3}System${alignr}${font DroidSans:size=8.4}${fs_type}${font}
##################
##  PROCESSORS  ##
##################
${voffset 6}${font DroidSans:bold:size=8}${color4}PROCESSORS${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color2}k${voffset -2}${font DroidSans:size=8.4}${color3}${offset 2}CPU1${offset 5}${font DroidSans:size=8.55}${cpu cpu1}%${font}
${voffset 2}${font StyleBats:size=10}${color2}k${voffset -2}${font DroidSans:size=8.4}${color3}${offset 2}CPU2${offset 5}${font DroidSans:size=8.55}${cpu cpu2}%${font}
##################
##    MEMORY    ##
##################
${voffset 6}${font DroidSans:bold:size=8}${color4}MEMORY${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color2}l${voffset -2}${font DroidSans:size=8.4}${color3}${offset 3}RAM${goto 97}${font DroidSans:size=8.55}${mem}${goto 133}/${offset 5}${memmax}${alignr}${memperc}%${font}
##################
##     HDD      ##
##################
${voffset 16}${font DroidSans:bold:size=8}${color4}HDD${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 5}${font StyleBats:size=10}${color2}x${voffset -2}${font DroidSans:size=8.4}${color3}${offset 4}ROOT${goto 95}${font DroidSans:size=8.55}${fs_used /}${goto 133}/${offset 5}${fs_size /}${alignr}${fs_free_perc /}%${font}
${voffset 15}${font StyleBats:size=10}${color2}x${voffset -2}${font DroidSans:size=8.4}${color3}${offset 4}HOME${goto 95}${font DroidSans:size=8.55}${fs_used /home}${goto 133}/${offset 5}${fs_size /home}${alignr}${fs_free_perc /home}%${font}
${voffset 15}${font StyleBats:size=10}${color2}4${voffset -2}${font DroidSans:size=8.4}${color3}${offset 4}SWAP${goto 95}${font DroidSans:size=8.55}${swap}${goto 133}/${offset 5}${swapmax}${alignr}${swapperc}%${font}
##################
# TOP PROCESSES ##
##################
${voffset 16}${font DroidSans:bold:size=8}${color4}TOP PROCESSES${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 1}${goto 120}${font DroidSans:size=8.55}${top_mem mem_res 1}${alignr}${top_mem mem 1}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 2}${goto 120}${font DroidSans:size=8.55}${top_mem mem_res 2}${alignr}${top_mem mem 2}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 3}${goto 120}${font DroidSans:size=8.55}${top_mem mem_res 3}${alignr}${top_mem mem 3}%${font}
${voffset 0}${if_running rhythmbox}${voffset -14}${else}${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 4}${goto 120}${font DroidSans:size=8.55}${top_mem mem_res 4}${alignr}${top_mem mem 4}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 5}${goto 120}${font DroidSans:size=8.55}${top_mem mem_res 5}${alignr}${top_mem mem 5}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 6}${goto 120}${font DroidSans:size=8.55}${top_mem mem_res 6}${alignr}${top_mem mem 6}%${font}${endif}
##################
##   NETWORK    ##
##################
${voffset 6}${font DroidSans:bold:size=8}${color4}NETWORK${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font PizzaDudeBullets:size=10}${color6}a${font DroidSans:size=8.65}${color3}${offset 5}Private${offset 3}IP${alignr}${font DroidSans:size=8.55}${addr eth0}${font}
${voffset 0}${font PizzaDudeBullets:size=10}${color6}a${font DroidSans:size=8.65}${color3}${offset 5}Public${offset 7}IP${alignr}${font DroidSans:size=8.55}${texeci 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}${font}
${voffset 4}${font PizzaDudeBullets:size=10}${color6}T${font DroidSans:size=8.65}${color3}${offset 5}Down${alignr}${font DroidSans:size=8.55}${downspeed eth0}${font}
${voffset 0}${font PizzaDudeBullets:size=10}${color6}N${font DroidSans:size=8.65}${color3}${offset 5}Up${alignr}${font DroidSans:size=8.55}${upspeed eth0}${font}
${voffset 4}${font PizzaDudeBullets:size=10}${color6}T${font DroidSans:size=8.65}${color3}${offset 5}Downloaded${alignr}${font DroidSans:size=8.55}${totaldown eth0}${font}
${voffset 0}${font PizzaDudeBullets:size=10}${color6}N${font DroidSans:size=8.65}${color3}${offset 5}Uploaded${alignr}${font DroidSans:size=8.55}${totalup eth0}${font}
##################
##   WEATHER    ##
##################
${voffset 6}${font DroidSans:bold:size=8}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 0}${goto 59}${font Weather:size=38}${color2}y${font}${voffset -33}${offset 14}${font RadioSpace:size=32}${color3}${texeci 1800 conkyForecast --location=USAZ0082 --imperial}${font}
${voffset 0}${font Ubuntu:size=24}${color4}${alignc}${texeci 1800 conkyForecast --location=USAZ0082 --datatype=CT}${font}
${voffset 15}${goto 20}${font ConkyWindNESW:size=41}${color3}${texeci 1800 conkyForecast --location=USAZ0082 --datatype=BS}${font}${voffset -40}${goto 98}${font ConkyWeather:size=45}${texeci 1800 conkyForecast --location=USAZ0082 --datatype=WF}${font}${voffset -40}${goto 186}${font MoonPhases:size=32.5}${texeci 1800 conkyForecast --location=USAZ0082 --datatype=MF}${font}
${voffset 6}${goto 28}${font DroidSansFallback:bold:size=8.45}${color4}${execpi 1800 conkyForecast --location=USAZ0082 --imperial --datatype=WS | sed -e 's/calm'/'\$\{offset 2}Calm/g' -e 's/mph'/'\$\{offset 2}mph/g'}${goto 88}Feels like ${texeci 1800 conkyForecast --location=USAZ0082 --imperial --hideunits --datatype=LT --centeredwidth=4}${execpi 1800 conkyForecast --location=USAZ0082 --datatype=MP | sed -e 's/First.*'/'\$\{goto 182}First Qtr/g' -e 's/Last.*'/'\$\{goto 184}Last Qtr/g' -e 's/New.*'/'\$\{goto 193}New/g' -e 's/Full.*'/'\$\{goto 195}Full/g' -e 's/Waning.*'/'\$\{goto 186}Waning/g' -e 's/Waxing.*'/'\$\{goto 186}Waxing/g'}${font}
${voffset 8}${goto 36}${font DroidSans:bold:size=8.55}${color6}${texeci 1800 conkyForecast --location=USAZ0082 --datatype=DW --startday=1 --shortweekday}${goto 89}${texeci 1800 conkyForecast --location=USAZ0082 --datatype=DW --startday=2 --shortweekday}${goto 143}${texeci 1800 conkyForecast --location=USAZ0082 --datatype=DW --startday=3 --shortweekday}${goto 197}${texeci 1800 conkyForecast --location=USAZ0082 --datatype=DW --startday=4 --shortweekday}${font}
${voffset 4}${goto 25}${font ConkyWeather:size=32}${color2}${texeci 1800 conkyForecast --location=USAZ0082 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${goto 25}${font DroidSans:bold:size=8.5}${color4}${texeci 1800 conkyForecast --location=USAZ0082 --imperial --hideunits --datatype=HT --startday=1 --centeredwidth=4}/${offset 3}${texeci 1800 conkyForecast --location=USAZ0082 --imperial --hideunits --datatype=LT --startday=1 --centeredwidth=4}${goto 79}${texeci 1800 conkyForecast --location=USAZ0082 --imperial --hideunits --datatype=HT --startday=2 --centeredwidth=4}/${offset 3}${texeci 1800 conkyForecast --location=USAZ0082 --imperial --hideunits --datatype=LT --startday=2 --centeredwidth=4}${goto 133}${texeci 1800 conkyForecast --location=USAZ0082 --imperial  --hideunits --datatype=HT --startday=3 --centeredwidth=4}/${offset 3}${texeci 1800 conkyForecast --location=USAZ0082 --imperial --hideunits --datatype=LT --startday=3 --centeredwidth=4}${goto 187}${texeci 1800 conkyForecast --location=USAZ0082 --imperial --hideunits --datatype=HT --startday=4 --centeredwidth=4}/${offset 3}${texeci 1800 conkyForecast --location=USAZ0082 --imperial --hideunits --datatype=LT --startday=4 --centeredwidth=4}${font}
##################
##     TIME     ##
##################
${voffset 6}${font DroidSans:bold:size=8}${color4}TIME${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 0}${if_match ${time %l}<=9}${voffset -4}${font RadioSpace:size=32}${color3}${alignc 7}${time %l:%M%p}${font}${else}${if_match ${time %l}>=10}${voffset -4}${font RadioSpace:size=32}${color3}${alignc -1}${time %l:%M%p}${font}${endif}${endif}
${voffset 0}${font DroidSansFallback:bold:size=6.2}${color4}${alignc 2}Sunrise${offset 1}${texeci 1800 conkyForecast --location=USAZ0082 --datatype=SR --startday=1}${color3}${offset 2}|${offset 2}${color4}Sunset${offset 1}${texeci 1800 conkyForecast --location=USAZ0082 --datatype=SS --startday=1}${font}
##################
##   CALENDAR   ##
##################
${voffset 4}${font DroidSans:bold:size=8}${color4}DATE${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 18}${font LiberationMono:size=8}${color3}${alignc 60}${time %A}${font}
${voffset -6}${if_match ${time %e}<=9}${font DroidSansFallback:bold:size=19}${color4}${alignc 65}${time %e}${font}${else}${if_match ${time %e}>=10}${font DroidSansFallback:bold:size=19}${color4}${alignc 60}${time %e}${font}${endif}${endif}
${voffset -1}${font LiberationMono:size=8}${color3}${alignc 60}${time %B}${font}
${voffset -3}${font LiberationMono:size=8}${color3}${alignc 60}${time %Y}${font}
${voffset -75}${font LiberationMono:size=8}${color3}${execpi 60 VinDSL_Cal_5=`date +%-d`; cal | sed '1d' | sed s/^/"\$\{offset 97"\}/ | sed '/^ *$/d' | sed 's/\<'"$VinDSL_Cal_5"'\>/${color4}&${color3}/'}${font}
${voffset -97}${font CutOutsFor3DFX:size=64}${color8}${alignc 97}2${font}
##################
##  RHYTHMBOX   ##
##################
${if_running rhythmbox}${voffset 25}${font DroidSans:bold:size=7.85}${color4}RHYTHMBOX${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font DroidSans:size=8.25}${color3}${alignc}${if_match "${execpi 2 expr length "`/usr/bin/rhythmbox-client --print-playing-format %tt | head -n 1`"}" >= "45"}${scroll 40 5 ${exec rhythmbox-client --print-playing-format %tt --no-start}}${else}${exec rhythmbox-client --print-playing-format %tt --no-start}${font}${endif}${endif}

---

