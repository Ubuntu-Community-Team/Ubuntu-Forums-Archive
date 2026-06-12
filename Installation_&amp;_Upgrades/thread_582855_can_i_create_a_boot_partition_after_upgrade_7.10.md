---
title: "can i create a /boot partition after upgrade 7.10?"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by loza on 2007-10-20
Hi All

I just performed an on line upgrade from feisty to gutsy and all seemed to go well until I rebooted and got the GRUB error 18 thing on the 2.6-22-14 but I can boot from the 2.6.-20-16 menu item.

The disk has one Windows partition and one Linux partition. 

Does anyone know if it is possible to shrink a partition, create a /boot at the front of the disk and move my /boot files to the front of the disk please?

Thanks in anticipation.

loza

---

### Post by thelocust on 2007-10-20
You can't shink anything unless you have LVM partitions. Before you do anything drastic get your hands on [The Super GRUB Disk]("http://geocities.com/supergrubdisk/") and see if you can reinstall grub.

---

### Post by Herman on 2007-10-20
Hello loza and thelocust,

Actually we can shrink Linux partitions now because Gutsy Gibbon has the latest version of GParted in it now, GParted 0.3.3, which has that functionality, and more as well! :)
And yes, it is possible to make a new partition on your hard disk, mount it, copy your /boot directory to it, and register it as your /boot partition in /etc/fstab.
That will be a little bit of work though.
I am not sure if that will fix anything either. 
It seems very strange to me that anyone would have a GRUB error 18 due to anything I can image might happen during an upgrade. It just doesn't make any sense.

I agree with thelocust, I think you should try re-installing GRUB before you do anything else and see if that helps at all.

I'd like to know more about your computer first. How old is this computer and how many hard disks do you have?
Can you please post the output from 'sudo fdisk -lu' here?
```
sudo fdisk -lu
```Regards, Herman :)

---

### Post by thelocust on 2007-10-20
I didn't know gparted could do that was this a recent release?

---

### Post by Herman on 2007-10-20
[GParted -- LiveCD]("http://gparted.sourceforge.net/") has been able to do that for quite a long time, (move Linux partitions around, and resize them from the start point as well as the end).

For a long time Ubuntu stayed with an old version of GParted. I imagine probably because it might be a lot of work to integrate important software like that into the system, I have no idea really. 

The great thing is we have the latest version of GParted now, which is really wonderful for Ubuntu! I'm really pleased about it!

It has another neat function I like too, that will help a lot of people, point and click file system checking! :)
Go ahead, try it out! You just open GParted in Ubuntu, right-click on any (unmounted) partition you want to run a file system check on and select 'Check' from the right-click menu. 
Then click 'Apply' on the toolbar, and 'Apply' in the confirmation box.
Wait while GParted goes to work.
When it is finished, click on the expansion triangle to show the details of what has been done.
You need to keep on clicking all the triangular expansion buttons to see the complete report.

For an ext3 file system it runs e2fsck -f -y -v /dev/hdx,y, and then resize2fs as well.

Regards, Herman :)

---

### Post by thelocust on 2007-10-20
I'll have to see what version I've been running I liked it before I found out about all this. Thanks.

---

### Post by Herman on 2007-10-20
Feisty had GParted 0.2.5, released 2006-05-13 11:39 (13th May 2006), so to jump to version 0.3.3 is quite an impressive leap. :)

---

### Post by loza on 2007-10-20
Hi there

Thanks for the replies!

My laptop is a toshiba satellite pro L-10 1gb RAM and 160Gb hard disk.

my drive shows the following:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c3d9c3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   138351779    69175858+   7  HPFS/NTFS
/dev/sda2       138351780   180666989    21157605    7  HPFS/NTFS
/dev/sda3       180666990   308672909    64002960   83  Linux
/dev/sda4       308672910   312576704     1951897+  82  Linux swap / Solaris

Thanks again!

loza

---

### Post by Herman on 2007-10-20
Hello loza
Thanks for taking the time and effort to show me your fdisk output, that's always important and often provides valuable clues about most booting problems. The good news is, yours looks okay to me. :)
> I just performed an on line upgrade from feisty to gutsy and all seemed to go well until I rebooted and got the GRUB error 18 thing on the 2.6-22-14 but I can boot from the 2.6.-20-16 menu item. The new kernel in Gutsy Gibbon is called vmlinuz-2.6.22-14-generic, and the latest kernel I have in Feisty Fawn is named vmlinuz-2.6.-20-16-generic. So your old kernel boots fine but your new kernel doesn't.  I think probably what has happened is the new kernel doesn't support your hardware. I have not studied anything at all about kernels and how they work, but I will sometime. You could probably submit a bug report if you know how.

If you do nothing and boot with the Feisty kernel, vmlinuz-2.6.-20-16-generic, and your operating system will work okay with that one, a newer kernel for Gutsy Gibbon might be installed in a regular update. You can try booting that one and see if it works better, that means you will be letting the kernel developers do the work for you, and there is a good chance you'll be lucky.

You can make a seperate /boot partition if you still want to, but I'm not sure if it will help or not. It might fix your problem. In your case there will be some extra steps involved. For one thing, according to your fdisk output, you have four primary partitions already.
That is the maximum number of primary partitions, so you will need to delete your swap area in order to make an extended partition somewhere before you will be able to create any more partitions.
After that, since you will want the /boot partition to be at the start of your hard disk, you will need to resize your first partition, so you'll have some free space in front of it. You can make an extended partition there. Then you can make a ext2 or ext3 partition in it for /boot, and a new swap area.
Make sure you pay attention to what the new partition numbers will be, numbers 5 and 6 I would guess.
Then you'll need to [mount your /boot partition]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_a_reiserfs_filesystem")  and use a sudo command to copy your /boot files to it. 
Then you'll have to [edit /etc/fstab]("http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu") with details of your new /boot partition.

Probably you will need some more, exact help with that.
If you really want to try doing that you can start it and then ask for help again when you come to a problem and I or someone here will help you.

But it would be easier to just comment out the line for the new kernel in /boot/grub/menu.lst and ignore the new kernel and wait for another one to come out in an update and hope you'll be luckier next time.
It's up to you, do whatever you think will be the best for you.

Regards, Herman :)

---

### Post by Herman on 2007-10-20
Just another thought, here is my collection of information about GRUB error 18, [     Grub error 18]("http://users.bigpond.net.au/hermanzone/p15.htm#18").
Re-reading that reminded me about the old 137 GB hard drive limit, but I don't think your laptop would be that old. You do have an 160 GB hard drive though, so it is possible. I wonder if your old kernel might have been situated inside the limit somehow and your new one went somewhere in the file system outside the limit? I don't know if that would be a feasible theory or not, maybe t is a ridiculous idea. But if that or something like that could be true then making a separate /boot partition might be the right answer.
This is an interesting situation.

You should look at some of the other solutions in that link, (like switching your hard disk detection in your BIOS to 'auto' and not on 'user' and so on first, before you go to too much work.

Regards, Herman :)

---

### Post by loza on 2007-10-23
Hi Herman

Thank you so much for your efforts! I really appreciate it! And sorry for the delay in getting back to you!

I suspect you are bang on right about the new kernel being outside the disk limit. I am going to try to merge my two ntfs partitions and create the /boot and this weekend after I backup all my data.

I am slowly trying to live without windows (I only need it for a couple of compilers and visio) so I can probably shrink the partitions right down.

I shall keep you posted and once again thank you for the pointers and links!

loza

---

### Post by Herman on 2007-10-24
Hello loza,
>  I suspect you are bang on right about the new kernel being outside the disk limit Well I wasn't sure if that was a possibility or not, but while searching for information about a completely different problem, I found an extremely interesting post in Nabble Grub forums. According to the author of this post, it is possible for the computer to fail to boot after a kernel update due to the new kernel being placed outside a BIOS limit. Here is a link to that post, [http://www.nabble.com/Grub-tf4291271.html#a12218543](http://www.nabble.com/Grub-tf4291271.html#a12218543)
Although that post is really talking about the 1024 (8.5 GB) limit, I imagine the same principle might also be a possible explanation for your problem if we think that your problem could have something to do with the 137 GB hard drive BIOS limit.
>  I shall keep you posted and once again thank you for the pointers and links! Thanks for your patience and tolerance yourself, and please do keep posting,  your news might possibly help other people with similar problems in the future. This is quite an interesting thread. 
Regards, Herman :)

---

### Post by loza on 2007-10-24
Hi Herman!

We did it! Thanks for the links they were priceless. Up until now the only boot manager I have ever played with was LILO.

GRUB is actually quite fantastic and the GRUB superdisk should be nominated for an award!

It was like you said, my new kernel was just out of reach.

1. In windows I merged both ntfs partitions sda2 into sda1 using partition magic (so now I have three primary partitions).
2. In Gutsy I installed 'gparted' using 'add/remove'
3. I shrank 1Gb off the front of sda1 (ntfs partition)
4. I created a 1Gb ext3 partition and set the boot flag (gparted seemed to core dump for some reason but it was sucessful in the operation)
5. I renamed my /boot to /boot2 as 'sudo'
6. I created a /boot as 'sudo'
7. I edited the fstab to reflect /boot was ono another partition.
8. This is where I made a dogs dinner of the whole thing! I backedup and edited the menu.lst as 'sudo' Because of what I did in step 4, I thought that my new boot partition would be hd0,0 and my ntfs would be hd0,1 and my linux ext3 would be hd0,2. So I edited my menu.lst from this:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2f8f68a5-c640-4a50-9345-9d77e76889b1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


To this (which the wrong thing to do!!)

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2f8f68a5-c640-4a50-9345-9d77e76889b1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


You see, I thought my root was on hd0,2. So I fired up GRUB and did the root (hd0.0) thing and the setup (hd0) and thought I was home and dry. I was wrong! When I rebooted I got the error 15 when I chose my new kernel and a 'partition format not supported' when I chose windows at boot up.

9. I got on to another pc and swiftly burnt the GRUB superdisk to a CD.
10. Through trial and error I managed to learn my windows partition is hd0,0 and my /linux filesystem is hd0,1 and my /boot must be hd0,0 *** I'm not really that sure even now! ***
11. So with the aid of the superdisk I edited the boot options and managed to get Gutsy up and running again.
12.  I had to mount /boot manually before I editted the menu.lst to this:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=2f8f68a5-c640-4a50-9345-9d77e76889b1 ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Now I have everything working (I only show the first menu option for linux and the windows option above for brevity).

So now a sudo fdisk -lu shows:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c3d9c3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *     2104578   180666989    89281206    7  HPFS/NTFS
/dev/sda2              63     2104514     1052226   83  Linux
/dev/sda3       180666990   308672909    64002960   83  Linux
/dev/sda4       308672910   312576704     1951897+  82  Linux swap / Solaris

Partition table entries are not in disk order

and a blkid shows:

/dev/sda1: TYPE="ntfs" UUID="48FA7A574EF8CA42" LABEL="WinXP" 
/dev/sda3: UUID="2f8f68a5-c640-4a50-9345-9d77e76889b1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="0f34da89-81fd-4d40-b423-d9bd74f2217f" 
/dev/sda2: UUID="72e667b2-5e92-4a00-bb9e-5edce5e2f9d1" SEC_TYPE="ext2" TYPE="ext3" 

I know I did somethings which were wrong and was my lack of understanding of how partitions get 'numbered', and I'm not too sure about the GRUB root and setup commands I did. I read the manual (for a change) and think I need to read it again! :)


Herman, thelocust - thank you very much - you guys rock! :guitar:

loza - a little bit wiser ( i think ) and a lot greyer...

---

### Post by Herman on 2007-10-25
Hello loza,
Hey, you fixed it already by yourself? That's great! Well done and congratulations! :)

Thank you very much for your valuable co-operation and feedback too, I have learned something from you that I didn't know before. I want to add a link to thsi thread to my [GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm"), in the part titled [Common Booting Errors and Some Possible Cures]("http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible"), under [     Grub error 18]("http://users.bigpond.net.au/hermanzone/p15.htm#18").
Will that be okay with you?

Bye for now, regards, Herman :)

---

### Post by loza on 2007-10-25
Hi Herman

Thanks! I would have been stumbling around for ages if you had not sent me those links and suggestions.

Of course I'd be delighted if you can use this thread and I hope it helps others to a swift solution too!

I've learned that GRUB is probably one of the most important programs and should be essential study.

Kind regards and bye for now

loza

---

### Post by Herman on 2007-10-27
Thanks Ioza, I have edited my GRUB error 18 help now, thanks again for your help! 
Regards, Herman :)

---

### Post by adrian15 on 2008-02-11
> **loza said:**
> 
GRUB is actually quite fantastic and the GRUB superdisk should be nominated for an award!

Thank you. :oops:
> **loza said:**
> 
10. Through trial and error I managed to learn my windows partition is hd0,0 and my /linux filesystem is hd0,1 and my /boot must be hd0,0 *** I'm not really that sure even now! ***

You can learn this information with **Boot & Tools -> Show Partitions ** Super Grub Disk option the next time you need it.
> **loza said:**
> 
11. So with the aid of the superdisk I edited the boot options and managed to get Gutsy up and running again.

You did use the 'e' key. This is a thing that not everyone knows how to do it. That's great.

adrian15

---

