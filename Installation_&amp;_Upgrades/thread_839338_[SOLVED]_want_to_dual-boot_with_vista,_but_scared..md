---
title: "[SOLVED] want to dual-boot with vista, but scared..."
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by muteXe on 2008-06-24
Hi,
I've successfully set up dual-boot machines three times now, each with windows xp running along side ubuntu.  I'd boot from the live CD, choose install, use the installer to resize my xp partition, make ubuntu install in this new space, and hey presto it would work.
I would now like to dual-boot my new laptop, but it's got vista on it.  I have been hearing some stories that the MBR is different (more complicated) in vista, and that vista has its own partitioning tool, and I would be better off making room for my linux-partition-to-be in vista using this partitioning tool.

ANy comments on this please?  If i try and install ubuntu on my machine in the way I have done it for my xp machines will it work?  Or do people suggest i use the vista partitioning tool?

Confused I am.
Many thanks.

---

### Post by niyonk on 2008-06-24
You have to use a diff. method
Try taking a look at [this]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")
:)

---

### Post by niyonk on 2008-06-24
Before i forget...
If you want to use Vista's Bootloader, use a program called easyBCD.

And...before u install. make sure u format using 
vista's partition manager, then using ubuntu at the installation.
(the reason behind this is a very annoying error) at times when u start ubuntu. 

something like this: "Partition 1 does not end on cylinder boundary."

Believe me it's annoying :(. But i got rid of it :)

---

### Post by muteXe on 2008-06-24
Cheers niyonk.  That's the page I've been looking at actually.  I guess it looks like i have to shrink vista partition in vista, then using the live cd install ubuntu into this unallocated space.
Does that sound right?  I'm still nervous to try this :)  I'll stick with grub to make things a bit easier as well.

---

### Post by Rallg on 2008-06-24
Two comments:

1. Yes, the Vista boot is different from XP boot. If you later change your mind and decide to go back to Windows-only, then be sure that the advice you read pertains to Vista, not XP. But I think you will like Ubuntu nowadays.

2. On my laptop, the MBR and Vista bootloader have not been modified. In addition to Vista, I have Ubuntu i386 and Ubuntu amd64. When I installed Ubuntu, I used the "Advanced" feature to place Grub on Ubuntu's own partition(s) rather than at (hd0,0) or at the Windows parition. Then, I put Grub4DOS on a bootable USB memory stick, and modified its menu.lst to point to the various systems on my hard drive. If I don't have the USB inserted and selected at boot time, my laptop boots directly to Vista with no knowledge of Grub or Ubuntu. With the USB inserted and selected, I can boot to any system. So, if you are worried about interfering with Vista's boot method, then consider using Grub4DOS on a USB (if your laptop supports it). If I lose the USB stick, no problem, since the info can be reconstructed onto another USB stick. There are some tricks involved (you will need to manually change info that would otherwise be maintained automatically). Since the methods involved are descibed in many places, I won't give the details here.

---

### Post by muteXe on 2008-06-24
thanks guys, good people on this forum.

---

### Post by muteXe on 2008-06-24
oops one more question:
when i'm in vista and I shrink it to leave me say, 40Gb of unallocated space, will my swap also go in this 40Gb, along with ubuntu?

cheers.

---

### Post by avtolle on 2008-06-24
Yes, your swap will go into the 40Gb space.

---

### Post by niyonk on 2008-06-24
> **muteXe said:**
>  I'll stick with grub to make things a bit easier as well. 
The reason behind my preference is because Grub isnt that much attractive lol

Do tell if you encounter more problems ;)

---

### Post by jimv on 2008-06-24
Balderdash.  There's no special procedure for dual booting Vista if you're installing Ubuntu on a machine that already has Vista.  I install Ubuntu on my Vista box last week, and dual boot works just fine.  I also ran Vista/Ubuntu on this laptop that came with Vista for several months before removing Vista to get more space.

Yeah, Vista loads differently than XP, but the point where Grub turns over control of the boot process to Windows is the same.

---

### Post by Rallg on 2008-06-24
Balderdash? Maybe. It's true that a correctly done install of Ubuntu with Vista dual-boot is the same as Ubuntu with XP. Really, there should not be a problem.

However, if the user wishes to make "variations" (or mistakes), then the methods for fixing it may be different for Vista and XP, becasue the two versions of Windows use different boot software.

Many users, having a problem, simply use a general search engine to find solutions. Since XP-related solutions are older, many results will be XP-specific, without mentioning Vista.

I can't begin to tell you how many XP-related fix-it solutions advise using the XP installation CD, despite the fact that the majority of computers (especially laptops) did not come with the CD, thereby making the advice useless.

---

### Post by muteXe on 2008-06-25
> **jimv said:**
> Balderdash.  There's no special procedure for dual booting Vista if you're installing Ubuntu on a machine that already has Vista.  

Now i'm really confused.  So i can just boot up the live CD, and install ubuntu like that as normal (normal for me being dual-booting with xp)?  No need to shrink the vista partition within vista??

---

### Post by Liakath on 2008-06-25
> **jimv said:**
> Balderdash.  There's no special procedure for dual booting Vista if you're installing Ubuntu on a machine that already has Vista.  I install Ubuntu on my Vista box last week, and dual boot works just fine.  I also ran Vista/Ubuntu on this laptop that came with Vista for several months before removing Vista to get more space.

Yeah, Vista loads differently than XP, but the point where Grub turns over control of the boot process to Windows is the same.

I agree. I was able to install Ubuntu 7.10 on my laptop (Toshiba A-200 with 2GB RAM) which had Vista Business Edition using Ubuntu partitioner without any difficulties. Grub also installed for dual boot without any hazzle.

Later I could upgrade to Ubuntu HH 8.04 after a clean install and happily running.

---

### Post by muteXe on 2008-06-26
Thank you Liakath, I think i'll wait til the weekend to try it :)

---

### Post by muteXe on 2008-06-27
Well that went disturbingly well :)
I installed 8.04 in the normal way without first shrinking the vista partition from within vista.  Worked like a dream.
Thanks for everyone's input.

mute

---

