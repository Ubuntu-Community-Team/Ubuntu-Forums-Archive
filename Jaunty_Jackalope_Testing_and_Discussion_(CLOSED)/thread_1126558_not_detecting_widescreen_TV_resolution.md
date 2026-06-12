---
title: "not detecting widescreen TV resolution"
date: 2009-04-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by davidmohammed on 2009-04-15
I've got a toshiba Satellite A30 with onboard Intel Corporation 82852/855GM Integrated Graphics

If I connect my VGA cable to my widescreen TV the widescreen TV resolution is not detected i.e. xrandr gives me
after connecting
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 1024
VGA connected (normal left inverted right x axis y axis)
   1024x768       60.0 +   60.0  
   800x600        60.3     56.2  
   640x480        59.9  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TMDS disconnected (normal left inverted right x axis y axis)


If I logout and login the TV resolution is detected correctly 
i.e. xrandr gives me
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1280 x 1280
VGA connected 1024x768+0+0 (normal left inverted right x axis y axis) 1200mm x 900mm
   1024x768       60.0*+   60.0  
   1280x768       59.9  
   800x600        60.3     56.2  
   640x480        59.9  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +   85.0     75.0     70.1     60.0* 
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TMDS disconnected (normal left inverted right x axis y axis)

Is this expected behaviour or a bug? If its a bug which package should I file against?

---

### Post by Kareeser on 2009-04-15
Hi David Mohammed!

I'd LOVE to say it's a bug, except it's not. It's a design feature which conserves physical memory from being used up for no reason.

Note that in the first xrandr output your "maximum" is 1024x1024. This is because on boot-up, the computer detected your LVDS screen and reads "ideal resolution is 1024x768, so I will make the maximum drawable area be 1024x1024" This works for most people since they never tend to change their resolution.

However, once you reboot with the VGA plugged in, X detects that the maximum resolution is now "1280x768", and adjusts accordingly, to "1280x1280".

You can work around this problem by adding a line called "Virtual" in your xorg.conf file.

```
Section "Screen"
[INDENT]SubSection "Display"[/INDENT]
[INDENT][INDENT]Virtual 1280 1024[/INDENT][/INDENT]
[INDENT]EndSubsection[/INDENT]
EndSection





.

```

You'll run into similar problems when you try to make your TV an extended desktop, as your horizontal maximum is going to be 1280+1024, which is greater than the set or detected value, so you'll have to change the Virtual size to something like... 2304 1024.

---

