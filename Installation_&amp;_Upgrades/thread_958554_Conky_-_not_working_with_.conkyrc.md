---
title: "Conky - not working with .conkyrc"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by rusty_jones on 2008-10-25
Running Hardy Herion 8.04. Installed conky works fine. As soon as I setup a hidden conkyrc file conky stops working. When i delete the .conkyrc file it works again

I purged the conky installation and reinstalled conky with same results.
I am also a newbie with linux, about two weeks so please explain the solution carefully.

Rusty

---

### Post by Denestria on 2008-10-25
The file is properly named .conkyrc and is in your /home/username directory?  When you start conky from the command line what does it say?  Post the config you are trying to use so we can see what is wrong with it.

---

### Post by rusty_jones on 2008-10-25
I downloaded the config file from conky home. I placed it it my home directory.

# Conky configuration
background yes
use_xft yes
xftfont Monospace:size=9
xftalpha 0.8
out_to_console no
update_interval 2
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
stippled_borders 5
border_margin 4
border_width 1
default_color grey
default_shade_color black
default_outline_color black
alignment top_right
gap_x 10
gap_y 47
no_buffers no
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
use_spacer no

TEXT
${color white}$alignc$sysname $kernel on $machine
${color white}$alignc${exec whoami} @ $nodename
$color$stippled_hr
${color}Date: ${color white}${time %A,%d %B}
${color}Time: ${color white}${time %k:%M:%S}${alignr}${color}Uptime: ${color white}$uptime
$color$stippled_hr
${alignc}Temperatures
${alignc}CPU: ${color white}${i2c 9191-0290 temp 2}Â°C$color - MB: ${color white}${i2c 9191-0290 temp 1}Â°C
$color$stippled_hr
${color}CPU:${color white} ${cpu cpu1}% ${cpubar cpu1}
${color}RAM:${color white} $memperc%  $mem/$memmax $membar
${color}Swap: ${color white}$swapperc% $swap/$swapmax ${swapbar}
$color$stippled_hr
${alignc}File systems
${color}/dev/sda1${color white} ${fs_used_perc /}%   ${fs_used /}/${fs_size /}   ${fs_bar /}
${color}/dev/sda3${color white} ${fs_used_perc /media/stuff/}% ${fs_used /media/stuff/}/${fs_size /media/stuff/} ${fs_bar /media/stuff/}
$color$stippled_hr${if_running amarokapp}
${color}${alignc}Now Playing${color white}
${alignc}${execi 10 ~/.conky/amarok artist}
${alignc}${execi 10 ~/.conky/amarok title}
${execibar 1 ~/.conky/amarok progress}
${alignc}"${execi 10 ~/.conky/amarok album}"
${alignc}${execi 10 ~/.conky/amarok year} - ${color white}${alignc}${execi 10 ~/.conky/amarok genre}
$color$stippled_hr
${alignc}Collection Information
Artists: ${color white}${execi 10 ~/.conky/amarok totalArtists} $color${alignr}Compilations: ${color white}${execi 10 ~/.conky/amarok totalCompilations}$color
Albums:  ${color white}${execi 10 ~/.conky/amarok totalAlbums} $color${alignr}Genres: ${color white}${execi 10 ~/.conky/amarok totalGenres}$color
Tracks:  ${color white}${execi 10 ~/.conky/amarok totalTracks}
$color$stippled_hr
${alignc}Collection Statisctics
Most songs by ${color white}${execi 10 ~/.conky/amarok most_songs_by_artist} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_by_artist_n}${color})
Most songs are ${color white}${execi 10 ~/.conky/amarok most_songs_are_genre} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_are_genre_n}${color})
Most songs during ${color white}${execi 10 ~/.conky/amarok most_songs_during_year} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_during_year_n}${color})
Most albums by ${color white}${execi 10 ~/.conky/amarok most_albums_by_artist} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_by_artist_n}${color})
Most albums are ${color white}${execi 10 ~/.conky/amarok most_albums_are_genre} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_are_genre_n}${color})
Most albums during ${color white}${execi 10 ~/.conky/amarok most_albums_during_year} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_during_year_n}${color})$endif

although it does not matter which config file i use none of them work.

rusty

---

### Post by Denestria on 2008-10-25
> ${alignc}CPU: ${color white}${i2c 9191-0290 temp 2}Â°C$color - MB: ${color white}${i2c 9191-0290 temp 1}Â°C

This is probably incorrect for your system if this is a config you copied from somewhere.  You need to change to it match your system or remove it.

---

### Post by Bruce M. on 2008-10-27
See my signature for a HowTo and if you still have problems pop into: 

[Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865") and ask away, you'll get LOTS of help.

Chimo!
Bruce

---

