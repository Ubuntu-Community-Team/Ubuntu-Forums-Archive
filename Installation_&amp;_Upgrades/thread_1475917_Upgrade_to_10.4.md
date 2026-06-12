---
title: "Upgrade to 10.4"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by daviddunford on 2010-05-07
I recently tried out Ubuntu 9.10 on an old computer and was so impressed I added it as a dual boot option to my main computer, alongside Windows 7. I installed it from Windows and it worked fine, booting from a Windows boot menu that defaulted, as I wanted, to W7. A few days ago I was offered an upgrade to 10.4. Half way through the upgrade the process hung (I think while installing MemTest) so I pressed Ctrl-Alt-Del and the system rebooted. It proceeded to load the remaining files then asked me where I wanted the Grub loader to be installed. As I had Ububntu installed on a different physical drive from Windows, I asked for Grub to go on that drive - then realised too late that this would give me an unbootable machine.
 
After much experimenting with rescue discs, I simply disconnected the secondary drive and was now able to boot into Windows again. I used a rescue disk to delete the Ubuntu folder from the reconnected secondary drive, rebooted Windows and tried to reinstall Ubuntu from Windows. This failed several times (wubi.exe - I think - refused to run). So I downloaded the iso of 10.4 and installed Ubuntu from that. This time it installed itself on a new partition on my primary disk and ran perfectly - except that the grub loader defaulted to booting Ubuntu, which would confuse the other users of the computer!
 
The advice I found was to edit menu.lst - but this file was nowhere to be found. It was only after much searching that I discovered that this had been replaced in this version by grub.cfg and that this couldn't be directly edited. So I traced the grub file that you are supposed to edit, only to find it was read only and I didn't have ownership of it to change its attributes. So that was another search to discover how to take ownership of a file. Eventually it was all sorted, my machine boots by default into W7, but the impressive Ubuntu 10.4 is available as well. I just wonder whether all things Ubintu are going to be as complicated as this. I'm an experienced PC user and I don't mind getting my hands dirty, but I imagine a lot of people would have given up in despair. Did I do anything absurdly wrong? I know I put the Grub loader in the wrong location, but it seems a natural mistake to make!

---

### Post by powerofpi on 2010-05-07
> Did I do anything absurdly wrong? I know I put the Grub loader in the wrong location, but it seems a natural mistake to make!

You are right, that is an easy mistake to make. I think the ubuntu installer process should make you explicitly select the partition for the bootloader, and possibly even autodetect other operating systems and allow you to set boot priority for them as well. Editing grub.conf works, but as you say, most users would give up in despair before they figure it out. 

In short, I agree that Ubuntu should be more friendly towards novice users.

---

### Post by daviddunford on 2010-05-09
Thanks, powerofpi. It's good to know that I wasn't a complete idiot! In fact, I see there have been a lot of threads in the last two or three days reporting installation issues with dual boot systems and 10.4. Perhaps the release needed a little more fine tuning before being made available.

---

