---
title: "Where to install GRUB on my SATA drive ?"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by siddukirk on 2008-11-09
Hi folks,

I seemed to lost big time , please help me out

Where do i need to install Grub on my SATA drive ?

Details : I got two drives one IDE (PATA) which has windows XP, and the other SATA which has got Vista . and i have got dual boot loader from vista on the MBR of the IDE (PATA)/dev/sdb . Now i have loaded ubuntu on one of ext3 partitions on the SATA drive and also allowed to installed grub on /dev/sda9 but when restarted its going back to my earlier boot loader !

Thanks in advance
Sid

---

### Post by caljohnsmith on 2008-11-09
You could install Grub to the MBR of the SATA drive, change your BIOS boot order to boot it, and then could add entries to your Grub menu to boot Vista/XP. That way you could boot all your OSes from Grub. Or if you want to use Vista's boot loader like you are currently doing, you could use EasyBCD to add Ubuntu to your Vista boot loader:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

I prefer to use Grub, but those are at least two of your choices. If you want help installing Grub and using it to boot all your OSes, let me know. Or if you decide to use EasyBCD, let me know how that goes. :)

---

### Post by siddukirk on 2008-11-10
Hi dude,

I am unable to boot ubuntu so one of the options which u mentioned is ruled out and the Easy BCD isnt working properly on my windows !

so Help me with the Grub . If u have any iso image of Grub so that i can boot with a cd and boot the ubuntu which is on  my /dev/sdc9 of the scsi partition   . Please mail it to me 

[email]siddu.sjce@gmail.com[/email]

Regards
Sid

---

### Post by bulldog on 2008-11-10
If you have a life install cd,you can install GRUB with it.
You only have to make the decision were to put it.

Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
This will get you a grub> prompt 
```
sudo grub
```
This will return a location which you have to use in the next command.
```
find /boot/grub/stage1
```
Enter the location given by the previous command in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.
Make the hdd which you installed GRUB your primary boot hdd,otherwise you won't see the GRUB menu.

If you want to know more about GRUB,and what you can do with it,I would recommend to take a look at Herman's GRUB Page.
[http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)

---

