---
title: "Can;t start Ubuntu 14.04 without live USB"
date: 2015-06-21
forum: Installation &amp; Upgrades
---

### Post by t-martin-v on 2015-06-21
I've seen the problem in other topics, but can get it fixed even with following the solutions presented there.

Last year I build a new pc. And used an old ssd on where I installed ubuntu. So far so good. Two weeks ago the ssd crashed beyond repair. And I put in a brand new one TB regular harddisc. I made a new Ubuntu installation with an usb key.

The thing is. It won work. And I can figure out what I&#7743; doing wrong. 

I won't boot without the live usb. I end up in the shell of the Bios or get an error message.

I tried boot repair. And got this link to use in a forum:   [http://paste.ubuntu.com/11749803/](http://paste.ubuntu.com/11749803/)

Because after I reboot it seems to start up okay. But when i really shut down. And start up half an hour later. The problem magically re-appears. 

I'm relatively new to ubuntu. Used it some years as a dual  boot on an old laptop. This is the first time I'm using it as a stand alone os.

---

### Post by ajgreeny on 2015-06-21
I wonder if you have fallen foul of the UEFI probem, ie the machine is using UEFI but you installed ubuntu in legacy mode.

However I see you also appear to have used LVM about which I know very little, so can't help with that.

Have a look at [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") which may help solve some of this, but if that gets you nowhere come back again and someone who is more familiar with Boot-repair and LVM may be able to tell you more.

---

### Post by t-martin-v on 2015-06-21
Thank you very much. Seems like this is what i'm struggling with. I'll read it and try to fix it. Haven't build a desktop myself since 1995. So I have some catching up to do :-)

---

### Post by yancek on 2015-06-21
Looking at your boot repair output, it shows you have not installed the Grub bootloader properly.  At the very top it shows no bootloader in the MBR.  This is necessary if you are using the MBR method to boot rather than UEFI.  You have a FAT32 partition at the beginning of the drive which is what is normally used for a UEFI boot but there are no files shown.  Generally, you will see the names of the files.  Did this machine previously have a version of windows installed and if so, which one?

I'm not familiar with LVM but I understand a separate boot partition is generally needed (that would be sda2).  Do you recall which option you selected during the installation of the booloader?  Do you have a specific reason for choosing LVM?

---

### Post by t-martin-v on 2015-06-21
I was just looking around, and don know why i chose LVM. I started over. Read the piece on UEFI. Mad a clean install, without LVM. The same problem happens. 

There was never a version of windows installed on this machine.

I've got a new link:  [http://paste.ubuntu.com/11750775/](http://paste.ubuntu.com/11750775/)

I end up in shell. It says map: cannot find required map

---

### Post by yancek on 2015-06-21
Your boot repair output shows you are using UEFI and has entries for Ubuntu.  There are also entries for windows even though it's never been installed.  I'm not sure that is standard but I don't use UEFI so can't offer any suggestions.

---

### Post by t-martin-v on 2015-06-21
I have somehow managed to find a solution. I simply moved my hdd to a different SATA port on the motherboard. No idea why it works, but somehow it did. Very unsatisfactory, since I don't understand it. But it works.

---

### Post by ajgreeny on 2015-06-21
No, I've no idea why that should have made any difference either, other than the SATA port change having also changed the device mapping.

Please mark as solved from the Thread Tools menu at the top.

---

