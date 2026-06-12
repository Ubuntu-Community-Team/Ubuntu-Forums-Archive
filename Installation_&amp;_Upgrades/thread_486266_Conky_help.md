---
title: "Conky help"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by gr1Mo on 2007-06-27
wtf

---

### Post by kerry_s on 2007-06-27
you just run conky> alt+f2 type conky

you'll also proably want to grab you a nice .conkyrc from some where, there's some on the conky web site and there's a huge thread on conky here.> [http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

here's mine->

```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background true

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
font -*-*-*-*-*-*-80-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Set conky on the bottom of all other applications
own_window_hints below

# Xft font when Xft is enabled
xftfont Sans-Serif:size=8

# Text alpha when using Xft
xftalpha 1

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 3.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window true
own_window_type override
own_window_hints undecorated,skip_taskbar,skip_pager

# Use pseudo transparency with own_window?
own_window_transparent true

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour hotpink

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 10

# border width
border_width 10

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 10

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# Allow for the creation of at least this number of port monitors (if 0 or not set, default is 16) 
#min_port_monitors 16

# Allow each port monitor to track at least this many connections (if 0 or not set, default is 256)
#min_port_monitor_connections 256

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

#${execi 300 fortune -a | fold -w50}

TEXT
${color white}              ${time %l:%M %a %b %d}
${hr}
CPU: ${freq_g}GHz / Clocked: ${freq_dyn}MHz / Temp: ${acpitemp}C 
Disk I/O:${diskio}    Uptime:$uptime 
Processes:$processes  Running:$running_processes
CPU Usage:$cpu% ${cpugraph  20, 125 ffffff 0000ff}

RAM Usage:$mem of $memmax - $memperc% 
Swap Usage:$swap of $swapmax - $swapperc% 
File systems: ${fs_used /} of ${fs_size /}

Name                     PID     CPU%   MEM%
${top name 1}         ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2}         ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3}         ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4}         ${top pid 4} ${top cpu 4} ${top mem 4}
${top name 5}         ${top pid 5} ${top cpu 5} ${top mem 5}

   IN:${downspeed eth0} k/s          OUT:${upspeed eth0} k/s 
${downspeedgraph eth0 20,125 ff0000 0000ff} ${upspeedgraph eth0 20,125 0000ff ff0000}

Connections: ${tcp_portmon 1 65535 count}
Netstat 
${execi 2 netstat -e -p -t | grep ESTABLISHED | cut -c45-68,80-86,102-140}
${hr}

```

---

### Post by gr1Mo on 2007-06-27
wow.

---

### Post by kerry_s on 2007-06-28
okay, i'm going to assume your using gonme.

press alt+f2 type> **gedit ~/.conkyrc**

and paste away

---

