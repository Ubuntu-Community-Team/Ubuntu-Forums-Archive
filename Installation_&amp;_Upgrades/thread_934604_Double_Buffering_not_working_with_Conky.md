---
title: "Double Buffering not working with Conky"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by crroush on 2008-09-30
I am having an issue with getting Conky to use the double buffering.
I have added dbe under the modules section and it doesn't solve my problem.

Here is the version of kernel I am using,
Linux labyrinth 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

Here is the output when I run conky from the command line
```
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: desktop window (12000ba) is subwindow of root window (13b)
Conky: window type - override
Conky: drawing to created window (3200001)
Conky: failed to set up double buffer
Conky: drawing to single buffer

```

Here is my conkyrc file
```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#
#override_utf8_locale yes
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes 

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font Arial:size=8
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
sda1:  ${fs_free_perc /media/windows}%   ${fs_bar 6 /media/windows}

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}WEATHER${hr 2}$color
Updated: ${execi 3600 conkyForecast --location=USCO0305 --datatype=LU} 
Temp: ${execi 3600 conkyForecast --location=USCO0305 --datatype=HT -u -x -i}/${execi 3600 conkyForecast --location=USCO0305 --datatype=LT -u -x -i}F   Cond: ${execi 3600 conkyForecast --location=USCO0305 --datatype=CC} 
Precip: ${execi 3600 conkyForecast --location=USCO0305 --datatype=PC}      Humi: ${execi 3600 conkyForecast --location=USCO0305 --datatype=HM}

${execi 3600 conkyForecast --location=USCO0305 --datatype=DW}      ${execi 3600 conkyForecast --location=USCO0305 --datatype=DW -s 1 -e 4 -w -S 7}
${execi 3600 conkyForecast --location=USCO0305 --datatype=HT -u -x -i}/${execi 3600 conkyForecast --location=USCO0305 --datatype=LT -u -x -i}F     ${execi 3600 conkyForecast --location=USCO0305 --datatype=HT -u -x -i -s 1}/${execi 3600 conkyForecast --location=USCO0305 --datatype=LT -u -x -i -s 1}F    ${execi 3600 conkyForecast --location=USCO0305 --datatype=HT -u -x -i -s 2}/${execi 3600 conkyForecast --location=USCO0305 --datatype=LT -u -x -i -s 2}F    ${execi 3600 conkyForecast --location=USCO0305 --datatype=HT -u -x -i -s 3}/${execi 3600 conkyForecast --location=USCO0305 --datatype=LT -u -x -i -s 3}F    ${execi 3600 conkyForecast --location=USCO0305 --datatype=HT -u -x -i -s 4}/${execi 3600 conkyForecast --location=USCO0305 --datatype=LT -u -x -i -s 4}F
${execi 3600 conkyForecast --location=USCO0305 --datatype=PC}        ${execi 3600 conkyForecast --location=USCO0305 --datatype=PC -s 1 -e4 -S 7}
${execi 3600 conkyForecast --location=USCO0305 --datatype=SR}      ${execi 3600 conkyForecast --location=USCO0305 --datatype=SR -s 1 -e4 -S 5}

${color orange}WIRELESS NETWORK${hr 2}$color
${color #888888}ip address: ${color #CCCCCC}${addr wlan0}
${color #888888}essid: $color${execi 5 iwconfig wlan0 | sed 's/  /\n/g' | grep ESSID | sed 's/ESSID:"//'| sed 's/"//'}
${color #888888}link status: $color${execi 5 iwconfig wlan0 | sed 's/  /\n/g' | grep Quality | sed 's/Link Quality://' | sed 's/Link Quality=//' | sed 's/ //g' } ${color #888888}signal: $color${execi 5 iwconfig wlan0 | sed 's/  /\n/g' | grep Signal | sed 's/Signal level=//' | sed 's/Signal level://' }

${color #888888}total download: ${color #CCCCCC}${totaldown wlan0}         ${color #888888}total upload: ${color #CCCCCC}${totalup wlan0}	 
${color #888888}download speed: ${color #CCCCCC}${downspeed wlan0} k/s	      ${color #888888}upload speed: ${color #CCCCCC}${upspeed wlan0} k/s
${color #888888}${downspeedgraph wlan0 25,100 ff0000 0000ff}                    ${color #888888}${upspeedgraph wlan0 25,100 0000ff ff0000}

${color orange}MEMORY${hr 2}$color
${color #888888}ram: ${color #CCCCCC}$mem${color #888888}/${color #CCCCCC}$memmax ${color #888888}, ${color #CCCCCC}$memperc%
${color #888888}swap: ${color #CCCCCC}$swap${color #888888}/${color #CCCCCC}$swapmax ${color #888888}, ${color #CCCCCC}$swapperc%
${color #888888}avg load: (${color #CCCCCC}$loadavg${color #888888})
${color #888888}processes: ${color #CCCCCC}$processes	${color #888888}running: ${color #CCCCCC}$running_processes
${color #ffccaa}Power:
${color #888888}Battery: $color${battery}

${color orange}${hr 1}$color

```

Here is my xorg.conf

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Thu Jun  5 09:26:53 UTC 2008

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder57)  Thu Jul 17 18:39:19 PDT 2008

Section "ServerLayout"

	#Inputdevice	"Mouse0"	"CorePointer"
    Identifier     "Layout0"
    Screen      0  "Screen0" RightOf "Screen1"
    Screen      1  "Screen1" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "on"
EndSection

Section "InputDevice"

	# generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 1908FP"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8700M GT"
    BusID          "PCI:3:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8700M GT"
    BusID          "PCI:3:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: 1920x1200 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: 1280x1024 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by JulienC on 2008-10-19
According to [this post on an nVidia forum]("http://www.nvnews.net/vbulletin/showthread.php?t=110660"), Xinerama prevents the double buffering extension from being initialized.

So you have to either disable Xinerama, or let conky flicker.

:(

---

