---
title: "karmic &amp; xrandr large screen dualhead problem"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jwmuelle on 2009-10-24
I've just switched from fedora 11 (where this configuration works) to ubuntu 9.10 (karmic), at today's current level, and am working on tweaking my desktop.  This problem is the same whether using xrandr line commands or the display app (System > Preferences > Display)...

side-by-side or too tall above/below configurations causes a blank screen on laptop and vga.  Below is the xrandr output for the largest I can specify above/below before encountering the error.

This is on a Thinkpad T60 laptop with the following Intel graphics card:
Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

As shown in the display, the xorg.conf is set to use virtual screen of 4096x4096.  No errors or obviously abnormal messages are in Xorg.0.log.

xrandr
Screen 0: minimum 320 x 200, current 1680 x 1914, maximum 4096 x 4096
VGA1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      59.9*+   60.0  
   1280x1024      75.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3     56.2  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS1 connected 1152x864+0+1050 (normal left inverted right x axis y axis) 285mm x 214mm
   1400x1050      60.0 +   85.0     74.8     70.0     60.0     50.0  
   1280x1024      85.0     75.0     60.0  
   1280x960       85.0     60.0  
   1360x768       59.8  
   1152x864      100.0*    85.1     85.0     75.0     75.0     70.0     60.0  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     60.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
   0x0             0.0  
DVI1 disconnected (normal left inverted right x axis y axis)


I've searched the forum and don't see any similar posts.

Thanks for any ideas.
Jeff.

---

### Post by jwmuelle on 2009-10-24
I'm not sure why, but this has resolved itself.  

As I moved forward to test the new, experimental gnome-shell (from terminal window, gnome-shell --replace), the screens flickered, some errors displayed from gnome-shell, and my 3rd display (problem described in a different thread) came up with the gnome desktop (gnome-shell exited after the errors).

With this working, also tried xrandr with full resolution on 1st 2 screens and this was resolved as well.

Confirmed across 2 additional re-boots (without needing to try starting gnome-shell).

Jeff.

---

