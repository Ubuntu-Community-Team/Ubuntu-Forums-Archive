---
title: "Problem boot Ubuntu"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by mestizo19 on 2009-12-06
Hi every one...well...i saw that the same problem as mine have many users...!Well...i upgrate a few days before my Ubuntu 9.04 to 9.10.Everything works perfect!!Today...when i restart my computer...when it shows me the options Windows XP or Ubuntu(Dual boot)when i choose Ubuntu it apears to me the fowlloing message:


                                 GNU GRUB version 1.97 beta4

[ Minimal BASH-like editing is supported. For the first world, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ]

sh:grub>_



Well...because i am not a pro user of Linux...tell me with simple words what can i do to fix this problem??thanks....

---

### Post by darkod on 2009-12-06
This error is common with users who have installed wubi from inside windows with running wubi.exe, which is slightly different to ubuntu.
Can you clarify if you have wubi or ubuntu?

---

### Post by mestizo19 on 2009-12-06
What is Wubi???I install inside the WinXP the 9.04 of Ubuntu...and then...i make the upgrate to 9.10...and sudenly...it apearce to me this problem..that's all..But i find one file with a name Wubi....what is that??and what can i do to fix it??

---

### Post by darkod on 2009-12-06
Wubi is exactly what you did, install from within windows. The executive file is called wubi.exe. Look at post number #10 here:
[http://ubuntuforums.org/showthread.php?t=1339203](http://ubuntuforums.org/showthread.php?t=1339203)

You will need to execute those commands but it depends what you need to use in the /dev/sda1 place. It all depends where did you select wubi to be installed. If it was your first partition C:, then you should use /dev/sda1. If you installed on another partition or second hard drive, you will need to change that accordingly (sda is first drive, sdb second, etc, and the number is the number of the partition on the drive).

---

### Post by mestizo19 on 2009-12-06
I don't have second hard drive...and not 2 partitions...i have one hard drive and i install ubuntu into!So...can i try the first soloution


[B]Solution for Windows ME/XP:
[/B] 
     Code:
     sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-26.31-14-generic
sh:grub>boot 




this??????????

---

### Post by darkod on 2009-12-06
Yes.
And if it boots succesfully do in terminal:
sudo update-grub2

as the instructions say.

---

### Post by mestizo19 on 2009-12-06
And when i do into the terminal "sudo update-grub2" what did happens?the grub2 will update?

---

### Post by darkod on 2009-12-06
Well the instructions say it will solve this problem and you should be able to continue booting ubuntu as before.

---

### Post by mantaor on 2009-12-06
Hi darkod,

I have wubi, 9.10 and the sh:grub after install 2.6.31-16. Do I use vmlinuz-2.6.31-14 or vmlinuz-2.6.31-16?
In xp I installed ubuntu via wubi in a 10 Gb partition (sd5), while XP is sd1. Do I have to use linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda**1** loop=/ubuntu/disks/root.disk ro

or 
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda**5** loop=/ubuntu/disks/root.disk ro

thanks a lot, as you see i'm a new ubuntu user

---

### Post by mestizo19 on 2009-12-06
Ok...wait to try it now...and i send a reply...

---

### Post by darkod on 2009-12-06
@mantaor
Use the -14 kernel in the commands because that is the basic one coming with 9.10. If you are sure wubi was installed on sda5 yes, you should use /dev/sda5

---

### Post by mestizo19 on 2009-12-06
Well...i try it and nothing...it start boot but it stuck...so now???what do you mean??to change something???

---

### Post by mantaor on 2009-12-06
@darkod
you're an hero :KS
there's only a little error in 
sh:grub>initrd /boot/initrd.img-26.31-14-generic

the correct is 

sh:grub>initrd /boot/initrd.img-2.6.31-14-generic

Then I had an error:
Failed to load Invidia kernel moduled    but I clicked OK

and then I chose 
Run ubuntu in low graphics mode

My desktop appeared with 1280*1024 res while mine is 1024*768 (my pc is 6 years old).

Then 

sudo update-grub2

and in the following boot i saw the beloved menu.lst but 2.6.31-16 doesn't works, neither in recovery mode. Reboot again.

Now my question is: the problem is wubi or 2.6.31-16? I'm writing you from a regular session of 2.6.31-15.

Thank you very much again
regards from sicily (Italy)

---

### Post by mestizo19 on 2009-12-06
Well...i write "vmlinuz-2.6.31-14-generic root....e.t.c" and nothing!!!!!!what i am doing wrong????????????

---

### Post by mantaor on 2009-12-06
have you checked the third command?

sh:grub>initrd /boot/initrd.img-2.6.31-14-generic

you're writing the second which is correct!
which error do you have?

---

### Post by mestizo19 on 2009-12-06
Wait to check it......

---

### Post by darkod on 2009-12-06
> **mantaor said:**
> 
Now my question is: the problem is wubi or 2.6.31-16? I'm writing you from a regular session of 2.6.31-15.

Thank you very much again
regards from sicily (Italy)

I believe the problem is wubi is trying to make linux work inside windows. That is never easy because there are fundamental differences and they depend on the other OS and its reaction.
I personally never use wubi and don't know much about it. I just found that post and directed you. My opinion is that having a proper side-by-side dual boot is the right way to use windows and linux. They reside on separate partitions. But wubi is very easy for windows users to install and because of that attractive, plus many users are not even aware they will not end up with the same setup compared to booting with ubuntu cd and selecting Install.
This is in some way "virtual" ubuntu inside windows.

---

### Post by mestizo19 on 2009-12-06
Well....it works!!!!!!!!!!!!!!:-D but i am trying to update Grub2 and it didn't works..:'(
Tell me exactly the command for the terminal plzz..

---

### Post by darkod on 2009-12-06
sudo update-grub2

or if that doesn't work
sudo update-grub

---

### Post by mantaor on 2009-12-06
If I decide to make a total installation of ubuntu, have I format the 10Gb partition that I'm using for ubuntu wubi or can I indicate this NTFS partition during installation?

When you say "proper side-by-side dual boot", do you refeer to grub2 or other bootloader?

Have you had problem with 2.6.31-16?

Thanks, I don't know much "real" ubuntu user

---

### Post by mestizo19 on 2009-12-06
Ok!!!!!!!!!done!!!!!!thanks a lot my friends!!!!!!!well....if i reboot my pc...will apearce again this problem???and...if i want to put again my custom grafics that i make with compiz..will work...?

---

### Post by mantaor on 2009-12-06
I guess if you use 2.6.31-15, the previous version of 2.6.31-16, you'll find your desktop before upgrade

---

### Post by mestizo19 on 2009-12-06
My desktop is as it was...!the only defference is that it hasn't any visual effect...

---

### Post by mantaor on 2009-12-06
But you have your desktop again :-\" be happy!!

---

### Post by mestizo19 on 2009-12-06
OK....it works ok...but....When i choose Ubuntu..then it apearce the follwoing:



2.6.31.16
2.6.31.16(recovery mode)
2.6.31.15
2.6.31.15(recovery mode)
2.6.31.14
2.6.31.14(recovery mode)

And it works only in "2.6.31.14" in the others it restarts my pc!
How can i delete them?ooh God.....i am vry tired...:-(

---

### Post by elenaa on 2009-12-07
Hi!
I have this identical problem.


I've done all,
but...
at the end, after entering the comands
[http://img25.yfrog.com/i/ubu237002.jpg/](http://img25.yfrog.com/i/ubu237002.jpg/)

What can I do?

Thanks.

---

### Post by darkod on 2009-12-07
> **elenaa said:**
> Hi!
I have this identical problem.


I've done all,
but...
at the end, after entering the comands
[http://img25.yfrog.com/i/ubu237002.jpg/](http://img25.yfrog.com/i/ubu237002.jpg/)

What can I do?

Thanks.

You can see the last ALERT message, /host/ubuntu/disk/root.disk does not exist. Go in the partition where you installed wubi (because this is wubi install) and in the folder ubuntu then folder disk see if the file root.disk is there.

Also you might have specified wrong /dev/sdXY parameter. Check if the file is there first.

---

### Post by elenaa on 2009-12-07
I've controlled... the file root.disk is there.

I'll try again.

Thanks

---

### Post by mantaor on 2009-12-07
@darkod, 
If I decide to make a total installation of ubuntu, have I format the 10Gb partition that I'm using for ubuntu wubi or can I indicate this NTFS partition during installation?

When you say "proper side-by-side dual boot", do you refeer to grub2 or other bootloader?

Have you had problem with 2.6.31-16?

Thanks

PS now I have a backup of grub.cfg stored in data partition. I've seen the lines: they have all the command we have typed to restore the right scenario1 I have to study a lot!

---

### Post by elenaa on 2009-12-09
I don't know why,
but it doesn't work yet......

---

### Post by darkod on 2009-12-09
> **mantaor said:**
> @darkod, 
If I decide to make a total installation of ubuntu, have I format the 10Gb partition that I'm using for ubuntu wubi or can I indicate this NTFS partition during installation?

When you say "proper side-by-side dual boot", do you refeer to grub2 or other bootloader?

Have you had problem with 2.6.31-16?

Thanks

PS now I have a backup of grub.cfg stored in data partition. I've seen the lines: they have all the command we have typed to restore the right scenario1 I have to study a lot!

No, you can not use ntfs partition for ubuntu. You could remove wubi with add/remove programs like any windows app, and then shrink the windows partition to make unallocated space for ubuntu. It all depends how your disk is partitioned at the moment. If you want, post a screenshot of Disk Management in windows and I can give you some advice.

Yes, dual boot, side-by-side would involve grub to be your bootloader. It can boot both ubuntu and windows so it's really not an issue. Thee is a way to add ubuntu to windows bootloader but unless you have specific knowledge of that, I think it's more complicated than letting grub run the show.

I am using 2.6.31-16 and haven't seen any issues so far with it.

---

### Post by darkod on 2009-12-09
> **elenaa said:**
> I don't know why,
but it doesn't work yet......

What exactly doesn't work? Any error message?

---

### Post by elenaa on 2009-12-09
> **darkod said:**
> What exactly doesn't work? Any error message?

Is the same thing as before...
I'm sure that is sda1, and the file root.disk is in the right place... but it always says that this file doesn't exist

---

### Post by darkod on 2009-12-09
> **elenaa said:**
> Is the same thing as before...
I'm sure that is sda1, and the file root.disk is in the right place... but it always says that this file doesn't exist

Are you executing these commands exactly as they are?

```
sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

```Try it and if it loads to the desktop open terminal (in Applications-Accessories) and execute:
sudo update-grub2

If the commands don't work, try with 2.6.31-15 instead of 2.6.31-14. Just replace it in both commands. Maybe you don't have the 31-14 kernel.

---

### Post by hhh81 on 2009-12-09
should be the bug explained here:
[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all)

---

### Post by elenaa on 2009-12-10
:oops:
I'm so stupid...
I wrote "disk" instead of "disks"...

Now Ubuntu works!

darkod, THANKS and sorry for having made you lose time...

---

