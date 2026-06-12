---
title: "Want to dual boot my laptop!"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by serlex on 2006-10-18
Got my dapper 6.06 CDs other day
I like to install Ubuntu on to my laptop, which already has XP Pro.
Bit I'm not sure about is the partition bit, how should i setup?

Thank You
Sercan Acar

---

### Post by Kateikyoushi on 2006-10-18
If your laptop has only one hard drive then just make free space for your new linux partition, and install ubuntu following [this guide]("http://www.psychocats.net/ubuntu/installing").

If you have a hidden recovery partition that can make things bit complicated.

---

### Post by serlex on 2006-10-18
yes my laptop has one HD, bit im comfused about is the partition bit. What should it look like? I got this atm:

ntfs       34.34GB
ext3       20.56GB
linux-swap 1020MB

is this right?

---

### Post by Kateikyoushi on 2006-10-18
Yes that's right, do not really worry about it, you can resize them later if you will find them inadequate.

---

### Post by serlex on 2006-10-19
Dont know how this has happened, but when my laptop boots the Grub shows me 2 Ubuntu OS & Windows XP

Like this:

Ubuntu Kernel
Ubuntu Kernel(Safe Mode)
Ubuntu Kernel
Ubuntu Lernel (safe mode)
Other OS
Windows XP Pro

when i first installed Ubuntu yesterday, it showed just one, but now there are two.

I checked the disk, it looks like only one Ubuntu is installed.

---

### Post by h4rdwire on 2006-10-19
yeah i think thats normal thats what i get too...i just use the first Option when i'm going to use ubuntu and of course theres ur XP partition.

---

### Post by Kateikyoushi on 2006-10-19
I guess you ran the update which installed a fresh kernel.
Now you can choose at startup ehich to use, it is good to keep a second one just in case.

---

### Post by serlex on 2006-10-19
lol, yeah i installed the 160+ updates :d

---

### Post by bodycoach2 on 2006-10-19
> **serlex said:**
> Dont know how this has happened, but when my laptop boots the Grub shows me 2 Ubuntu OS & Windows XP

Like this:

Ubuntu Kernel
Ubuntu Kernel(Safe Mode)
Ubuntu Kernel
Ubuntu Lernel (safe mode)
Other OS
Windows XP Pro

when i first installed Ubuntu yesterday, it showed just one, but now there are two.

I checked the disk, it looks like only one Ubuntu is installed.

That's what it should look like (the GRUB bootloader).
On my computers, it only give me a few seconds to make the OS choice (I'd like to know how to slow that down). Use the page down key to go right to WindowsXP.

I'm in school for Computer Information Technology, so I have to use Windows. Otherwise, I'd only have Ubuntu on all my computers.

---

### Post by h4rdwire on 2006-10-19
> **bodycoach2 said:**
> That's what it should look like (the GRUB bootloader).
On my computers, it only give me a few seconds to make the OS choice (I'd like to know how to slow that down). Use the page down key to go right to WindowsXP.

I'm in school for Computer Information Technology, so I have to use Windows. Otherwise, I'd only have Ubuntu on all my computers.

you know if you move the cursor the time is delayed..but in the options you should be able to add seconds on the loader

---

### Post by gn2 on 2006-10-19
> **bodycoach2 said:**
> 
On my computers, it only give me a few seconds to make the OS choice (I'd like to know how to slow that down). Use the page down key to go right to WindowsXP.

I'm in school for Computer Information Technology, so I have to use Windows. Otherwise, I'd only have Ubuntu on all my computers.

Here you go: [http://www.ubuntuforums.org/showthread.php?t=228104](http://www.ubuntuforums.org/showthread.php?t=228104)

---

### Post by horatiub on 2006-10-25
> **Kateikyoushi said:**
> If your laptop has only one hard drive then just make free space for your new linux partition, and install ubuntu following [this guide]("http://www.psychocats.net/ubuntu/installing").

If you have a hidden recovery partition that can make things bit complicated.

I'm trying to create a dual boot as well, and I have the regular C partition then I have a recovery D partition, which is not hidden though, I can see it and access it through My Computer. Is this going to be a problem in my case?

---

### Post by horatiub on 2006-10-26
can anybody help me out? I really wanna try the new Ubuntu

---

