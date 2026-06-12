---
title: "Unbuntu 8.04 installation problems."
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by PerfectSanity on 2008-05-14
Hi all,

I'm totally new to the linux scene, I've tried researching this but with no concrete answer, hope you can help...

I've burnt my image to CD, when booting to the CD though and selecting Install Ubuntu, the status bar goes back and forth as usual but after a while the following message appears:

udevd-event[1551]: run_program: '/sbin/modprobe' abnormal exit.

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter help for a list of built in commands.
(initramfs) _

Of course I can type help, but thats useless because I dont know whats what. I have installed Unbuntu before without this problem.

I'm currently running a Pentium Dual Core 1.73Ghz with 2gb ram, also I have Vista installed.

If you can help, please do, it would be most appreciated :)

---

### Post by macaholic on 2008-05-14
Well I think it is failing at loadign some default driver. I would recommend trying the alternative install disc instead.

---

### Post by PerfectSanity on 2008-05-14
I'll give it a shot, it might also be worth noting that I installed Ubuntu sucessfully through Vista, but when booting to Ubuntu, I get the same message.

Thanks.

---

### Post by PerfectSanity on 2008-05-14
Ok, that nearly did it, everything seemed to install ok with no errors along with the GRUB bootloader.

After selecting Ubuntu, I now get:

udevd-event[1486]: run_program: '/sbin/modprobe' abnormal exit.

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter help for a list of built in commands.
(initramfs) _

That's after using the alternate installation.

Any ideas?

---

### Post by luigi-br on 2008-05-14
i'm with same problem. But in my case that happen after a upgrade from Ubuntu 7.10 to 8.04.
i tried instalation on a new pc but got the same result.

pc configuration:
dual boot XP / Ubuntu
XP SP2 ok, Ubuntu 7.1 ok, Ubuntu 8.04 down

Pentium III, 512 mb RAM, Geforce FX5200 128 mb.


new pc:
triple boot: Vista, Fedora, Ubuntu.
Vista ok, Fedora ok, Ubuntu down

Athlon 64 X2 +4000, 4G Ram, Geforce FX5200 128 mb, 2 X HD 400G WD

and i dont have any clue about solutions... anyone have some idea?

best regards,
Luigi

---

### Post by PerfectSanity on 2008-05-15
I seem of really messed things up now, I formatted my Ubuntu partition to start again now windows says winload.exe is missing or corrupt. Good times. I guess I dont need your help now lol.

---

### Post by PerfectSanity on 2008-05-15
After totally screwing everything up, I formatted the hard drive, removed everything and installed Ubuntu by itself. I still get the error.

Is anyone able to help? I seem to be banging my head against the wall with this at the moment.

---

### Post by dstew on 2008-05-15
This is probably a kernel bug. Try the kernel parameter **all_generic_ide** which you can add to the kernel line at the grub menu by pressing 'e', or to the line in the /boot/grub/menu.lst file on the disk. See [this bug thread]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/154591").

---

### Post by PerfectSanity on 2008-05-15
I dont have GRUB installed now so how would I do that?

---

### Post by bsmith1051 on 2008-05-15
not that this helps now (post hard-drive wipe) but it sounds like a hw incompatibility.  I've seen similar problems with motherboards that use the new Intel SATA controller, so the advice re tweaking the GRUB entry sound right (to make the kernel use a fallback IDE setting).  You also might check your BIOS to see if there's a "compatible" mode you can select for the SATA controller.

---

### Post by PerfectSanity on 2008-05-15
Scratch that, I think I just need help executing that command.

---

### Post by PerfectSanity on 2008-05-15
I added that after the -- when booting to the CD. It still did not work.

---

### Post by PerfectSanity on 2008-05-15
Ok after a lot of finding our which buttons to press where, I added  that command line to the end of the kernel within the e menu of GRUB.

I also found a "Compatability" mode in the BIOS which i've turned on.

To no avail.

---

### Post by bsmith1051 on 2008-05-15
does it work with the LiveCD, i.e., can you successfully boot the LiveCD and get to the Ubuntu desktop?  If so, then it's much less likely to be a hw issue.

---

