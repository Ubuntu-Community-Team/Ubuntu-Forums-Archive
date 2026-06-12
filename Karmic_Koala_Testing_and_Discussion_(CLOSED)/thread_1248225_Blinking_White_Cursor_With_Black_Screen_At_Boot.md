---
title: "Blinking White Cursor With Black Screen At Boot"
date: 2009-08-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2009-08-23
I am using Kubuntu Karmic (64-bit) and I have a problem I'm trying to figure out. And I need some help. This may be a bug but before I report it, I thought I would check in here first.

Most of the time, my computer (specs in signature) boots to a black screen with a blinking white cursor, and that's it. I am able to SSH into it from another box, but as soon as I do, the terminal on the other box freezes before I can enter a command. ALT+CTRL+Backspace does nothing, neither does ALT+CTRL+DEL. With most Kubuntu installations, I could press the power button which tells the machine to shut down, and then it does. That doesn't work either. Unfortunately, I keep resetting my box until (eventually) I get a full X server and everything is good until the next time I boot. (This isn't a good practice, I know, but it's all I can do as far as I know).

Today I thought I would just wipe my hard drive and start over with Alpha 4. I figured that would probably fix it. Unfortunately, the live CD does this too! Same exact behavior!

I checked for updates today, and there were a bunch. I installed them all, and rebooted. This time, I got the same blinking white cursor with it freezing, but eventually (after five minutes) X does start, so I guess this problem is getting better with the updates.

The strangest thing is that there are no errors in my Xorg log. I can't even find a warning.

I am hoping someone has some insight in this or is already aware of this?

Thank you!

---

### Post by jerrylamos on 2009-08-24
I've had similar problems with 32 bit both intel video graphics and ati graphics.  I don't have 64 bit or nvidia.  I could suggest:

On initial grub menu, if installed, select recovery mode.  On recovery mode menu, down arrow to get root prompt
nano /etc/X11/xorg.conf
enter:
Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
Endsection
Ctrl-o
enter
Ctrl-x
resume boot
Maybe it will work....
There used to be a recovery mode option to do that automatically but some developer(s) decided to remove it.
Another way is to copy in a xorg.conf from a running image.

 You can do the same thing on CD Live by doing
on initial grub menu
e
down arrow to the linux line
replace "quiet splash" with "single"
Ctrl-x to continue boot
which boots to recovery mode menu then continue with above

At various times "vesa" works, sometimes it doesn't, sometimes it is faster than ati radeon drivers & intel drivers, certainly is with kms modeset=1...  Might be worth a try.

I don't know if nvidia is trying to boot in kms modeset=1.  
If it is, then on initial grub menu add
nomodeset
just after quiet 

Cheers...

Jerry

---

### Post by jlacroix on 2009-08-27
> **jerrylamos said:**
> I've had similar problems with 32 bit both intel video graphics and ati graphics.  I don't have 64 bit or nvidia.  I could suggest:

On initial grub menu, if installed, select recovery mode.  On recovery mode menu, down arrow to get root prompt
nano /etc/X11/xorg.conf
enter:
Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
Endsection
Ctrl-o
enter
Ctrl-x
resume boot
Maybe it will work....
There used to be a recovery mode option to do that automatically but some developer(s) decided to remove it.
Another way is to copy in a xorg.conf from a running image.

 You can do the same thing on CD Live by doing
on initial grub menu
e
down arrow to the linux line
replace "quiet splash" with "single"
Ctrl-x to continue boot
which boots to recovery mode menu then continue with above

At various times "vesa" works, sometimes it doesn't, sometimes it is faster than ati radeon drivers & intel drivers, certainly is with kms modeset=1...  Might be worth a try.

I don't know if nvidia is trying to boot in kms modeset=1.  
If it is, then on initial grub menu add
nomodeset
just after quiet 

Cheers...

Jerry

Thank you. I tried Vesa, and still no go. I have the blinking white cursor right now. The Live CD does the same thing. I tried to remove my hard drive thinking that it may be bad, but I had the same problem with the Live CD without the hard drive, and the hard drive and RAM passes all diagnostic tests...

Strangely enough I seem to be the only one with this problem, so perhaps not too many other Linux users use the same motherboard as I have?

---

### Post by jlacroix on 2009-08-31
Am I seriously the only one with this problem? I did more extensive testing on my hardware and it's all fine. The Jaunty Live CD boots perfectly, so this has to be a bug, right?

---

### Post by Bucky Ball on 2009-08-31
> I checked for updates today, and there were a bunch. I installed them all, and rebooted. This time, I got the same blinking white cursor with it freezing, but eventually (after five minutes) X does start, so I guess this problem is getting better with the updates.Correct. Karmic is testing. If you want stable then drop back to 8.04 (and 9.04 gets stabler all the time).

---

### Post by cariboo on 2009-08-31
Have you tried completely removing /etc/X11/xorg.conf, start in recovery mode and drop to a root prompt then type: 

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Next type exit and at the menu select resume. Once back at the desktop reinstall the restricted drivers.

---

### Post by jlacroix on 2009-09-01
First of all, before I get to the replies, let me point out that I was mistaken: My system does NOT start on its own if left alone. As of the time I am writing this, it will freeze 4 out of every 5 times I start it, and even waiting an hour will not start X.

> **Bucky Ball said:**
> Correct. Karmic is testing. If you want stable then drop back to 8.04 (and 9.04 gets stabler all the time).

No offense, but I really hope comments like those stop around here. I'm well aware that this is testing, which is why I clicked on " Karmic Koala **Testing** and Discussion" on my way in here. I never said I wanted stable and my intentions are to help test, which is what I am doing.

> **cariboo907 said:**
> Have you tried completely removing /etc/X11/xorg.conf, start in recovery mode and drop to a root prompt then type: 

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Next type exit and at the menu select resume. Once back at the desktop reinstall the restricted drivers.

Thank you for the suggestion, but that did not fix it. I am pretty sure that this is locking up before X is a factor, because when this happens, SSH will time out when I try to connect to this box, and TTY's do not work either. Usually when X fails I can operate "behind the scenes" but there are no behind the scenes because it isn't fully booted.

Recovery mode does not work either. Since my machine does come up one in five times, that's how I renamed the xorg.conf file.

Also, the Live CD does the same thing too, so reinstalling will not fix it.

Finally, the Jaunty live CD does work perfectly, so in my case it is a Karmic-specific issue.

Anything I might be able to provide that may help you guys help me? Maybe that will give me something to put in my bug report, other than "it doesn't boot".

Thanks!

---

### Post by CuddlyCombine on 2009-10-02
> **jlacroix said:**
> Am I seriously the only one with this problem? I did more extensive testing on my hardware and it's all fine. The Jaunty Live CD boots perfectly, so this has to be a bug, right?

I hate to necropost, but I've got the exact same problem with Karmic. The general formula (for me at least) is: 
1. computer working
2. shut down
3. unsuccessful boot attempt
4. force power off
5. successful boot
6. repeat

I'm no computer expert, but the above seems a bit wonky.

If it helps (and again, this may just be me), the Ubuntu login sound plays at the appropriate time (where it should when the computer boots properly) even if the screen is black with a blinking cursor. However, even when this happens, the keyboard is still unresponsive.

---

### Post by Mr.Crack on 2009-10-02
Ubuntu Newbie here, I have am currently running karmic on an nb205 Toshiba, and i have the same problem. My netbook will boot but the grub screen never shows...*confused*...it goes from blinking white cursor to the login window....Jaunty didnot used to do this...Any suggestions.

Thanks

---

### Post by kansasnoob on 2009-10-02
I don't really have an answer but as far as rebooting the next time try Right Alt > Sys Req (same as Print Screen) > B. A bit awkward at first I know.

I just start by pressing the Right Alt button with the side of my left thumb, then SysReq with my right hand, then while both are still depressed I press B with some finger on my left hand and usually after about 3 to 5 seconds the keyboard lights flash and the box will reboot.

The B of course is from REISUB:

[http://www.definition-of.com/REISUB](http://www.definition-of.com/REISUB)

It's easier on hardware.

As far as the root of the problem I'm clueless. I had the same problem with kernels -8 and -9 but both -10 and -11 have worked OK for me.

---

### Post by GoldNugget on 2009-10-02
Not sure if this is related to your problem but according to the beta release notes:

"Some users with Intel video chipsets will experience a black screen on reboot after install because the fbcon module is not being loaded. As a workaround, users can boot with the i915.modeset=0 option. Investigation of this issue is ongoing. (431812).."

[http://www.ubuntu.com/testing/karmic/beta](http://www.ubuntu.com/testing/karmic/beta)

---

### Post by HarshReality on 2009-10-04
Im just looking for a command line entry to force it to use vesa.. yes I am aware of the term 'beta'. Daily installed fine on my laptop (vaio VGN-NS375J) but my DT is using nv card(s)/chipset and the screen flickers like no tomorrow. I remember somewhere I could remove quiet and specify vesa for the dsriver but as I dont recall where it makes it a bit rough..

Suggestions (aside of a link to a bug report)?

RESOLVED:
Had to think.. added vga=792 to force 16bit 1024x768 to get into the live xsession ;) installing as we speak. This does NOT work however when booting into the system after the install and xorg.conf is nowhere to be found..
ARG!

UPDATE #2
A bit of detail into my machine.. Im running an internal nVidia chipset as well as a 9600 PCIe card.. now before to get all 3 screens to work I had to set the internal as the primary display. Ironically I couldnt even get into X using karmic. On a wild hunch I threw BIOS up as makng my PCIe card as my primary and *POOF* it works.. Now lets see if I can get the dual X going via Karmic!

---

