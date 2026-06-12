---
title: "Dual Monitors Cause Sluggish Display"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by ddbal on 2010-06-27
PROBLEM SUMMARY 
 In Ubuntu 10.4 the display is sluggish when two monitors are active.   Sluggish  means any action involving the display is slow.  For example, moving a window is slow, scrolling up or down is slow, even typing in GEdit is slow.  If I shut off one monitor the sluggishness disappears - everything is normal. 
 
 Previously, both displays  worked well in Windows XP (no sluggish behavior).  I am trying to leave Windows for Ubuntu 10.4, but I need my two monitors to work for that to happen. 

 HARDWARE 
 My computer is a T400 Lenovo thinkpad laptop.  I have two monitors with resolution 1920 x 1200.  I use the two monitors through a docking station in pivot mode (rotated left 90 degrees).  This video chip is on-board Intel GMA 4500MHD. 
 
 WHAT I HAVE TRIED: 
 I can turn on both displays through system -> preferences -> displays.  It took me a little while to learn that I needed to turn off the laptop display before I could configure the resolution of the external monitors.  After overcoming that hurdle I was overjoyed to see both monitors working.  Unfortunately, I soon discovered that the display is too sluggish.  
 
 I thought that if I lowered the color depth to 16-bit color the display performance may improve.  Unfortunately, the color depth can not be changed in display preferences.  I found a forum entry with instructions to make a xorg.conf file below: 
 [URL="http://georgia.ubuntuforums.org/showthread.php?t=1238639"]http://georgia.ubuntuforums.org/showthread.php?t=1238639  
[/URL]
 I made the xorg.conf file and restarted.  The change was *mostly* successful.  The display performance was faster – in fact, good enough.  However, a new problem appeared.  The top of every window was gone.  That means the little "x" "v" and box in the left corner was gone.  The window title was gone as well.  This strange side-effect means I can not close any window, minimize it, or maximize it.  I had to delete the xorg.conf file to restore normal window appearance.

 I also tried to use the monitors in regular, not rotated,  mode.  There is no effect.  It is sluggish with two monitors, rotated or not, and fine with one.
 
 REQUEST FOR HELP
 I am very happy with Ubuntu in many ways.  I want to use it regularly, but I don't want to use only one monitor.  Any suggestions on how I can speed up the dual monitor performance?

---

