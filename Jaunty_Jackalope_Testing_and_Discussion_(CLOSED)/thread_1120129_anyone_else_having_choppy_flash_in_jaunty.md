---
title: "anyone else having choppy flash in jaunty?"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2009-04-08
i have the latest flash (10.0 r22) installed and it is incredibly choppy since the upgrade to jaunty. on intrepid, i had the same flash and it ran "quick and nimble." if there are others out there, anyone have a clue where i can start my debugging?

---

### Post by gnomeuser on 2009-04-08
Things to start with perhaps would be observing the usage in top to see if anything else is suddenly jumping to the plate. Another thing would be collecting a log from pulseaudio by running it with the -vvvv option. This would reveal if you are hitting an ALSA bug which causes underruns. 

Aside that you can try:

sudo mkdir -p /etc/adobe/
sudo echo "OverrideGPUValidation=1">  /etc/adobe/mms.cfg

Though this is unsupported entirely, but it might smoothen  things out

---

### Post by ThrobbingBrain66 on 2009-04-08
I have the same problem, though it's only fullscreen flash with compiz enabled.  Flash works perfectly when metacity is running.

If you have an Intel graphics card you could try using [UXA]("https://wiki.ubuntu.com/X/UxaTesting").  Be aware that it can be very buggy depending on chipset.  It helps my flash/compiz issues but introduces a couple other bugs that keeps me from using it.

---

### Post by moore.bryan on 2009-04-08
> **gnomeuser said:**
> Things to start with perhaps would be observing the usage in top to see if anything else is suddenly jumping to the plate. Another thing would be collecting a log from pulseaudio by running it with the -vvvv option. This would reveal if you are hitting an ALSA bug which causes underruns. 

Aside that you can try:

sudo mkdir -p /etc/adobe/
sudo echo "OverrideGPUValidation=1">  /etc/adobe/mms.cfg

Though this is unsupported entirely, but it might smoothen  things out
thanks for the suggestions... nothing suddenly jumps, no alsa bug readily seen, no change with the mms.cfg "tweak."
> **ThrobbingBrain66 said:**
> I have the same problem, though it's only fullscreen flash with compiz enabled.  Flash works perfectly when metacity is running.

If you have an Intel graphics card you could try using [UXA]("https://wiki.ubuntu.com/X/UxaTesting").  Be aware that it can be very buggy depending on chipset.  It helps my flash/compiz issues but introduces a couple other bugs that keeps me from using it.
my problem is also with fullscreen flash and i do have compiz running. i'll check-out uxa and see if that changes anything. any insight into why the same version of flash would have issues from intrepid to jaunty?

---

### Post by Bakon Jarser on 2009-04-08
A quick search would have gotten you an answer to that question.

[http://ubuntuforums.org/search.php?searchid=57707897](http://ubuntuforums.org/search.php?searchid=57707897)

And probably led you to the bug report.

[https://bugs.launchpad.net/ubuntu/+bug/346289](https://bugs.launchpad.net/ubuntu/+bug/346289)

---

### Post by moore.bryan on 2009-04-08
> **Bakon Jarser said:**
> A quick search would have gotten you an answer to that question.

[http://ubuntuforums.org/search.php?searchid=57707897](http://ubuntuforums.org/search.php?searchid=57707897)

And probably led you to the bug report.

[https://bugs.launchpad.net/ubuntu/+bug/346289](https://bugs.launchpad.net/ubuntu/+bug/346289)
thanks, bakon jarser; did both the search and found the bug report... i was hoping someone had played with some settings and discovered a new avenue to a solution, other than just waiting for developers to fix it.

it would seem some changes i made to compiz and my xorg.conf file improved things a bit. when i opened my xorg.conf file, i found two lines under Section "Device" commented-out by recent upgrades:
```

Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"

```
I uncommented them, restarted, and saw less lag and choppiness, but still not what i was after. i then moved-on to my compiz settings. after firing-up the compizconfig settings manager, i unchecked "Unredirect Fullscreen Windows" under the "General" tab and unchecked the "Detect Refresh Rate" selection under "Display Settings;" i chose "67" for the new refresh rate. now, things are MUCH less choppy, but still not what they were under intrepid. i'm going to continue playing and report back.

---

### Post by Bakon Jarser on 2009-04-08
Some updates to flash-plugin-nonfree just came through for me a couple of minutes ago.  Maybe they will help.

Edit:  Just tried flash and it seems to be running much smoother now.

---

### Post by moore.bryan on 2009-04-08
> **Bakon Jarser said:**
> Some updates to flash-plugin-nonfree just came through for me a couple of minutes ago.  Maybe they will help.
i don't have flash-plugin-nonfree installed; i went straight to the source to get flash.

i can, however, report COMPLETE success with the uxa method previously mentioned, added to my xorg.conf and compiz settings changes. that's right, fullscreen flash in firefox on hulu, fancast, and youtube works FLAWLESSLY for me.

---

### Post by sports fan Matt on 2009-04-08
I'll try the uxa method, thanks for that!

---

### Post by moore.bryan on 2009-04-08
hope it works for you, too.

---

### Post by Nullack on 2009-04-08
Because linux has a broken video architecture if you use compiz, you wont get accelerated flash. Turn off compiz.

---

### Post by zaphodbblx on 2009-04-09
> **Nullack said:**
> Because linux has a broken video architecture if you use compiz, you wont get accelerated flash. Turn off compiz.

ok the problem is I am not useing compiz..any ideas for those of us who arnt?

---

### Post by raiwo on 2009-04-09
having similar problem & not using compiz. in 8.10 flash was as smooth as... well something that is smooth

---

### Post by moore.bryan on 2009-04-09
have you tried the uxa method mentioned above?

---

### Post by DarKnyht on 2009-04-09
I will try what was suggest above, but I have been having this issue since 9.04 Alpha 5 (that is when I switched).  

I think the bigger issue is that it doesn't matter if we can tweak under the hood to fix it, but that someone new to Ubuntu would look at this and say, "Flash doesn't work on Linux."  This is something that needs to be fixed before 9.04 goes out the door.  As others have said, this version of flash worked in 8.10 and it should work properly in 9.04.

---

### Post by Bakon Jarser on 2009-04-09
> **DarKnyht said:**
> I will try what was suggest above, but I have been having this issue since 9.04 Alpha 5 (that is when I switched).  

I think the bigger issue is that it doesn't matter if we can tweak under the hood to fix it, but that someone new to Ubuntu would look at this and say, "Flash doesn't work on Linux."  This is something that needs to be fixed before 9.04 goes out the door.  As others have said, this version of flash worked in 8.10 and it should work properly in 9.04.

That is why a bug report was filed.  If these fixes work for you please say so on the bug report so that the developers can make them part of 9.04.  This is the whole purpose of beta testing, so the noobs get to have a smooth ride. :p

---

### Post by moore.bryan on 2009-04-09
+1

---

### Post by DarKnyht on 2009-04-09
I have filed a bug report for this.  It got thrown into a bug report that had nothing to do with what I described.

Fortunately a different bug report was filed that described the problem, but so far the advice is to do the above despite it doesn't fix anything.

---

### Post by Nullack on 2009-04-09
Theres no way this will ever be fixed before release.

Canonical contributes little to the ecosystem in comparison to red hat, novell, intel and so on. This isnt a criticism - Im just pointing out that in terms of the real work in the ecosystem right now Ubuntu is quite a way down the list. I understand they are yet to make a profit and I fully appreciate why its where its at. Ubuntu is ofcourse my chosen distro and I put many many hours of my personal time into contributing.

The ecosystem needs to build in major fixes to the linux video architecture before this can be fixed in a complete way.

---

### Post by moore.bryan on 2009-04-10
are any of you guys (being generic, not sexist) using the Intel graphics driver testing ppa? ([https://launchpad.net/~intel-gfx-testing](https://launchpad.net/~intel-gfx-testing)) like i wrote above, the fixes i described COMPLETELY fixed my choppiness in flash fullscreen. i'm VERY interested to see if it's a semi-permanent fix.

---

### Post by chris lynn on 2009-04-13
i'd really like to try the xorg.conf fix, but i can't seem to find the file.  'whereis' states that it's in usr/lib/xorg but i can't seem to find it in nautilus...trying to edit it directly with nano in terminal created a blank xorg.conf...i have no idea what's going on here.

---

### Post by psyke83 on 2009-04-13
> **moore.bryan said:**
> are any of you guys (being generic, not sexist) using the Intel graphics driver testing ppa? ([https://launchpad.net/~intel-gfx-testing](https://launchpad.net/~intel-gfx-testing)) like i wrote above, the fixes i described COMPLETELY fixed my choppiness in flash fullscreen. i'm VERY interested to see if it's a semi-permanent fix.

No, because that repository has no packages targeted towards Jaunty. You probably meant this one: [https://launchpad.net/~xorg-edgers](https://launchpad.net/~xorg-edgers)

I still don't get good 2D performance until I enable UXA or enable the EXA tweaks (ExaOptimizeMigration and/or the "greedy" MigrationHeuristic).

A more serious problem is that Jaunty's Xorg doesn't set the MTRR ranges correctly for Intel (and probably other) cards. This causes stuttering for video-intensive operations such as movie playback in Totem.

Verbose lspci output for my card:

```
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
	Subsystem: Dell Device [1028:0164]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
	Latency: 0
	Interrupt: pin A routed to IRQ 11
**	Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]**
	Region 1: Memory at faf80000 (32-bit, non-prefetchable) [size=512K]
	Region 2: I/O ports at c000 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb
```


Here's my MTRR setup:
```
reg00: base=0x000000000 (    0MB), size=  512MB, count=1: write-back
reg01: base=0x020000000 (  512MB), size=  256MB, count=1: write-back
reg02: base=0x02ff00000 (  767MB), size=    1MB, count=1: uncachable
reg03: base=0x0feda0000 ( 4077MB), size=  128KB, count=1: write-through
```

Here's what it should be:

```
reg00: base=0x000000000 (    0MB), size=  512MB, count=1: write-back
reg01: base=0x020000000 (  512MB), size=  256MB, count=1: write-back
reg02: base=0x02ff00000 (  767MB), size=    1MB, count=1: uncachable
reg03: base=0x0feda0000 ( 4077MB), size=  128KB, count=1: write-through
**reg04: base=0x0f0000000 ( 3840MB), size=  128MB, count=1: write-combining**
```

Enabling the write-combining range allows Totem to play 720p content smoothly on an ancient 855GM chipset.

Here's the bug report: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928)

**N.B.** To see if you're affected, simply check your MTRR setup:
```
$ cat /proc/mtrr
```

If you don't see a range marked "write-combining", you're probably suffering from this bug as well.

---

### Post by chris lynn on 2009-04-13
forget my noob post on xorg...i found it where it's supposed to be, in x11 folder. anyway, adding the options mentioned did nothing, but my problem seems to be solved by simply removing gnash and swfdec. i supposed that forced firefox to actually use the adobe plugin.

---

### Post by sansa dude on 2009-04-13
i had choppy flash on intrepid but that seems to be all fixed in jaunty

---

### Post by moore.bryan on 2009-04-13
> **psyke83 said:**
> No, because that repository has no packages targeted towards Jaunty. You probably meant this one: [https://launchpad.net/~xorg-edgers]("https://launchpad.net/%7Exorg-edgers")

sorry, but there are jaunty packages
```
deb http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu jaunty main
```
i've been in regular contact with the maintainers for a while now on a completely unrelated problem.

---

### Post by psyke83 on 2009-04-13
> **moore.bryan said:**
> sorry, but there are jaunty packages
```
deb http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu jaunty main
```
i've been in regular contact with the maintainers for a while now on a completely unrelated problem.

I must be going blind, because I can only see packages for Hardy and Intrepid in that PPA; perhaps the Jaunty packages were recently deleted?

Nevertheless, the Xorg-Edgers PPA *does* have testing drivers for Jaunty.

---

### Post by moore.bryan on 2009-04-13
i don't think you're going blind... it doesn't seem as though they're listing jaunty; however, the packages are there.

---

### Post by davidmohammed on 2009-04-13
have also tried the UXA trick - without the UXA flash is unwatchable due to the low frame-rate.  With UXA - this works for a short time - approx 2-3 minutes before the frame-rate drops to make flash unwatchable.

Have noticed though, if I use the "CPU Frequency Scaling Monitor" and drop the speed of the laptop down to "power save" - the frame rate starts to speed up again after about 30 seconds.  Switching back to "performance" gives me the 2-3 minutes of good FPS full screen before the frame-rate drops again.

Weird!

---

### Post by collinp on 2009-04-13
Things like watching videos on YouTube are choppy until the video gets done loading, but that is more than likely a problem with my seriously old hardware than the code itself. Other than that, things are smooth.

---

### Post by Normad on 2009-04-14
I've had a weird experience with flash in Jaunty. 
When I first installed it about couple months ago, full screen flash perfomance was rather poor (I should point out that I had the same problems in Intrepid).
 
Then couple weeks ago, completely out of nowhere, I started getting windows-like flash performance. I was actually able to watch HD flash videos in full screen and my CPU was sitting at 80% idle. I'm not sure what was the cause. If memory serves, it happened when I installed the latest NVidia drivers (180.44).

And several days ago flash performance dropped again. The only reasonable explanation I can think of is that one the recent upgrades caused a degradation, since I haven't changed my configuration at all, besides minor gtk tweaks.
I wish I could rollback my system to the state with a working flash. I would never touch it again. Or at least I could figure what package is the culprit, but alas... :(

P.S.: Using E8300 & 9800gtx, no compiz, pure metacity. Flash from flashplugin-nonfree installer.

---

### Post by davidmohammed on 2009-04-14
I've got a similar issue at psyke83 - his trick did it for me - I've got onboard Intel Corporation 82852/855GM Integrated Graphics.

If anybody is interested in trying I found the following two useful links that I used to calculate the values to enter into the /proc/mtrr file
[http://www.mplayerhq.hu/DOCS/HTML/en/mtrr.html](http://www.mplayerhq.hu/DOCS/HTML/en/mtrr.html)
[http://www.cyberciti.biz/faq/howto-find-linux-vga-video-card-ram/](http://www.cyberciti.biz/faq/howto-find-linux-vga-video-card-ram/)

Anybody got any recommendations on the best way to tweak the /proc/mtrr file on startup of X?

---

### Post by crjackson on 2009-04-14
> **davidmohammed said:**
> I've got a similar issue at psyke83 - his trick did it for me - I've got onboard Intel Corporation 82852/855GM Integrated Graphics.

If anybody is interested in trying I found the following two useful links that I used to calculate the values to enter into the /proc/mtrr file
[http://www.mplayerhq.hu/DOCS/HTML/en/mtrr.html](http://www.mplayerhq.hu/DOCS/HTML/en/mtrr.html)
[http://www.cyberciti.biz/faq/howto-find-linux-vga-video-card-ram/](http://www.cyberciti.biz/faq/howto-find-linux-vga-video-card-ram/)

Anybody got any recommendations on the best way to tweak the /proc/mtrr file on startup of X?

Thanks for that. I'm sure many will find use in a few days.

---

### Post by Normad on 2009-04-14
It seems I just found out what was causing my problem.
The problem library was 'libglx'. Both xserver-xorg-core and nvidia driver have their own libglx.so and I was getting bad performance with native libgxl. I've reinstalled nvidia drivers and I'm back to happy days again.
I think I'll put xserver-xorg-core on hold until better solution arrives.

---

### Post by zaphodbblx on 2009-04-14
ok I did this:
sudo -s
echo "base=0xb0000000 size=0x10000000 type=write-combining" > /proc/mtrr

now I get this:

reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0bf700000 ( 3063MB), size=    1MB, count=1: uncachable
reg03: base=0x0bf800000 ( 3064MB), size=    8MB, count=1: uncachable
reg04: base=0x0bf600000 ( 3062MB), size=    1MB, count=1: uncachable
reg05: base=0x0d0000000 ( 3328MB), size=  256MB, count=1: write-combining

Its alot better but it still liks a bit gimpy to me(or perhaps Im seeing things)
But this isn't a permanent fix right?
 from what I'm reading you have to do this on every re-start! hope they fix this bug...it would be a deal breaker to a new switcher!
P.s> im one of those "dellbuntu" people with the onboard intell graphics


UPDATE 4/15/09
I cant get the fix to work today...when I put in the code that fixed it YESTERDAY I get this
bash: echo: write error: Invalid argument
WTF?

---

### Post by davidmohammed on 2009-04-15
wouldn't hold out for a fix in the near future given the imminent gold release... 

to answer my own question on how to run the echo... > /proc/mtrr command on login I did the following... if there was a more simple and obvious way please let me know!

1. in a terminal window create a file using your favourite text editor such as 'gedit' with your echo... > /proc/mtrr command and save this as /home/<user>/insertmtrr.  The file should have one line in it - your echo statement.
2. type the following
```
chmod +x ~/insertmtrr
```
3. test that the file does what you want by
```
sudo /home/<user>/insertmtrr
cat /proc/mtrr
```
4. create a file called .xinitrc with the following:
```
#!/bin/bash
if ! `cat /proc/mtrr | grep \"write-combining\"` ; then
  sudo /home/<user>/insertmtrr
fi

exec gnome-session
```
5. type the following:
```
ln -s ~/.xinitrc .xsession
```
6. type the following 
```
sudo -i
visudo
```
add the following on a new line after #Cmnd alias specification
```
Cmnd_Alias ADMIN_CMDS = /home/<user>/insertmtrr
```
add the following on a new line at the end of the file
```
ALL ALL=(ALL) NOPASSWD: ADMIN_CMDS
```
7. logout and login.

---

### Post by zaphodbblx on 2009-04-16
Im completely lost(big supprise heh!) on the echo command!   The temp fix shown before wont work for me anymore either
YELP!
Most likely a PEBKAC problem......


can anyone recommend a good book for getting a handle on these commands?

---

### Post by davidmohammed on 2009-04-16
If you 'lspci -v' what is your base value and memory size? ie. look for the line with "VGA Compatible Controller" and just below should be two lines containing a hex value and a MB value for the video card memory size.  the line you are interested in looks like
01:00.0 VGA compatible controller: Intel Integrated Graphics: Unknown device 0525
Memory at d0000000 (32-bit, prefetchable) [size=128M]
what does your /proc/mtrr look like before you do the echo command?

---

### Post by zaphodbblx on 2009-04-16
> **davidmohammed said:**
> If you 'lspci -v' what is your base value and memory size? ie. look for the line with "VGA Compatible Controller" and just below should be two lines containing a hex value and a MB value for the video card memory size.  the line you are interested in looks like
01:00.0 VGA compatible controller: Intel Integrated Graphics: Unknown device 0525
Memory at d0000000 (32-bit, prefetchable) [size=128M]
what does your /proc/mtrr look like before you do the echo command?
Ok I'm gonna assume that this is for me so here goes!


00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
	Subsystem: Dell Device 020d
	Flags: bus master, fast devsel, latency 0, IRQ 2301
	Memory at fdf00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ff00 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at fdb00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>



/proc/mtr

reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0bf700000 ( 3063MB), size=    1MB, count=1: uncachable
reg03: base=0x0bf800000 ( 3064MB), size=    8MB, count=1: uncachable
reg04: base=0x0bf600000 ( 3062MB), size=    1MB, count=1: uncachable

as ive stated before I applied the temp fix

sudo -s
echo "base=0xb0000000 size=0x10000000 type=write-combining" > /proc/mtrr
and it worked fine ONCE
now this is all I get:


<myname>@dell-desktop:~$ sudo -s
root@dell-desktop:~# echo "base=0xb0000000 size=0x10000000 type=write-combining" > /proc/mtrr
bash: echo: write error: Invalid argument

any one heard from the dellbuntu team on this?

---

### Post by wsonar on 2009-04-16
I got nothing  sorry

mine has been working fine

---

### Post by davidmohammed on 2009-04-16
I assume you meant d instead of b in your echo statement as in...

echo "base=0x**_d_**0000000 size=0x10000000 type=write-combining" > /proc/mtrr

as to your write error, looks like some sort of kernel lock.

I presume you ls -l on /proc/mtrr looks like this
-rw-r--r-- 1 root root 0 2009-04-16 21:32 /proc/mtrr

also could you try suffixing with 2>/dev/null
i.e echo "base=0x**_d_**0000000 size=0x10000000 type=write-combining" > /proc/mtrr 2>/dev/null

---

### Post by davidmohammed on 2009-04-16
...alternatively - could you try a smaller 'size' e.g.
echo "base=0xd0000000 size=0x1000000 type=write-combining" > /proc/mtrr

... possibly a bug in the kernel that doesn't like 256M in hex.

---

### Post by platykurtic on 2009-04-17
I was getting choppy flash on my eeepc using the netbook remix thing. youtube was alright, but the daily show and hulu were running at about 1 fps. the uxa trick fixed this alright, but now the whole netbook remix interface is running super-slow, which I can live with, but is dissapointing

---

### Post by Rabidmonkey1 on 2009-04-18
Sense. This thread makes none. 

I too am getting the Flash playback error, but I've read through the thread and have no idea how to begin approaching a fix... This is really bad form for Ubuntu so close to a final release.

Should I install the Intel Gfx testing PPA and hope for the best?

Should I be editing various config files?

Or should I just wait and hope the issue gets fixed by the time the release is finalized?

---

### Post by Confuseling on 2009-04-20
Can anyone help a confused person? I've got dynamic video RAM allocation, and I'd like to try out the MTRR setting, but really don't know how much I should set it to.

Any hints? Which region am I supposed to be looking at?

lspci -vv
```

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 830f
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 830f
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f7f00000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at dc80 [size=8]
	Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at f7ec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 830f
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at f7f80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

```

---

### Post by davidmohammed on 2009-04-20
suggest this bit
Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]

with something like

echo "base=0xd0000000 size=0x10000000 type=write-combining" > /proc/mtrr
 

it would be interesting if you get the same "write failure" as zaphodbblx

---

### Post by Confuseling on 2009-04-20
Thanks for the swift response.

Just echoing that line responded with a 'Permission denied', but placing it in a file then chmoding and executing it seems to have worked.

```

cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable
reg02: base=0x0d0000000 ( 3328MB), size=  256MB, count=1: write-combining

```

I'm not noticing a marked increase in performance - do I need to set that up as part of the initialisation of X, as per your instructions earlier in the thread, in order for it to take effect?

---

### Post by davidmohammed on 2009-04-20
seems to work in combination - have you amended your xorg.conf to include the "UXA" or "greedy" options?

Remember, each time you restart, you'll loose the mtrr setting.

I would test by amending your xorg.conf with UXA/greedy and when logged in amend your mtrr setting.  Then watch a youtube flash video at full screen at both standard and HQ quality settings.

When you've got the correct xorg.conf then you may want to think about amending your mtrr file automatically on startup of X.

---

### Post by rajeev1204 on 2009-04-20
Can anyone give me a link to the older version of flash 64 alpha?

It seemed to work very well.Newer alpha is as bad as any release version,

Or is it really a jaunty problem and a newer alpha never came out??

---

### Post by krazyd on 2009-04-20
> **Rabidmonkey1 said:**
> Sense. This thread makes none. 

I too am getting the Flash playback error, but I've read through the thread and have no idea how to begin approaching a fix... This is really bad form for Ubuntu so close to a final release.

Should I install the Intel Gfx testing PPA and hope for the best?

Should I be editing various config files?

Or should I just wait and hope the issue gets fixed by the time the release is finalized?
The root of this problem is that Adobe's flash player is a closed-source binary blob. We can guess at what it's doing, and play around with driver settings, system configs etc. but really it's just a black box.

This makes it difficult to do anything about bugs. In fact, there's not much to be done besides wait for Adobe to fix their stuff.

In the meantime, why not try out [Gnash]("http://www.gnu.org/software/gnash/") or [Swfdec]("http://swfdec.freedesktop.org/wiki/") and report the bugs you find?:D

---

### Post by stewacide on 2009-04-20
Getting UXA working with the 2.6.30rc2 kernel and bleeding-edge Intel drivers has made flash video watchable again for me. Where before a YouTube video would consume 100% of CPU time and still skip and tear badly, now it's down to ~30% and plays smoothly without tearing.

---

### Post by wfp on 2009-04-20
Having the same problem with choppy flash on full screen. Processors are set to on-demand if I boost them up to 1.8Ghz everything plays fine. Also wanted to add that compiz would cause desktop to lock-up constantly, but after setting cpu to 1.8Ghz I have had no lock ups. If I set my cpu back to on-demand desktop locks up right away and can not play flash full screen

---

### Post by carrozza on 2009-04-21
I'm sad to say that Flash issues is the only reason I'm sticking with Windows XP.

That's unbelievable: I managed to work out my company's ERP software, various graphic programs, Lotus Notes e-mail... and now I'm blocked because of this so basic but important feature! :(

---

### Post by zaphodbblx on 2009-04-21
ok I've figured out what i had going on with the on the echo command (echo "base=0xe0000000 size=0x10000000 type=write-combining" > /proc/mtrr)..now how do I make it persistant?
I see the step by step davidmohammed posted but im not sure how to make the file ...do i just run the echo command with the additions(/home/myname/)
Lame? yes I know but we dont want to fracture my baby!

---

### Post by davidmohammed on 2009-04-21
zaphodbblx... create a file using any text editor such as gedit...

also I'm curious - your lspci -vv in an earlier post reported a base=0xd0000000 but you are now using base=0xe0000000 - how did you arrive at that?

---

### Post by zaphodbblx on 2009-04-21
> **davidmohammed said:**
> zaphodbblx... does post#35 work for you?

also I'm curious - your lspci -vv in an earlier post reported a base=0xd0000000 but you are now using base=0xe0000000 - how did you arrive at that?
I think  my "fixes"  got confused.....anyhow I just ran :

sudo s-
echo "base=0xe0000000 size=0x10000000 type=write-combining" > /proc/mtrr


and I get

cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0bf700000 ( 3063MB), size=    1MB, count=1: uncachable
reg03: base=0x0bf800000 ( 3064MB), size=    8MB, count=1: uncachable
reg04: base=0x0bf600000 ( 3062MB), size=    1MB, count=1: uncachable
reg05: base=0x0e0000000 ( 3584MB), size=  256MB, count=1: write-combining


which shows this if I "lspci -vv"

0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
	Subsystem: Dell Device 020d
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 2301
	Region 0: Memory at fdf00000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at ff00 [size=8]
	Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at fdb00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>


but I still have choppy flash...I did set my onboard card back to its default setting though(256 mb)

as for post #35
I don't know im still stuck on the first part do I do this to make the file?
sudo s-
echo "base=0xe0000000 size=0x10000000 type=write-combining" > /proc/mtrr/home/<user>/insertmtrr ?

---

### Post by davidmohammed on 2009-04-21
from a terminal window
type 'gedit'

copy and paste one line into the file

echo "base=0xe0000000 size=0x10000000 type=write-combining" > /proc/mtrr

... however before you do that your lspci region 2 says d0000000 but you are using e0000000.  How did you arrive at e0000000

Also - in your xorg.conf are you using UXA or greedy options?

---

### Post by zaphodbblx on 2009-04-21
> **davidmohammed said:**
> from a terminal window
type 'gedit'

copy and paste one line into the file

echo "base=0xe0000000 size=0x10000000 type=write-combining" > /proc/mtrr

... however before you do that your lspci region 2 says d0000000 but you are using e0000000.  How did you arrive at e0000000

Also - in your xorg.conf are you using UXA or greedy options?


david I havent a clue...really
how do I access the xorg.conf?

is this waht your looking for?
brian@dell-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280
VGA connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0     60.0* 
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1

---

### Post by davidmohammed on 2009-04-21
Sorry to divert you off - you might want to have a look at the following [wiki]("https://wiki.kubuntu.org/X/Troubleshooting/IntelPerformance")

... your xorg.conf is in /etc/X11/xorg.conf

edit with
sudo gedit /etc/X11/xorg.conf

---

### Post by DarKnyht on 2009-04-21
> **krazyd said:**
> The root of this problem is that Adobe's flash player is a closed-source binary blob. We can guess at what it's doing, and play around with driver settings, system configs etc. but really it's just a black box.

This makes it difficult to do anything about bugs. In fact, there's not much to be done besides wait for Adobe to fix their stuff.

In the meantime, why not try out [Gnash]("http://www.gnu.org/software/gnash/") or [Swfdec]("http://swfdec.freedesktop.org/wiki/") and report the bugs you find?:D

The problem with that thinking is that their blob hasn't changed since 8.04.  The blob worked in 8.10, so it is something that changed in 9.04.  If you track when the problem started you probably will get an idea what caused it, but I do not think it was the flash binary.

More importantly, flash works everywhere else in the Linux world.  A new user isn't going to blame flash for the problem, they are going to blame Ubuntu.  So it might not be Ubuntu's fault, but it definately is their problem.

---

### Post by stewacide on 2009-04-21
> **DarKnyht said:**
> The problem with that thinking is that their blob hasn't changed since 8.04.  The blob worked in 8.10, so it is something that changed in 9.04.  If you track when the problem started you probably will get an idea what caused it, but I do not think it was the flash binary.

More importantly, flash works everywhere else in the Linux world.  A new user isn't going to blame flash for the problem, they are going to blame Ubuntu.  So it might not be Ubuntu's fault, but it definately is their problem.

Agreed. Flash worked fine with Hardy and Intrepid, and if my experience testing bleeding-edge drivers and kernel is an indication it will be fixed in Karmic, but as things stand the shipping Jaunty is a diaster, and will drive Ubuntu users away in droves when the UI becomes unbearable laggy and their YouTube stops working.

re: Intel drivers (the apparent source of most of these problems), why not just keep shipping the old dependable (2.4) drivers with all systems they support? I understand that means two driver branches for Jaunty (one for systems supported by the old drivers, and one for the newest configurations supported only by the latest drivers), but they can be merged back together for Karmic.

---

### Post by Mercury_Alpha on 2009-04-21
I'm getting the same problem with my Radeon x1500 (AGP) and the generic drivers, so I don't think it's an Intel issue. Some Flash does play smoothly, but the bulk of it is unwatchable.

Furthermore, switching to Gnash does not solve the problem. Instead of being choppy, the Flash video *does not load at all*.

Doesn't matter if Compiz is enabled or disabled. And I know it's not my system. I have an Athlon 64 4000+ and 4GB of RAM. Flash played smooth as butter in 8.04 and 8.10.

:(

---

### Post by Nullack on 2009-04-21
You cant reasonably expect gnash at this point of its life to compete with Adobe.

---

### Post by rajeev1204 on 2009-04-22
You guys should try swfdec.Its much better.In the repos too.

---

### Post by Confuseling on 2009-04-22
> **davidmohammed said:**
> seems to work in combination - have you amended your xorg.conf to include the "UXA" or "greedy" options?

Remember, each time you restart, you'll loose the mtrr setting.

I would test by amending your xorg.conf with UXA/greedy and when logged in amend your mtrr setting.  Then watch a youtube flash video at full screen at both standard and HQ quality settings.

When you've got the correct xorg.conf then you may want to think about amending your mtrr file automatically on startup of X.

Thanks for this advice - I haven't actually gone through systematically yet, but just wanted to say cheers before the forum vanishes.

Enjoy Jaunty, eh? :P

---

