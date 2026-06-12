---
title: "[SOLVED] SOS - Error 15 - Please help."
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by shankariyer on 2007-07-27
Every thing has been working perfect. This is a xp / ubuntu box. The last thing
I did was use partition magic to partition my external hard-drive before shutting
down this machine, last night.

I'm sure I partitioned the external drive :) not hdd.

I boot up this morning - Error 15.

I've only 1 hdd.

It doesn't even get to the grub menu now. I used the same feisty fawn installation cd and from the desktop, using gparted, I'm able to see the whole structure.

Please see the attachments and the gparted image.

Please help me rescue this machine.  I'm not sure what I've to do now.

Thanks.

---

### Post by merlinus on 2007-07-27
You can use SuperGrub to reinstall grub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

1. Make sure your computer is booting from the CD drive first.
   2. Put in the disk, and select &#8220;English Super GRUB Disk
   3. Select &#8220;GNU/Linux&#8221;
   4. Select &#8220;Fix Boot of GNU/Linux (GRUB)&#8221;
   5. Select the partition containing linux, you will see the message &#8220;SGD has succeeded&#8221;

This is an especially useful tool to have, regardless.

An alternative method is to boot from the ubuntu live cd, mount your hda10 partition manually, and in a terminal:

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

Substitute your results for (hdx,x).

-merlin

---

### Post by shankariyer on 2007-07-27
Pardon my ignorance - I'm not clear about this LiveCD, as while I've the fiesty fawn cd, that I used to install it in the 1st place, the words on this page [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) are a bit confusing...

Now, can I use the same CD as LiveCD and if so, the screen-shots that I posted, were using that only. So, can I proceed with the instructions here using Linux/Ubuntu Live CD ?

Or, should I download any of the previous versions as mentioned here [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

Thanks.

---

### Post by merlinus on 2007-07-27
You can boot from the ubuntu live cd, and use the terminal to mount your linux partition and enter the commands in the last part of my post.

Or you can download and burn the supergrub iso, boot from that, and follow those instructions.  SuperGrub is a small download.

-merlin

---

### Post by Gremlinzzz on 2007-07-27
Error# 15 : "Error while parsing number"
This error is returned if GRUB was expecting to read a numbur and encountered bad data.

---

### Post by shankariyer on 2007-07-27
You guys rock! Ubuntu support/wiki/community is awesome...
It worked !

Thanks Merlinus ! and every one... Here is what I did...

Boot onto the LiveCD {Feisty Fawn's installation CD itself is LiveCD, as you can open up a terminal and issue these commands or access the drives( which has windoze or other OS ) } and follow the log below.

> 
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,9)

grub> root (hd0,9)
root (hd0,9)

grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,9)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

grub> quit
quit


---

### Post by shankariyer on 2007-07-27
I spoke a bit fast I guess... Now, while windoze is recovered correctly, Ubunbu is not.

When I choose Ubuntu from the grub, it says Error 15 : File not found :(

---

### Post by rbmorse on 2007-07-27
> **merlinus said:**
> You can boot from the ubuntu live cd, and use the terminal to mount your linux partition..."

Do you really have to mount the linux partition?

---

### Post by shankariyer on 2007-07-27
I didn't get your question - I'd like to revert it back as how it was and I'd like to access Ubuntu.

---

### Post by shankariyer on 2007-07-27
I may be wrong but when the output of the 'find' was
> 
grub> find /boot/grub/stage1
find /boot/grub/stage1
**  (hd0,9)**
But the **/boot/grub/menu.lst** has
> 
title        Ubuntu, kernel 2.6.20-16-generic
**root        (hd0,10)**
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=563677d3-e3a8-43de-9a79-0df36866cf59 ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-16-generic (recovery mode)
**root        (hd0,10)**
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=563677d3-e3a8-43de-9a79-0df36866cf59 ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu, memtest86+
**root        (hd0,10)**
kernel        /boot/memtest86+.bin
quiet
I'm not sure whether I can modify this? Please advice.

---

### Post by merlinus on 2007-07-27
(hd0,9) is correct, because numbering starts at 0 and not at 1.

So sda10 is 9 for these purposes.

You can edit /boot/grub/menu.lst to reflect this.

-merlin

---

### Post by shankariyer on 2007-07-27
Yes, it worked !

Didn't realize that the grub mod won't update the /boot/grub/menu.lst accordingly.

---

