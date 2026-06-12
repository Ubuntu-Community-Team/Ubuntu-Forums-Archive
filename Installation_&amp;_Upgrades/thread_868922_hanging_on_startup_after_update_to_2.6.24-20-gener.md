---
title: "hanging on startup after update to 2.6.24-20-generic"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by Chris11 on 2008-07-24
I justs updated to 2.6.24-20-generic, but now the system hangs at the screen "startup..."_

What can I do?  Can I switch back to 2.6.24-19-generic?

Chris

---

### Post by tgrisier on 2008-07-24
Same problem here.  

What I did was edit my grub file and took out the section containing the 2.6.24-20-generic option.  Probably not the right thing to do, but it works.

---

### Post by Chris11 on 2008-07-24
yea I did the same. I ## the 2.6.24-20 entries in menu.lst and it works.. anyway.... what could be the reason for the failing of 2.6.24-20?

Chtris

---

### Post by avtolle on 2008-07-24
Do a forum search, and you will find several threads on this topic. There is a bug report already filed on Launchpad concerning the problem, which is discussed in at least one other thread. My suggestion is to  follow the bug report, and if you like, provide the devs information as to your particular problem.

EDIT: That particular upgrade came from the proposed repository, the purpose of which is to put packages out for testing. Unless you are interested in testing, and having your system break from time to time, you should disable that particular repository.

---

### Post by tgrisier on 2008-07-24
> **avtolle said:**
> EDIT: That particular upgrade came from the proposed repository, the purpose of which is to put packages out for testing. Unless you are interested in testing, and having your system break from time to time, you should disable that particular repository.


Thanks for the insight.  I was wondering how that happened.

---

### Post by Pumalite on 2008-07-24
I want to go on record saying that both 32 bit and 64 bit upgrades worked in my machines. One Asus P4p800 SE, Pentium 4 3.2 GHZ "Prescott"; Asus P5K SE, Core 2 Duo 2.6 GHZ; Intel D975XBX, Core 2 Duo 2.6 GHZ. All with Nvidia cards and 2 GB of RAM each.

---

### Post by Chris11 on 2008-07-25
Thanks for the answers - I'll look into it... may bee I should drink a other cup of Ubuntu before updating my system ... 

Chris

---

### Post by jgcamp99 on 2008-07-25
> **avtolle said:**
> EDIT: That particular upgrade came from the proposed repository, the purpose of which is to put packages out for testing. Unless you are interested in testing, and having your system break from time to time, you should disable that particular repository.

That's a pretty weak explanation. I can understand buggy proposed repository updates & upgrades, but one that's placed in the repository that breaks the system that early in the boot process should never be in a proposed repository. How can a kernel be tested when it won't even boot other than it's plain just broken ? I don't mind being a bleeding edge test bed, but lets face it, not even getting past the startup after recognizing the cpu's L1 & L2 caches doesn't (that I had to get from the "recovery mode" option) relay any information back to Canonical.

BTW, 2.6.24-20-rt is borked too ! Anyone get a good 2.6.24-20-* experience to relay ?

---

### Post by nitePhyyre on 2008-07-25
I'm having problems also.  The new kernel kills networkmanager.  It also added a new device to Harware Drivers. The component is called "wl". And the tooltip doesn't give any info on hardware.

---

### Post by Pumalite on 2008-07-25
> **jgcamp99 said:**
> That's a pretty weak explanation. I can understand buggy proposed repository updates & upgrades, but one that's placed in the repository that breaks the system that early in the boot process should never be in a proposed repository. How can a kernel be tested when it won't even boot other than it's plain just broken ? I don't mind being a bleeding edge test bed, but lets face it, not even getting past the startup after recognizing the cpu's L1 & L2 caches doesn't (that I had to get from the "recovery mode" option) relay any information back to Canonical.

BTW, 2.6.24-20-rt is borked too ! Anyone get a good 2.6.24-20-* experience to relay ?

Read post # 6

---

### Post by rbringh on 2008-07-26
How does a very new user edit the grub file? The machine will not boot up, if I load the Live Session CD it will not save any changes to the file. The file is owned by root. Thanks for the help.

---

### Post by Shazaam on 2008-07-26
> **rbringh said:**
> How does a very new user edit the grub file? The machine will not boot up, if I load the Live Session CD it will not save any changes to the file. The file is owned by root. Thanks for the help.

1. Boot the livecd
2. Mount your drive/partition in terminal....
```
sudo mount /dev/yourdrivenumber /mnt
```
example= sudo mount /dev/sda3 /mnt

3. Enter this in terminal....
```
gksudo gedit /mnt/boot/grub/menu.lst
```
(small L) , put a # in front of the broken kernel listing (each line) like this....
```
#title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda8)
#root		(hd0,7)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda8 ro quiet splash 
#initrd		/boot/initrd.img-2.6.22-14-generic
#savedefault
#boot
```
4. Save the modified file (File>Save)
5. Umount the drive/partition (not a typo)...
```
sudo umount /dev/sda3
```
6. Reboot pc

---

### Post by rbringh on 2008-07-27
Shazaam,

Thanks for the help. System is back up and running just as before the upgrade.

---

