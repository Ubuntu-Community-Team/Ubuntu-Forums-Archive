---
title: "Installation Ubuntu 7.10 does not work, even with alternate CD"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by BA20 on 2007-10-31
Hi all,

I would like to install Ubuntu 7.10 on my PC. I tried the normal live CD and the alternative CD, but none of them works on my pc.

The normal Live CD:
Afther booting, I get the menu whre I choose "start or install Ubuntu". The Linux Kernel loads. A couple of seconds later I get the following error:

--->
udevd-event[2286]: run_program: '/sbin/modprobe' abnormal exit


BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
<----

Looking on differents forums, I decide to try the alternate CD. In the menu I choose "Install in text-mode". The Linux Kernel loads. Again a couple of seconds later, this error:

udevd-event[1776]: run_program: '/sbin/modprobe' abnormal exit


Almost twice the same error, only the code (2286/1776) is different. Does anyone knows what I should do?

The computer is an Athlon XP (0.13) 1155 MHz
chipset: VIA KT400(A)/600

Thanks in advance,

BA20


PS: To be sure, I also tried the 64-bit installation CD. Since it is not a 64-bit computer, I get the following error: "Your CPU does not suppport long mode. Use a 32bit distribution."

---

### Post by Cato2 on 2007-11-01
At the (initramfs) prompt, try typing dmesg | less to see boot messages and scroll to end to see what exactly caused modprobe to fail - this is trying to load a Linux kernel module, usually to support specific hardware in your system.

Also, try burning a copy of Knoppix on CD and booting that, to see if it can successfully boot your system - at least then you know your hardware is compatible with Linux.  Useful commands in Knoppix to see what it loaded are: lsmod - also try lspci -v and lsusb -v to see what you have attached, and try to correlate those with the output of dmesg.

---

### Post by BA20 on 2007-11-01
Hi Cato2,

Thank you for your answer. I tried what you said: I entered dmesg | less at the (initramfs) prompt, but it returns this:

/bin/sh: dmesg: not found
/bin/sh: less: not found

I entered 'help' like the first error-message suggested, but I can't see "dmesg" nor "less" in the list.

In attach, I have a picture of the error I get when trying the alternate CD. I do not understand what all these codes mean.

The second thing: trying Knoppix. The result: Knoppix works fine on my computer. I have no problems starting and when booting, it seems that it recognises all my hardware.

I hope that there is still a possibility to install Ubuntu 7.10 on my computer. (Once I already installed Dapper and that worked fine.)

BA20

---

### Post by Cato2 on 2007-11-02
I don't have any great suggestions here, other than to use Knoppix and the commands mentioned to figure out what drivers (modules) it loads, and to find more about Ubuntu install debugging - e.g. what commands to use at the (initramfs) prompt - probably just whatever busybox provides. 

The screenshot shows that there appears to be an issue getting IDE working (used by disk and CD normally)- it might be good to boot from the Ubuntu Desktop CD and see if that works, though that is probably via IDE CD-ROM.

If the Gutsy CD doesn't work, you could try Feisty as well - if that boots it helps narrow the problem down to something introduced in Gutsy, and it's easier to try new kernels, new modules, etc, from that base.

Also, try posting a bug in Launchpad - this does seem to be an Ubuntu bug not misconfiguration, and you may get more useful help there if you are willing to help the developers diagnose the problem.

---

### Post by BA20 on 2007-11-02
Hi Cato2,

Thank you for your answer. Ubuntu Feisty works on my computer, so, as you say, it should have something to do with Gutsy.

Thank you for mentioning Launchpad. I never heard of it. I posted my problem on their site. ([https://answers.launchpad.net/ubuntu/+question/16854](https://answers.launchpad.net/ubuntu/+question/16854)) I hope they can tell me what I should do.

greatings,

BA20

---

### Post by Whodoes on 2007-11-04
BA20, 
  exact same issue here... on a system that installs 6.06 LTS with no issues.

---

### Post by hplehn on 2007-11-04
Same problem on amd64 here. I had no problems with feisty and can even use gutsy without problems with the feisty kernel.  I installed gutsy by dist-upgrade and ran into problem after first reboot. By using a rescue cd i was able to switch to feisty kernel. Error occurs with gutsy install cds, too.

---

### Post by Desd on 2007-11-04
I've encountered a similar problem, while loading the LiveCD, the progress bar got stuck somewhere at 1/3. On another computer it worked fine, so the CD is ok.

I installed Feisty fresh and upgraded, got so many errors on my screen and resolution that I reinstalled Feisty again and will stick with that.

If your system does not like 7.10 from the LiveCD, be carefull with upgrading too. 

Greetings,


Desd

---

### Post by soaro77 on 2007-11-04
Same thing happened to me. I upgraded to Gutsy on my PC just fine although it takes forever to start up applications now. But when upgrading my wife's laptop it seemed to upgrade just fine but when I boot the laptop I get a kernel panic. I burned the Gutsy CD and tried booting it and the bar stops about one third of the way and nothing happens. Fiesty CD boots up just fine.

---

### Post by Whodoes on 2007-11-04
cant find my last fiesty cd so ill be going back to a fresh 6.06.

fudge!

i guess thats why 6.06 is gtg through 2009 though. cheers !

---

### Post by netbandit on 2007-11-04
try adding acpi=off to your boot options.  It worked for me.
-nb

---

### Post by hplehn on 2007-11-06
acpi=off does not help for me.

---

### Post by BA20 on 2007-11-14
Hi all,

As you can see here:
[http://ubuntuforums.org/showthread.php?t=600872&page=3](http://ubuntuforums.org/showthread.php?t=600872&page=3)

all_generic_ide solved my problem.

greetings,

BA20

---

### Post by soaro77 on 2007-11-14
> **netbandit said:**
> try adding acpi=off to your boot options.  It worked for me.
-nb

But this makes it so you can't use the nvidia drivers and cannot get all the nice compiz fusion toys. I didn't have to do this with Fiesty. I don't understand why I would now with Gutsy.

---

### Post by torgrot on 2007-11-15
You might want to try pci=biosirq acpi=off to your boot options.  You could try it without the acpi=off and just try the pci=biosirq.  I don't understand what it does, but it allows me to boot Linux reliably all the time.  I was so fed up with GRUB, I was ready to abandon Ubuntu.  I did a search for Linux kernel parameters and tested them until I found one that worked to boot my machine reliably.  I guess it would be worth a shot.  Here is the page I found [http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php](http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php)

torgrot

---

