---
title: "Problems With GRUB"
date: 2006-09-14
forum: Installation &amp; Upgrades
---

### Post by Lauren926 on 2006-09-14
I've been running Windows XP and Ubuntu on dual boot for about six months. Yesterday, I decided to format the Windows XP partition and install FreeBSD on it instead, including FreeBSD's own booter. The new booter wouldn't allow me to load up Ubuntu for some reason, so I decided to format the FreeBSD partition and install GRUB again. Unfortunately, I'm having trouble with it. 

After I formatted the FreeBSD partition I ran the Ubuntu CD and tried the following in the terminal:

sudo grub
root (hd0,2)
setup (hd0)

(My Ubuntu is installed on the hda3 partition, so GRUB recognises that as hd0,2, is that correct?)

Anyway, that hasn't worked. Now all I get when I boot up is a black screen.
Is there something that I'm not doing? I'd appreciate it if someone could explain what I need to do to get Ubuntu booting again, step by step. Thanks in advance.

---

### Post by wieman01 on 2006-09-14
Have you made corresponding changes in "/etc/fstab"? You need to adjust the mount points accordingly.

Your GRUB command seems ok.

---

### Post by Lauren926 on 2006-09-14
> **wieman01 said:**
> Have you made corresponding changes in "/etc/fstab"? You need to adjust the mount points accordingly.

Your GRUB command seems ok.

What would I need to change in /etc/fstab? And can I do it with just a normal text editor?

---

### Post by wieman01 on 2006-09-14
Text editor is fine. If your partitions' sequence has changed you need to change the numbering in "fstab" as well. 

E.g.

/[root] : hda3
/home   : hda2
/[swap] : hda1

Depends on how your partitioning looks like. You can change "fstab" after booting the LiveCD and mounting your Ubuntu root partition.
> sudo mount /dev/hda3 /mnt
sudo gedit /mnt/etc/fstab

---

### Post by Lauren926 on 2006-09-14
> **wieman01 said:**
> Text editor is fine. If your partitions' sequence has changed you need to change the numbering in "fstab" as well. 

E.g.

/[root] : hda3
/home   : hda2
/[swap] : hda1

Depends on how your partitioning looks like. You can change "fstab" after booting the LiveCD and mounting your Ubuntu root partition.

I've checked "fstab" and this is what it looks like:



# /etc/fstab: static file system information.
#
# <file system>    <mount point>   <type>  <options>       <dump>  <pass>
proc               /proc           proc    defaults        0       0
/dev/hda3          /               ext3    defaults,errors=remount-ro 0      1
/dev/hda6          none            swap    sw              0       0
/dev/hdc           /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd           /media/cdrom1   udf,iso9660 user,noauto     0       0




Is that right? I know that Ubuntu is definitely installed on hda3 and hda6 is the swap partition.

---

### Post by Lauren926 on 2006-09-14
It's not letting me post it properly, but it basically looks like this:

proc............/proc.....proc
/dev/hda3......./.........ext3
/dev/hda6........none.....swap

---

### Post by wieman01 on 2006-09-14
Cannot tell if this is correct or not, you'll have to attach a screenshot of "Gnome Partition Editor" so that I can tell what going on on your HD. Could you upload it?

The Partition Editor should tell you what the sequence is & what the numbering should like.

---

### Post by Lauren926 on 2006-09-14
There's a screenshot of Gnome Partition Editor and one of the "fstab" file.

---

### Post by wieman01 on 2006-09-14
Lauren, your commands are totally fine. I cannot see any issue, "fstab" is ok as well. However, "hda1" has the boot flag when you look at the GParted screenshot. I think that's your problem, you need to undo that.

As I am not in front of my own computer, could try to remove the flag? I seem to remember that you can achieve this using GParted.

I suspect that your GRUB points to "hda1" rather than "hda3". Formating the MBR with a Win98 CD would do as well I reckon (fdisk).

---

### Post by wieman01 on 2006-09-14
Oh, hang on a minute... Could you also post:
> /boot/grub/menu.lst
Perhaps the fault lies there.

---

### Post by Lauren926 on 2006-09-14
> **wieman01 said:**
> Lauren, your commands are totally fine. I cannot see any issue, "fstab" is ok as well. However, "hda1" has the boot flag when you look at the GParted screenshot. I think that's your problem, you need to undo that.

As I am not in front of my own computer, could try to remove the flag? I seem to remember that you can achieve this using GParted.

I suspect that your GRUB points to "hda1" rather than "hda3". Formating the MBR with a Win98 CD would do as well I reckon (fdisk).

I removed the boot flag from hda1 and I'm still experiencing the same problem. Just a black screen when I boot up, no GRUB menu or anything. I don't have a Win98 CD either. :(

---

### Post by wieman01 on 2006-09-14
Ok, please open this file and post the content. I think that's where the problem is:
> sudo gedit /boot/grub/menu.lst

---

### Post by randell6564 on 2006-09-14
> **Lauren926 said:**
> I've been running Windows XP and Ubuntu on dual boot for about six months. Yesterday, I decided to format the Windows XP partition and install FreeBSD on it instead, including FreeBSD's own booter. The new booter wouldn't allow me to load up Ubuntu for some reason, so I decided to format the FreeBSD partition and install GRUB again. Unfortunately, I'm having trouble with it. 

After I formatted the FreeBSD partition I ran the Ubuntu CD and tried the following in the terminal:

sudo grub
root (hd0,2)
setup (hd0)

(My Ubuntu is installed on the hda3 partition, so GRUB recognises that as hd0,2, is that correct?)

Anyway, that hasn't worked. Now all I get when I boot up is a black screen.
Is there something that I'm not doing? I'd appreciate it if someone could explain what I need to do to get Ubuntu booting again, step by step. Thanks in advance.

post the result of [B]find /boot/grub/stage1

[/B]

---

