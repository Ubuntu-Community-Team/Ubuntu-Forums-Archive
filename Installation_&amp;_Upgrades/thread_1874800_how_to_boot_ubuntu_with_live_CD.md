---
title: "how to boot ubuntu with live CD"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by teodosio on 2011-11-03
Hi everyone!
Today I have changed my pc motherboard for another one. Before that I had Ubuntu 10.04 installed with no problems. After setting the new motherboard the Ubuntu doesn't boot at all. I tried to run it with the live original Ubuntu 10.04 CD but I can't boot it, the CD just gives me the chance of trying it or installing it. If I install it I will loose all data I had before, I guess. Anyone can help me doing to solve this problem?

---

### Post by MAFoElffen on 2011-11-03
> **teodosio said:**
> Hi everyone!
Today I have changed my pc motherboard for another one. Before that I had Ubuntu 10.04 installed with no problems. After setting the new motherboard the Ubuntu doesn't boot at all. I tried to run it with the live original Ubuntu 10.04 CD but I can't boot it, the CD just gives me the chance of trying it or installing it. If I install it I will loose all data I had before, I guess. Anyone can help me doing to solve this problem?
- First, what motherboard make/model? 
- Did "you" swap the motherboard? (lets me in on your skill level)
- Are you using the sme CPU or another CPU?  Same Architecture- x86 or x86_64?
- Does the motherboard go into BIOS Setup and after that does it POST?  
- After the post does it hit the hard disk and what... say no bootable OS installed?
- Do you have the hard disk on IDE, SCSI, SATA 2 or SATA 3 ports?
- Are you using the same Graphics GPU as before? What brand, model?

Last questions is on booting the LiveCD: Can you boot the LiveCD using TRY and get into the Live Image on the CD?  Please try that for a test.  If you can, then go to places and see if you can see hard disks and the partition where you have your install.  If you can see your install from a LiveCD, then I can tell you a way to mount the sytem externally.

If you have SATA disks, make sure they'er installed as SATA2... 

If you install as 10.04 alongside, it will create a new install.  If you normal, it will overwrite the old install...

There is some ways around all that, but.... Fix your old or reinstall-- both still hinge on seeing your hard disks.

---

### Post by Mark Phelps on 2011-11-04
> **teodosio said:**
> ... the CD just gives me the chance of trying it or installing it.

That is HOW it works!  To run Ubuntu in LiveCD mode, choose Try Ubuntu.

---

### Post by teodosio on 2011-11-04
Dear friend:
thanks for your interest in helping me. I'm sorry I can't answer you the first questions as I didn't personally made those changes. I may ask the friend who did it if it is crucial for solving the troubel.
As for your last questions, yes, with the live CD session, I can get into the computer and see the version of the Ubuntu 10.04 I had - and still have - installed before the changes and I even can get to all the files I had stored, the hard disks and the partitions.
Could you tell me how can I confirm if the SATA disks are installed as SATA2?
I would very much like if you could explain me how to mount the system externally as it would spare me a lot of time copying all the files I have inside the disks and installing everything again. 
So, thank you very much again for your interest and kind help. :)

Teodosio.

> **MAFoElffen said:**
> - First, what motherboard make/model? 
- Did "you" swap the motherboard? (lets me in on your skill level)
- Are you using the sme CPU or another CPU?  Same Architecture- x86 or x86_64?
- Does the motherboard go into BIOS Setup and after that does it POST?  
- After the post does it hit the hard disk and what... say no bootable OS installed?
- Do you have the hard disk on IDE, SCSI, SATA 2 or SATA 3 ports?
- Are you using the same Graphics GPU as before? What brand, model?

Last questions is on booting the LiveCD: Can you boot the LiveCD using TRY and get into the Live Image on the CD?  Please try that for a test.  If you can, then go to places and see if you can see hard disks and the partition where you have your install.  If you can see your install from a LiveCD, then I can tell you a way to mount the sytem externally.

If you have SATA disks, make sure they'er installed as SATA2... 

If you install as 10.04 alongside, it will create a new install.  If you normal, it will overwrite the old install...

There is some ways around all that, but.... Fix your old or reinstall-- both still hinge on seeing your hard disks.

---

### Post by MAFoElffen on 2011-11-05
> **teodosio said:**
> Dear friend:
thanks for your interest in helping me. I'm sorry I can't answer you the first questions as I didn't personally made those changes. I may ask the friend who did it if it is crucial for solving the troubel.
As for your last questions, yes, with the live CD session, I can get into the computer and see the version of the Ubuntu 10.04 I had - and still have - installed before the changes and I even can get to all the files I had stored, the hard disks and the partitions.
Could you tell me how can I confirm if the SATA disks are installed as SATA2?
I would very much like if you could explain me how to mount the system externally as it would spare me a lot of time copying all the files I have inside the disks and installing everything again. 
So, thank you very much again for your interest and kind help. :)

Teodosio.
First 2 questions are not cruical.  Seeing the install from the LiveCD tells me it is not SATA3. Linux doesn't support SATA3 yet...

Do you have 2 hard disks? If so, either switch the cables on the hard disks -or- it might have a BIOS boot drive setting where you can change the order of multiple hard disk boot-order -or- if the BIOS has a boot hotkey to change the boot drive order ...

What I'm thing there is that there should be no logical reason that is should not boot and run, except if had more than one hard disk and during the swap that order is now different. Say grub was install to sda... which in the swap is now sdb and the BIOS is still point to sda.

Try that first and get back to me. Even if your MBA was borked, since you can see everything from a LiveCD, then I'll guide you through mounting your install OS and installing grub from the LiveCD.

---

### Post by teodosio on 2011-11-05
Dear MAFoElffen:

YES! I don't have my problem solved but, thanks to you, I guess it will not be far from solving it! I could'nt change the cables because the hard disk where my Ubuntu is installed has a different cable. It's red and thinner. Before last thursday changes all the 2 hard disks were connected with the same cable, that traditional large cable. Of course the hard drive were the ubuntu is was connected to the other through an adaptator as it is more recent that the other hard disk. Now, with the hardware changes the adaptator is not necessary and it was removed.
Well, after reading you I decided first to disconect the cable from the hard disk I use just to store files. And guess what? The computer BOOTED and RUN as it allways did!\\:D/
So it is easier, I guess, to solve this! I just need you to explain me how can I have the 2 hdd's connected at the same time. I went to the Bios to change the order of booting, tryied every combination but nothing has resulted. I guess the trick is in the cables connecting, but I do I do it? I send you a picture of the situation.
Appreciated very much if you could help me once again...
Teodosio.

> **MAFoElffen said:**
> First 2 questions are not cruical.  Seeing the install from the LiveCD tells me it is not SATA3. Linux doesn't support SATA3 yet...

Do you have 2 hard disks? If so, either switch the cables on the hard disks -or- it might have a BIOS boot drive setting where you can change the order of multiple hard disk boot-order -or- if the BIOS has a boot hotkey to change the boot drive order ...

What I'm thing there is that there should be no logical reason that is should not boot and run, except if had more than one hard disk and during the swap that order is now different. Say grub was install to sda... which in the swap is now sdb and the BIOS is still point to sda.

Try that first and get back to me. Even if your MBA was borked, since you can see everything from a LiveCD, then I'll guide you through mounting your install OS and installing grub from the LiveCD.

---

### Post by MAFoElffen on 2011-11-05
> **teodosio said:**
> Dear MAFoElffen:

YES! I don't have my problem solved but, thanks to you, I guess it will not be far from solving it! I could'nt change the cables because the hard disk where my Ubuntu is installed has a different cable. It's red and thinner. Before last thursday changes all the 2 hard disks were connected with the same cable, that traditional large cable. Of course the hard drive were the ubuntu is was connected to the other through an adaptator as it is more recent that the other hard disk. Now, with the hardware changes the adaptator is not necessary and it was removed.
Well, after reading you I decided first to disconect the cable from the hard disk I use just to store files. And guess what? The computer BOOTED and RUN as it allways did!\\:D/
So it is easier, I guess, to solve this! I just need you to explain me how can I have the 2 hdd's connected at the same time. I went to the Bios to change the order of booting, tryied every combination but nothing has resulted. I guess the trick is in the cables connecting, but I do I do it? I send you a picture of the situation.
Appreciated very much if you could help me once again...
Teodosio.
Okay... Here goes.  Hook your drives back up... These instructions are for booting, mounting for installed system and reinstalling Grub.  Pick "sda" for the boot drive as that is the one your BIOS boots from, the first drive. It sounds as if you SATA drive now ends up as being sdb or the second drive.

1. Boot on the LiveCD. Needs to be same version and architecture of installed.)

2. Open a terminal session

3. Determine your normal system partition - (the switch is a lowercase "L")
```

sudo fdisk -l

```If you aren't sure, run **df -Th**. Look for the correct disk size and ext3 or ext4 format. 


4. Mount your normal system partition: 

 - Substitute the correct partition: sda1, sdb5, etc. 
```

sudo mount /dev/sdXX /mnt

``` - Example: *sudo mount /dev/sda1 /mnt* 

5. sdYY is the /boot partition designation 
```

sudo mount /dev/sdYY /mnt/boot

``` - Example: sudo mount /dev/sdb6 /mnt/boot 

6. Mount the critical virtual filesystems. Run the following as a single command: 
```

for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done

```7. Chroot into your normal system device: 
```

sudo chroot /mnt

```8. Here is too separate options... 

  a. Sometimes this happens during an install where Grub is installed but the the menu was not generated.  If there is no /boot/grub/grub.cfg or it's not correct, create one using 
[FONT=monospace][/FONT]```
update-grub

``` b. If Grub was not installed during the install- Reinstall GRUB 2: 

9. Substitute the correct device - sda, sdb, etc. Do *not* specify a partition number. 
```

grub-install /dev/sdX

```10. Verify the install (use the correct device, for example *sda*. Do *not* specify a partition): 
```

grub-install --recheck /dev/sdX

```11. Exit *chroot*: **CTRL-D** on keyboard 


12. Unmount virtual filesystems. Run the following as a single command: 
```

for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done

```13. If you mounted a separate /boot partition: 
```

sudo umount /mnt/boot

```14. Unmount last device: 
```

sudo umount /mnt

```15. Reboot.
```

sudo reboot

```

---

### Post by teodosio on 2011-11-06
Dear MaFO:

I'm despairing! I did everything you said, but it still doesn't boot after that! Here is the serial of procedures I did. Will I beeing dumm in any step?

ubuntu@ubuntu:~$ sudo fdisk -l


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008db94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00072cf5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38551   309657600   83  Linux
/dev/sdb2           38551       38914     2911233    5  Extended
/dev/sdb5           38551       38914     2911232   82  Linux swap / Solaris

ubuntu@ubuntu:~$ df -Th

Tipo de Sistema de Ficheiros    Tamanho Utilizado disponível Use% Montado em
aufs          aufs    502M   19M  484M   4% /
none      devtmpfs    497M  260K  497M   1% /dev
/dev/sr0   iso9660    700M  700M     0 100% /cdrom
/dev/loop0
          squashfs    672M  672M     0 100% /rofs
none         tmpfs    502M  228K  501M   1% /dev/shm
tmpfs        tmpfs    502M   12K  502M   1% /tmp
none         tmpfs    502M   92K  502M   1% /var/run
none         tmpfs    502M     0  502M   0% /var/lock
none         tmpfs    502M     0  502M   0% /lib/init/rw


ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/boot

ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done

ubuntu@ubuntu:~$ sudo chroot /mnt

root@ubuntu:/# update-grub
Generating grub.cfg ...
done

root@ubuntu:/# grub-install /dev/sdb
Installation finished. No error reported.

root@ubuntu:/# grub-install --recheck /dev/sdb
Installation finished. No error reported.

root@ubuntu:/# exit

ubuntu@ubuntu:~$ for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done

ubuntu@ubuntu:~$ sudo umount /mnt/boot

ubuntu@ubuntu:~$ sudo umount /mnt

ubuntu@ubuntu:~$ 

sudo reboot


> **MAFoElffen said:**
> Okay... Here goes.  Hook your drives back up... These instructions are for booting, mounting for installed system and reinstalling Grub.  Pick "sda" for the boot drive as that is the one your BIOS boots from, the first drive. It sounds as if you SATA drive now ends up as being sdb or the second drive.

1. Boot on the LiveCD. Needs to be same version and architecture of installed.)

2. Open a terminal session

3. Determine your normal system partition - (the switch is a lowercase "L")
```

sudo fdisk -l

```If you aren't sure, run **df -Th**. Look for the correct disk size and ext3 or ext4 format. 


4. Mount your normal system partition: 

 - Substitute the correct partition: sda1, sdb5, etc. 
```

sudo mount /dev/sdXX /mnt

``` - Example: *sudo mount /dev/sda1 /mnt* 

5. sdYY is the /boot partition designation 
```

sudo mount /dev/sdYY /mnt/boot

``` - Example: sudo mount /dev/sdb6 /mnt/boot 

6. Mount the critical virtual filesystems. Run the following as a single command: 
```

for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done

```7. Chroot into your normal system device: 
```

sudo chroot /mnt

```8. If there is no /boot/grub/grub.cfg or it's not correct, create one using 
[FONT=monospace]```


```[/FONT]```
update-grub

```Reinstall GRUB 2: 

9. Substitute the correct device - sda, sdb, etc. Do *not* specify a partition number. 
```

grub-install /dev/sdX

```10. Verify the install (use the correct device, for example *sda*. Do *not* specify a partition): 
```

grub-install --recheck /dev/sdX

```11. Exit *chroot*: **CTRL-D** on keyboard 


12. Unmount virtual filesystems. Run the following as a single command: 
```

for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done

```13. If you mounted a separate /boot partition: 
```

sudo umount /mnt/boot

```14. Unmount last device: 
```

sudo umount /mnt

```15. Reboot.
```

sudo reboot

```

---

### Post by MAFoElffen on 2011-11-06
> **teodosio said:**
> Dear MaFO:

I'm despairing! I did everything you said, but it still doesn't boot after that! Here is the serial of procedures I did. Will I beeing dumm in any step?

ubuntu@ubuntu:~$ sudo fdisk -l


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008db94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00072cf5

   Device Boot      Start         End      Blocks   Id  System
[COLOR=Red]/dev/sdb1   *           1       38551   309657600   83  Linux[/COLOR]
/dev/sdb2           38551       38914     2911233    5  Extended
/dev/sdb5           38551       38914     2911232   82  Linux swap / Solaris

ubuntu@ubuntu:~$ df -Th

Tipo de Sistema de Ficheiros    Tamanho Utilizado disponível Use% Montado em
aufs          aufs    502M   19M  484M   4% /
none      devtmpfs    497M  260K  497M   1% /dev
/dev/sr0   iso9660    700M  700M     0 100% /cdrom
/dev/loop0
          squashfs    672M  672M     0 100% /rofs
none         tmpfs    502M  228K  501M   1% /dev/shm
tmpfs        tmpfs    502M   12K  502M   1% /tmp
none         tmpfs    502M   92K  502M   1% /var/run
none         tmpfs    502M     0  502M   0% /var/lock
none         tmpfs    502M     0  502M   0% /lib/init/rw


ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/boot

ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done

ubuntu@ubuntu:~$ sudo chroot /mnt

root@ubuntu:/# update-grub
Generating grub.cfg ...
done

root@ubuntu:/# [COLOR=Red]grub-install /dev/sdb[/COLOR]
Installation finished. No error reported.

root@ubuntu:/# [COLOR=Red]grub-install --recheck /dev/sdb[/COLOR]
Installation finished. No error reported.

root@ubuntu:/# exit

ubuntu@ubuntu:~$ for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done

ubuntu@ubuntu:~$ sudo umount /mnt/boot

ubuntu@ubuntu:~$ sudo umount /mnt

ubuntu@ubuntu:~$ 

sudo reboot
LOL- You mounted your system, but you installed the Grub MBR to your second disk instead of the first.  The first is where your BIOS is looking to for a disk to boot.  The current second disk is where it was installed to and where the BIOS can't find it... Remember?  What we need to do is mount the system on the second disk and install the MBR (boot sector) to the first disk... Doing that, Bios will find it and That Grub MBR will point to the installed partition on the second disk... 

Now that I know your installed layout, here is "your" instructions, tailored to you and yours. Mount your installed system and install grub:

1. Boot a Live-CD. Use the :Try" menu item.  Open a terminal session.
2. Your "Installed" partition is. [COLOR=Red]/dev/sdb1[/COLOR] (where you've installed the OS ... the "/" partition)
```

sudo mount /dev/[COLOR=Teal]sdb1[/COLOR] /mnt

```3. Mount the installed system
```

sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -t proc /proc /mnt/proc

```4. "changeroot" to /mnt
```

sudo chroot /mnt /bin/bash

```5. Now you're "on" your installed system... Install grub to your first disk, where on your PC, your BIOS looks:
```

sudo grub-install --root-directory=/mnt /dev/[COLOR=Green]sda[/COLOR]

```6. Now we need to get out of the chroot with the keyboard hot-key: <cntrl><d>

7. Now we unmount our mount. 
```

sudo umount /mnt

```8. Now we reboot.  From the LiveCD you can choose to reboot- it will shutdown and ask you to remove the LiveCD...

---

### Post by teodosio on 2011-11-06
Hi MAFoElffen!
Waters are not very clear around here and gods aren't definitively on my side. :confused: I got this:

ubuntu@ubuntu:~$ sudo mount /dev/sdb /mnt
mount: /dev/sdb already mounted or /mnt busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
mount: /dev/sdb1 already mounted or /mnt busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# sudo grub-install --root-directory=/mnt /dev/sda
sudo: unable to resolve host ubuntu
Installation finished. No error reported.
root@ubuntu:/# exit
ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ 

I don't know what to tell you more and how to thank you for all this... but I really can't make it work right!


> **MAFoElffen said:**
> LOL- You mounted your system, but you installed the Grub MBR to your second disk instead of the first.  The first is where your BIOS is looking to for a disk to boot.  The current second disk is where it was installed to and where the BIOS can't find it... Remember?  What we need to do is mount the system on the second disk and install the MBR (boot sector) to the first disk... Doing that, Bios will find it and That Grub MBR will point to the installed partition on the second disk... 

Now that I know your installed layout, here is "your" instructions, tailored to you and yours. Mount your installed system and install grub:

1. Boot a Live-CD. Use the :Try" menu item.  Open a terminal session.
2. Your "Installed" partition is. [COLOR=Red]/dev/sdb1[/COLOR] (where you've installed the OS ... the "/" partition)
```

sudo mount /dev/sdb /mnt

```3. Mount the installed system
```

sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -t proc /proc /mnt/proc

```4. "changeroot" to /mnt
```

sudo chroot /mnt /bin/bash

```5. Now you're "on" your installed system... Install grub to your first disk, where on your PC, your BIOS looks:
```

sudo grub-install --root-directory=/mnt /dev/[COLOR=Green]sda[/COLOR]

```6. Now we need to get out of the chroot with the keyboard hot-key: <cntrl><d>

7. Now we unmount our mount. 
```

sudo umount /mnt

```8. Now we reboot.  From the LiveCD you can choose to reboot- it will shutdown and ask you to remove the LiveCD...

---

### Post by MAFoElffen on 2011-11-06
> **teodosio said:**
> Hi MAFoElffen!
Waters are not very clear around here and gods aren't definitively on my side. :confused: I got this:

ubuntu@ubuntu:~$ sudo mount /dev/sdb /mnt
mount: /dev/sdb already mounted or /mnt busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
mount: /dev/sdb1 already mounted or /mnt busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# sudo grub-install --root-directory=/mnt /dev/sda
sudo: unable to resolve host ubuntu
Installation finished. No error reported.
root@ubuntu:/# exit
ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ 

I don't know what to tell you more and how to thank you for all this... but I really can't make it work right!LOL!  We all had to start learning somehow.  I know it's a bit more stressful if your learning and trying to fix something at the same time.
> 
***[SIZE=3][COLOR=Green]"Don't worry, you'll be fine; I saw it work in a cartoon once..."[/COLOR][/SIZE]***
It was a fresh install... As long as it's isolated to that disk and partition, there is nothing that you could do to anything there that couldn't be saved or reinstalled, right?  I wish I was there to help and this would be over in a matter of minutes... But it isn't that way, so we have to paint a picture to each other so that we both understand what is going on. I know your sense of adventure on this is probably wearing thin, so I'll try to be clear and concise with my instructions.

Problems you had said you already had sda1 mounted, therefore sda1 could not be mounted.

If after you booted the LiveCD- if you looked at the disks with the file manager, it would have mounted it with a mount name and poof, those commands wouldn't work (and therefore the error saying it was already mounted or busy).  So.. 

----------------------------------------------------------------------------------------
Reboot and try again please.  This time, immediately when you the desktop appears:  Stop and take a breath. Relax.

Then gently press <cntrl><alt><t>.  That will bring up a terminal session.

Then do the commands I wrote out for you in  Post #9.  Note that I changed the first command... If you get an error on any of them, STOP, reboot and start again.

Don't worry - I'm very patient and empathic.

---

### Post by teodosio on 2011-11-08
Hi MAFoElffen!

Yes, I took a deep breath and relaxed. Then I've repeated your post #9 commands :P and here's what I got in several tries:

try 1
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount -t proc /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# sudo grub-install --root-directory=/mnt /dev/sda
sudo: unable to resolve host ubuntu
Installation finished. No error reported.
root@ubuntu:/# exit
ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ 

try 2
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# sudo grub-install --root-directory=/mnt /dev/sda
sudo: unable to resolve host ubuntu
Installation finished. No error reported.
root@ubuntu:/# exit
ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ 

try 3
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# sudo grub-install --root-directory=/mnt /dev/sda
sudo: unable to resolve host ubuntu
Installation finished. No error reported.
root@ubuntu:/# exit
ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ 
:-({|=

So, although what I've seen in cartoons it still didn't work. In the boot start I still can read "Secondary master: sata device not found.
And if I go to the disk properties - with the live cd - I can see the pictures I post now. The disk where the system is installed is the one with 320 Gb.
Hope this information to be useful. Thanks again for your patience and sympathy from someone who is despairing.

Teodosio.




> **MAFoElffen said:**
> LOL!  We all had to start learning somehow.  I know it's a bit more stressful if your learning and trying to fix something at the same time.
It was a fresh install... As long as it's isolated to that disk and partition, there is nothing that you could do to anything there that couldn't be saved or reinstalled, right?  I wish I was there to help and this would be over in a matter of minutes... But it isn't that way, so we have to paint a picture to each other so that we both understand what is going on. I know your sense of adventure on this is probably wearing thin, so I'll try to be clear and concise with my instructions.

Problems you had said you already had sda1 mounted, therefore sda1 could not be mounted.

If after you booted the LiveCD- if you looked at the disks with the file manager, it would have mounted it with a mount name and poof, those commands wouldn't work (and therefore the error saying it was already mounted or busy).  So.. 

----------------------------------------------------------------------------------------
Reboot and try again please.  This time, immediately when you the desktop appears:  Stop and take a breath. Relax.

Then gently press <cntrl><alt><t>.  That will bring up a terminal session.

Then do the commands I wrote out for you in  Post #9.  Note that I changed the first command... If you get an error on any of them, STOP, reboot and start again.

Don't worry - I'm very patient and empathic.

---

### Post by MAFoElffen on 2011-11-08
> **teodosio said:**
> Hi MAFoElffen!

Yes, I took a deep breath and relaxed. Then I've repeated your post #9 commands :P and here's what I got in several tries:

try 1
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount -t proc /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
[COLOR=Red]root@ubuntu:/# sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]
sudo: unable to resolve host ubuntu
Installation finished. No error reported.
root@ubuntu:/# exit
ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ 

try 2
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# sudo grub-install --root-directory=/mnt /dev/sda
sudo: unable to resolve host ubuntu
Installation finished. No error reported.
root@ubuntu:/# exit
ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ 

try 3
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# sudo grub-install --root-directory=/mnt /dev/sda
sudo: unable to resolve host ubuntu
Installation finished. No error reported.
root@ubuntu:/# exit
ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ 
:-({|=

So, although what I've seen in cartoons it still didn't work. In the boot start I still can read "Secondary master: sata device not found.
And if I go to the disk properties - with the live cd - I can see the pictures I post now. The disk where the system is installed is the one with 320 Gb.
Hope this information to be useful. Thanks again for your patience and sympathy from someone who is despairing.

Teodosio.
Soory- when you do the chroot... notice the prompt change?  command at that prompt should instead be 
```

root@ubuntu:/#  grub-install --root-directory=/mnt /dev/sda

```Because you are already "root" at that point, so do not need to use "sudo"... Please try again.

---

### Post by teodosio on 2011-11-08
Again I have tried.
After the chroot the prompt doesn't change, the installation happens and no error message. The erros message seems to be after last command. Here it is what I got:

ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
root@ubuntu:/# exit
ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ 

:confused:


> **MAFoElffen said:**
> Soory- when you do the chroot... notice the prompt change?  command at that prompt should instead be 
```

root@ubuntu:/#  grub-install --root-directory=/mnt /dev/sda

```Because you are already "root" at that point, so do not need to use "sudo"... Please try again.

---

### Post by MAFoElffen on 2011-11-08
Does it boot now?

---

### Post by teodosio on 2011-11-08
No it doesn't!
Same situation!
Grrrr......

> **MAFoElffen said:**
> Does it boot now?

---

### Post by MAFoElffen on 2011-11-08
> **teodosio said:**
> No it doesn't!
Same situation!
Grrrr......Try it again with a few changes.

After the "grub-install --root-directory=/mnt /dev/sda", do this:
```

update-grub

```Go until until the umount... In the unmount command, try it. If it says it's busy, then do this:
```

sudo umount -f /mnt

```Which should force the unmount, even if the status is busy.

Then reboot and test.

---

### Post by teodosio on 2011-11-09
Same results! :confused:
The forced umount doesn't work: Look at this:

```
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-34-generic
Found initrd image: /boot/initrd.img-2.6.32-34-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found linux image: /boot/vmlinuz-2.6.32-32-generic
Found initrd image: /boot/initrd.img-2.6.32-32-generic
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-30-generic
Found initrd image: /boot/initrd.img-2.6.32-30-generic
Found linux image: /boot/vmlinuz-2.6.32-29-generic
Found initrd image: /boot/initrd.img-2.6.32-29-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done
root@ubuntu:/# exit
ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ sudo umount -f /mnt
umount2: Dispositivo ou recurso ocupado
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount2: Dispositivo ou recurso ocupado 
```

I'm passing away!!!!!!!!


MAFoElffen;11439276]Try it again with a few changes.

After the "grub-install --root-directory=/mnt /dev/sda", do this:
```

update-grub

```Go until until the umount... In the unmount command, try it. If it says it's busy, then do this:
```

sudo umount -f /mnt

```Which should force the unmount, even if the status is busy.

Then reboot and test.[/QUOTE]

---

### Post by Hakunka-Matata on 2011-11-09
```
das@sdb1GUID:~$ sudo mount /dev/sdb4 /mnt
[sudo] password for das: 
mount: special device /dev/sdb4 does not exist
das@sdb1GUID:~$ sudo mount /dev/sdc4 /mnt
das@sdb1GUID:~$ sudo mount -o bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
das@sdb1GUID:~$
```


As you may see right away, I've tested your command series by copying and pasting, notice the output produced.

**EDIT: please suppy output of ```
sudo ls -l /mnt
```**

---

### Post by Hakunka-Matata on 2011-11-09
[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

```

**ChRoot**

 This method of installation uses the *chroot*  command to gain access to the broken system's files. Once the chroot  command is issued, the LiveCD treats the broken system's / as its own.  Commands run in a chroot environment will affect the broken systems  filesystems and not those of the LiveCD. 

[LIST=1]
[*]Boot to the LiveCD Desktop. The CD should be the same release and architecture (32/64 bit).
[*]Open a terminal - *Applications, Accessories, Terminal*.
[*]Determine your normal system partition - (the switch is a lowercase "L") sudo fdisk -l
[LIST]
[*]If you aren't sure, run **df -Th**. Look for the correct disk size and ext3 or ext4 format.
[/LIST]
 
[*]Mount your normal system partition:
[LIST]
[*]Substitute the correct partition: sda1, sdb5, etc.
[/LIST]
sudo mount /dev/sdXX /mnt
[LIST]
[*]Example: ***sudo mount /dev/sda1 /mnt***
[/LIST]
 
[*]*Only if you have a separate boot partition*:
[LIST]
[*]sdYY is the /boot partition designation
[/LIST]
sudo mount /dev/sdYY /mnt/boot
[LIST]
[*]Example: **sudo mount /dev/sdb6 /mnt/boot**
[/LIST]
 
[*]Mount the critical virtual filesystems. Run the following as a single command: **for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done**
[*]Chroot into your normal system device: **sudo chroot /mnt**
[*]If there is no /boot/grub/grub.cfg or it's not correct, create one using update-grub
[*]Reinstall GRUB 2:
[LIST]
[*]Substitute the correct device - sda, sdb, etc. Do *not* specify a partition number.
[/LIST]
**grub-install /dev/sdX**
[*]Verify the install (use the correct device, for example *sda*. Do *not* specify a partition): 
**grub-install --recheck /dev/sdX**
[*]Exit *chroot*: **CTRL-D** on keyboard
[*]Unmount virtual filesystems. Run the following as a single command: **for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done**
[*]If you mounted a separate /boot partition:
[LIST]
[*]**sudo umount /mnt/boot**
[/LIST]
 
[*]Unmount last device: sudo umount /mnt
[*]Reboot. **sudo reboot**
[/LIST]

```

---

### Post by teodosio on 2011-11-09
> **Hakunka-Matata said:**
> ```
das@sdb1GUID:~$ sudo mount /dev/sdb4 /mnt
[sudo] password for das: 
mount: special device /dev/sdb4 does not exist
das@sdb1GUID:~$ sudo mount /dev/sdc4 /mnt
das@sdb1GUID:~$ sudo mount -o bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
das@sdb1GUID:~$
```
As you may see right away, I've tested your command series by copying and pasting, notice the output produced.

**EDIT: please suppy output of ```
sudo ls -l /mnt
```**

The output was:
ubuntu@ubuntu:~$ sudo ls -l /mnt
total 0
ubuntu@ubuntu:~$

---

### Post by teodosio on 2011-11-09
Dear friends,
after all the attempts I did on your advice, the only way my PC boots is by removing the second hard drive I had and where I used to store my files. That was what I did. Now I'm writting from my beloved Ubuntu pc and everything seems perfect... 
As for that hdd I won't give up to find the way of re-installing it and have my ubuntu booting as well as it did before the motherboard change... if you can help me I will appreciate, if you can't I'm also grateful for the help you gave me through last days. 
Thank you.
T.

---

### Post by MAFoElffen on 2011-11-10
> **teodosio said:**
> Dear friends,
after all the attempts I did on your advice, the only way my PC boots is by removing the second hard drive I had and where I used to store my files. That was what I did. Now I'm writting from my beloved Ubuntu pc and everything seems perfect... 
As for that hdd I won't give up to find the way of re-installing it and have my ubuntu booting as well as it did before the motherboard change... if you can help me I will appreciate, if you can't I'm also grateful for the help you gave me through last days. 
Thank you.
T.
No problem with that.... The error on the "unmount" should not have had any impact on the installing grub.  Since it was after... the most it would have done was hung your machine while trying to shutdown because it still mounted... But if it was still mounted on the LiveCD, it would also show up as a mount on the desktop, where you could right-click and unmount it from there... 

Beyond that, the results back from the grub install:
> 
root@ubuntu:/# grub-install --root-directory=/mnt /dev/sda 
Installation finished. No error reported.[FONT=monospace]

[/FONT]root@ubuntu:/# update-grub Generating grub.cfg ... 
Found linux image: /boot/vmlinuz-2.6.32-34-generic 
Found initrd image: /boot/initrd.img-2.6.32-34-generic 
Found linux image: /boot/vmlinuz-2.6.32-33-generic 
Found initrd image: /boot/initrd.img-2.6.32-33-generic 
Found linux image: /boot/vmlinuz-2.6.32-32-generic 
Found initrd image: /boot/initrd.img-2.6.32-32-generic 
Found linux image: /boot/vmlinuz-2.6.32-31-generic 
Found initrd image: /boot/initrd.img-2.6.32-31-generic 
Found linux image: /boot/vmlinuz-2.6.32-30-generic 
Found initrd image: /boot/initrd.img-2.6.32-30-generic 
Found linux image: /boot/vmlinuz-2.6.32-29-generic 
Found initrd image: /boot/initrd.img-2.6.32-29-generic 
Found linux image: /boot/vmlinuz-2.6.32-28-generic 
Found initrd image: /boot/initrd.img-2.6.32-28-generic 
Found linux image: /boot/vmlinuz-2.6.32-27-generic 
Found initrd image: /boot/initrd.img-2.6.32-27-generic 
Found linux image: /boot/vmlinuz-2.6.32-26-generic 
Found initrd image: /boot/initrd.img-2.6.32-26-generic 
Found linux image: /boot/vmlinuz-2.6.32-25-generic 
Found initrd image: /boot/initrd.img-2.6.32-25-generic 
Found linux image: /boot/vmlinuz-2.6.32-24-generic 
Found initrd image: /boot/initrd.img-2.6.32-24-generic 
Found linux image: /boot/vmlinuz-2.6.32-21-generic 
Found initrd image: /boot/initrd.img-2.6.32-21-generic 
Found memtest86+ image: /boot/memtest86+.bin 
done [FONT=monospace]
[/FONT]Seemed like it installed fine with no errors. Although if it didn't boot, then  "somehow" it really didn't install corectly. Right not I'm a little confused on this also. Like it's playing ghost.

---

### Post by Hakunka-Matata on 2011-11-10
> **teodosio said:**
> The output was:
ubuntu@ubuntu:~$ sudo ls -l /mnt
total 0
ubuntu@ubuntu:~$

That is _***NOT***_ the command I sent, copy my command to the command line, you typed it with a space missing.

---

### Post by MAFoElffen on 2011-11-10
> **Hakunka-Matata said:**
> That is _***NOT***_ the command I sent, copy my command to the command line, you typed it with a space missing.
That command would assume that the mnt was still active, so it would be executed after mounting something... So just copying that command, which is asking to list the directory of a mount called mnt in long format, to the commandline and executing it without anything mounted to mount, would return that error, right? (Just a little push in the right direction with that...)

---

### Post by teodosio on 2011-11-11
I didn't try yet because, as I have said, I decided to unconnect the 2nd hard drive from the pc and I'm just using the main hard drive (sdb1) which now, isolated, appears to be sda!
I'm trying to win some courage to repeat every command you both sent me. Anyway I wonder to myself if the problem wouldn't come from the hardware hdd's conections. As I told before, one hdd is older that the other one - where the ubuntu is - and the conections are different. I say this because when I went to the BIOS I never saw the 2 hard disks listed and I don't know why. But these are only suppositions...

> **MAFoElffen said:**
> That command would assume that the mnt was still active, so it would be executed after mounting something... So just copying that command, which is asking to list the directory of a mount called mnt in long format, to the commandline and executing it without anything mounted to mount, would return that error, right? (Just a little push in the right direction with that...)

---

### Post by Hakunka-Matata on 2011-11-11
yes, only disk was sdb, and now appearing as sda, no errors there!

Interesting what  you say about your HDDs being distinct.  Is one a SATA and the other an IDE/PATA, where you may select it's mode of appearance to first time visitors?  
I'll guess you have an older IDE/PATA HDD and it's jumpered to appear as a Slave drive.  If that is the case, and it's the only drive on that PATA cable, I suggest your change it to a Master.  Mixed mode and then the second level/mode "Master - Slave" sometimes make goofy guesses, like me.  
What do you have?

---

### Post by teodosio on 2011-11-12
When I go to the Bios I can find this:
IDE Primary Master: none
IDE Primary Slave: ST3800 11A
IDE Secondary Master: none
IDE Secondary Slave: Philips etc... the CD ROM

The STT3800 is the old hdd which is a Barracuda 7200.T

The strange thing is that when I leave the Bios configurations and the computer continues to boot,  before the unsusccess boot ends, I can read this:

Primary master: WDC WD3200AAKS-00V1A0
Secondary master: [SATA device not found]

The WDC.... is the new hdd where the ubuntu system is, which is an wetern digital 320 Gb SATA.

These facts are the ones who make me wonder that this may be a conection problem.

As for the command Hakunka-Matata told me, yes I put it correctly and I got the same:
ubuntu@ubuntu:~$ sudo ls -l  /mnt
total 0
Grrrr!

> **Hakunka-Matata said:**
> yes, only disk was sdb, and now appearing as sda, no errors there!

Interesting what  you say about your HDDs being distinct.  Is one a SATA and the other an IDE/PATA, where you may select it's mode of appearance to first time visitors?  
I'll guess you have an older IDE/PATA HDD and it's jumpered to appear as a Slave drive.  If that is the case, and it's the only drive on that PATA cable, I suggest your change it to a Master.  Mixed mode and then the second level/mode "Master - Slave" sometimes make goofy guesses, like me.  
What do you have?

---

### Post by MAFoElffen on 2011-11-12
> **teodosio said:**
> When I go to the Bios I can find this:
IDE Primary Master: none
IDE Primary Slave: ST3800 11A
IDE Secondary Master: none
IDE Secondary Slave: Philips etc... the CD ROM

The STT3800 is the old hdd which is a Barracuda 7200.T

The strange thing is that when I leave the Bios configurations and the computer continues to boot,  before the unsusccess boot ends, I can read this:

Primary master: WDC WD3200AAKS-00V1A0
Secondary master: [SATA device not found]

The WDC.... is the new hdd where the ubuntu system is, which is an wetern digital 320 Gb SATA.

These facts are the ones who make me wonder that this may be a conection problem.

As for the command Hakunka-Matata told me, yes I put it correctly and I got the same:
ubuntu@ubuntu:~$ sudo ls -l  /mnt
total 0
Grrrr!
As I tried to explain, but will in simpler terms... You didn't have anything mounted, so it returned the correct data = 0.  If your had done the previous mount coummands and then mounted the system--> Then use that command, you could then see if that the list of files where from your installed partition, to confirm that you have a correct mount.

What could have also been done is to use the --verify option to check it, but that is broke and instaead of checking to see if it is there, it reinstalls again.

IDE and PATA- I have 3 boards with the combo.  In BIOS it's natural order goes PATA > SATA > eSATA > Removable USB > SCSI RAID ... Natural Drive order goes: 
PATA 
 - Primary Master 
 - Primary Slave 
 - Secondary Master 
 - Secondary Slave
SATA
 - Port #1
etc, etc

Me I can override and change my boot drive order, even on a primary master or slave... I remember boards like the OP's.  It searches down the list and whatecer it finds in that order is how it gets assigned.  Changing a PATA slave to master will not change it's order relate to SATA.

Once he gets grub installed > the MBR on a Boot Drive pointing to his install > then he's back.  Unfortunating the twist in this is the OP's boot drive is locked to whatever is the first drive assigned.... and something is going on with not reinstall grub when he has both drives in?

@Hakunka-Matata-->
You are a fresh perspective here.  Theres something in this that just doesn't seem right nor logical.  What should and has worked is not working for this OP.  Any ideas?

---

### Post by Hakunka-Matata on 2011-11-12
Using PATA/IDE HDDs and SATA drives on the same motherboard has proven problematic (I read it in the forums after all!).  

I would re-jumper both IDE devices to be MASTER, for starters.  
Another combo would be put **both IDE devices on same cable**, jumpered as one master, and one slave.
unplug some drives and see what fdisk or gparted reports for drive assignments

---

### Post by MAFoElffen on 2011-11-12
> **Hakunka-Matata said:**
> Using PATA/IDE HDDs and SATA drives on the same motherboard has proven problematic (I read it in the forums after all!).  

I would re-jumper both IDE devices to be Slave, for starters.  
Another combo would be put both IDE devices on same cable, jumpered as one master, and one slave.
unplug some drives and see what fdisk or gparted reports for drive assignments
The OP had both drives on the same cable with a PATA-to-SATA adapter- the SATA as the master. Therefore the PATA being jumpered as slave.  SATA don't have jumpers, but the adapters do. The SATA adpater was jumpered as the master... 

Who ever changed over his mobo kept his adapter, thinking it wasn't needed anymore.

Yes, he should try the PATA on the PATA, with the jumper to cable select on the end (Master port) on the PATA cable.  Same on his CD drive.  He should post his motherboard brand and model number. It's hard to belove that he has one of those very few boards that had IDE and SATA that wouldn't allow BIOS select of which boot drive.  That was the big selling point of those boards.... Adaptability.

I diagnosed this quick, but what should have worked on this was to mount the SATA (sdb, where his install is) and reinstall Grub with /dev/sdb/boot as the grub directory and /dev/sda (where his BIOS is locked into for the boot drive) to install the MBR.

Why that didn't work?  Got me wondering.

---

### Post by MAFoElffen on 2011-11-13
> **teodosio said:**
> I didn't try yet because, as I have said, I decided to unconnect the 2nd hard drive from the pc and I'm just using the main hard drive (sdb1) which now, isolated, appears to be sda!
I'm trying to win some courage to repeat every command you both sent me. Anyway I wonder to myself if the problem wouldn't come from the hardware hdd's conections. As I told before, one hdd is older that the other one - where the ubuntu is - and the conections are different. I say this because when I went to the BIOS I never saw the 2 hard disks listed and I don't know why. But these are only suppositions...When you look at the Motherboard, what is the name and any number on that board?  I know with early motherboards that had both IDE and SATA, that the Boot Order said "Drive," and buried in another page was the setup for what order to put the drives in / defining 'Drive."  I'm just wondering if your board might be one of those.

I also asked someone else to look at this.  He is who I respect on Grub issues and would be a welcome new perspective. He should be back tonight.

---

### Post by Hakunka-Matata on 2011-11-13
please post file generated by following code:

```
sudo lshw > M3Ahardware
```

---

### Post by Hakunka-Matata on 2011-11-13
> **MAFoElffen said:**
> The OP had both drives on the same cable with a PATA-to-SATA adapter- the SATA as the master. Therefore the PATA being jumpered as slave.  SATA don't have jumpers, but the adapters do. The SATA adpater was jumpered as the master... 

Who ever changed over his mobo kept his adapter, thinking it wasn't needed anymore.

Yes, he should try the PATA on the PATA, with the jumper to cable select on the end (Master port) on the PATA cable.  Same on his CD drive.  He should post his motherboard brand and model number. It's hard to belove that he has one of those very few boards that had IDE and SATA that wouldn't allow BIOS select of which boot drive.  That was the big selling point of those boards.... Adaptability.

I diagnosed this quick, but what should have worked on this was to mount the SATA (sdb, where his install is) and reinstall Grub with /dev/sdb/boot as the grub directory and /dev/sda (where his BIOS is locked into for the boot drive) to install the MBR.

Why that didn't work?  Got me wondering.

@MAF...: What I have read and sorta-more-or-less proved on my own hardware is that when using both SATA & PATA/IDE HDDs on the same machine, a good initial bet on setup, is to jumper 1st PATA/IDE device to be a Master, and second (on same cable) PATA/IDE device to be Slave.  Of course Cable select might work in some iterations of BIOS/MOBO/OEM/AGE.

---

### Post by MAFoElffen on 2011-11-13
> **Hakunka-Matata said:**
> @MAF...: What I have read and sorta-more-or-less proved on my own hardware is that when using both SATA & PATA/IDE HDDs on the same machine, a good initial bet on setup, is to jumper 1st PATA/IDE device to be a Master, and second (on same cable) PATA/IDE device to be Slave.  Of course Cable select might work in some iterations of BIOS/MOBO/OEM/AGE.
@Hakunka-Matata

Please check your "email"... You have mail.

---

