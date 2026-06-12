---
title: "Dual boot Ubuntu/XP with operational recovery partition"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by markjamie on 2007-12-05
Hi

I own an Acer laptop which currently runs Win XP and has the hidden partition for recovery of the OS. I'd like to dual boot this machine with Ubuntu. From reading around online, this seems very easy to do, however I also want to retain the feature of XP recovery from the hidden partition should I need it in the future.

At present, my disk paritions are as follows

C:\ 50GB FAT32 (Windows XP)
D:\ 50GB FAT32 (Data)

I would like to be able to reduce the size of C:\ and install Ubuntu in the free space (the easy part). Is is possible to retain the ability to recover Win XP with such a dual boot system on an Acer laptop? I'm familiar with the fact that Acer use customised MBRs which pick up Alt + F10 during boot up to allow recovery. If the Alt+F10 approach cannot be kept, is it possible to triple boot the system (XP, Ubuntu, Recovery partition) such that if I wish to recover win XP, I simply select boot #3?

Has anyone had experience of this and could offer me some advice?

Apologies for offering up a question that I'm sure you've seen a thousand times but I've looked hard and long and failed to find any solution. Everyone appears to simply accept the fact that dual boot will knacker Acer's e-recovery!!

Thanks

Mark

---

### Post by Pumalite on 2007-12-05
Have you thought of making a CD off your Recovery Partition?

---

### Post by Pumalite on 2007-12-05
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by markjamie on 2007-12-05
Thanks for your advice.

I've made recovery DVDs from the hidden partition, so in theory I can always recovery from those. From what I've heard using DVDs is a lot slower than direct D2D recovery from the hidden partition, so I'd rather not have to resort to them (of course there might not be a choice!)

Ideally I'd like to maintain the ability to recover from the hidden partition, with a dual boot XP/Ubuntu system.

---

### Post by Pumalite on 2007-12-05
You can use my first links without problems.

---

### Post by markjamie on 2007-12-05
Will this method not overwrite the acer customised MBR and hence remove the ability to boot into the recovery partition?

I really appreciate your help, I've had loads of troubles finding the right information.

---

### Post by Pumalite on 2007-12-05
Grub installs to MBR by default. You could try installing it to the partition and then booting it with Super Grub:[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by meierfra on 2007-12-05
You can  add ubuntu to the windows boot loader:

Boot from the LiveD.

Step 1)   Install Ubuntu. On the last screen click on the  "advanced" button and replace (hd0) by /dev/sda3. (Here  you need to replace sda3 by whatever partition Ubuntu is on)

Don't reboot immediately. Instead stay on the LiveCD.

Step 2) Mount your Windows partition:

```
sudo mount  -t ntfs-3g  /dev/sda2 /windows
```
(Here replace sda2 by whatever partition Windows is on)

Step 3) Copy the first sector of the Ubuntu partition to a file on  the Windows partition:

```
sudo dd if=/dev/sda3 of=/windows/ubuntu.bin bs=512 count=1
```
(Be very careful when using "dd". [Info on dd]("http://linuxreviews.org/man/dd/"))

Step 4)  Add ubuntu to the windows boot loader:

Open "boot.ini" from the Windows partition via
```
sudo gedit /windows/boot.ini
```

Add this line to the end of the file:
c:\ubuntu.bin="Ubuntu"

Save the file.

Reboot and you get  should get a menu with a Windows and Ubuntu choice.

---

### Post by markjamie on 2007-12-06
Thanks for your advice - I might try that at the weekend. Adding Ubuntu to the Windows bootloader should allow me to retain my current MBR and hence pick up the Alt+F10 command required during boot up to recover XP from the hidden partition - is that correct?

Apologies for being slow on this topic - I really appreciate everone's help.

Mark

---

### Post by meierfra on 2007-12-06
> Adding Ubuntu to the Windows bootloader should allow me to retain my current MBR and hence pick up the Alt+F10 command required during boot up to recover XP from the hidden partition - is that correct?

Yes.

---

### Post by markjamie on 2007-12-07
Fantastic -  hopefully give it a go this weekend.

You're a genius! Thanks for your advice. Will let you know if i all goes smoothly.

Mark

---

### Post by markjamie on 2007-12-09
Just thought I'd let you know it worked fine. I've now got an XP/Ubuntu dual boot laptop with the Acer recovery feature still intact!

Just got to sort out a couple of ATI driver errors

Thanks ever so much for your help.

Mark

---

