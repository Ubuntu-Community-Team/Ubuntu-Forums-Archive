---
title: "Upgraded To 9.04 and ext4, Later Get Grub Error 13"
date: 2009-03-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by woozyking on 2009-03-24
Hi,

I don't know if anybody else have experienced this.

I've recently upgraded my Ubuntu from 8.10 to 9.04 (alpha 6), everything seemed so smooth and even the conversion of ext3 to ext4 was really successful.

Later today I did a apt-get upgrade, and noticed something strange - the update-manager's asking for an upgrade to kernel 2.6.28.11, which was already there (if I remembered correctly). And after rebooting, Grub gives me an Error 13: "Invalid or unsupported executable format"

I searched around and on Arch Linux's wiki, they provided a solution to this type of problem, but as I'm not an expert of Linux/Ubuntu, I really need help, but this might help you guys to come up with a solution: [http://wiki.archlinux.org/index.php/Ext4](http://wiki.archlinux.org/index.php/Ext4) (and there is a specific sub-topic talking about GRUB Error 13)

Please help me on this, thank you guys in advance :D

---

### Post by overdrank on 2009-03-24
Moved to Jaunty Jackalope Testing and Discussion

---

### Post by Bakon Jarser on 2009-03-24
Try this (the command line version is probably faster and easier):

[https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)

You may need a jaunty live cd because your install is on ext4, I'm not sure.  If you do:

[http://www.ubuntu.com/testing/jaunty/alpha6](http://www.ubuntu.com/testing/jaunty/alpha6)

BTW, alpha testing kinda is for advanced users.

---

### Post by TheUnderTaker on 2009-03-24
Did you make your partitions fstab entry from ext3 to ext4?

---

### Post by TBD on 2009-03-29
> **woozyking said:**
> Hi,

I don't know if anybody else have experienced this.

I've recently upgraded my Ubuntu from 8.10 to 9.04 (alpha 6), everything seemed so smooth and even the conversion of ext3 to ext4 was really successful.

Later today I did a apt-get upgrade, and noticed something strange - the update-manager's asking for an upgrade to kernel 2.6.28.11, which was already there (if I remembered correctly). And after rebooting, Grub gives me an Error 13: "Invalid or unsupported executable format"

I searched around and on Arch Linux's wiki, they provided a solution to this type of problem, but as I'm not an expert of Linux/Ubuntu, I really need help, but this might help you guys to come up with a solution: [http://wiki.archlinux.org/index.php/Ext4](http://wiki.archlinux.org/index.php/Ext4) (and there is a specific sub-topic talking about GRUB Error 13)

Please help me on this, thank you guys in advance :D

I had your same problem...

upgraded to jaunty, converted to ext4, acknowledged that i need to update the fstab entries, tweaked around in the new system, reinstalled network-manager (somehow it was lost during the upgrade from intrepid), installed a bunch of updates (including a new kernel version)...

and rebooted only to find the error 13...

trying to do update-grub and grub-install on a livecd was the first thing i tried...

the link to the arch linux's wiki solved my issue:


(assuming /dev/sda1 is the root partition)
> boot from the live medium and chroot into the Linux installation: 
```
sudo mkdir /mnt/linux
sudo mount -t ext4 /dev/sda1 /mnt/linux
sudo mount -t proc proc /mnt/linux/proc
sudo mount -t sysfs sys /mnt/linux/sys
sudo mount -o bind /dev /mnt/linux/dev
sudo chroot /mnt/linux

```
If /boot is on a separate partition, this partition must also be mounted: 
```
sudo mount -t ext4 /dev/sda2 /boot

```
Then, the following command should resolve the issue. (Does anyone know why?): ```

sudo grub-install --recheck /dev/sda

```


by avoiding to mount /proc /sys and /dev you'll get some errors during the grub-install (such as it being unable to locate /dev/null)... don't know if they're warnings or fatal errors for the grub installation

hovewer i don't understood: you gave the commands but it didn't work for you, or you can't follow the instructions (e.g. you don't know if /dev/sda1 is your system's correct device)?

---

### Post by autocrosser on 2009-03-29
There is a known bug with updating a system from 8.10 to 9.04---the update-grub is not changed to the newest version & you will not get ext4 to boot under that condition....you need to chroot into your 9.04 install from a LiveCD & reinstall grub to fix the problem. If you search thru the forum, there are a couple of threads about this very problem.

Read Bakon's post above for the correct fix.

---

### Post by TBD on 2009-03-29
> **autocrosser said:**
> 

Read Bakon's post above for the correct fix.

actually, that solution won't work...

---

### Post by binbash on 2009-03-29
If you converted your boot partition to ext4, add rootfstype=ext4 to your kernel at grub.

---

### Post by TBD on 2009-03-29
> **binbash said:**
> If you converted your boot partition to ext4, add rootfstype=ext4 to your kernel at grub.

i tried even that but nothing changed, dunno if woozyking's issue is the same:confused:

---

### Post by meierfra. on 2009-03-29
In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by caryb on 2009-03-29
This may or not help but after upgrading on Saturday I couldn't get back into my laptop. I found after booting from (jaunty) live cd & looking at the /boot/grub/menu.lst it had kernels 2.6.28-7 & 8 in the list but they are not installed so I edited them to 11 & 10 instead of 7 & 8 & now I'm typing this from the problematic PC:P


Cary

---

### Post by anystupidname on 2009-03-29
> **TBD said:**
> I had your same problem...

upgraded to jaunty, converted to ext4, acknowledged that i need to update the fstab entries, tweaked around in the new system, reinstalled network-manager (somehow it was lost during the upgrade from intrepid), installed a bunch of updates (including a new kernel version)...

and rebooted only to find the error 13...

trying to do update-grub and grub-install on a livecd was the first thing i tried...

the link to the arch linux's wiki solved my issue:


(assuming /dev/sda1 is the root partition)


by avoiding to mount /proc /sys and /dev you'll get some errors during the grub-install (such as it being unable to locate /dev/null)... don't know if they're warnings or fatal errors for the grub installation

hovewer i don't understood: you gave the commands but it didn't work for you, or you can't follow the instructions (e.g. you don't know if /dev/sda1 is your system's correct device)?

Thanks! That hit the spot... Fixed me right up.

---

### Post by woozyking on 2009-03-31
Sorry guys, I've been quite busy for a little while.

Anyways, yea I fixed the problem using a 9.04 live CD to reinstall grub. In fact when I tried to do the same thing for my other laptop, I followed the correct way to avoid the problem.

To those who haven't upgraded to ext4 file system and wish to, please simply read this: [http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta) and follow what it says under the Ext4 section. In short, after converting file system to ext4, simply do a grub-install /dev/sdaX , and you'll never get the pain that I experienced earlier.

Regards.

---

