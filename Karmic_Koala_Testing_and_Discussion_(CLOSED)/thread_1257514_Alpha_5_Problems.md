---
title: "Alpha 5 Problems?"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by TheForkOfJustice on 2009-09-03
List your bugs and then head to Launchpad (which seems to be overloaded at the moment) to report each one.

- Grub2 did not list my other operating systems by default.  Had to do 'sudo update-grub' when I booted up Karmic.  
- System sound was at 0% when it should have been around 75%.  Essentially muted but the sound card was detected.
- Green 'noise' on my 1920x1080 LCD monitor (BENQ G2410HD) that appeared during the new boot screen and remained for a few minutes after going to desktop before vanishing.  It wasn't so thick that it blocked the desktop and I could still operate it.  I have an Nvidia 250GTS as my vid card and  have not rebooted to see if the drivers work yet.  Having the drivers installed may fix this irregularity. Or not. I'll find out soon.

Not exactly a bug, but there was a lot of boot text before the new boot screen appeared. It would be nice if usplash's behavior was copied and you only got the see the boot text if something was going wrong (or slow).

EDIT

Just rebooted to test the Nvidia drivers.  The green snow is gone and the bootup to screen was flawless. There wasn't even any boot text spam this time around.  Perhaps the first time was just Xorg configuring itself.

I've also had a few program crashes but they are being taken care of by the error reporter.

---

### Post by Merk42 on 2009-09-03
In the installation slideshow, there is a 'u' in "Color" when talking about F-Spot.  I'm in America!! :P

---

### Post by crimsun on 2009-09-03
Also, there are known crashers (#418448, #419658, #422451) in the version of PulseAudio shipped in Ubuntu Karmic Alpha 5. They have been fixed already; you should use the latest snapshot in the ~ubuntu-audio-dev PPA until it lands in Karmic proper.

There are two significant bugs remaining for Karmic, and those are

1) audio devices not being detected via module-udev-detect and
2) volumes not being restored properly across sessions.

Both are known to affect all distros shipping PulseAudio 0.9.16-test5+; we're working to resolve them.

---

### Post by ChrT on 2009-09-04
> **Merk42 said:**
> In the installation slideshow, there is a 'u' in "Color" when talking about F-Spot.  I'm in America!! :P

So choose the "American" localisation. "No localisation" or "English" defaults to, well, English.

---

### Post by ELD on 2009-09-04
Downloading ATM, hopefully this will actually boot up!

---

### Post by piotrekp on 2009-09-04
> **Merk42 said:**
> In the installation slideshow, there is a 'u' in "Color" when talking about F-Spot.  I'm in America!! :P
If You want to solve this "bug", You have to move to England. :D

---

### Post by KrazyPenguin on 2009-09-04
> **piotrekp said:**
> If You want to solve this "bug", You have to move to England. :D

.... or Canada, EH!!!!!

:P

---

### Post by moma on 2009-09-04
Hello,

Creative Labs' Audigy2 sound card is a bit spooky in Karmic.
Ref: [https://bugs.launchpad.net/ubuntu/+bug/400629](https://bugs.launchpad.net/ubuntu/+bug/400629)

ps. Android starter [guide.]("http://www.futuredesktop.org/developing_android_apps_on_ubuntu.html")

---

### Post by crimsun on 2009-09-04
> **moma said:**
> Hello,

Creative Labs' Audigy2 sound card is a bit spooky in Karmic.
Ref: [https://bugs.launchpad.net/ubuntu/+bug/400629](https://bugs.launchpad.net/ubuntu/+bug/400629)

ps. Android starter [guide.]("http://www.futuredesktop.org/developing_android_apps_on_ubuntu.html")

Your bug is incredibly difficult to resolve without regressing the users who need that mixer element to be _muted_. I've explained in the bug report.

---

### Post by drdabbles on 2009-09-04
I can not boot my Dell XPS system from the Alpha 5 live CD with an nVidia or ATI graphics card installed.

This is an issue, because I've tried to fix my system's graphics not working, and now I can't boot to edit the xorg.conf file.

If I could choose the "Rescue" option (Single User mode) from the grub 2 menu, none of this would be a problem. But there are no instructions about how to choose which kernel to boot.

These three issues are major regressions, and I'm trying to access the system to collect logs so I can report bugs...but of course there is no way for me to get in. Lovely.

---

### Post by forcecore on 2009-09-04
Kubuntu A5 has very slow Gdebi installer because it searches other needed dependencies long time, i tested it when i disabled software sources then it worked fast.

---

### Post by dudude on 2009-09-05
> **ChrT said:**
> So choose the "American" localisation. "No localisation" or "English" defaults to, well, English.

One of the first things asked of the user in the installer is their timezone and city/country.

This should mean that the slideshow could potentially be localized correctly since it is at the end of the installer.

Anyways, the slideshow is apparently not finished yet, as shown by the Pidgin slide even though Empathy is the current default IM client.

---

### Post by Piscium on 2009-09-06
I did not manage to install alpha 4 with either the Live CD or by doing “update-manager –d” on a Ubuntu 9.04.

So for alpha 5 I did something different, an alternate CD. The install went smoothly, there was no error message and nothing unexpected happened. 

There is however a major issue. About one to two minutes after I log in the screen freezes, and I have to power off the PC. This happened both times I logged in. I have no idea where the problem lies, if on xorg, gdm or intel graphics driver.

António

---

### Post by jerrylamos on 2009-09-06
> **Piscium said:**
> 

There is however a major issue. About one to two minutes after I log in the screen freezes, and I have to power off the PC. This happened both times I logged in. I have no idea where the problem lies, if on xorg, gdm or intel graphics driver.

António

Which video graphics do you have?  Try lspci | grep VGA.  I've i845 and i830 intel graphics both of which have fits with A5.  

With the IBM Thinkpad R31 i830 graphics finally got to a gdm screen by using the "install" option on the CD which doesn't use the intel driver, however after install I had to edit the boot line to add "nomodeset" and had to add an /etc/X11/xorg.conf (there wasn't any) to:
Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection

Boots to a graphic screen with top line icons, cursor, the whole bit however the cursor won't move and the keys don't do anything.  Dead.

Next step is to file an launchpad bug which involves boot in recovery, do:
apt-get install openssh-server
then after booting and getting the hang see if I can log in from another pc, gather /var/log/Xorg.0.log, .xsession-errors, dmesg, all that other documentation.

I could just go back to using A2 then from time to time in recovery on A5 do "fix broken packages" to see if ubuntu developers ever fix what they just broke.  Speaking of broken, the register backtrace tool on intel is broken for my pc's so isn't any help I'm told.

By the way, going back to A2, I had to edit A5's grub.cfg to add to the A2 linux line:
ro quiet splash
which were missing....so Grub is screwed up also.

Jerry

---

### Post by Piscium on 2009-09-06
> **jerrylamos said:**
> Which video graphics do you have?  Try lspci | grep VGA.  I've i845 and i830 intel graphics both of which have fits with A5.  

With the IBM Thinkpad R31 i830 graphics finally got to a gdm screen by using the "install" option on the CD which doesn't use the intel driver, however after install I had to edit the boot line to add "nomodeset" and had to add an /etc/X11/xorg.conf (there wasn't any) to:
Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection

Boots to a graphic screen with top line icons, cursor, the whole bit however the cursor won't move and the keys don't do anything.  Dead.

Next step is to file an launchpad bug which involves boot in recovery, do:
apt-get install openssh-server
then after booting and getting the hang see if I can log in from another pc, gather /var/log/Xorg.0.log, .xsession-errors, dmesg, all that other documentation.

I could just go back to using A2 then from time to time in recovery on A5 do "fix broken packages" to see if ubuntu developers ever fix what they just broke.  Speaking of broken, the register backtrace tool on intel is broken for my pc's so isn't any help I'm told.

By the way, going back to A2, I had to edit A5's grub.cfg to add to the A2 linux line:
ro quiet splash
which were missing....so Grub is screwed up also.

Jerry

I am booting into alpha 4 from my Ubuntu 9.04 partition which has Grub 1.96. There is no problem in the boot stage. For me Grub 1.96 has been 100% reliable.

To answer your question, when I ran "lspci | grep VGA" (on Ubuntu 9.04) I get:
VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

Today I made my third attempt to log into karmic alpha 4. The login went fine. Then after I got the Gnome desktop I went into System/Administration/Log File Viewer. I spent around 10 minutes looking at the various logs to find out if there was anything that looked suspicious. I found nothing, though I have very little experience with Linux. 

Then I closed the log viewer window, called the update manager, and when I clicked on the scrollbar to see the updates further down, the screen locked, just like the two times before. I had to power off the computer.

The problem is not with the update manager though, because the first time the screen froze I was organising the Firefox bookmarks.

António

---

### Post by retrow on 2009-09-08
I have an ATI Radeon card on my laptop. Things were fine until Alpha4. But the update to Alpha 4 (kernel 2.6.31.5 and onwards) makes the gdm screen go into a loop. It asks me for my login name and password. But once I specify the username and password, the screen then reverts back to login window. It keeps doing this in a loop. You can't drop to shell with Ctrl+Alt+F1 either. Hard reboot is the only option.

---

### Post by hgergo on 2009-09-08
I can't use since alpha3 the desktop efects with a2 livecd the normal mode its go ok but wit a5 with normal for exemple i open nautilus and when a move it the frame remains there. :(

---

### Post by taavikko on 2009-09-08
> **retrow said:**
> I have an ATI Radeon card on my laptop. Things were fine until Alpha4. But the update to Alpha 4 (kernel 2.6.31.5 and onwards) makes the gdm screen go into a loop. It asks me for my login name and password. But once I specify the username and password, the screen then reverts back to login window. It keeps doing this in a loop. You can't drop to shell with Ctrl+Alt+F1 either. Hard reboot is the only option.

[https://bugs.launchpad.net/bugs/419126](https://bugs.launchpad.net/bugs/419126)
At the moment, adding xorg-edgers PPA and disabling DRI is a work-around.

haven't tested fglrx will it work...

---

### Post by mike555 on 2009-09-08
Handbrake doesn't work , says "Internal error. Could not parse UI description"

---

### Post by n6yga on 2009-09-08
I installed A5 on a Dell 1405 laptop, replacing Jaunty, but KEEPING my home partition.

Everything went perfectly with the install and the only issues was no Windows partition in the first running of Grub2. However, after doing a "update-grub2" all partitions showed up and could be booted properly.

All-in-all, A5 is extremely stable on this laptop, where Jaunty was not at all. All compiz effects work perfectly and all video is very smooth.

Empathy is the only issue at the moment as I can't add a Yahoo account. No biggie because Pidgin seems MUCH improved and very stable. Why are we replacing Pidgin?

Good job, guys!

Mark.

---

### Post by Longinus00 on 2009-09-08
Changes I've noticed...

"Show icons in menus" is no longer enabled by default after a fresh install. Is this on purpose?

The downloads directory is named "Download" even though firefox is set up to use "Downloads". "Downloads" works better since the other directories in the home folder are all plural. It also wouldn't hurt if "Downloads" was linked like "Documents" and "Videos" are.

gedit is now called "gedit" instead of "Text Editor" in the applications menu. Intentional?

Pulseaudio also seems completely broken for me (totem crashes after playing wav files, constant pops) but when hasn't that been the case?

---

