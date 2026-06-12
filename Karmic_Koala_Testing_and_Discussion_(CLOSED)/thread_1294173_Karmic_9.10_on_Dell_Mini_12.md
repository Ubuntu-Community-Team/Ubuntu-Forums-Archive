---
title: "Karmic 9.10 on Dell Mini 12"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by michael37 on 2009-10-18
LPIA version works very well, but is incredibly difficult to install.

UPDATE: I recently switched from LPIA to i386 release because LPIA is not going to be supported with Lucid.  I still prefer LPIA, but it's just not a workable long term solution.

[indent]I installed Karmic Alpha a month ago or so, and juts finished clean install of Karmic Beta.  I am running LPIA release, not i386 nor UNR (whcih is also i386), because [it saves 10%+ power]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_power_usage&num=1").  I also see little advantage for UNR interface compared to standard desktop interface since Mini 12 screen at its sharp 1280x800 resolution easily accommodates standard desktop GUI.[/indent]

*VERY* brief instructions:
1. i386: Download Ubuntu Desktop 32-bit from [http://ubuntu.com](http://ubuntu.com).  OR lpia (not recommended anymore): Download karmic-alternate-lpia.iso
2. Use usb-creator to create a USB image
3. Boot from USB and install whatever the software.  Wireless network, video and sound will not work as desired out of box.
4. Wireless: Enable universe repository and enable Broadcom STA wireless driver in Hardware Drivers.
5. Video: Use [script from this page]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/") to install psb video driver. 
6. Audio: Modify last line of /etc/modprobe.d/alsa-base.conf to read
options snd-hda-intel model=dell
instead of
options snd-hda-intel power_save=10 power_save_controller=N

UPDATE: 7. Fix brightness by following instructions in this post: [http://ubuntuforums.org/showpost.php?p=8860939&postcount=838](http://ubuntuforums.org/showpost.php?p=8860939&postcount=838) 

Optional enhancements.
1. Compiz works.  Enable psb driver in /usr/bin/compiz, but stability isn't great.
2. Skype works with audio and video.  My favorite is skype-mid version from archive.canonical.com partner repository.  In Settings, configure both sound output device and sound capture device to HDA Intel MID. Also, don't forget to right click on the Sound icon in top right corner, choose Sound Preference, select Input tab and unmute the microphone.

---

### Post by jetpeach on 2009-10-20
Just want to say THANKS! I will try this day after tomorrow when the release candidate comes out (which should be virtually identical to the final...)

---

### Post by Michael%S on 2009-10-25
I just did it, and it wasn't easy but it worked.
A few notes for those who want to try this:
-Installation doesn't "just work", it was kind of problematic, at least for me and for michael37. I had only a small number of the problems he describes in this other thread: [http://ubuntuforums.org/showthread.php?t=1293178](http://ubuntuforums.org/showthread.php?t=1293178)

-When installing the poulsbo graphics driver using lucazade's scripts, it seems only the ppa-based version works, at least for me. With the other script, I had an issue with architechture mismatch.

-It almost goes without saying that special function keys like the brightness adjustment fn combos won't just magically work, and these need to be set up manually as well.

---

### Post by michael37 on 2009-10-26
> **Michael%S said:**
> I just did it, and it wasn't easy but it worked.
A few notes for those who want to try this:
-Installation doesn't "just work", it was kind of problematic, at least for me and for michael37. I had only a small number of the problems he describes in this other thread: [http://ubuntuforums.org/showthread.php?t=1293178](http://ubuntuforums.org/showthread.php?t=1293178)

-When installing the poulsbo graphics driver using lucazade's scripts, it seems only the ppa-based version works, at least for me. With the other script, I had an issue with architechture mismatch.

-It almost goes without saying that special function keys like the brightness adjustment fn combos won't just magically work, and these need to be set up manually as well.

Hrm, I just noticed that my brightness adjustment fn combo doesn't work.. I just don't really use it.  All other fn combos work just fine (esp sound -- that's what I use).   How do you fix brightness adjustment?

---

### Post by Michael%S on 2009-10-26
Still working on it. I use it a lot. But I got exhausted and went to bed shortly after writing that post. :P

---

### Post by Michael%S on 2009-10-26
By the way, I noticed I can't tick the box in Software Sources for the security updates repo. Any idea why that is?

---

### Post by michael37 on 2009-10-26
> **Michael%S said:**
> By the way, I noticed I can't tick the box in Software Sources for the security updates repo. Any idea why that is?

No idea, but it's enabled in /etc/apt/sources.list, so not a problem.

---

### Post by Michael%S on 2009-10-26
Right you are.
I just ran a BIOS update to try to solve the brightness thing but it's no good. Apparently it's supposed to work over acpi, which is now a linux kernel thing (as of a while ago), but I have no idea how to fix it.

---

### Post by Michael%S on 2009-10-26
Okay, so here's what I've managed to figure out so far, although to no real results:
The Poulsbo module is supposed to let brightness be adjusted via files in /sys/class/backlight/ - but that folder is empty and doesn't let me create anything inside it (even as root).
None of the other locations where there is a file that is supposed to control brightness seem to exist in this installation right now.
If I can find the right place/file, it should be possible to create a script that adjusts brightness, as here: [http://mankikannan.blogspot.com/2008/01/more-linux-fun-screen-brightness.html](http://mankikannan.blogspot.com/2008/01/more-linux-fun-screen-brightness.html)

Anyone happen to have a Dellbuntu Mini on hand? I would be interested in how brightness adjustment is handled there, maybe we can find some clues...

---

### Post by Michael%S on 2009-10-26
I've decided to give it up for now because I have other stuff I want to do, but here's an old guide that might be relevant, this time using the HAL fdi policy files:
[http://www.berthon.eu/wiki/foss:ubuntu:wikishelf:hal:feisty](http://www.berthon.eu/wiki/foss:ubuntu:wikishelf:hal:feisty)
If someone finds a solution or gets some new information about the brightness thing, please post it here!

---

### Post by michael37 on 2009-10-27
> **Michael%S said:**
> Okay, so here's what I've managed to figure out so far, although to no real results:
The Poulsbo module is supposed to let brightness be adjusted via files in /sys/class/backlight/ - but that folder is empty and doesn't let me create anything inside it (even as root).
None of the other locations where there is a file that is supposed to control brightness seem to exist in this installation right now.
If I can find the right place/file, it should be possible to create a script that adjusts brightness, as here: [http://mankikannan.blogspot.com/2008/01/more-linux-fun-screen-brightness.html](http://mankikannan.blogspot.com/2008/01/more-linux-fun-screen-brightness.html)

Anyone happen to have a Dellbuntu Mini on hand? I would be interested in how brightness adjustment is handled there, maybe we can find some clues...

Dellbuntu Mini handles brightness via acpi.  It has functional /proc/acpi/video.  While the off-the-shelf script from [thread="4800605"]this thread[/thread] would not work on Dellbuntu 8.04, it can be easily customized to work (if it was actually necessary since Dellbuntu brightness keys just work).  

It looks like hardy acpi-support package contains lots of brightness-related stuff in /etc/acpi.  Karmic acpi-support does not.    Must be stuff changing.

---

### Post by michael37 on 2009-10-27
> **Michael%S said:**
> I've decided to give it up for now because I have other stuff I want to do, but here's an old guide that might be relevant, this time using the HAL fdi policy files:
[http://www.berthon.eu/wiki/foss:ubuntu:wikishelf:hal:feisty](http://www.berthon.eu/wiki/foss:ubuntu:wikishelf:hal:feisty)
If someone finds a solution or gets some new information about the brightness thing, please post it here!

In fact, this was very helpful!  

Hal in Jaunty has dell brightness stuff.  Here is file list:
[http://packages.ubuntu.com/jaunty/i386/hal/filelist](http://packages.ubuntu.com/jaunty/i386/hal/filelist)
Hal in Karmic does not.
[http://packages.ubuntu.com/karmic/i386/hal/filelist](http://packages.ubuntu.com/karmic/i386/hal/filelist)

---

### Post by Michael%S on 2009-10-27
So the question now is where Karmic actually deals with brightness. Let's hope the reason those different options don't work is because there's some super-effective unified system that Karmic uses to deal with all different possible brightness systems!

---

### Post by Michael%S on 2009-10-28
The package "xbacklight" from universe looked promising but doesn't seem to work. At least not right away.

---

### Post by Onesimus on 2009-10-28
I had a similar problem on my Dell Inspiron.  The work around I used was to add an applet to the top panel.  Simply right click on top panel, then 'add to panel' and select brightness applet.

This allowed me to adjust the brightness as required.  I would have liked to use the buttons, but I find I am not constantly altering the brightness so was able to live with it.

---

### Post by Michael%S on 2009-10-28
A few (potentially) related bugs:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/428054](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/428054)
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/438537](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/438537)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/406515](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/406515)

A different problem I've been having is that waking up from suspend (but not hybernate). The screen turns on but just shows all kinds of pretty colors instead of waking up. michael37, have you had any problems with that? I haven't been able to figure out any way to improve it so far.

---

### Post by Michael%S on 2009-10-28
> **Onesimus said:**
> I had a similar problem on my Dell Inspiron.  The work around I used was to add an applet to the top panel.  Simply right click on top panel, then 'add to panel' and select brightness applet.

This allowed me to adjust the brightness as required.  I would have liked to use the buttons, but I find I am not constantly altering the brightness so was able to live with it.
The applet doesn't work at all here. :(

---

### Post by michael37 on 2009-10-28
> **Michael%S said:**
> The applet doesn't work at all here. :(

Same.  Brightness applet (a part of gnome-power-manager) says "Cannot get laptop panel brightness".

Re: Onesimus, could you please check if there is anything in your /proc/acpi/video?

---

### Post by michael37 on 2009-10-28
> **Michael%S said:**
> 
A different problem I've been having is that waking up from suspend (but not hybernate). The screen turns on but just shows all kinds of pretty colors instead of waking up. michael37, have you had any problems with that? I haven't been able to figure out any way to improve it so far.

No, I haven't had this problem at all.  Ever since I my xorg.conf working and X stable, suspend works perfectly for me.  

Also, my computer doesn't ever hibernate.  It usually takes at least 30-45 seconds to wake up from hibernate.  That's too long for me.  I like Atom for that reason alone -- the computer can be in suspend mode for more than a day and then wake up in <5 seconds.

xorg.conf, [thread=1253406]source[/thread]
```

Section "Device"
        Identifier      "GMA500"
        Option 		"AccelMethod" "EXA"
        Option 		"MigrationHeuristic" "greedy"
        Option 		"IgnoreACPI" "yes"
        Driver 		"psb"
EndSection

Section "DRI"
    Mode    0666
EndSection

```

---

### Post by michael37 on 2009-10-28
OK, I got a clue from [here]("https://wiki.ubuntu.com/Hotkeys/Troubleshooting").  Given that acpi-support and hal are deprecated, it seems accurate that brightness key support was taken away from there.  So, udev is supposed to handle the keyboard and the associated events.  The remaining question is HOW.

Addon: After testing following the troubleshooting guide in the link above, I found that
xev doesn't record the Fn-F9/Fn-F10
neither does acpi-listen
lshal -m happily records the events (what does it do with them afterwards?)
09:19:08.944: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = brightness-down
09:19:11.899: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = brightness-up

---

### Post by Michael%S on 2009-10-28
My xorg.conf is identical. Still, I've only managed to resume from suspend a couple of times, mostly it fails. I wouldn't use hibernate either, but it's marginally better than shutting down completely and starting anew.

Speaking of which, startup is really slow since I installed Karmic. I did something I read somewhere to the grub config file (to disable checking the disk every time I start up) but startup is still at least a minute long. On Dellbuntu Hardy it was around a half minute. Hmpf.

---

### Post by Michael%S on 2009-10-28
A new clue for brightness: [http://dirk.net/2009/08/09/adjust-screen-brightness-in-ubuntu-via-xrandr/](http://dirk.net/2009/08/09/adjust-screen-brightness-in-ubuntu-via-xrandr/)
Didn't work for me, but might be worth checking out.

---

### Post by Onesimus on 2009-10-28
> **michael37 said:**
> Same.  Brightness applet (a part of gnome-power-manager) says "Cannot get laptop panel brightness".

Re: Onesimus, could you please check if there is anything in your /proc/acpi/video?

I have 3 directories here are the listings:

```
/proc/acpi/video/:
VID  VID1  VID2

/proc/acpi/video/VID:
CRT  DOS  DVI  info  LCD  POST  POST_info  ROM  TV

/proc/acpi/video/VID/CRT:
brightness  EDID  info  state

/proc/acpi/video/VID/DVI:
brightness  EDID  info  state

/proc/acpi/video/VID/LCD:
brightness  EDID  info  state

/proc/acpi/video/VID/TV:
brightness  EDID  info  state

/proc/acpi/video/VID1:
CRT  DOS  DVI  info  LCD  POST  POST_info  ROM  TV

/proc/acpi/video/VID1/CRT:
brightness  EDID  info  state

/proc/acpi/video/VID1/DVI:
brightness  EDID  info  state

/proc/acpi/video/VID1/LCD:
brightness  EDID  info  state

/proc/acpi/video/VID1/TV:
brightness  EDID  info  state

/proc/acpi/video/VID2:
DOS  info  POST  POST_info  ROM

```

However, all of the files are empty.

---

### Post by Michael%S on 2009-10-28
Thanks.
This should probably all go in a bug report, but I'm too lazy to file one and I'm not about to ask someone else to.

Anyway, another observation I've made is that on my Mini, the power manager also doesn't dim the screen anymore when going on battery power. In other words, it seems like there is no working interface for adjusting brightness at all. (It's not just about the buttons - although they are suspicious in the way they register via xev, etc.)

---

### Post by michael37 on 2009-10-28
> **Michael%S said:**
> Thanks.
This should probably all go in a bug report, but I'm too lazy to file one and I'm not about to ask someone else to.

Anyway, another observation I've made is that on my Mini, the power manager also doesn't dim the screen anymore when going on battery power. In other words, it seems like there is no working interface for adjusting brightness at all. (It's not just about the buttons - although they are suspicious in the way they register via xev, etc.)

Try to run commands
xset dpms off; sleep 5; xset dpms on

See if that works...

---

### Post by michael37 on 2009-10-28
> **Michael%S said:**
> My xorg.conf is identical. Still, I've only managed to resume from suspend a couple of times, mostly it fails. I wouldn't use hibernate either, but it's marginally better than shutting down completely and starting anew.

Speaking of which, startup is really slow since I installed Karmic. I did something I read somewhere to the grub config file (to disable checking the disk every time I start up) but startup is still at least a minute long. On Dellbuntu Hardy it was around a half minute. Hmpf.

Are u running compiz?  I noticed that 2D resumes fine, but 3D often has problems with resume.  

I switched to metacity and hadn't problems with suspend since.

---

### Post by michael37 on 2009-10-28
> **Onesimus said:**
> I have 3 directories here are the listings:


However, all of the files are empty.

I am totally confused.  Do you have the same Dell Mini 12 with the same Karmic and you have different configuration?  Or do you have another computer?

---

