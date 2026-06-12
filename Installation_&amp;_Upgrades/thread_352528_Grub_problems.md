---
title: "Grub problems"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by Diablos_Raven on 2007-02-03
I have a Windows box with a Raptor drive (which is SATA for those who dont know) running my OS's and I decided to use Ubuntu Edgy because of Beryl being less hardware intensive than Vista and my small hatred for Microsoft. Anyways, I booted the Ubuntu cd and went through the install section and got to the part about installing GRUB. I installed GRUB to hd0 (defaulted) and restarted my system, after POST I was expecting to be loaded straight to a menu to select Ubuntu or Windows, but no it boots straight to Windows. So I restart and use the disc to boot Ubuntu and it boots the Ubuntu partition without a hitch. I try reinstalling GRUB and rebooting and it now brings up the list of OS's but wont recognize the the Ubuntu partition, but will still boot from the cd just fine and loads Windows just fine also.

HELP!

---

### Post by stoeptegel on 2007-02-03
Sounds like you have a vista bootloader interfering with grub.
I have read something about it somewhere, but all i really got out of it is that it was a new fresh pain in the rear.

---

### Post by DistroTech on 2007-02-03
[Here's a link that might help out.]("http://neosmart.net/dl.php?id=1")

That's a program that tweaks the Vista bootloader to help you run dual boot systems, it can work with GRUB, LILO, or whatever else as far as I know.  Not a Vista user, so I'd research it a little bit before doing anything you can't reverse.  Just heard it was a good program, and might help solve some of the Vista woes.

-DT

---

### Post by Diablos_Raven on 2007-02-03
I'm sorry i misled you I'm running XP Pro

---

### Post by stoeptegel on 2007-02-03
Weird.
Well, i don't know other than checking the entries from fdisk and menu.lst, so i will tell how you can do that.

Enter the command "sudo fdisk -l" and locate the partition where the ubuntu OS should be installed. (the filesystem should have been tagged as Linux from there) 
If you found it, take the number from x in /dev/sdaX in that line and subtract it with one number, so i.e. /dev/sda6 would make 5.

Check this number with the file /boot/grub/menu.lst 
(scroll down to get down of the examples)

It should view somehting like this:
```
## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

Previous checked number should be located after "root", (hd0,**5**) here.

Note that the number before 5 in this example, zero, tells grub it should search on the first SATA hard drive to find the kernel. So if you would have had installed ubuntu on a second SATA disk this number would make it 1. (but fdisk -l should tell you this by looking which letter /dev/hdX gives you)

---

### Post by Diablos_Raven on 2007-02-03
OK.... Here's an update. I went into menu.lst and moved the info around. I moved the Windows info above the linux info and saved and rebooted. Now the MBR is showing the list of OS's and I tried to load Ubuntu and it says error 22 but I havent moved or deleted any of the partitions. I'm truly kinda happy that I at least get the list but it still doesn't boot.

---

### Post by stoeptegel on 2007-02-03
Error 22.
[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors) says:

Error 22:
 No such partition
 This error is returned if a partition is requested in the device part of a
 device- or full file name which isn't
 on the selected disk.

---

### Post by Diablos_Raven on 2007-02-03
OK.... It's fixed now. Everything is running fine now. It was something about the drive and partition naming scheme. I went into menu.lst and changed

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)

TO

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)

I dont know why ubuntu named it that way but it did.
Thanks all for the help.

---

### Post by stoeptegel on 2007-02-03
Yeah that should not happen normally.

But i have to say, for someone who has just installed a complete new and different OS on the pc you have done very well in fixing this not so noob-friendly issue!

Congrats and happy times.

---

