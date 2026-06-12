---
title: "Detecting screen resolutions with multiple displays"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Rob2687 on 2010-03-13
So here's my setup. Display 1 is a 1920x1200 LCD screen. Display 2 is a 1920x1080 HDTV. Display 1 is my primary display and display 2 is something I've hooked up once in a while to the PC for watching movies. This system has a Radeon x1900 which uses the open source ATI driver.

The multiple monitor support on Ubuntu has been quite frankly pretty iffy in previous releases but since Karmic and now Lucid things have been getting better. In Karmic if I had both screens plugged in at boot it would mirror the displays and pick a common resolution between the two. Usually the highest was something like 1280x1024 (with KMS). These are both wide screen LCD displays so anything other than the native resolution looks horrendous on them. That is just a boot screen so it's no big deal what resolution it's at. Now on the desktop it's the same problem as during boot except it's not usable at all with a resolution like that.

Flash forward to Lucid with the glorious KMS mode enabled by default. The 2D graphics performance is fantastic in Lucid and movie playback is quite smooth and flicker free so I decided to plug in the HDTV again.

The HDTV displays the Plymouth screen at it's native 1920x1080 and everything looks great on both displays. (I can't check the resolution Plymouth is using on Display 1 because the boot faster than I can navigate the monitors OSD menu. Near as I can tell it is either 1920x1200/1080). Now GDM comes up and it opts to drop down to 1024x768 in mirrored mode. Next the desktop loads on my primary display, I open gnome-display-properties and enabled mirrored mode. Low and behold the highest resolution available between the two monitors is only 1280x1024. The highest common resolution between the two should be 1920x1080.

For Display 1 in single mode the 1920x1080 is listed in gnome-display-properties. I check xrandr as well and my Display 1 shows a list of resolutions. For some reason that resolution is not listed in xrandr. So according to xrandr and gnome-display-properties the highest common resolution between the two displays in mirrored mode is indeed 1280x1024.
```

DVI-0 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 519mm x 324mm
   1920x1200      60.0*+
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1

DVI-1 connected (normal left inverted right x axis y axis)
   1920x1080      60.0 +
   1400x1050      60.0  
   1280x1024      60.0  
   1360x768       60.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   720x480        59.9  
   640x480        72.8     75.0     60.0  
   720x400        70.1    

```

I have tried running it with each display by itself and it uses the native res. from Plymouth to GDM to desktop for each display.

TLDR: I think there's 2 issues here. First GDM seems to take a super low res in mirrored mode for some reason. Second the screen resolutions aren't reading properly at the desktop when using clone/mirrored mode.

Is anyone else running into something similar when using multiple displays?

---

