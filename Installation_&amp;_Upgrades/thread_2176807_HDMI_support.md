---
title: "HDMI support"
date: 2013-09-26
forum: Installation &amp; Upgrades
---

### Post by Paul_Dobbe on 2013-09-26
Hi,

I'm having trouble installing my HTPC. I've tried with XBMCbuntu, but after some issues I switched to Ubuntu 12.04 LTS. I've installed it on a Dell Optiplex 740 (2.2 GHz AMD Athlon with on-board graphics card). I have a Zotac Nvidia 8400GS plugged in, needed for HDMI support to the 4 year old Philips TV. The BIOS disables the build in card as soon as it detects an additional card (it says).

After installing XBMC-, Xu- or plain Ubuntu the system reboots, the splash screen appears, the progress bar lights up one time and then my TV tells me it's got no signal...

All live CDs operated flawless.

Could use some help hear I guess...

Paul

---

### Post by mastablasta on 2013-09-26
interesting - during system load oyu can press esc to see if there are any errors.

also can you boot into recovery mode to trouble shoot?

did you install any porprietary drivers?

if you can get into troubleshooting mode try lshw to see what hardware is recognised by system. if bios diabled onboard chip automaticly then i believe it shouldn't be listed. 

also if card has more audio out exits try to move th ecable to another output. it happens to me sometimes on windowsxp that someohow it changes primarry video output. :-O

---

### Post by Paul_Dobbe on 2013-09-26
Hi Mastablasta,

Thanks for the tips, I'll give them a go.

I didn't install any proprietary drivers yet - I need a screen to do so... Maybe in CLI mode.

Also thanks for the moderator who kindly updated my thread's title :roll:

Paul

---

### Post by Paul_Dobbe on 2013-09-26
> **mastablasta said:**
> interesting - during system load oyu can press esc to see if there are any errors.

After the blinking cursor in the upper left, the splash screen appears for about 5 seconds. Then the screen seems to split in half horizontally, with blurry stripes in the upper part. Short after that the TV turns blue with a 'No Signal' message. So it's very early in the boot process. There's no reaction on pressing the escape key.

> **mastablasta said:**
> also can you boot into recovery mode to trouble shoot?

Nope, it plugs out before the menu I guess.

> **mastablasta said:**
> did you install any porprietary drivers?

No chance...

> **mastablasta said:**
> if you can get into troubleshooting mode try lshw to see what hardware is recognised by system. if bios diabled onboard chip automaticly then i believe it shouldn't be listed.

also if card has more audio out exits try to move th ecable to another output. it happens to me sometimes on windowsxp that someohow it changes primarry video output. :-O

The card has a VGA, HDMI and DVI outlet. Sounds interesting, suppose it drops back to VGA for compatibility reasons... could be. Maybe a jumper or so could force something. Trouble is, I do not have a VGA cable :(.

Thanks for the ideas!

Paul

---

### Post by Paul_Dobbe on 2013-09-26
New results: I tried the Mageia 3 image (just to see something else then Ubuntu-variants), but even the live-CD failed this time, at the same point: splash screen (without logo) splits in half horizontally with a blurred upper half. I suppose this is the computer's output, although somewhat twisted.

What's fun of Mageia: it has a hardware detection tool (Manon) which can be started from the live-CD boot menu! And it showed my card... nVidia Corporation - G98 (GeForce 8400 GS) VGA compatible controller! Sounds pretty accurate.

Leaves me MastaBlasta's last option: the card somehow forces VGA output for whatever reason...

The story continues...

Paul

---

### Post by mastablasta on 2013-09-27
> **Paul_Dobbe said:**
> After the blinking cursor in the upper left, the splash screen appears for about 5 seconds. Then the screen seems to split in half horizontally, with blurry stripes in the upper part. Short after that the TV turns blue with a 'No Signal' message. So it's very early in the boot process. There's no reaction on pressing the escape key.

Nope, it plugs out before the menu I guess.


Out of curiousity - when you boot hold left shift. grub menu shout pop up
Now oyu should be able to select revorery. But before you go into that try to set nomodeset in the boot options: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

> 
No chance...

i do not know much about opensource nvidia drivers. however since you use a slightly "non standard" setup it might be good to try and install them. this can be done from comand line. but you migth get a GUI option with recovery mode. another option is to update the opensoruce drivers. i see you are nto the only one with this card issue. some further reading on this topic:
[http://ubuntuforums.org/showthread.php?t=1968516](http://ubuntuforums.org/showthread.php?t=1968516)
[http://ubuntuforums.org/showthread.php?t=2001658](http://ubuntuforums.org/showthread.php?t=2001658)


it seems to me this card is well supported in 12.04. however, some users still had some issues with it.

---

### Post by Paul_Dobbe on 2013-09-27
> **mastablasta said:**
> Out of curiousity - when you boot hold left shift. grub menu shout pop up
Now oyu should be able to select revorery. But before you go into that try to set nomodeset in the boot options: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


The nomodeset option brought me back in Ubuntu, hurray! It seems it has been the driver anyway...

> **mastablasta said:**
> i do not know much about opensource nvidia drivers. however since you use a slightly "non standard" setup it might be good to try and install them. this can be done from comand line. but you migth get a GUI option with recovery mode. another option is to update the opensoruce drivers. i see you are nto the only one with this card issue. some further reading on this topic:
[http://ubuntuforums.org/showthread.php?t=1968516](http://ubuntuforums.org/showthread.php?t=1968516)
[http://ubuntuforums.org/showthread.php?t=2001658](http://ubuntuforums.org/showthread.php?t=2001658)

The nVidia driver works ok. I suppose this was yet another classical nomodeset-issue... 8-[

Thanks MastaBlasta for your advise on this!

Paul

---

