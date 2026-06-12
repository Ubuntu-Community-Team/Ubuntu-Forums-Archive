---
title: "simple partition question"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by tone33 on 2008-09-13
I've got a dual boot setup with vista/kubuntu and want to add another distro (gentoo) to the mix to make it a tri-boot.  I've maxed out my 4 primary partitions so i will have to use a logical partition for gentoo.  Can i do this?  Can a logical drive be a boot drive?

---

### Post by caljohnsmith on 2008-09-13
> **tone33 said:**
> I've got a dual boot setup with vista/kubuntu and want to add another distro (gentoo) to the mix to make it a tri-boot.  I've maxed out my 4 primary partitions so i will have to use a logical partition for gentoo.  Can i do this?  Can a logical drive be a boot drive?
Sure, linux can be easily booted from a logical partition with no extra effort. If you all ready have 4 primary partitions, you will have to convert one of them to an extended partition, and then within that extended partition you can have up to 63 logical partitions.

---

### Post by 1/0 on 2008-09-13
1st off. You do not want to mess this up! Back up everything. Really!

Yes you can boot from logical partitions. Just enter the correct root path (hdX,Y) in GRUB (*/boot/grub/menu.lst*). Older boards can't handle large hard drives but that's probably not your case, or?

---

### Post by tone33 on 2008-09-13
i've got everything backed up..  i'm well aware of the accidents that can happen when you fdisk thanks for the warning though. 

i'm actually now thinking about repartitioning everything...  i need to reorganize anyway and now seems like a good time.  So I want to be able to run windows and several linux distros and share some of the same files (See data partition below).


Here's initial thoughts on the partitioning of my 300GB drive:

80GB Pri Windows (NTFS)
50GB Pri for Data (NTFS) used as home partition in linux
10GB Extended Ubuntu
10GB Logical Kubuntu
10GB Logical Gentoo
 4GB Swap

164GB TOTAL

136GB Free - to be used for whatever...


I'll use GRUB to boot into whichever OS i want.  3 questions:

1) Will i come across any issues sharing the NTFS Data Partition between windows and linux?  I have files that will be accessed from both os's.  

2) Are there any particular advantages to using a /home partition formatted in XFS over my Data partition formatted in NTFS?

3) Can each of the linux distros use the same Swap partition?

---

### Post by 1/0 on 2008-09-13
1) Don't really know but I would say its probably fine. 

2) NTFS is not a good FS at all. It fragments, slow and just bad. But, if you use any other FS, Windows is going to be a problem. Access wont be easy. SO I doubt you really have a choice.

3) Yes, they can use the same Swap partition

I would probably give some more space to Gentoo since it compiles so much. /var and /usr usually gets quite large.

---

### Post by 1/0 on 2008-09-13
Oh, and why one partition for Kubuntu and one for Ubuntu? Thats the same distro... Just install ubuntu-desktop and kubuntu-desktop. You'll choose which window manager to log into in gdm/kdm.

---

### Post by tone33 on 2008-09-13
Actually i may just run kubuntu, but i'll keep that in mind if I decide to play around with gnome again in the future.  

So I think it is time for me to take the plunge as much into linux as i can.  I still need to share a data partition to share though for some things...  and i write software in .net so i can't escape completely, but i can move all my videos, pictures, and music to linux partitions (also building a media server so this falls in line with doing that).  I've read that XFS is a good file system for large files like this.  do you agree?  disagree?  any other recommendations?

How much space do you think Gentoo needs?

---

### Post by 1/0 on 2008-09-14
Well, I don't use Gentoo any more but my /usr grew to some 6 Gb alone... Also /var was close to 5 Gb. I'd give it at least 15 Gb in total. Its just irritating realizing you have to re-partitioning... (I'm there now.) If you only make 1 partition for Gentoo you wont have to worry about /var growing or /usr. 

I would(n't install windows in the first place but in your case I would) do something like this:

[list][*] 80GB Pri Windows (NTFS)
[*] 50GB Pri for Data (NTFS)
[*] 15GB Extended Ubuntu
[*] 15GB Logical Gentoo
[*] 4GB Swap[/list]

[This article](http://www.debian-administration.org/articles/388) about file systems might be interesting. I'm old fashioned and stick to ext3. Its just stable and ok in speed. You can tweak it and do many things with ext3. There's a guide about that on the Gentoo Linux forum. I think you'll learn a lot from Gentoo; I know i did. The next you'll know, you'll be installing LFS ;)

---

### Post by tone33 on 2008-09-28
thanks for the link and suggestions.  i partitioned before i got your reply so i ended up going with 10GB for Kubuntu, 15GB for Gentoo, and i think 2 or 4GB for swap.  I did indeed learn a lot with Gentoo, but have yet to get sound working... so i'm switching back to kubuntu for a bit.

---

### Post by 1/0 on 2008-09-28
No problem. [This guide](http://www.gentoo.org/doc/en/alsa-guide.xml) might help you configure your sound card.

---

### Post by WWSmith36 on 2008-09-28
> 80GB Pri Windows (NTFS)
50GB Pri for Data (NTFS) used as home partition in linux
10GB Extended Ubuntu
10GB Logical Kubuntu
10GB Logical Gentoo
4GB Swap

Not to split hairs with you but, an extended partion is block which can only contain logical partitions and swap partitions.  Therefore Ubuntu will really be on a logical partition as well.

I like the fact that you are using 10GB blocks for your Linux partitions.  I prefer small OS partitions due to the fact that I like to image drives for backup purposes.  I like to keep the OS separated from my data.  If any folder ¨grows¨ too large, it can easily be move to other data partition and linked symbolically.

Nice job

---

### Post by tone33 on 2008-09-28
> **1/0 said:**
> No problem. [This guide](http://www.gentoo.org/doc/en/alsa-guide.xml) might help you configure your sound card.

yea i've been through that.  Actually got alsa working, but i just don't hear any sound.  i've been posting about it over in the gentoo forums... getting some good help, but i just like the ease of ubuntu/kubuntu...  Gentoo forces you to learn a lot (which is not a bad thing).

---

### Post by tone33 on 2008-09-28
> **WWSmith36 said:**
> Not to split hairs with you but, an extended partion is block which can only contain logical partitions and swap partitions.  Therefore Ubuntu will really be on a logical partition as well.

I like the fact that you are using 10GB blocks for your Linux partitions.  I prefer small OS partitions due to the fact that I like to image drives for backup purposes.  I like to keep the OS separated from my data.  If any folder ¨grows¨ too large, it can easily be move to other data partition and linked symbolically.

Nice job

you're right..not sure why i listed it that way.  Thanks for pointing it out.

---

