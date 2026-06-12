---
title: "installation Failed"
date: 2018-07-07
forum: Installation &amp; Upgrades
---

### Post by webdoc on 2018-07-07
I'm trying to install Ubuntu 18.04 on my desktop, but the installation process is halted with 2 fail lines as follows.

Failed to idle channel 2
Failed to idle channel 3

At this point it's as if the installation has frozen, so I am unable to get to the try ubuntu or install ubuntu screen.

---

### Post by Autodave on 2018-07-07
Is Windows on the hard drive now? Did you disable *fastboot* yet?  Are you trying to dual boot or wipe Windows and install Ubuntu?

Some specs on the machine might be useful.

---

### Post by webdoc on 2018-07-07
Windows 10 is on the machine already, fastboot & hibernation have been disabled I will be hopefully setting up as dual boot with Ubuntu this will be on another hard drive and not my windows hard drive,  

Geforce 8800 GTX graphics
Intel Core 2 Quad CPU Q6600 2.40.GHz

Ubuntu install went fine on my laptop but on desktop all I get is a lot of writing on a black screen and it just hangs there not able to get past this.

---

### Post by oldfred on 2018-07-07
Only use Something Else install option.
And choose on partitioning screen to install grub2's boot loader into same drive as you are installing Ubuntu.

Older nVidia card should just work, but you may need nomodeset.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If you do install a proprietary nVidia driver, it will have to be an older one. Check which is correct, but only install from Ubuntu repository.
       
 Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

---

### Post by webdoc on 2018-07-07
Thanks for your answer & help

But I cannot use the something else option as the liveCD does not load that far, not even able to get at grub menu also I am on the old BIOS not UEFI

---

### Post by oldfred on 2018-07-07
With BIOS you do not get grub menu on install, but purple screen.
You do need to press the "any key" then f6 to add nomodeset. 
(The "any key" is a joke as some read that literally and cannot find that key.) 

After install, you do then use the edit grub instructions to add nomodeset.

You want the BIOS screen.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Just checked and links, now seem to be broken.

this seems to show BIOS boot screen.
[https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#2](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#2)

---

### Post by webdoc on 2018-07-07
Update I got further using the setting NOMODESET as the text was scrolling on the screen I did notice that 3 or 4 items went by as failed, I then had a mouse pointer for so long then the screen died and just sat there with a black background, starting to think it is graphics related is there a way to load a graphics driver to ubuntu so that I can see the install screens?

---

### Post by webdoc on 2018-07-08
Update thanks for the help but have now give up trying to get ubuntu setup as dual boot on my desktop, I like things that just work and it seems ubuntu does not like my nvidia graphics drivers as well as few others that say failed, I have no idea what they are but it's enough for me to give up.

Thanks again

---

### Post by oldfred on 2018-07-08
I had a similar system.
CPU was Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz and video originally in 2006 was 7600GT, but in 2009 that video card blew out its capacitors, it also took motherboard & I replaced power supply not knowing for sure if still good. The CPU and drives were the same but then added a new 9600GT video card.
I dual booted with XP (until 2011) and Ubuntu until I retired system in 2014. Originally I had lots of issues configuring nVidia, but in more recent years using nomodeset & then adding nVidia driver worked well.
I had itch for new system in 2011, but added a small SSD which would not work with XP, so it go retired. And then system was so good it took another 3 years before I finally upgraded.

Not sure what issues are on your system. Some motherboards need additional boot parameters. Many need BIOS settings changed.
I have a long list of potential issues that we have seen, if you want to try again.

---

