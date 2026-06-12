---
title: "Grub Rescue prompt after 12.10 upgrade"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by FloydPink on 2012-10-19
Dual boot HP desktop that had Windows 7 and Ubuntu 12.04 working fine until yesterday. Upgraded to 12.10 and the grub install gave an error of not being able to write to the boot sector. It looks like the situation is similar to the one in this [bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1053793").

Here is the pastebin from an unsuccessful boot-repair - [http://pastebin.ubuntu.com/1290132/](http://pastebin.ubuntu.com/1290132/)

Not booting at all now and goes back to grub rescue all the time.

Can someone help so that the system shall start booting again?

---

### Post by TheFuzz4 on 2012-10-19
I just fixed mine.  I ended up having to use the terminal method of repairing it.  I followed the guide from here [http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)

Just scroll down to the terminal section of it.  Its not that bad.  I have a different issue now though where neither my USB or network will work on the 3.5 kernel so I'm currently on the 3.2-31 kernel until I can figure out what else went wrong during my upgrade.  I hope that this helps you get your system back up and running.

---

### Post by FloydPink on 2012-10-19
Thanks for the suggestion, but unfortunately that also didn't help me. Here is the log of what I tried: [http://pastebin.ubuntu.com/1290276/](http://pastebin.ubuntu.com/1290276/)

---

### Post by FloydPink on 2012-10-20
After struggling for more than a day, uninstalled Ubuntu from this desktop !

---

### Post by TheFuzz4 on 2012-10-20
Did you just reinstall it?  Or did you go with a different distro?  I am starting my migration over to the Ubuntu Remix.  Its still Ubuntu just no Unity :) Its all Gnome

---

### Post by YannBuntu on 2012-10-23
According to your Boot-Repair log, you have this error when installing GRUB:
```
/usr/sbin/grub-bios-setup: warning: this LDM has no Embedding Partition; embedding won't be possible.
/usr/sbin/grub-bios-setup: error: embedding is not possible, but this is required for RAID and LVM install.
```

You can mark yourself "affected" by this bug:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

As a workaround, you can install GRUB Legacy: 
run Boot-Repair --> Advanced options --> GRUB options --> tick the "GRUB Legacy" option --> Apply.

---

### Post by ZoLToR on 2012-10-25
> **YannBuntu said:**
> 
As a workaround, you can install GRUB Legacy: 
run Boot-Repair --> Advanced options --> GRUB options --> tick the "GRUB Legacy" option --> Apply.
It workaround didn't helped me. I received error message with advise to setup grub in separate boot partition. :(
Boot-info script [http://paste.ubuntu.com/1305754/](http://paste.ubuntu.com/1305754/)

---

### Post by YannBuntu on 2012-10-26
ok. 
So for the moment, you can restore direct access to Windows:
1) backup your documents if not done yet
2) Boot-Repair --> Advanced options --> tick "Restore MBR" --> Apply , 
3) tell me the new URL that will appear, 
4) reboot the pc and tell me what you observe.

tell i 'll tell you how to create a separate /boot.

---

### Post by ZoLToR on 2012-10-26
I restored acces to windows with bootable flash drive with win7 distributive, so I can't do this action now, sorry:
> 
3) tell me the new URL that will appear, 

Now I have only one OS with windows bootloader and I can't access to installed ubuntu... I will be searching information in google on weekend.
> 
 i 'll tell you how to create a separate /boot.

I don't want to do this. Maybe some way exists how to install old grub into MBR from bootable flash drive for example? 
I tried to install LinuxMint 13 with KDE a few weeks ago and nothing problems was with it GRUB

---

### Post by YannBuntu on 2012-10-26
> **ZoLToR said:**
> LinuxMint 13 with KDE a few weeks ago and nothing problems was with it GRUB

AFAIK, Mint13 uses GRUB1.99 (same as Ubuntu12.04), so the problem may come from:
- either GRUB2.00 (included in Ubuntu12.10)
- or the location of your boot files (in this case you will need a /boot at the start of the disk)

> **ZoLToR said:**
> Maybe some way exists how to install old grub into MBR from bootable flash drive for example? 

If you want to try GRUB Legacy, you can run Boot-Repair --> Advanced options --> GRUB options --> tick "GRUB Legacy" --> Apply.

---

### Post by ZoLToR on 2012-10-26
> 
If you want to try GRUB Legacy, you can run Boot-Repair --> Advanced  options --> GRUB options --> tick "GRUB Legacy" --> Apply.
I wrote before that it's operation finished with error at me.

Found workaround in installing burg. Instructions (for exapmle, Ubuntu installed on /dev/sda5):
1. Load from LiveCD image.
2. Type command:
```

sudo mount /dev/sda5 /mnt

```3. Add burg repository: 
```

sudo apt-add-repository "deb http://ppa.launchpad.net/bean123ch/burg/ubuntu lucid main"

```4. And update:
```

sudo apt-get update

```5. Install burg
```

sudo apt-get install burg

```6. In appearing questions press ENTER every time. If you will be asked for confirm to remove your current GRUB, click on "Yes" for removing GRUB2.
7. Install burg to HDD:
```

sudo burg-install --boot-directory=/mnt /dev/sda

```If  after step 7 in terminal appeared message "Installation finished, no  errors occured" (or similar, don't remember), then continue. Else - this  workaround not for you :(
8. Reboot computer.
9. In grub console type comand:
```

set root=(hd0,5)/boot/burg

```and press ENTER.
10. 
```

linux /boot/vmlin

```press TAB - for complete comand and after it append it with this:
```

root=/dev/sda5

```In result you must enter something like this:
```

linux /boot/vmlinuz-3.6.18-194.ubuntu root=/dev/sda5
```and press ENTER.
11. Enter this comand:
```

initrd /boot/initrd

```then press TAB for completing comand and ENTER for it applying.
12. Enter "boot" end press ENTER.
If all is correct you will be boot to your ubuntu. If so, then:
13. Repeat steps 3-6.
14. Run comand:
```

sudo burg-install /dev/sda

```15. ?????
16. Profit.

This helped for me. Now I have dual boot windows and Ubuntu. Please, correct me if I somwhere wrong... I'm very want to sleep, deep night now in my country))

---

### Post by YannBuntu on 2012-10-29
@Zoltor: good job :)
I think that BURG too is based on GRUB1.99, so you should definitely report the bug against GRUB2.00 here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug](https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug)

---

### Post by amtur_poet on 2013-01-25
Edit: Whoops, wrong thread. :P

---

