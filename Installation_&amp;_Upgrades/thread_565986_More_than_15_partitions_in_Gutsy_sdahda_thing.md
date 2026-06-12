---
title: "More than 15 partitions in Gutsy? sda/hda thing?"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by plamen_todoroff on 2007-10-02
I have one hdd in my laptop, separated in 20 partitions, 3 primary (win, boot, root) and 1 extended with 17 logical partitions in it. When I first installed Feisty I used Partition Magic 8 to repartition the hdd and form the above mentioned scheme, then I mounted all partitions manually in the feisty graphical installer, installation finished and login successful, and then i found that only the first 15 partitions were available, the last 5 showed up empty in nautilus. I google-d a little to find that this was due to some libata thingy changed in the new kernels and from 2.6.19 all hda drives were to be handled as sda thus limited to 15 partitons. I played with fglrx, xgl, c-fusion a little and messed it all up so i decided to go for a clean reinstall, i put the exactly same dvd again and did the exactly same things during installation, and when i logged in all 20 partitions where mounted and my files were nicely showing in nautilus. So the question is wtf could have been different in my reinstall, and, if from now on all hda will be treated as sda does this mean that i won't be able to use my 20 partitions in gutsy? It's really important to me. I've never expected  to be so much attracted be linux as to not want to go back to windows anymore, but it happened and i need some help to stay in the free world. Every answer is appreciated.

---

### Post by Pumalite on 2007-10-02
What do you need 20 partitions for???

---

### Post by plamen_todoroff on 2007-10-02
If I had separate partitions for /, /boot, /usr, /home and /var, installing 3 distros and a swap file exceeds the limit of 15, doesn't it? This is not my situation but just an answer to your question.

---

### Post by Pumalite on 2007-10-02
Just curious.

---

### Post by shad0w_walker on 2007-10-02
This doesn't help with your problem at all. But i simply have to know.

What the hell do you need all those partitions for? I can't think of a single thing that requires that kind of setup.

---

### Post by plamen_todoroff on 2007-10-02
I thought I was the linux newbie here :) Can I get at least one answer, not a question?

---

### Post by shad0w_walker on 2007-10-02
I genuinely don't have a clue what could have caused this behavior. Possibly libata updated and that limit was removed. However I still want to know why you have all these partitions. There is no reason on earth i can think of that makes this worthwhile?

---

### Post by Pumalite on 2007-10-02
Try Gutsy in two weeks. It might very well support 100 partitions.

---

### Post by plamen_todoroff on 2007-10-02
Is this the famous ubuntu forum a lot of people get help in? If I had separate partitions for /, /boot, /usr, /home and /var, installing 3 distros and a swap file exceeds the limit of 15, doesn't it? This is not my situation but just an answer to your question, and i hope everybody else's not looking farther than ubuntu as the ONE distro to rule them all.

---

### Post by Montsegur87 on 2007-10-02
I think you cant make more than 16 partition (logicals + primaries) in any HD.

---

### Post by plamen_todoroff on 2007-10-02
Believe me, you can. What about the libata thing, i need some answers about the hda/sda transition, please.

---

### Post by plamen_todoroff on 2007-10-03
Please, does anybody know what the situation with libata in Gutsy will be? Are hda disk to be treated as sda and thus having a limitation of 15 partitions?

---

### Post by tomski on 2007-10-04
really dont know about this but i have serious issue with this change to sda from hda 
because my cd keeps being accessed every couple of seconds & i am confused as to edit my
 fstab now as i do not know how to get the UUID for each device

---

### Post by dabl on 2007-10-04
Well, I think I wrapped multiple answers into my reply to OP's first post, which has fallen down the list, so I'll copy that reply here.

You asked for help ....  here's the best I got.  :lolflag:

For desktop/workstation use, unless you need one of the exotic filesystems (xfs, jfs, etc.), you really only want 3 partitions for Linux:

/
/home
swap

If it's important to have a shared NTFS data partition, then add /NTFSDATA to your /etc/fstab table after you have a successful installation up and running with the 3 listed above.

So, Help #1 is -- you're overdoing the complexity of your installation and getting bit by it.  You can share the swap with any other Linux, but I don't recommend sharing any of the other partitions -- /home, for example, has desktop settings and autostart programs in it, and will get messed up by the "most recent Linux" that used it, if you try to share it.

hda vs. sda vs. libata driver vs. ata.piix -- IMHO, there's been an exaggerated over-reaction to the simple need to change the Linux device-identifying architecture to accommodate the proliferation of USB and SATA devices.  It seems that everyone who was so comfortable with the /dev/hdn system has a dent in his karma, but the reality is it doesn't handle the USB bus worth a %&*@, so they fixed it with the UUID system.  Why PATA/IDE drives needed to be dumped into the /dev/sdn device nomenclature I have no idea, but it doesn't really matter for any practical purpose.  Just set up your /etc/fstab table using UUID numbers, and you'll be fine.  For USB drives (thumb or external), use ```
fdisk -l
``` or ```
hwinfo
``` to determine their /dev/disk/by-id number, and use the UUID number that you get from ```
blkid
``` and it will be fine.

Help #2:  do /etc/fstab like this (FYI, sda is an old IDE drive and the others are SATA drives, with a NTFS-formatted USB thumb drive at the end):

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sdb1
UUID=b1869c3e-b13a-4772-914c-bcc6db718967 / reiserfs nouser,notail,noatime,auto,rw,dev,exec,suid 0 1
# /dev/sdb2
UUID=a6c2ba7b-8492-4746-92af-5182dcb4daab /home reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sda1
UUID=f222f97f-278f-4db5-8642-513294f30193 /media/sda1 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sda3
UUID=adf641ca-f64e-4311-bc30-86bfcdcb669c /media/sda3 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sdc1
UUID=1ddd0144-0875-4667-9f98-e90a23f58ff3 /media/sdc1 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sdc2
UUID=710efad8-9f97-4bcd-8f57-8f8cc1facc2f /media/sdc2 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sdc3
UUID=f1912a56-2e5c-45ce-b91b-3ebbe69e20f4 /media/sdc3 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sdd1
UUID=cffddf89-57f3-40ab-a97f-40bb1ea45f16 /media/sdd1 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sdd3
UUID=9b7658da-59e1-4b2b-a4b9-fa3ee11b68cf /media/sdd3 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sde1
UUID=d182b7c3-298c-49b3-ac66-b378033b815c /media/sde1 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sdd2
UUID=94d4d572-3581-491b-90dc-e5f619c65908 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
# /dev/sdf1
UUID=A8FC3435FC33FC5E /media/NTFSTICK ntfs-3g user,atime,rw,nodev,nosuid 0 0
```

fglrx -- I fixed my ATI problem with my wallet and bought an Nvidia card .....  :lolflag:

Good luck with it!  :)


EDIT: Says [[COLOR="Lime"]**here**[/COLOR]](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/install-guide/ch-partitions.html), if you read down far enough, "due to the way partitions are accessed in Linux, you should avoid defining more than 12 logical partitions on a single hard drive".  For whatever that's worth.  So I'm deducing that 4 primary + 12 logical = 16 total is kind of the outer limits of a "smart" partitioning scheme for a single disk.   ;-)

---

### Post by louieb on 2007-10-04
I don't care why you have 20 partitions. But to answer the question. Starting with Edgy Ubuntu used the sata drivers in some cases for ide drives. Sata has that limit on the # of partitions you ran into first. Ide drives have no such limit. Want a hundred go for it. 

There appears to be nor rhyme or reason to Ubuntu saying an IDE drive appears as hd@  (ide) or sd@  (sata). So if you want Ubuntu to see more that the sata limit all I can say is ***"Do you feel lucky" ***- Dirty Harry       
> 
        Is this the famous ubuntu forum a lot of people get help in?:lolflag: Yes this is it. But you never know. This is a friendly bunch for the most part. You may not get an accurate answer. But you'll also almost never get the RTFM crops up.

One of my favorites from the wiki of another distro
> **FAQs**

 **Q)** When I run "pacman --sync" it comes up with "could not open sync database:reponame have you used --refresh yet?" but when I run pacman --refresh it does nothing?! 
**A)** This error is due to your inability to read man pages.  We recommend you try the pacman man page - it really is very useful. 

---

### Post by plamen_todoroff on 2007-10-05
> **louieb said:**
> I don't care why you have 20 partitions. But to answer the question. Starting with Edgy Ubuntu used the sata drivers in some cases for ide drives. Sata has that limit on the # of partitions you ran into first. Ide drives have no such limit. Want a hundred go for it. 

There appears to be nor rhyme or reason to Ubuntu saying an IDE drive appears as hd@  (ide) or sd@  (sata). So if you want Ubuntu to see more that the sata limit all I can say is ***"Do you feel lucky" ***- Dirty Harry       
:lolflag: Yes this is it. But you never know. This is a friendly bunch for the most part. You may not get an accurate answer. But you'll also almost never get the RTFM crops up.

One of my favorites from the wiki of another distro

There must be some rhyme or reason after all I guess. I don't want to get rid of my "luckily" installed Feisty and then destiny to say "NO" to my 20 partitions in Gutsy.

---

