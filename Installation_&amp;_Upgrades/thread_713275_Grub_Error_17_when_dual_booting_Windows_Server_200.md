---
title: "Grub Error 17 when dual booting Windows Server 2003 and xubuntu"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by motoperpetuo on 2008-03-02
I've installed the evaluation version of Windows Server 2003 on my old desktop to use for studying for my MCSA (don't hate me, I'm trying to destroy the system from the inside). However, I'd like to use Linux on this machine when I'm not studying, so I figured I'd install xubuntu also and dual boot. However, after installing xubuntu I'm getting "GRUB error 17" after POST.

i've spent a lot of time looking around on this forum and others and trying different things. No success yet, but I've inferred that the problem is likely caused by the entries in my /boot/grub/menu.lst not matching up with the my actual partition information as reported when I run "fdisk -l" from a command prompt. Problem is, I'm not sure what exact changes to make to menu.lst.

Here is the output from "fdisk -l":

------------------------------------------------------
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x477a4779

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       16617   133468020    7  HPFS/NTFS
/dev/sda2   *       16618       19364    22065277+  83  Linux
/dev/sda3           19365       19457      747022+   5  Extended
/dev/sda5           19365       19457      746991   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
--------------------------------------------------------

Here is my menu.lst (excluding the REMed out parts at the beginning):

--------------------------------------------------------
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d5449ddd-5dfb-4c89-8588-ce12071f5ebe ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d5449ddd-5dfb-4c89-8588-ce12071f5ebe ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1
-----------------------------------------------------

Can anyone tell me what I need to change in menu.lst? Or, if that's not it, what I need to do?

---

### Post by Pumalite on 2008-03-02
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by motoperpetuo on 2008-03-02
Hmm...lotsa links there. I've been meaning to get more familiar with GRUB, so I'll definitely check this out.

In the meantime, if any kind soul has the *specific* answer (I think it would be simple for someone who is knowledgeable about GRUB), please do tell. I'm hoping to get this working today. Gotta go back to working on MS Windows tomorrow, unfortuantely...

---

### Post by motoperpetuo on 2008-03-02
I checked out the section on grub error 17 in the link above, and as near as I can tell, the entries in my menu.lst file are correct. that is, if i only have one physical hard drive in my system and my linux partition is sda2, grub should expect that to be hd0,1, correct?

can anyone verify this? if my menu.lst isn't the problem, can someone give me more suggestions? i tried running a disk check in the partition editor on the xubuntu live cd, but it errored out (something generic on the lines of "there was an error"). i'm not sure how to try a disk check from the command line.

any help would be greatly, greatly appreciated.

---

### Post by Pumalite on 2008-03-02
Your menu.lst is in accordance with your fdisk. Your problem lies somewhere else. I wish I knew. Dig into that link I gave you. It's the best source of Grub errors I know.

---

### Post by motoperpetuo on 2008-03-02
> **Pumalite said:**
> Your menu.lst is in accordance with your fdisk. Your problem lies somewhere else. I wish I knew. Dig into that link I gave you. It's the best source of Grub errors I know.

Thank you, I appreciate the confirmation. If anyone else has any ideas, please let me know. Meanwhile, I'll be checking out the info on that link.

---

### Post by motoperpetuo on 2008-03-02
When I try to do a manual direct boot with the Super GRUB CD, I get "Error 18: Selected cylinder exceeds maximum supported by BIOS," for what it's worth. Windows boots fine through SG.

---

### Post by Pumalite on 2008-03-02
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by Pumalite on 2008-03-02
That usually means you have to make a 200 MB /boot partition at the beginning of your drive. There are other details, but I'm not very knowledgeable about that. There are others in this forum that can help you with the details.

---

### Post by motoperpetuo on 2008-03-02
> **Pumalite said:**
> That usually means you have to make a 200 MB /boot partition at the beginning of your drive. There are other details, but I'm not very knowledgeable about that. There are others in this forum that can help you with the details.

this is true. i've vanquished the dreaded grub error 18 before by doing just that. actually, i tried it before on this computer too, sometime around the second hour of this six + plus hour attempt to get this to work. although, i may have been doing something wrong that time. i might as well give it another shot.

the bright side is that i've at least figured out how to get windows to boot again with the super grub disk. i really do appreciate your help. and, as i said, if anyone else has any ideas, please send 'em my way.

---

### Post by motoperpetuo on 2008-03-02
Tried installing again, using the 200mb /boot partition as suggested. No dice. I'm back to grub error 17 again.

---

### Post by danielcc on 2008-03-02
i had a heap of grief with grub today... here's what i found... [http://ubuntuforums.org/showthread.php?t=713427](http://ubuntuforums.org/showthread.php?t=713427)

---

### Post by motoperpetuo on 2008-03-02
I found a reference to fsck sometimes fixing this problem, so I tried the following (based on the commands that fixed this problem for someone on this thread: [http://ubuntuforums.org/showthread.php?t=442945&page=7](http://ubuntuforums.org/showthread.php?t=442945&page=7)).

     sudo e2fsck -C0 -p -f -v /dev/sda2

     sudo e2fsck -C0 -p -f -v /dev/sda2

still no luck. i'll keep researching. if anyone has any ideas, please let me know. thanks!

---

### Post by motoperpetuo on 2008-03-03
> **danielcc said:**
> i had a heap of grief with grub today... here's what i found... [http://ubuntuforums.org/showthread.php?t=713427](http://ubuntuforums.org/showthread.php?t=713427)

Ah, you're a lucky man. Sounds like you were getting the grub error 17 for the common reason (entries in menu.lst don't match the actual numbers of your partitions). my problem  seems to be much more obscure. i'm gonna be proud of myself if i figure this one out.

anyway, i'm going to bed for now...

---

### Post by Nibblyn on 2008-03-05
redundant

---

