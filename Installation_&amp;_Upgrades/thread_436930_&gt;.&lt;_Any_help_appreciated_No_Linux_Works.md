---
title: "&gt;.&lt; Any help appreciated: No Linux Works"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by theaceoffire on 2007-05-08
Ok, basics:

Hardware:
HP Pavilion a1120n
Original OS: Windows XP Media Center
Pentium 4 3.02 Ghz Processor
1536 MB of Ram
200GB 7200RPM SATA drive
LightScribe DVD+-Writer/CD+-Writer Disk Drive
Video Card: RADEON 9200 PRO

Operating Systems Attempted:
Gparted 2.3-0 Live CD ~ Failed (Kernel Panic, attempting to kill init)
Gparted 3.4-6 Live CD ~ Failed (Kernel Panic, attempting to kill init)
Ubuntu 7.04 Live CD ~ Failed (Freezes when loading hardware)
openSUSE 10.2 Live DVD ~ Failed (Cd:///?devices=/dev/hda,/dev/hdb 
~~~~~~~~~~~~~~~~ (Unknown Error: Unable to copy media directory to /var/tmp/TmpDir.XXXX/Media)
XP pro Corporate ~ Succeeded (WHY?)
XP home ~ Succeeded(GRR)
XP Media Center Recovery Disc ~ Succeeded (*sigh*)

^_^ I did FINALLY get Gparted and Ubuntu to load, but only by going into my bios and forcing it to use my on board video card...

O.o if I do not do that, my linux live cd's won't load, and my linux OS wont start...

Please, I want to be able to use my card, and my money is too tight to buy a new one...

If needed, I will find and tell any BIOS setting... Thanks for the help.

---

### Post by H.E. Pennypacker on 2007-05-08
I am inclined to believe there is a problem with your video card: Radeon 9200 Pro.

I don't have this card myself, but if I am not mistaken, many people have problems with this, and similar, card.

For a solution, try these threads:

[http://ubuntuforums.org/showthread.php?t=407908&highlight=RADEON+9200+PRO](http://ubuntuforums.org/showthread.php?t=407908&highlight=RADEON+9200+PRO)

[http://ubuntuforums.org/showthread.php?t=412138&highlight=RADEON+9200+PRO](http://ubuntuforums.org/showthread.php?t=412138&highlight=RADEON+9200+PRO)

That's all I could find for now, but try doing a forum search on this particular video card for any other solutions (if the above ones don't work).  Also, try searching the same card on google.com/linux.  It only searches Linux related websites.

Good luck.  If you have any other, unrelated, problems, please create a new thread instead of replying to this one.  Last, don't give up.

---

### Post by theaceoffire on 2007-05-14
OK, I got it going!

First, I changed in my bios the setting so that it booted from onboard rather than my pci video card ( which of course is radeon).

This let me install ubuntu, as well as get stuff started.

First thing first, type the following in to a terminal (Applications, Accessories, Terminal):
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
```

If ANYTHING goes wrong, you now have a backup, which you can restore by typing :
```
sudo cp /etc/X11/xorg.conf_bak /etc/X11/xorg.conf
```

After upgrading the original basics, I ran 
```
lspci | grep ATI
```

This game me this out put:
02:03.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
02:03.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)

Now, the /etc/X11/xorg.conf file only needs to know about the VGA compatible controller, and the name of mine is "ATI Technologies Inc RV280", and it can be found at PCI:2:3:0 (See above?)

So I just need to edit my xorg.conf file, and make it see my video card.

Open this with GEdit.
```
sudo gedit /etc/X11/xorg.conf
```

I went down to where it said :
> Section "Device"
	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

And put a "#" in front of each line to comment it out.

Then I copyed and pasted it, right below, to say this:

> #Section "Device"
#	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
#	Driver		"i810"
#	BusID		"PCI:0:2:0"
#EndSection
Section "Device"
	Identifier	"ATI Technologies Inc RV280"
	Driver		"vesa" #gonna change this later
	BusID		"PCI:2:3:0"
EndSection

I used the vesa for stabilities sake for now. I just wanted to verify it saw my card...

Of course, since I edited out my OLD video card, I couldn't just leave it's name laying around:
```

Section "Screen"
	Identifier	"Default Screen"
#	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Device 		"ATI Technologies Inc RV280"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```

So I commented out my old device and stuck in my test one.

I exited, saved, and pressed ctrl+alt+backspace to restartx.
> Other useful commands:
ctrl+alt+F1 to get to a command prompt
sudo startx to start the x server
sudo init 0 to turn it off at comamnd prompt
sudo cp /etc/X11/xorg.conf_bak /etc/X11/xorg.conf   (This uses the original, working config)
Tab (Auto completes where there is only one option, if it doesn't then you are typing something wrong)


Once I verified I had a working connection to my video card, I changed it as suggested by this tutorial:
[http://howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

> Other tutorials I used/saved/thought were neat:
Envy, automatically installs MOST ATI and NVIDIA drivers. Try this first. 
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Very nice one [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

[http://ubuntuforums.org/showthread.php?t=22496](http://ubuntuforums.org/showthread.php?t=22496)

ATI's driver search page (Choose linux) [http://ati.de/support/driver.html](http://ati.de/support/driver.html)

General multi boot how tos [http://wiki.osx86project.org/wiki/index.php/Installation_Guides#10.4.8_Guides](http://wiki.osx86project.org/wiki/index.php/Installation_Guides#10.4.8_Guides)

Tried to stop my video from stuttering using this [[COLOR="Red"]tut.[/COLOR]]("http://www.clipmarks.com/print_clips.aspx?mode=clip&print=true&c=28280FB2-D4CE-4204-8F7D-45D3988622CD&frame=doc")

Some more data here:
[http://wiki.serios.net/wiki/Debian_ATI_proprietary_display_driver_installation](http://wiki.serios.net/wiki/Debian_ATI_proprietary_display_driver_installation)

And finally:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Some performance threads, which I am gonna check out next.
[http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192)
[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)


NOW that  I have beryl going, I can tweak my video to work smoothly.... then fast. 

I hope that SOME of this makes someone else's trek into linux less painfull.

---

### Post by Sammi on 2007-05-16
@theaceoffire

That was beautiful. You really learned Linux fast. Salute!

---

