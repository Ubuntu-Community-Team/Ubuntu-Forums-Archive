---
title: "Grug, burg and dualboot."
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by Kaheil on 2010-12-27
Hello,

[FONT=Arial]I've reinstalled my setup quite a few times (dual boot windows/ubuntu, using windows for gaming) and I've installed burg. Ubuntu boots fine, but I get the following error [/FONT]when trying to boot on vista: 
"Found Windows Vista (loader) on /dev/mapper/isw_cicedciaeh_Raid01
/usr/sbin/burg-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cicedciaeh_Raid01.  Check your device.map."
[FONT=Arial]
I don't really know what that means, even less how to solve the problem. Could you help me?

Thank you :)[/FONT]

---

### Post by Malcolm Waterman on 2010-12-27
What options do you get when you boot up your system?

Also, I think that on my system there's the option of Windows Vista (loader), there isn't though Windows Vista. So are you sure that Windows is that option. On my system, there's the Vista loader. Then there's Microsoft Windows XP Professional. Also, I'm not sure if:> /dev/mapper/isw_cicedciaeh_Raid01 is actually a valid drive configuration.

---

### Post by Kaheil on 2010-12-27
[FONT=Arial]I'm completly sure that Vista is installed and used to work just fine, it's only recently that it has become unavailable. 

Complete log: 
[/FONT]
kaheil@Master:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/mapper/isw_cicedciaeh_Raid01
done
kaheil@Master:~$ sudo update-burg
Generating burg.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found Windows Vista (loader) on /dev/mapper/isw_cicedciaeh_Raid01
/usr/sbin/burg-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cicedciaeh_Raid01.  Check your device.map.
done

---

### Post by Malcolm Waterman on 2010-12-27
Try seeing if there's a Linux file called: >  /dev/mapper/isw_cicedciaeh_Raid01. If Burg is like Grub, which it should be similar since Burg is based on Grub, that should refer to a place on the Linux system. It also sounds like a Linux device.

---

### Post by Kaheil on 2010-12-27
There is a shortcut with that name, indeed.

PS: could reinstalling grub be of any use?

---

### Post by Malcolm Waterman on 2010-12-27
Possibly, I've never tried Burg. Since I've found the Grub interface fine and Grub always worked with me, it gave me options to my two OSes, on both of my machines, without problems. You can try installing Grub again.

First though, are you running Windows and Linux on the same hard drive. If you are you can test to see if there's a problem with Windows by going into the setup.

---

### Post by Kaheil on 2010-12-27
No, they running on separated harddrives.

---

### Post by Malcolm Waterman on 2010-12-27
During bootup there should be a keyboard combination or key stated with something like Boot Device, if you go into that you'll get a series of options. 

Theoretically, one of those options will be a CD drive, probably say CD or DVD in the name.
The selected option will probably be the Ubuntu hard drive.
There might be a option mentioning network or networking.
There'll probably be a fourth saying mentioning hard drive, hdd or something. 

If you go into the fourth and Windows loads, you'll know there's no problem with Windows. I feel that before reinstalling Grub you should find out if Windows is the problem. It shouldn't be a problem but Windows is not always very adaptable to problems.

If Windows doesn't load then there's probably a problem with Windows, probably related to Linux. At which point we'll know where the fault lies and perhaps we can sort it out. Just make a note of what's said. It might be a different option and I've never tried this sort of boot up before.

---

