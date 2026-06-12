---
title: "Ubuntu 13.10 has become unusable -- hard freeze after 1-5 hours"
date: 2014-03-16
forum: Installation &amp; Upgrades
---

### Post by sfordin on 2014-03-16
Summary:

Unfortunately, after happily using Ubuntu for many years through many versions on several different machines, and in dual-boot and single-boot configurations, Ubuntu 13.10 on my current laptop freezes so often as to be unusable. After 1-5 hours of unattended operation, the system freezes hard, the display and keyboard become unresponsive, and pings from remote machines report that the Ubuntu box is down, even though it's still powered up. The only thing for it in this state is to hold down the hardware power button to shutdown the machine.

My rough understanding is that the problem is related to Unity and/or the indicator-application-service, but I'm not sure. The issue has been reported pretty widely on the Web, and in several issues on bugs.launchpad.net (for example, [https://bugs.launchpad.net/bugs/1228478](https://bugs.launchpad.net/bugs/1228478)), but I can't seem to find exactly the right thread in this forum. My apologies in advance if this issue has already been addressed here. 

Clarifications:

I'm running an old Toshiba Satellite A205-S4617 laptop with 4 GB RAM and a brand new 1 TB Western Digital hard drive. My old hard drive started throwing input/output errors during the last week, so I figured it was a goner, and I replaced it with the new WD drive. I use this laptop primarily as a NAS/Plex/Squeezebox server in my home, so most of the time it runs unattended. I have a 3 TB Seagate USB drive and two 4 TB Seagate USB drives connected to the machine. I've been using this laptop in this way without any problems since Ubuntu 11.x.

The problems started when I did a kernel upgrade from Ubuntu 13.04 to 13.10. Shortly thereafter, I started to get input/output errors on the hard drive -- reported by dmesg and actively when I tried to access various files on disk -- and the system would freeze overnight. I used gparted to do disk repairs and did a fresh install of Ubuntu 13.10. Eventually I decided that the disk had just died, and did not think that any of the "freeze" issues were related to Ubuntu itself.

I then installed the new hard drive, and did a fresh install of Ubuntu 13.10. No more input/output errors, but the system freezes persisted. Tried again: Did another from-scratch installation of Ubuntu 13.10, but still no joy. Tried adding the "Proposed" packages to my apt sources.list and then doing all the upgrades. Even worse. Tried to boot the machine, but now I just get a mesmerizing flashing of colored horizontal lines as the machine enters the boot loader phase.

Conclusions:

Something in Ubuntu 13.10 is so badly broken that it's become unusable. From what I've been able to find on the Web, I'll try installing KUbuntu instead, and completely bypass Unity and Gnome for now. Don't know if it'll help. If not, I suppose it's on to Debian...

Thanks in advance for any assistance.

---

### Post by Ubi_one_2014 on 2014-03-16
seems to my opinion a hardware issue

can you do a memorycheck?
otherwise, i will wait until you installed kubuntu, and inform us if the problem still exists.

what kernel do you run?
try install latest kernel from: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13.6-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13.6-trusty/)

---

### Post by sfordin on 2014-03-18
Thanks for the quick reply, Ubi_one_2014. I really appreciate it.

Summary:

I ran memtests several times from the boot loader, and they all passed just fine. I tried going back to 12.04 LTS, and I tried XUbuntu 13.10 32-bit. I ended up not trying KUbuntu because I figured, between the 64-bit versions of Ubuntu 13.10, 13.10 with a whole mess o' stuff turned off (like all the Unity indicator apps), Ubuntu 12.04 LTS, and the 32-bit version of XUbunutu 13.10, I had a reasonable set of test cases to depress myself with. No joy in any of those configurations. In each case, the machine started out fine, but after 1-5 or so hours, depending on the load (or not), the machine would become unresponsive to keyboard, touchpad, and network. The machine appeared to be powered on, but there would be nothing I could do with it except hold down the power button to power it off. Occasionally, early in some of the test cycles while the machine was still responsive, the display would freeze, and I'd have to do a Ctrl+Alt+F2 to drop into a command-line login. I would then typically see Input/Output errors on sda1 when I tried to log in. I'm reasonably confident that there's nothing wrong with the physical disk at sda1 because that disk is brand new, only a few days old. In any case, the errors were the same with the original disk that I had in there.

Conclusion:

She's dead, Jim. The disk I/O errors, display freezes, and network disconnects all imply hardware problems. Perhaps it's a power supply gone south -- I've seen bad power supplies produce all manner of strange errors on other machines. However, given the age of the machine, I'm thinking it's one or more controllers or suchlike that have gone bad on the motherboard. Sadly, I think it's time to give the last rites to this machine. She served well for many years, and always looked cool doing it, but she's gone now. Your initial assessment, Ubi_one_2014, that this was a hardware issue appears to be correct.

I think it's time to build me a new mini system. The good news is that Ubuntu 13.10 seems inculpable with regard to these problems, similar sounding reports on the Web notwithstanding.

Thanks again for your quick and thoughtful response, Ubi_one_2014. I really appreciate it.

---

