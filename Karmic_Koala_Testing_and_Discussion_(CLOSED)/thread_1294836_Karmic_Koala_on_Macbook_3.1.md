---
title: "Karmic Koala on Macbook 3.1"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by topher- on 2009-10-18
Hello.

My roommate has a macbook 3.1.  She lost all of her apple restore CDs and such during a move, and there was some sort of problem preventing her computer from booting at all.  After dealing with Best Buy (where she purchased the computer), and them telling her they would not fix it without her original CDs, I decided to try to install Ubuntu on it for her.

I used Karmic Koala because it actually came on a cd with a Linux magazine I purchased, and figured it would be easier than downloading another (eariler, more stable perhaps) distro.  In any case, I installed Ubuntu on the computer as the only OS (there is no mac partition or anything anymore).  However, now it will not boot into Ubuntu at all.  I have been reading around on the forums about rEFIt and such, and tried to use that to boot from the "legacy OS", but when I select that option from the rEFIt menu, it does the same thing as a normal boot and just gives me a blinking cursor.  I have also tried to go into the partition tools on rEFIt, but it always gives me "Analysis inconclusive, will not touch this drive."

Any help with this issue would be greatly appreciated.  The only solutions I have seen on the forums deal with a dual-boot OS and using OSX/Mac tools from the Mac partition.  Which no longer exists on this computer.

Again, any help would be super :)

Thanks.

---

### Post by Bachstelze on 2009-10-18
Basically, you need to install GRUB in the boot sector of your Ubuntu partition, *not* on the "MBR". I don't know if a Live CD will let you do that, did you see anything that looked like it?

---

### Post by topher- on 2009-10-19
I don't see the option on the LiveCD anywhere.  Is there another way to do this?  I'm going to look around online to see if I can find any solutions.

---

### Post by Bachstelze on 2009-10-19
> **topher- said:**
> I don't see the option on the LiveCD anywhere.  Is there another way to do this?  I'm going to look around online to see if I can find any solutions.

You'll probably have to install using an Alternate CD. When you're at the partitioning step, remember the number of the partition you installed Ubuntu on (for example /dev/sda1) and use that when you're prompted where you want to install GRUB.

---

### Post by N_Nick on 2009-10-19
If i am not mistaken you can choose where to install the bootloader at the last step of the installation where you can see the overview.

You can do that by clicking on advanced.

Ubuntu does that automatically on my 4,1 and 5,5 MBP though, so i'm not sure that this is your problem. I could be wrong.

Good luck anyway

---

### Post by mabovo on 2009-10-19
You can also use a bootable iso cd from [http://refit.sourceforge.net/](http://refit.sourceforge.net/)
and install refit in a separate partition aproximately 200 MB to have choice booting into Ubuntu.

---

