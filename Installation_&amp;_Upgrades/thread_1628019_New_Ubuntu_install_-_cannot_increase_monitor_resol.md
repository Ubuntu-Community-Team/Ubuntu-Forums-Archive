---
title: "New Ubuntu install - cannot increase monitor resolution. Onboard graphics card."
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by greggles77 on 2010-11-22
Hi everyone, I know there are** *many*** threads on similar issues but I can't find anything that will work. I am a big fan of this forum and I hope you can help.

Not sure if I need drivers or what to do - I feel really stupid as I should be able to get this right but I am at a brick wall.

Basically I have a 20inch monitor hooked up to the on-board graphics card and cannot get higher resolution than 900 x 600. It should be at 1280 by 1240. This is a brand new install with the latest Ubuntu 10. Under monitor preferences its says 'unknown' for monitor type and I don't have any driver disk for this screen but never needed one previously.

Thank you in advance for your help.

Here is my information so far:

lshw -c display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 65x/M650/740 PCI/AGP VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:f0000000-f7ffffff memory:e7800000-e781ffff ioport:d800(size=128)

When I run xrandr:

~# xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 960 x 600, maximum 960 x 600
default connected 960x600+0+0 0mm x 0mm
   960x600        60.0* 
   960x540        60.0  
   800x600        60.0     56.0  
   768x576        60.0  
   720x576        60.0  
   856x480        60.0  
   800x480        60.0  
   720x480        61.0  
   640x480        60.0  
   400x300        60.0  
   320x240        61.0 

When I type:

lspci | grep VGA01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter




If I need to do an addmode command then what would it be? PS my xconfig file when I open it with sudo gedit /etc/X11/xorg.conf  it opens up the file but it has not text in it...

Any help you can give would be great  :p

---

### Post by mikewhatever on 2010-11-22
You could try 'xrandr -s' just to check if it works.

```
xrandr -s 1280x1240
```

Is that really a rectangular monitor?

---

