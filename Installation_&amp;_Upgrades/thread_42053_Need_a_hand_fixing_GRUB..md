---
title: "Need a hand fixing GRUB."
date: 2005-06-15
forum: Installation &amp; Upgrades
---

### Post by jrronimo on 2005-06-15
I'm not sure if 'installation help' is /exactly/ where I need to be as I've had a working installation, but it's about GRUB, and that's an /early/ use thing, heh.

I think I've broken my GRUB. Here's the setup (that I learned in my Linux class, kind of) 

1. Install Windows to partition 1. 
2. Install Ubuntu to partition 2. 
3. Install Webmin because it makes hard things easy. 
4. Install Grub to /dev/hda2 (Stage 2 -- the installation comes up 'failed', but it works) 
5. dd if=/dev/hda2 of=/mnt/c/ubuntu.bin bs=512 count=1 
6. fdisk /mbr 
7. add c:\ubuntu.bin "Ubuntu Linux!" to c:\boot.ini 

So, to recap up to this moment, I'm switching from using GRUB to using the Windows bootloader to boot my Linux. It works well, and I like it. I don't have to worry about any Windows repair hosing the mbr and having to deal with re-installing grub or whatnot, even if it is easy. Regardless, this is what I have done. 

Part B. 

Since we use(d) Fedora Core 3 for my class, I used Acronis ([http://www.acronis.com/](http://www.acronis.com/)) to make an image of my Linux install, deleted the partition and installed Fedora. I learned what was needed and now I want to go back to Ubuntu. So I re-load the image. 

As expected (and as we've seen in class), attempting to boot using the Ubuntu selection in the Windows boot loader brings up a screen that says 'GRUB' and nothing else, since GRUB can no longer find it's sweet sweet Stage 2 bits. 

I know that I need to get back into Ubuntu and use webmin to reinstall GRUB stage 2 to /dev/hda2 and I will be happy again. 

There-in lies the problem. I can't boot into Ubuntu to fix my boot loader to boot Ubuntu. In class we've used a rescue disc that magically boots to the partition, but I neglected to steal that CD, so that is not an option. 

SO, my question is this: Is there a way to boot to Ubuntu using the install CD? Can I pass kernel=/boot/[blah blah] initrd /boot/[blahblah] into the boot command? 

Other tools at my disposal: A set of Fedora Core 3 Install CDs (minus the rescuecd) and Knoppix 3.9. 

If I can just get into my Ubuntu install I'll be set. 

Things I've tried thus far: 
boot to Fedora CD in rescue mode -> mount /dev/hda2 -> chroot /mnt/ubuntu -> grub-install /dev/hda 
result: errors out 
Can get into the grub shell, but can't figure out the syntax to install stage 2 to /dev/hda2. 

boot to Ubuntu CD in rescue mode -> grub-install /dev/hda 
result: "The file /boot/grub/stage1 not read correctly." 
attempting to enter the grub shell in this mode returns 'Error opening terminal: bterm." 

Boot to knoppix -> try the same stuff as Fedora 
result: I dont' even remember, but it didn't work.

Thanks in advance.

---

### Post by wvslkr on 2005-06-16
I may be totally off here since I have never used the NT loader method,nor even read the docs for it at this point, but if I am understanding correctly you want to pass your commands to grub loaded on hda2 not hda.  If I am off, ignore me, but it just seems to me your path is not right.
GL.

---

### Post by jrronimo on 2005-06-16
Basically you write a binary of the GRUB Bootloader and then overwrite it and have the NT boot loader launch straight to GRUB stage2.

I downloaded the Ubuntu live cd today and was able to get GRUB installed properly again. :D So I'm A-OK.

Hopefully this helps someone else eventually. haha.

---

### Post by alainhenry on 2005-06-17
If I understand well, I had a similar problem, and had to reconfigure GRUB to boot Ubuntu.  I did this:

Use any live CD to boot your machine, launch a root terminal, mount Ubuntu root partition (hda2 in your case, for exmaple to /mnt/hda2) and then go to directory where brub lies: /mnt/hda2/boot/grub

Launch grub
$>grub

from the grub command prompt execute the followin command
>root (hd0,1)       
    (this is hda2 in grub talk)
>setup (hd0)

and then reboot.  I assume you have a correct menu.lst in /mnt/hda2/boot/grub.  


Alain

---

