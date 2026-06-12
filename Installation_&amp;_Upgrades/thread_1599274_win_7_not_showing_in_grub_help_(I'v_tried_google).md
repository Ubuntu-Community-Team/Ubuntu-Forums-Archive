---
title: "win 7 not showing in grub help (I'v tried google)"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by codydbgt on 2010-10-17
OK so i had windows 7 installed to start with... i then partitioned the drive inside win7 with there partitioner and then installed Ubuntu 10.10. When i restarted grub only showed all the normal options but no win7 the only win 7 option iv got is the restore partition witch says "windows vista (loader)"  so iv tried these things. 

i found the guide here  [http://www.linuxquestions.org/questions/ubuntu-63/grub-wont-boot-windows-7-a-764813/]("http://www.linuxquestions.org/questions/ubuntu-63/grub-wont-boot-windows-7-a-764813/")


```
 gksudo gedit /boot/grub/menu.lst 
```

Then I put in the file  

```
rootnoverify     (hd0,3)
makeactive
chainloader      +1
```

i put 3 since i got this for fdisk -l

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x58b3cac5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1314    10547200   27  Unknown
/dev/sda2   *        1314        1326      102400   82  Linux swap / Solaris
/dev/sda3            1326       22809   172556288    7  HPFS/NTFS
/dev/sda4           22809       38914   129362945    5  Extended
/dev/sda5           22809       38914   129362944   83  Linux

```
once i rebooted nothing changed 
that didn't work or I'm doing something wrong. and then out of frustration I tried the restore disk for win7 and opened cmd and then put ```
boottrc/fixmbr
``` that screwed it up it said after a reboot there was no os to load so i had to fix the grub boot loader so i gust reinstalled ubuntu    

I'v tried this also 

[http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/]("http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/")

so can any one figure this one out I would really like some help on this thanks.

---

### Post by codydbgt on 2010-10-17
any one there have any ideas

---

### Post by ronparent on 2010-10-17
Menu.lst is a grub legacy file. Your best bet may be to do a grub 2 reinstall (which in you case would be a grub 2 install). Follow the instructions in this link: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

In your case it looks pretty simple. Boot the 10.10 live cd and open a terminal. In the terminal enter the command: 
> sudo mount /dev/sda5 /mnt
Then install grub 2 with the command:
> sudo grub-install --root-directory=/mnt/ /dev/sda
This should put you in business. Let us know how it works out.

Note: Windows should now be in the grub menu.

---

### Post by codydbgt on 2010-10-17
it seams aftur doing some irc chating somone said that thsi is the problem 

[http://pastebin.ubuntu.com/515215/]("http://pastebin.ubuntu.com/515215/")


/bootmgr /boot/bcd
 
but i dont know what to. add he said that i need to add somthing what how would i add the files that need to be there where would i get them

---

### Post by ronparent on 2010-10-17
The grub install by itself would add anything you needed.

---

### Post by dougalkerr on 2010-10-17
In Ubuntu 10.10 I believe grub 2 is used for the boot menu and you would be editing /etc/default/grub and change the bootmenu default = to the number you think Windows responds to (3 in your example).

You must also open terminal and type 'sudo grub-update' to force grub to change permanently.

Reboot and you should now boot directly to Windows if that is your choice but, if you don't see Windows as an option on tour menu anyway then something else is wrong. You could try downloading the Supergrub.iso and make a boot cd from it to try to fix the missing Windows entry then set-up your default boot option after that is done.

It has been a while since I used Supergrub but, it used to be a fantastic program for sorting this sort of thing.

Good luck.

---

### Post by codydbgt on 2010-10-17
so i just reloaded windows off the recovery partition now im gussing i know what I did wrong there are 4 partitions on win7 from left to right they show this 
[IMG]https://sites.google.com/site/codydbgt/home/2010-10-17_172143.png?attredirects=0&d=1[/IMG]
if you see that there is a partition called system reserved when i  loaded Ubuntu i did a manual partition setup and it asked for a swap area well since this partition was somthing i didi't think you needed i slected that. :(

if you also see that below each partition it says Helthy("folowed by some more info"). well in the system reserved and the c: drive 
they have importan key words healthy(system,active) while the other has healthy(boot,primary partition) those are the reason they did not work because they need each other..im guessing and i dont know exactly what each one meens but i just wanted to point it out. :)


with the info iv given can any one tell me so i dont screw somthing up again. 

also i was wondering hould would i get Wubi to work i think that works only when i tryed it and it didnt seem to load right...im goint to try it now thoe.

---

