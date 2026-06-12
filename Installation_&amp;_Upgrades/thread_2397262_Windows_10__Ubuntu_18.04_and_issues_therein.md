---
title: "Windows 10 / Ubuntu 18.04 and issues therein"
date: 2018-07-27
forum: Installation &amp; Upgrades
---

### Post by Linux Pilot on 2018-07-27
Hello all,

First, I apologize for the 'duplicate' thread.  I created it only because I have read a lot and continue to get further confused and turned around.  I also have several issues seemingly not completely addressed elsewhere.

1st:

I have Win10 on an SSD
I want to place Ubuntu on a 2nd SSD (complete drive, not a partition)

When I created a USB live drive and installed via that, it installs per some previous instructions I found (no date on the post, but seems relatively new) for dual HDD and dual boot.  So far, it is not working well.  When I install, get the reboot prompt, I reboot and it goes straight to Ubuntu and hangs at the purple screen with the cursor able to move around.

I can manually reboot, F12 to get the one time boot menu and boot into windows that way, but otherwise I assume it is not detecting windows as when I install (though I use the other option) it does not offer to install alongside windows.

I do not assume it matters but I have several other HDDs that are storage only at this point for Windows files.

The basics of the instructions were to turn on UEFI only boot, turn off secure boot, and turn off fast boot.  Then create partitions as follows:

650MB EFI 
XXXMB /  (root)
a swap partition
remaining drive /home partition

I can create all the partitions in the install fine.  I point the bootloader at the EFI partition and all goes well, installs without issue but then I get the purple / pink whatever screen on boot.  Whether that is my only issue or not, I do not know.  It may all resolve once I am actually able to boot into Ubuntu and ensure all the grub stuff has loaded and is up to date.

Finally, are the partitions necessary for 18.04?  Or can I point it at a formatted SSD and allow it to install on it's own?

Thanks for any help, and I apologize for the duplicate thread, but this has gotten annoying with so much old information floating around in various places.

Thanks again,

---

### Post by yancek on 2018-07-27
Your windows SSD already had an EFI partition in all likelihood if it was an EFI install.  Did you create a separate EFI partition on the Ubuntu SSD?  Did you update grub from Ubuntu to see if it detected windows?  Not sure which option you chose but it should have been the Something Else option.  The best site for instructions is the link below which is the official Ubuntu documentation on the subject.  Maybe that will help, otherwise I would suggest getting the boot repair software and running it then posting the output here to get some help.

  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2018-07-27
What video card/chip?
Often video issues related to which card/chip you have.
Can you boot recovery mode? It has nomodeset built in which probably will work but give low quality graphics.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Linux Pilot on 2018-07-27
Yancek,

Thanks for replying and helping.  
I did create a separate EFI partition on the ubuntu and.  I did read that upgrading grub sometimes fixes the issue with it seeing windows, etc, but have yet to get into the OS.  Even ctrl shift f1-for doesn't work.  I will read through when I get back home.  Thanks again.

Oldfred, 

Thank you as well for replying and helping out.  Video card is nvidia gtx 1070.  I cant remember off hand which chipset the mobo has.  I will try to get into recovery mode as well as the other options when I get back home tonight.

Thank you again!

---

### Post by oldfred on 2018-07-27
It seems the newer nVidia cards/chips need nomodeset & install of the nVidia proprietary driver.
Very new ones like yours will probably need you to add ppa to get latest version. Do not download directly from nVidia.

       nVidia install, purge if needed.
[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)

---

### Post by Linux Pilot on 2018-07-29
Thank you oldfred!  

The nVidia issue was exactly my problem.  It is sorted now.  I an working on the other.  I formatted the ssd I had installed onto and will try again after I read through the thread in your signature to make sure I get that portion done without issue.  It is much easier to restart it now than when I have several months of tweaks and work on the drive.

Thank you, and I will mark the thread solved.

---

### Post by Linux Pilot on 2018-07-29
I wanted to add a final note to hopefully be helpful to those fellow converts from a Windows environment.  I ultimately discovered my issue when I happened to notice my Windows SSD was in an MBR format and the Ubuntu drive was gpt.  I finally sorted that (you can convert the drive if your situation allows) through a format and reinstall of Windows.  When that was complete, I formatted and reinstalled Ubuntu as described in my original post.  Grub popped right up.  I booted into Windows just to make sure, then into Ubuntu, updated drivers and am now happily in a linux environment sorting things.

Thank you again, Fred, for all of your help, and time in doing so.

---

