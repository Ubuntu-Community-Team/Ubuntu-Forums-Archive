---
title: "&quot;Try Ubuntu before installing&quot; does not work"
date: 2015-12-01
forum: Installation &amp; Upgrades
---

### Post by lgriffel on 2015-12-01
I'm trying to test ubuntu before I install it on a new laptop. After I select "Try Ubuntu without installing" I get some error messages (with nouveau) and the system hangs. I've tried restarting and editing the boot options by removing "quiet splash" with "nomodeset", but no luck. I don't get an error message, but it hangs on detecting the hardware. I've repeated the process a few times, and I've gotten the purple screen a couple of times (when I retry without adding the nomodeset) but it still hangs. I'm worried if I try to install ubuntu I will have problems. My end goal is just to install ubuntu, no dual boot.

My machine specs are as follows:
asus GL552VW
intell core i7-6700HQ @2.60GHz 
intel hd graphics 530
nvidia geforce gtx 960m graphics card

I am booting from a USB I created with unetbootin; I did checksum the ISO. I'm trying to install 15.10. Can anyone offer suggestions?

Thanks!

---

### Post by sudodus on 2015-12-01
Welcome to the Ubuntu Forums :-)

I think you are right, when you describe problems concerning the graphics. There can be problems with some nvidia cards. One possibility is to test with the newest version, the one that is still being developed. You can find it at this link

[ubuntu-xenial-desktop-amd64-daily.iso](http://cdimage.ubuntu.com/daily-live/current/xenial-desktop-amd64.iso)

If it does not work, you might be able to boot in text mode with the boot option **text** (instead of **nomodeset**), and in text mode try to install a proprietary driver for the nvidia graphics chip.

But I hope you  will get more advice. There are people around here, who know more than I about solving problems with graphics. If you are lucky, someone might have experience of the same nvidia graphics.

---

### Post by lgriffel on 2015-12-01
Thanks for your reply.

I tried the iso that you suggested three times: the first with the default boot options, the second with "nomodeset" and the third with "text". None of those options worked. I also tried openSUSE's live cd ISO, and that did not work either.

The error I keep seeing looks like this:
[   10.812920] nouveau E[   PFIFO][0000:01:00.0] SCHED_ERROR [ UNK06 ]

---

### Post by lgriffel on 2015-12-01
I've also tried:
nouveau.modeset=0

but no dice.

---

### Post by ubfan1 on 2015-12-01
Here are some more options to try, I'd suggest the skylake one first.

Skylake needs this (15.04...):
i915.preliminary_hw_support=1

Options for Video problems:

nomodeset
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

Older Intel video card:
i915.modeset=1 or i915.modeset=0
newer:
i915.i915_enable_rc6=1

video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

To allow Nvidia hybrid machines to boot.
nouveau.blacklist=1

---

### Post by lgriffel on 2015-12-01
Thanks for your help.

I added the skylake option first. I tried it with both with "quiet splash" and "text" to see if it would work, but it still is not working.

I will try the other options to see if anything works.

---

### Post by lgriffel on 2015-12-01
I've tried the options you've listed, but nothing seems to work.

Is there a combo you suggest?

Also, I get a message saying "nouveau: unknown parameter 'blacklist' ignored" when I add that parameter.

---

### Post by turin86 on 2015-12-07
Hello!

I have the same computer bought 2 days ago. Its being a little pain...

Ubuntu 14.04 works fine, except that the touchpad is not recognized ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1520519](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1520519)) . It seems to be something related to [https://bugs.launchpad.net/hwe-next/+bug/1488395](https://bugs.launchpad.net/hwe-next/+bug/1488395) , so I'm trying to test the Ubuntu 15.10 live to check if touchpad works with this version.

The only way to make ubuntu start is with the following options:

[COLOR=#333333][FONT=monospace]nouveau.modeset=0 options nouveau blacklist acpi=off[/FONT][/COLOR]

It runs, but the touchpad is still not working (maybe because of this acpi=off)

Also found this question: [http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)

Did you managed to run Ubuntu without problems?

---

