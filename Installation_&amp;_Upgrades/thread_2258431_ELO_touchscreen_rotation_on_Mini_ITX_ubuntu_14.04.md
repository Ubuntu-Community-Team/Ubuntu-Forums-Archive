---
title: "ELO touchscreen rotation on Mini ITX ubuntu 14.04"
date: 2014-12-27
forum: Installation &amp; Upgrades
---

### Post by Art_Zito on 2014-12-27
I have run Ubuntu versions successfully with ELO touch screens, but having problems with this Mini ITX to get the screen rotated.  I have one Mini ITX that runs ubuntu 14.04 from a flash drive USB, and the ELO touchscreen 15" works fine in terms of calibration etc.  I have the same Mini ITX setup with a similar screen but in vertical orientation, and the usual command won't load:
xrandr --output VGA-0 --rotate right

maybe the problem is that I originally loaded it for a serial VGA 12" screen, and I deleted the ELO files and reinstalled but it still finds VGA-0

The setup that works runs VGA1

I've exhausted the searches for solutions.  There seems to be an additional issue running the ubuntu from the flash drive that the offered solutions can't account for.

Mini ITX
Ubuntu 14.04 form flash USB drive
ELO 15" vertical position

Thanks.

---

### Post by MAFoElffen on 2014-12-27
Use
```

xrandr -q

``` 
and look for the screen you are trying to use... then change your command from VGA-0 to the one (Name/ID) you are trying to rotate. xrandr is picky about that and uses it's own kind of Names/IDs. Those are also case sensitive.

---

### Post by Art_Zito on 2014-12-28
I have used xrandr -q and VGA-0 and LVDS1 are the only ones shown; LVSD1 will do nothing, whereas xrandr --ouptput VGA-0 --rotate right will result in a blank screen and I have to pull up the command and change to --rotate normal to restore.  So VGA-0 appears to be the device name.

---

### Post by Art_Zito on 2014-12-28
That's LVDS1, sorry for the typo.

---

### Post by MAFoElffen on 2014-12-28
That looks to be the correct syntax for that. The only suggestion I might have is to try it long-hand so it has less assumptions:
```

xrandr  --output  VGA-0 --auto --rotate right --pos 0x0 

```
Other than that, I don't know. It should have worked that way.

I know if it werein conjunction with another monitor (dual display), if you rotate one monitor, you have to say rotate for both, even if one is not turned... telling the unturned monitor to "--rotate normal".

---

### Post by Art_Zito on 2015-02-01
I'm just coming back to this: was working on other CPU boards for a long time.  I tried other monitors, and verified it is the Mini-ITX board because these other monitors will work with other CPU boards.  Maybe some interference of running the OS from a USB drive for this Mini-ITX.  When I try your long-hand command, I get the favor of avoiding the blank screen, but instead it blink and repositions the terminal window (as well as split in the display that does not appear to diminish function).  So clearly the right VGA-0 call but still not rotating the screen.  Seems like I'm close but still not victory.
Thanks.
Art

---

