---
title: "Laptop won't boot live USB"
date: 2020-07-11
forum: Installation &amp; Upgrades
---

### Post by rickseiden on 2020-07-11
Hello,

My laptop won't boot 20.04 (or any other version I've tried) from a live USB stick made according to the official Ubuntu instructions.  And it's not just Ubuntu, it's any Linux distro that isn't incredibly stripped down, like TinyCore.

It's an HP Envy m6-p114dx.  Its processor is an AMD FX-8800P Radeon R7, which I know causes issues because AMD requires proprietary, non-open drivers that I'm not going to find on a live USB stick. 

I get to the GRUB menu just fine (after turning on Legacy and turning off Secure boot).  I tried normal Ubuntu and Ubuntu safe graphics, and they both hang.  I've tried editing the launch of both the options in GRUB to ad radeon.modeset=0.

What I end up with is either the word Ubuntu at the bottom of my screen with a progress wheel spinning above it, or the text output of the boot process that just stops and doesn't go any further.

That's not even a start at what I need to supply to get help for my issue, I know.  But I don't know how to get logs of the startup, or any other information that is needed.  So, I'm not asking for help to diagnose my problem, yet.  I'm asking for help gathering information that people need to help diagnose my problem.  Specifically, how can I get a log of the boot process?  There's got to be something in there that is useful.

I've tried adding debug= to the end of the launch of both GRUB options, by the way, and did not find anything on the USB stick, even with a persistent partition.

Thanks in advance for you understanding and help,

Rick

---

### Post by jp734 on 2020-07-12
Did you check the md5sum of the downloaded iso to make sure you have a good copy? You might just need to re-download and recreate a live usb.

---

### Post by mastablasta on 2020-07-13
> **rickseiden said:**
> 
It's an HP Envy m6-p114dx.  Its processor is an AMD FX-8800P Radeon R7, which I know causes issues because AMD requires proprietary, non-open drivers that I'm not going to find on a live USB stick. 


they are all in kernel now, no proprietary ones (well the AMDGPU-pro is not actually needed)


> 
I get to the GRUB menu just fine (after turning on Legacy and turning off Secure boot).  I tried normal Ubuntu and Ubuntu safe graphics, and they both hang.  I've tried editing the launch of both the options in GRUB to ad radeon.modeset=0.


what boot options have you tried? if you suspect you need to later load additional drivers then have you used the nomodeset kernel option? : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Replacing quiet splash with text should show up text, so you can maybe see where it get's stuck. Additionally you can press "Esc" when loading screen appears or should appear to see if any error messages go up on the screen:
[https://askubuntu.com/questions/1024895/why-do-i-need-to-replace-quiet-splash-with-nomodeset](https://askubuntu.com/questions/1024895/why-do-i-need-to-replace-quiet-splash-with-nomodeset)


try pressing crtl+alt+F2 to drop to console. maybe it booted, but GUI has not. then you can investigate the dmesg log (you can use ">" to create a text file.
for example
```
dmesg > dmesg.txt
```


you can also boot to console using recovery mode:
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
[https://askubuntu.com/questions/859630/how-to-start-ubuntu-in-console-mode](https://askubuntu.com/questions/859630/how-to-start-ubuntu-in-console-mode)



also my recent experience with AMD and HP taught me i have to have charger plugged in on boot.  so try that as well if you haven't already.

---

### Post by rickseiden on 2020-07-13
> **jp734 said:**
> Did you check the md5sum of the downloaded iso to make sure you have a good copy? You might just need to re-download and recreate a live usb.

Thank you for your reply.  I have checked, and the download is good. I also checked the USB drive that it was written to on another laptop, and it booted in legacy mode, no problem.

---

### Post by rickseiden on 2020-07-13
Thanks for your reply.  There's a lot there.  Let me try to get it one at a time.

> **mastablasta said:**
> they are all in kernel now, no proprietary ones (well the AMDGPU-pro is not actually needed)



what boot options have you tried? if you suspect you need to later load additional drivers then have you used the nomodeset kernel option? : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


First I tried just booting using the base Ubuntu option in the GRUB menu. Then I tried the safe graphics option in the GRUB menu.  Then I tried removing quite splash and adding nomodeset to the base Ubuntu option. Then I tried adding radeion.modeset=0.

> **mastablasta said:**
> 
Replacing quiet splash with text should show up text, so you can maybe see where it get's stuck. Additionally you can press "Esc" when loading screen appears or should appear to see if any error messages go up on the screen:
[https://askubuntu.com/questions/1024895/why-do-i-need-to-replace-quiet-splash-with-nomodeset](https://askubuntu.com/questions/1024895/why-do-i-need-to-replace-quiet-splash-with-nomodeset)


That's why I'm hoping to get a log of what went on during boot.  Too much goes by for me to even begin to look at while it's booting.  And, I can't get that information off my screen and into a forum post to say, "Here's what's happening."  But I'll check out that link and see if there's anything in there I haven't tried, and try it.

> **mastablasta said:**
> try pressing crtl+alt+F2 to drop to console. maybe it booted, but GUI has not. then you can investigate the dmesg log (you can use ">" to create a text file.
for example
```
dmesg > dmesg.txt
```


you can also boot to console using recovery mode:
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
[https://askubuntu.com/questions/859630/how-to-start-ubuntu-in-console-mode](https://askubuntu.com/questions/859630/how-to-start-ubuntu-in-console-mode)



I'll give those a try and report back.

> **mastablasta said:**
> also my recent experience with AMD and HP taught me i have to have charger plugged in on boot.  so try that as well if you haven't already.

It was plugged in at the time.

Thanks again.

---

### Post by rickseiden on 2020-07-13
OK.  I've tried the recovery mode and console mode links:

> **mastablasta said:**
> you can also boot to console using recovery mode:
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
[https://askubuntu.com/questions/859630/how-to-start-ubuntu-in-console-mode](https://askubuntu.com/questions/859630/how-to-start-ubuntu-in-console-mode)



When I boot to the GRUB menu, I only have the following choices:

*Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings

I get this menu when I boot with legacy mode on in my BIOS, and with legacy mode and secure boot both off.

Both of those links rely on their being an "Advanced" option somewhere in the GRUB menu.  I don't know why I don't have one. :(

I'm going to try editing the GRUB options as indicated [here]("https://askubuntu.com/questions/326528/how-to-boot-to-the-recovery-mode-if-it-is-not-listed-in-grub"), and using the c+a+f12 option if that doesn't work.

I'll report back shortly.

---

### Post by rickseiden on 2020-07-13
I edited the safe graphics mode option to remove quiet and splash, and it went through the process of booting, and then hung [here]("https://photos.app.goo.gl/WRGiT6LaEpywq7bX8").  Ctrl-Alt-F12 did nothing, but I could type stuff on the screen.  It didn't do anything, but I could type.

Then I tried the recovery stuff from the link in my last post by adding "root=<uuid> single" to the end, and that gave me a syntax error.  Then I removed the root=<uuid> and just put the single, and that gave me [this]("https://photos.app.goo.gl/WRGiT6LaEpywq7bX8").

Finally, I tried the "ro recovery nomodeset" and that gave me the same result as the first option.

[IMG]https://photos.app.goo.gl/WRGiT6LaEpywq7bX8[/IMG][IMG]https://photos.app.goo.gl/WRGiT6LaEpywq7bX8[/IMG]I'm at my wits ends. I really appreciate your help!

---

### Post by rickseiden on 2020-07-14
An update!

I was looking at the screenshots, and I saw an error when I used nomodeset: AE_NOT_FOUND. That led me to adding acpi=off to the boot along with nomodeset, and that got me to the desktop.

But, I have no wireless, and no sound.  The system seemed to think that there was a sound card, as I had volume control, but no sound.

But, most importantly, I did not have a hard drive!  I tried the Install option from the desktop, but it couldn't find any place to install the system to.  So it appears that I can boot when I have acpi=off, but I can't install it.

---

### Post by GhX6GZMB on 2020-07-14
Getting to the desktop does not mean you have an installation, you just have a live boot.
You'll need to click on the "Install Ubuntu" icon to start the real install. The live DVD or USB-stick must stay in the machine all the time until you're prompted to remove it at the end.

---

### Post by rickseiden on 2020-07-14
> **ml9104 said:**
> Getting to the desktop does not mean you have an installation, you just have a live boot.
You'll need to click on the "Install Ubuntu" icon to start the real install. The live DVD or USB-stick must stay in the machine all the time until you're prompted to remove it at the end.

Thanks for your response.  That's what I meant when I said that I got to the desktop, but then clicked on the install and didn't have a hard drive.

---

### Post by GhX6GZMB on 2020-07-14
You'll not have a hard drive until you do the install. The only thing you have is your live boot DVD or USB. Part of the install is creating the hard drive (formatting, partitioning etc.).

But at least you've arrived at the live boot desktop.

I've done this dozens of times and never had any issues, it just runs.

It seems to me that the most issues arise with USB-stick live boots. DVDs are mostly painless.
But perhaps that's just because DVD are not that much in use any more.

---

