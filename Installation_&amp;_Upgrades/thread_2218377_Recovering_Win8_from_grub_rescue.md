---
title: "Recovering Win8 from grub rescue"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by HakitoCZ on 2014-04-20
I messed up. I know I did. The most in my whole life, it seems.
But here's the story.
I've got laptop, Lenovo g500.  Windows 8 preinstalled. I wanted linux dualboot, naturally. Found the way to replace UEFI with Legacy booting system. And switched the fastboot off as well. Then I made linux flash disk and successfully installed. Well, without Ethernet support. Then I rebooted and didn't belive. Grub loaded and offered only linux distro and win recovery mode, which didn't boot at all. Linux distro without internet and no win access. It made me dessperate and I did the most stupid thing. Not quite sane I booted gparted flash and removed all three linux partitions. /home, boot and /swap. Grub cannot boot win, as I assumed from few sources I've read. Okay, I thought, now I boot to win, there's anything else to boot to. And then grub recovery mod appeared. I can't boot flash, because grub is faster.
I have no idea what to do from this point so I honestly appriciate any kind of help.

Grub rescue> ls
(hd0) (hd0,gpt7) (hd0,gpt6) (hd0,gpt5) (hd0,gpt4) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1)

It there's anything I can do to fix it, I'd be very grateful. Looking forward for replies.

---

### Post by HakitoCZ on 2014-04-20
If I do understand this situation, I need to get rid of grub. In short.
Since I can't access win from grub loader, maybe I can access os from flash drive..

---

### Post by oldfred on 2014-04-20
If Ubuntu was in BIOS mode, it could not boot Windows in UEFI mode from grub menu. Once you start booting in one mode you cannot switch.

You need to go into UEFI/BIOS and turn UEFI back on to boot Windows.

Do not know if y500 is similar or not.
       Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)


 Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.

---

