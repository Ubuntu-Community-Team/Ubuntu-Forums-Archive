---
title: "Installing Grub to partition bootsector"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by ModusOperandi on 2007-04-14
Here's the scenario: I currently dual-boot Windows XP and Vista on one drive. I have another drive that I want to install Ubuntu on. Since I already have one bootloader in place, I want to just install Ubuntu to the second drive and use EasyBCD to add the Ubuntu entry to the Vista bootloader. For that to work, however, GRUB or LILO has to be installed on the bootsector of the partition.
 
What I hope I can do is install Grub directly to the bootsector instead of having it install to the MBR then have to go remove it. I'll be installing Dapper, but I will download the Edgy image if that's what it takes. I will also do it if Grub has to be installed to the MBR first, I'm really open to just about anything.
 
Thanks in advance.

---

### Post by yabbadabbadont on 2007-04-14
I believe that the Alternate Installation CD (use Expert mode) will allow you to install grub to a partition instead of the MBR.

Edit: I can't find the information since they redesigned the stupid download webpage, but on the old page the description of the alternate installation CD specifically mentioned that it was needed if you wanted to install grub anywhere other than the MBR.  They don't even have any links to the documentation for the Dapper version of the alternate installation CD anymore, just Edgy...  :roll:  I'm sure that the Dapper Alternate Installation CD will let you install grub where you want to though.

---

### Post by ModusOperandi on 2007-04-14
Yeah, I found the link after a bit of searching. The edgy one will install grub elsewhere, as well, which is just as well since I was going to update to Edgy immediately anyway.
 
The page is here: [http://releases.ubuntu.com/6.10/](http://releases.ubuntu.com/6.10/)
 
Thanks.

---

### Post by ModusOperandi on 2007-04-15
Ok, I installed it to what I hope is the correct partition (hd1,0) for the (I think) first partition of the second drive. I added the entry in EasyBCD for Ubuntu at Hard Drive 1, Partition 1 because that's the lowest partition number it goes to. When I boot and use the Ubuntu option from the bootloader, it just shows a black screen with the word GRUB in the top left corner. I'll search for a solution to that problem, but I figured I should post it here, as well.

---

### Post by yabbadabbadont on 2007-04-15
You could try installing grub to (hd1) -- the MBR of the second drive, if ubuntu is all that will be on it.  However, it kind of sounds like grub can't find the stage1.5 file.  You might boot a live CD, mount your ubuntu /boot partition (or just root if you didn't put /boot on it's own partition), and then check the /boot/grub/menu.lst file to see where it thinks the grub root is located.

---

### Post by Computer Guru on 2007-04-25
We just rewrote the entire Linux documentation for EasyBCD, the new instructions are much more failproof (and you can use SGD with them too!): [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by iminj on 2007-04-25
Interesting thread ... and thanks for that updated EasyBCD documentation, Computer Guru !!

Here is my issue with all of this - dual-booting Vista and ubuntu on the same drive with the Vista Bootloader:

If you install from the feisty LiveCD, it seems that GRUB is loaded into the MBR by default .. without any other options. So, if you want more flexibilty, you have to install from the ubuntu 7.04 "Alternate Install" CD.

When I switched to the "Alternate" CD, I used the partitioner to create a Root partition (/) and a SWAP partition for ubuntu. Now, where should I place GRUB if I want to use EasyBCD? Computer Guru refers to the *"bootsector of the partition that linux is being installed to".* In the installation field, do I simply enter my new feisty Root partition (hd0,1) .. or is there some other method to place GRUB specifically in some location called the bootsector? 

Thanks.
-iminj

---

### Post by yabbadabbadont on 2007-04-25
> **iminj said:**
> When I switched to the "Alternate" CD, I used the partitioner to create a Root partition (/) and a SWAP partition for ubuntu. Now, where should I place GRUB if I want to use EasyBCD? Computer Guru refers to the *"bootsector of the partition that linux is being installed to".* In the installation field, do I simply enter my new feisty Root partition (hd0,1) .. or is there some other method to place GRUB specifically in some location called the bootsector? 

You would install it to the root partition like you suggested.

---

### Post by Computer Guru on 2007-04-28
Yeah, the bootsector would be (hd0,1) - if that's where you are install Ubuntu to.
HOWEVER, I couldn't get it to work that way myself -> Ubuntu install errors out "Invalid location" to install GRUB.

I'd guess this is a bug. If the same happens to you, install it to the MBR, then from within Ubuntu install it to the bootsector.

Cheers!

---

