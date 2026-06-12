---
title: "Conky on Jaunty?"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by JECHO on 2009-04-03
Hey guys, I am using the same conkyrc i used back on intrepid but with jaunty i cant seem to get it to stay hidden behind windows when it auto starts... anyone know a work around for this? 

here is my config file:


```
background yes
font Sans:size=8
xftfont Sans:size=8
use_xft yes
xftalpha 0.1
update_interval .5
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 206 5
maximum_width 206
default_color cccccc
default_shade_color 000000
default_outline_color 000000
alignment bottom_right
gap_x 6
gap_y 22
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT
${font Aerial:style=Bold:pixelsize=12}Ubuntu${font Sans:size=8} ${hr 1 }

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg

Battery    ${battery_time BAT0} ${alignr}(${battery BAT0})
${battery_bar 4 BAT0}

CPU       ${alignc} ${freq}MHz / ${acpitemp}C ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph cccccc 333333}

RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}

SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}


${font Aerial:style=Bold:pixelsize=12}Network${font Sans:size=8}${hr 1}

Down ${downspeed wlan0} k/s ${alignr}Up ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,107 cccccc 333333} ${alignr}${upspeedgraph wlan0 25,107 cccccc 333333}
Total ${totaldown wlan0} ${alignr}Total ${totalup wlan0}
```

---

### Post by nostradamnit on 2009-04-21
Did you ever get this problem fixed? I'm having the same problem...

--Sam

---

### Post by biji on 2009-04-21
do you use compiz?

---

### Post by Insane_Homer on 2009-04-21
same problem,

if I launch conky from the command line it stays behind other windows correctly. If I launch it from startup it is always on top.

x64 9.04 with Compiz with NVidia drivers.

---

### Post by xtoudi on 2009-04-21
Set 

** sh -c "sleep 15 && conky"**

as a start - works great. You can change "15" in secs if you need (in my case 15 seconds is enough).

Its because conky need to wait until compiz will start completely.

---

### Post by biji on 2009-04-21
yup.. like xtoudi said, need some delay before loading conky in my case 25s

---

