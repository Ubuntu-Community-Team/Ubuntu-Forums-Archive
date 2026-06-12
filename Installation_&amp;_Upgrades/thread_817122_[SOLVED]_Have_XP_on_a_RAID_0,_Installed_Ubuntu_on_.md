---
title: "[SOLVED] Have XP on a RAID 0, Installed Ubuntu on seperate drive fine but can't boot"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by apedeaux on 2008-06-03
Okay this seems like a problem several people have been having, but I can't find a good solution for it:

I have 3 SATA drives. First 2 are software RAID0 from my M2E-SLI mobo (nvidia) running XP64. I have a 3rd seperate SATA I am putting Ubuntu on.  The installation goes fine, but when I reboot, of course it goes straight to XP, without asking me which OS I want to boot.  If I go into my bios and tell it to boot from the Linux drive, I get a blank screen with a flashing cursor in the top left corner right after POST.  This is the same thing that happens if I try to boot off of a completely empty drive.

Reading through the forums, it seems like the problem is that Ubuntu needs to install GRUB on the (master) XP drive, but since it is in a RAID, the installer sees the 2 separate drives instead of one big drive, and either 1) puts GRUB on one of the separate RAIDed drives, which is inaccessible as soon as the RAID drivers load at boot (because it sees only the RAID, not the separate drives) 2) puts GRUB on the Linux drive, where it is useless b/c it can't get to the MBR, or 3) tries to put in on the RAID, fails, and doesn't put it anywhere.

At the end of my installation, I get the bars saying it is installing and configuring GRUB on hd0, with no error messages, so I think it may be sticking it on the first SATA on the RAID.  

When installing XP and setting up a RAID, you put in a floppy disk at the start of the install that gives XP the RAID drivers so it can see the array; is there a similar trick for Ubuntu? 

I have seen a number of different suggestions to others with this problem, but there are many different answers (dmraid, fakeraid, etc.) and they all seem fairly complicated.  Is there no simple way to let the Ubuntu installer see the RAID so it can put GRUB in the right place?

Thanks.

*edit* I'm at work now so can't try anything, but I was thinking, what if I unplug the two RAID drives from the mobo so that only the 3rd drive is connected, then install Ubuntu.  GRUB should load onto the Ubuntu drive, and I would guess I could boot it that way.  But once I plug back in my 2 RAID drives, will I be right back where I started?  I assume I wouldn't get the boot menu when booting up, but if I forced the bios to boot from the Ubuntu drive, would the GRUB be able to start it?  Also, would there be any risk of damaging my XP RAID by doing this?

---

### Post by linux4me on 2008-06-03
> what if I unplug the two RAID drives from the mobo so that only the 3rd drive is connected, then install Ubuntu. GRUB should load onto the Ubuntu drive, and I would guess I could boot it that way. But once I plug back in my 2 RAID drives, will I be right back where I started? I assume I wouldn't get the boot menu when booting up, but if I forced the bios to boot from the Ubuntu drive, would the GRUB be able to start it? Also, would there be any risk of damaging my XP RAID by doing this? 

Have you seen this article on [How to dual-boot Ubuntu and XP after installing them separately on two HDs]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs")?

It doesn't discuss the RAID issue, but the RAID drivers are already loaded on your XP RAID drives, aren't they? It seems like if you unplugged your RAID array from the MOBO, did the Ubuntu install, set the Ubuntu drive as your first boot device in the BIOS, plugged your RAID array back in, then followed the steps in the article above in order to add the option to boot XP from grub, you might be in business.

Another option would be to unplug the RAID array, do the install on the Ubuntu drive, plug the RAID array back in, and use the F8 key to determine which drive to boot from. That way, you'd have MBR's on both drives and Grub would be installed on the Ubuntu drive configured for an Ubuntu-only boot.

---

### Post by apedeaux on 2008-06-03
Worked like a charm!

Unplugged both RAID drives, installed Ubuntu to separate drive, plugged RAID back in, now I can boot XP and Ubuntu :)

The GRUB menu does not come up; instead I simply hit F8 at boot which is my MOBOs boot selector, then just pick if I want the XP drive or the Ubuntu drive to work.  At the moment I think I will stick with that, instead of trying to get GRUB to list both OSes.

Hooray! Now to try and get everything else to work ;)

---

### Post by linux4me on 2008-06-04
Excellent! Glad you got it working. 

Soon you will be ready to format over that nasty Windoze install and put Hardy x64 on that RAID array with dmraid. ;)

---

### Post by mike4ubuntu on 2008-06-04
Well, it's great that you got things to work, but this just sounds like a work-around for some kine of bug in the Ubuntu (Hardy) installation code.  Is anybody working on correcting the installation code?

---

### Post by apedeaux on 2008-06-04
Just so you know, before I realized the problem was with the RAID and GRUB, I tried installing Gutsy to see if anything would be different, and had the exact same problem, so it doesn't seem isolated to Hardy.

---

