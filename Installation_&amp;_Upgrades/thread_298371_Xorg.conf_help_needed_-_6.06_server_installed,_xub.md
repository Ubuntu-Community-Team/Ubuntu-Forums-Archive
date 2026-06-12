---
title: "Xorg.conf help needed - 6.06 server installed, xubuntu-desktop installed, no gdm"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by Brian Smith on 2006-11-12
I'm very close to a working GDM on this installation, I think.
I've been learning a lot searching forums and usinig the command line interface on this now installed Xubuntu 6.06 installation (on an oldworld Macintosh using Bootx) but when I used "gdm start," I got a blank screen and some hard drive activity, but no Xfce...

It looks like I may have 2 configuration problems, vrefresh and one other?

I had to break the log into 2 parts in order to upload it all to the forum.

Thanks for any help!

---

### Post by DaveBorealis on 2006-11-12
> **Brian Smith said:**
> I got a blank screen and some hard drive activity, but no Xfce...

There's a known bug effecting certain Macs, so you might be out of luck until they fix it.  Some machines, however, have a work around:

1) When you get the blank screen, wait a few minutes for the system to finish booting the destop, then 'Control-Option-F1' to bring up a console.

2)Backup '/etc/X11/xorg.conf' file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

3)  Get 'monitorname' and monitorrange'
```
 sudo ddcprobe
```

4)  Use 'monitorname' to match up with Identifier in '/etc/X11/xorg.conf'
```
sudo nano /etc/X11/xorg.conf
```
```
Secition "Monitor"
     Itentifier "Generic Monitor"
     Option "DPMS"
     HorizSync 60-60
     VertRefresh 43-127
EndSection
```

5) And use 'monitorrange to set 'HorizSync' and 'VertRefresh'.  They'll match up with monitorrange first and last respectively, e.g. 'monitorrange: 60-60, 43-127'

6) Restart X
```
sudo /etc/init.d/gdm restart
```
(Or replace gdm with kdm is using KDE.)

7)  If things are still messed up (or worse):
```
sudo mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```
Or  use the following to retrieve original settings:
        sudo dpkg-reconfigure -phigh  xserver-xorg
followed by another 'sudo /etc/init.d/gdm restart'

HTH,
Dave

---

### Post by Brian Smith on 2006-11-12
> **DaveBorealis said:**
> There's a known bug effecting certain Macs, so you might be out of luck until they fix it.  Some machines, however, have a work around:

1) When you get the blank screen, wait a few minutes for the system to finish booting the destop, then 'Control-Option-F1' to bring up a console.

2)Backup '/etc/X11/xorg.conf' file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

3)  Get 'monitorname' and monitorrange'
```
 sudo ddcprobe
```


ddcprobe is only giving me:

oem: ATY Mach64
memory: 6140kb
noedid

However:  When I use my monitor's hardware buttons, I can see that it is unchangeably set to 65Hz vrefresh, which is outside of what my Xorg.conf specified (60Hz maximum.)
I edited that Xorg.conf using sudo vi, saved it successfully with the range extended to 65Hz.
Unfortunately, it's still not working.

> **DaveBorealis said:**
> 

4)  Use 'monitorname' to match up with Identifier in '/etc/X11/xorg.conf'
```
sudo nano /etc/X11/xorg.conf
```
```
Secition "Monitor"
     Itentifier "Generic Monitor"
     Option "DPMS"
     HorizSync 60-60
     VertRefresh 43-127
EndSection
```

5) And use 'monitorrange to set 'HorizSync' and 'VertRefresh'.  They'll match up with monitorrange first and last respectively, e.g. 'monitorrange: 60-60, 43-127'

6) Restart X
```
sudo /etc/init.d/gdm restart
```
(Or replace gdm with kdm is using KDE.)

7)  If things are still messed up (or worse):
```
sudo mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```
Or  use the following to retrieve original settings:
        sudo dpkg-reconfigure -phigh  xserver-xorg
followed by another 'sudo /etc/init.d/gdm restart'

HTH,
Dave


That all makes sense.
Here's one additional caveat, which may help.
I booted back into Mac OS9.2, and saw that the only configuration that is available with this display adapter and monitor is 1152 x 870, 75Hz.
I don't see that one listed in the log as having been tried, though there are some other entries at 1152x870.

Maybe I could simply edit one the configurations in Xorg.conf to match that known working (for MacOS 9.2) configuration?

Thanks for the input!

---

### Post by Brian Smith on 2006-11-12
I've just tried using a different monitor, and doing a 
sudo dpkg-reconfigure xserver-xorg

Success!
The other monitor was a better unit, but I can better live with something more standard that actually is recognized.
Maybe a future project will be to find a working configuration for the other monitor, especially if any of that previous info I've given gives anybody here an idea of what to try.

I tried to look at this site to generate a custom modeline for the monitor at 75HZ and 1152 x 870.
I couldn't figure out how to do so.

[http://www.dkfz-heidelberg.de/spec/linux/modeline/](http://www.dkfz-heidelberg.de/spec/linux/modeline/)

Thanks for any further advice!
-Brian Smith

---

### Post by Brian Smith on 2006-11-13
:-k Hi again.
I'm attempting use that same monitor that gave me trouble (Dell E770s) on another system, using a fresh Xubuntu 6.10 installation.
Installation was succesfful, but when xfce is supposed to come up (after the splash, etc...) I have to resort again to the command line.
Here's a new Xorg.0.log and xorg.conf.  I used the instructions above, concerning the sudo ddcprobe command, and it appears that the .conf file does have, on this machine, the correct monitorname and monitorrange, but still it's not working properly.

Would someone advise me about this monitor and these files?

Thanks for any help!

---

### Post by DaveBorealis on 2006-11-19
Hello Brian,

I read over you attachments, and I've something else to try, but it's only a bit of a guess.  From the errors in the xorg logs, you seem to be trying monitor settings that your system can't handle.  So how about lowering the DefaultDepth and use some of the following combinations:

```

[FONT="Courier New"]..... Colour .... | ............. Resolution .................
..... Depth ..... | . 640x480 . 800x600 . 1024x768 . 1280x1024
--------------------------------------------------------------
256 ..... (8 bit) | ... 769 ..... 771 ...... 773 ...... 775
32768 ... (15bit) | ... 784 ..... 787 ...... 790 ...... 793
65536 ... (16bit) | ... 785 ..... 788 ...... 791 ...... 794
16.7M ... (24bit) | ... 786 ..... 789 ...... 792 ...... 795
[/FONT]
```

For instance:

> Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. 86c764/765 [Trio32/64/64V+]"
	Monitor		"DELL E770s"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection


Also, I got the above chart from the following thread:
[http://www.ubuntuforums.org/showthread.php?t=302556&page=2]("http://www.ubuntuforums.org/showthread.php?t=302556&page=2")
If the above suggestion doesn't help, read over the last two posts of the thread and try booting into vga (perhaps 791 like in the post) and see what happens.

---

### Post by Brian Smith on 2006-11-20
"Default depth 16" did the trick!
I'm still at 1024 x 768, which is fine.

I had previously tried the "VGA" boot option to no avail, perhaps I should have manually fed it "vga=(whatever it is, 791?)" but anyway, it's up and working, and I can experiment from here to find my favorite default settings.

Thanks so much, Dave, for finding me that detail.
This support community is excellent!

---

