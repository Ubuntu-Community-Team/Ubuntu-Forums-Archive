---
title: "Fresh Install -- No swap"
date: 2005-09-24
forum: Installation &amp; Upgrades
---

### Post by greenwom on 2005-09-24
I did an install of fedora core and then Ubuntu to do a dual boot.
As far as I know I placed the OS's on seperate partions.

Well when I boot the system I only get Ubunutu in the grub loader 
and then in Ubuntu I don't have a SWAP (I need it w/ only 128mb)

How do I point Ubuntu to the SWAP?

Free shows 0 swap

---

### Post by aysiu on 2005-09-24
What's the output when you type *top* into a terminal? For example, when I do so, I get this at the top: ```
Tasks:  94 total,   1 running,  93 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.6% us,  1.4% sy,  0.4% ni, 80.3% id,  9.1% wa,  0.1% hi,  0.0% si
Mem:    451852k total,   439600k used,    12252k free,    14784k buffers
Swap:  1060248k total,    12476k used,  1047772k free,   230424k cached
```

---

### Post by heimo on 2005-09-24
You could run 
 ```
sudo fdisk -l | grep swap
``` 
to find if you have any swap partitions. I got this:
```
/dev/sda5		 9546	 9733	 1510078+ 82 Linux swap / Solaris

``` 

Then you should have corresponding lines in /etc/fstab, like this:
```
/dev/sda5	 none		 swap sw			 0	 0
``` 

You can run *sudo swapon -a *and see what happens. (check [i]free)
[/i]
If you don't have swap partition, you can always make swap file - or arrange some space, repartition (make swap partition) and initialize using mkswap. Then you need to add line to fstab (as above) and start swapping using swapon command (you can turn it off using swapoff).

Instructions for making swapfile:
[http://ubuntuforums.org/showpost.php?p=287528&postcount=6]("http://ubuntuforums.org/showpost.php?p=287528&postcount=6")

:)

---

### Post by greenwom on 2005-09-24
Just did it, and it worked thanks.

Mike

---

### Post by wozzinator on 2008-03-24
> **greenwom said:**
> I did an install of fedora core and then Ubuntu to do a dual boot.
As far as I know I placed the OS's on seperate partions.

Well when I boot the system I only get Ubunutu in the grub loader 
and then in Ubuntu I don't have a SWAP (I need it w/ only 128mb)

How do I point Ubuntu to the SWAP?

Free shows 0 swap

**Offtopic-ish:**
Since a swap partition is just for using the hard disk to store memory when you run out of memory from the RAM, can't you just not have a swap partition if you have a reasonably large amount of memory on your computer?

---

### Post by chex_m8 on 2008-03-24
seems reasonable to me. even if you dont have a swap file as long as theres free space on the drive it should use that, is that not right? swap file is creating a dedicated space for memory just in case no more RAM and hard drive is full.

---

### Post by Apprenti-chercheur on 2008-03-25
I have the same kind of problem.

I installed ubuntu gutsy but I did not make a swap partition.

I created one afterwards with mkswap and changed fstab to add a line with the UUID of the new swap partition.
It worked.


BUT I tried to hibernate and when I booted the swap partition disappeared 
> Unable to find swap space signature
I had to do the above procedure again.

I reasonably think that if I want to be able to hibernate I would have to add the UUID of my swap partition to  /etc/initramfs-tools/conf.d/resume
Unfortunately my directory /etc/initramfs-tools/conf.d/ is empty. I guess it is because I installed ubuntu without the swap partition.

Could you please tell me how to create it?

Thank you.

---

### Post by forestpixie on 2008-03-25
```
gksudo gedit /etc/initramfs-tools/conf.d/resume
```

will open a new file with that name - enter the information - mine shows 

RESUME=UUID=8ca57b15-061f-47f8-935f-4d5f9ede2b24

change the UUID to suit your partition, save the file close and reboot I assume.

You cna get the UUID with 
```
blkid
```

---

### Post by Apprenti-chercheur on 2008-03-25
But I don't have any file /etc/initramfs-tools/conf.d/resume!
Do I create one with only the line:
RESUME=UUID=8ca57b15-061f-47f8-935f-4d5f9ede2b24
(adapted to my UUID) and nothing else?

Thanks.

---

### Post by forestpixie on 2008-03-25
The first command will create the file - so do that and adapt it to suit, I've never actually used hibernate so am just assuming that this will work for you.

If it does cause a problem when booting use this command in recovery mode to rename the file

sudo mv /etc/initramfs-tools/conf.d/resume /etc/initramfs-tools/conf.d/resume.old

Edit - in future it might be best to look for newer threads - I know that it has recent posts but it's 2 or more years old and probably a few versions behind gutsy.

---

