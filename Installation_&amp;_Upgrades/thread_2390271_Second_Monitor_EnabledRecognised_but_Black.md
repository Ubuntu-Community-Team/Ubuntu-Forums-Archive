---
title: "Second Monitor Enabled/Recognised but Black"
date: 2018-04-27
forum: Installation &amp; Upgrades
---

### Post by craige2 on 2018-04-27
Hello guys,

I just made a clean install with Kubuntu 18.04 on AMD R9 380X and system is fully updated.

The second monitor is recognised and enabled but remains black.

Power settings are set to never turn off monitors.

I see the bios screen when the PC boots, as soon as I get at the login screen the second monitor goes to Power Saving Mode.

Below is my xrandr.

```

[FONT=monospace][COLOR=#000000]Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 16384 x 16384[/COLOR]
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
HDMI-A-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080     60.00*+  50.00    59.94   
   1680x1050     59.88   
   1600x900      60.00   
   1280x1024     75.02    60.02   
   1440x900      59.90   
   1280x800      59.91   
   1152x864      75.00   
   1280x720      60.00    50.00    59.94   
   1024x768      75.03    70.07    60.00   
   832x624       74.55   
   800x600       72.19    75.00    60.32    56.25   
   720x576       50.00   
   720x480       60.00    59.94   
   640x480       75.00    72.81    66.67    60.00    59.94   
   720x400       70.08   
DVI-D-0 disconnected (normal left inverted right x axis y axis)
DVI-D-1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 477mm x 269mm
   1920x1080     59.93*+  60.00   
   1680x1050     59.95   
   1280x1024     75.02    60.02   
   1440x900      59.93   
   1280x960      75.04   
   1280x800      59.93   
   1152x864      75.00   
   1280x720      75.02   
   1024x768      75.03    60.00   
   800x600       75.00    60.32   
   640x480       75.00    59.94   
   720x400       70.08  

[/FONT]
```

[FONT=monospace]HDMI-A-0 is my primary.

[/FONT]DVI-D-1 is the blacked out.

The applications like firefox, open at the black screen and I have to drag them into the active monitor.

What I have done so far:
1) Disconnect the second monitor and reboot. Connect it again and issue remains
2) I ran 
[FONT=monospace][COLOR=#000000]xrandr --output DVI-D-0 --auto
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]xrandr --output DVI-D-1 --auto
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]xrandr --output DVI-D-1 --auto --right-of HDMI-A-0
[/COLOR]and issue remains.
[/FONT][FONT=monospace]

[/FONT][FONT=monospace]Many thanks.


[B]UPDATE:
[/B]I connected my laptop to monitor and it is working.
I tried to disable the blacked out monitor from the Displays menu and both monitors were inaccessible after. Reboot got me to black screen with no terminal mode access. I had to make a new install (new ISO image) and the issue remains.[/FONT]

---

