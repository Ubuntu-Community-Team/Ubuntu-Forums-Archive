---
title: "ubuntu 14.04 LTS not booting after installation"
date: 2015-12-07
forum: Installation &amp; Upgrades
---

### Post by jay108 on 2015-12-07
Hi,
I am new here, and hope to get some help as I wasted already 3,5 days trying to install ubuntu 14.04 LTS on a Dell Optiplex 745 (Core2 Duo CPU).
Initially I tried to install ubuntu alongside with Win XP, but did not find a way to get both into a boot manager (1. installed XP, 2. installed ubuntu; but no way to start ubuntu... first tried to add ubuntu to the Win boot manager, but ubuntu did not start; then tried to put Grub into the MBR, which worked, but left me with Grub starting only, but still no ubuntu (or Win XP anymore)).
1.5 years ago we did the same with a notebook, where we installed ubuntu 12.04 alongside with Win 7 without any problems, and had immediately a boot menue with the option to choose between ubuntu and Win 7. So thought it would be an easy task...
However, now I realized that I cannot waste more of my precious working time (don't want to get into trouble with my new boss...) and decided to install ubuntu on another hard drive (and swap hard disks everytime I need to boot the other OS... which would suck A LOT... but did not see another choice... just space for one HDD in the PC).

So, I deleted all partitions (again.....) and I installed ubuntu from an USB stick, installation went well (again...), but after restarting there is just a black screen with a flashing dash in the top left corner (did that 3 times now, everytime the same result).
Any idea what went wrong?
Old computer, no EFI; not trying to boot from a wrong device or so; set boot flag with gparted (which I read somewhere else)...

I am quite sure I am not the first person with this problem, but still I did not find anything useful in the forums, thats why I post here.

Would be great if anybody has an idea about this...

Thank!
Jay

---

### Post by v3.xx on 2015-12-07
On older equipment "nomodeset" may be required.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by grahammechanical on 2015-12-07
You do not mention the amount of RAM in that machine or the specification of the video adapter. According to this link the machine could have one of three video options.

1) Intel graphics media accelerator 3000 with up to a maximum 256 MB of memory shared with system RAM
2) ATI Radeon X1300 with 128 MB memory
3) ATI Radeon X1300 Pro with 256 MB memory

[https://www.dell.com/downloads/global/products/optix/en/opti_745techspecs.pdf](https://www.dell.com/downloads/global/products/optix/en/opti_745techspecs.pdf)

Option 3 is the only one anywhere near being capable of running present day Ubuntu and even then it would be borderline. One thing is certain. If the video adapter is either of the 2 ATI adapters then I doubt that they are supported by the ATI proprietary video drivers that come with Ubuntu 14.04.

You could try installing and not ticking the box "Install third party software." Then a proprietary video driver will not be installed during the installation process. Anyway, I would be trying again with Lubuntu.

If you installed Ubuntu but decided not to install a boot loader (Grub), then for a certain you will not be able to load Ubuntu. Windows boot loaders do not recognise another OS other than a Microsoft OS. If during the install process the installer was allowed to install Grub into the MBR of the first hard disk (sda) then you should have got the Grub boot menu with an option to load either Ubuntu or Windows.

But there is another consideration. MBR partitioning. With MBR partitioning we are only allowed 4 primary partitions. And if the manufacturer has used up that allocation with Windows partition and diagnostic partitions then the Ubuntu installer will not allow us to install alongside because there is no place alongside to create the 2 partitions that Ubuntu needs.

Regards

---

### Post by jay108 on 2015-12-07
Thanks for the reply.
Its the the Radeon X1300 Pro with 256 MB Ram. The system has 3 GB ram.
When I boot from the USB drive with the "try ubuntu" option, ubuntu works fine, which made me assuming the graphics driver is not the main problem.
Also, ubuntu does not even start booting after installation, so its probably not the graphics driver.

I can try installing without ticking the third party software box, so far I always checked it.

I was not asked whether Grub or Grub2 should be installed, so I was assuming it would just be installed.
When I still tried to get Win XP and ubunto together onto the system, I added ubuntu manually to the windows boot manager (the way they describe it here for example: [http://www.linuxdevcenter.com/pub/a/linux/archive/dual-boot-laptop.html?page=3](http://www.linuxdevcenter.com/pub/a/linux/archive/dual-boot-laptop.html?page=3)), which did not work.
Next time I tried installing grub after booting from an USB drive and changing to the installed ubuntu. That just in Grub working somehow... but not giving me any options what to boot, but just have Grub (similar to the this thread: [http://askubuntu.com/questions/616811/gnu-grub-terminal-instead-of-ubuntu-login-screen](http://askubuntu.com/questions/616811/gnu-grub-terminal-instead-of-ubuntu-login-screen)), but did not get that fixed.

Last point: I deleted all partitions (several times now), during the last 2 times I installed ubuntu after deleting all existing partitions, hoping that ubuntu would do everything the way it needs it (of course it created partitions then), but still it is not booting...

---

### Post by yancek on 2015-12-07
You might review the site at the link below on installing Ubuntu which has a lot of additional useful information.  Seeing a blinking cursor and nothing else could be a number of things some of which are discussed at the second link below.  Never had this problem myself?

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

[http://askubuntu.com/questions/2622/blank-screen-blinking-cursor-on-boot](http://askubuntu.com/questions/2622/blank-screen-blinking-cursor-on-boot)

---

### Post by jay108 on 2015-12-12
Many thanks for trying to help, but I finally had to give it up, cannot waste more time on it. Unfortunately ubuntu is still so much more inconvenient compared to windows...
I am using VirtualBox instead now, that works fine, just incredibly slow...

Cheers :-)

---

