---
title: "Help. How can I get my ubuntu back"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by oldnumber7 on 2006-06-15
Hi, 
I had Windows system machie and I installed ubuntu 5.10. The dual system works well. Suddenly Windows crash and I have to re-install Windows. I am sure my ubuntu is still there but I cannot load the boot menu with 'ubuntu, windowsxy'. How can I get my ubuntu back. Right now I can only access Windows system. Thanks.

---

### Post by bruce89 on 2006-06-15
Start up the Ubuntu CD in recovery mode, and when the prompt comes up type ```
grub-install /dev/hda1 
```
Actually, I now realise there is no recovery mode on the CD, why did this happen?

---

### Post by Jason_25 on 2006-06-15
You can probably just boot the live/install cd and run the same command.  I would use 
```

swapoff -a

```
before running that too.

---

### Post by oldnumber7 on 2006-06-15
I cannot find recovery mode on the CD, what can I do?

[QUOTE=Jason_25]You can probably just boot the live/install cd and run the same command.  I would use 
```

swapoff -a

```
before running that too.[/QUOTE]

---

### Post by oldnumber7 on 2006-06-15
I used the live cd to run ubuntu, but I cannot find any 'hda1, hda2..' something. 
Does that means my ubuntu gone? :(

[QUOTE=oldnumber7]I cannot find recovery mode on the CD, what can I do?[/QUOTE]

---

### Post by Jason_25 on 2006-06-15
[QUOTE=oldnumber7]I used the live cd to run ubuntu, but I cannot find any 'hda1, hda2..' something. 
Does that means my ubuntu gone? :([/QUOTE]
Post the output of 
```

sudo fdisk -l

```

---

### Post by oldnumber7 on 2006-06-15
after I use 'sudo fdisk -l', it shows:
device      boot      start       end      blocks           id    system
/dev/hda1                1         4            32098+     14  Hidden fat16
/dev/hda2  *             5      2299        18434587+   7   HPFS/NTFS
/dev/hda3             2300     3588        10353892+   83  Linux
/dev/hda4            3589     3648            481950      5  Extended
/dev/hda5             3589     3648           481918+    82  Linux swap/solris

but when I use 'grub-install /dev/hda3', after a long time, it shows:
"/dve/mapper/casper -snapshot does not have any corresponding BIOS driver"
What can I do for this ? thanks



[QUOTE=Jason_25]Post the output of 
```

sudo fdisk -l

```[/QUOTE]

---

### Post by anindya_m on 2006-06-15
Form your fsck output it appears that /dev/hda3 is the (~10GB) linux partition, and has all the directories (/etc , /usr, etc) on the same filesystem - good. Please do the following:

1. Boot up from the live cd into the GNOME desktop.
2. Open a terminal. Run the following:```
sudo -s
cd /
mkdir disk
mount /dev/hda3 disk
chroot /disk
grub-install /dev/hda
(some output here)
exit
exit
```Now reboot and the grub menu should appear. The important thing here is to chroot into the mounted image so that grub-install runs from your hard disk and finds all its files in the expected places.

regards,
Anindya

---

### Post by oldnumber7 on 2006-06-15
It works great! Thank you.

[QUOTE=anindya_m]Form your fsck output it appears that /dev/hda3 is the (~10GB) linux partition, and has all the directories (/etc , /usr, etc) on the same filesystem - good. Please do the following:

1. Boot up from the live cd into the GNOME desktop.
2. Open a terminal. Run the following:```
sudo -s
cd /
mkdir disk
mount /dev/hda3 disk
chroot /disk
grub-install /dev/hda
(some output here)
exit
exit
```Now reboot and the grub menu should appear. The important thing here is to chroot into the mounted image so that grub-install runs from your hard disk and finds all its files in the expected places.

regards,
Anindya[/QUOTE]

---

### Post by Marcelino on 2006-06-16
It doesn't work for me :(. When I type "grub-install /dev/hda" it return: "/dev/hda: Not found or not a block device.". The hda is my primary master...

---

