---
title: "External HDD Ubuntu 12.04 won't boot on desktop but does on laptop"
date: 2014-01-26
forum: Installation &amp; Upgrades
---

### Post by harlan2 on 2014-01-26
I have Ubuntu 12.04 installed on a External drive. It boots up on my laptop without problems but when I try to boot it on my desktop, it gets stuck on a black screen with a blinking underscore. (I boot it through bios and selecting USB. Grub does not show up)
I've checked around and it seems that this could be a problem from different boot modes between UEFI/EFI and legacy. I found out that Windows should be on legacy mode (I found online to 'use bcdedit /enum' in cmd and since my Windows Boot Loader path ends in .exe, it should be legacy).
Ubuntu 12.04 should also be on legacy mode since the 'seperate /boot partition' option is grayed out in boot-repair.
I am all out of ideas on what to do. Here is my boot-repair link. The one corresponding to the external should be sdb
[http://paste.ubuntu.com/6823399/](http://paste.ubuntu.com/6823399/)

---

### Post by fantab on 2014-01-27
Ubuntu was probably installed on the External HDD from the Laptop you are using. Correct?
When Ubuntu installs it configures itself according to the hardware present. Most of the configuration Ubuntu does can be used on other computers.
However if and when there is difference in the Hardware, especially Graphic Cards then it will not load correctly.

You can try '**[nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997")**' kernel parameter when booting on desktop. Nomodeset prevents Ubuntu from loading any specific Graphic Driver and works only with the generic open-source graphics driver.
 If 'nomodeset' helps then, you will have use it everytime you want to boot Ubuntu on desktop. Normally you will have to install the specific Graphics driver after booting with 'nomodeset' parameter.

Find out what Graphics Card you have on desktop and install the relevant driver.
Then boot on laptop and see how it goes.... I am not sure how this will fare because you would have installed two graphics driver. Theoretically, it should not make a difference though.

---

### Post by oldfred on 2014-01-27
Neither sda nor sdb show grub in MBR for BIOS boot or efi partition for UEFI boot, so how are you booting at all?
Also no Windows is shown?

---

### Post by harlan2 on 2014-01-27
> **fantab said:**
> Ubuntu was probably installed on the External HDD from the Laptop you are using. Correct?
When Ubuntu installs it configures itself according to the hardware present. Most of the configuration Ubuntu does can be used on other computers.
However if and when there is difference in the Hardware, especially Graphic Cards then it will not load correctly.

You can try '**[nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997")**' kernel parameter when booting on desktop. Nomodeset prevents Ubuntu from loading any specific Graphic Driver and works only with the generic open-source graphics driver.
 If 'nomodeset' helps then, you will have use it everytime you want to boot Ubuntu on desktop. Normally you will have to install the specific Graphics driver after booting with 'nomodeset' parameter.

Find out what Graphics Card you have on desktop and install the relevant driver.
Then boot on laptop and see how it goes.... I am not sure how this will fare because you would have installed two graphics driver. Theoretically, it should not make a difference though.
i have a nvida gtx660 but how would i go about doing the nomodeset option? when i boot the external from the desktop, all i get is a black screen with a blinking underscore. i have tried pressing buttons but nothing shows up on the screen

> **oldfred said:**
> Neither sda nor sdb show grub in MBR for BIOS boot or efi partition for UEFI boot, so how are you booting at all?
Also no Windows is shown?
nope. no windows. i originally had ubuntu on the laptop but every so often when i boot, it gets bad sectors and i have to repair so i just put ubuntu on a external and booted from there. when i boot the external, grub does show up and i am able to select the other options like memory test, etc.

---

### Post by oldfred on 2014-01-27
At grub menu press e for edit, scroll to linux line and replace quiet splash with nomodeset.

 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by harlan2 on 2014-01-27
> **oldfred said:**
> At grub menu press e for edit, scroll to linux line and replace quiet splash with nomodeset.

 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

When i do nomodeset, it gets stuck on a black screen on the laptop. I cannot get into grub when i try to boot from the desktop, it is just a black screen with a blinking underscore. i could try to set nomodeset permanently but if it doesnt boot on either then that would be bad

---

### Post by oldfred on 2014-01-27
Are you sure you are not booting from internal drive on laptop to load system on external. As your BootInfo showed no boot loaders. Usually then you would get  a BIOS error, but may just get black screen.

Post bootinfo report from laptop.

---

### Post by fantab on 2014-01-27
Use 'nomodeset' on desktop, which you tell us is not booting EXT HDD. Since your Ext HDD is booting on laptop no need to use nomodeset there.
When creating and posting Bootinfo Summary make sure your Ext HDD is plugged in. Probably you installed Grub on ext HDD.

---

### Post by harlan2 on 2014-01-27
> **oldfred said:**
> Are you sure you are not booting from internal drive on laptop to load system on external. As your BootInfo showed no boot loaders. Usually then you would get  a BIOS error, but may just get black screen.

Post bootinfo report from laptop.

> **fantab said:**
> Use 'nomodeset' on desktop, which you tell us is not booting EXT HDD. Since your Ext HDD is booting on laptop no need to use nomodeset there.
When creating and posting Bootinfo Summary make sure your Ext HDD is plugged in. Probably you installed Grub on ext HDD.

the bootloader info is here: [http://paste.ubuntu.com/6830194/](http://paste.ubuntu.com/6830194/)
it has both the internal, external, and c is how i'm running boot-repair. i couldn't install it on the internal due to some https error when i run sudo apt-get update, etc.
i dont know why it didnt display the one on sda before. maybe because before, it needed to fix the sectors? cause when i tried to boot into the internal, it said / was not found and needed to repair itself.

if this seems too troublesome, is there a way to fresh install a stand-alone copy of linux that works on any computer?

---

### Post by fantab on 2014-01-28
Your bootinfo summary looks okay to me.
Is USB booting enabled in Laptop BIOS? Check the HDD boot order, USB boot must be enabled and made the first boot priority.

> if this seems too troublesome, is there a way to fresh install a stand-alone copy of linux that works on any computer? 
Only Live Ubuntu can work on 'any' computer. You can BURN the ubuntu.iso to a Pendrive or ExtHDD with Persistence (without persistence nothing is saved permanently on the USB or ExtHDD ). Persistence IIRC has 4Gb limit.
[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
Persistence with more than 4Gb storage:
[http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb](http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb)

---

### Post by harlan2 on 2014-01-28
is it already too late to make this into a live ubuntu?
Live ubuntu wouldn't matter if the machine has an OS and wouldn't matter what hardware is available correct?
how does the casper-rw thing work? is it like partitioning except i can use the casper-rw partition as if it is apart of the / (so you can read,write,execute, etc)? and were would i download/install updates?

---

### Post by oldfred on 2014-01-28
The only boot loader I see is syslinux on live flash drive. Nothing on sda 500GB nor sdc 320GB drives. BIOS has to boot from MBR.
>  => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.



You do have grub install to a lot of PBRs or partition boot sectors, but you cannot boot from those without another boot loader. And installing to PBR is not recommended as it can have issues. Often needs reinstall on updates.

---

### Post by fantab on 2014-01-28
Thanks oldfred, I missed that.

@harlan2: use boot repair and install Grub to /dev/sdc or your ExtHDD and NOT on its partition like /dev/sdc1 or /dev/sdc2 etc.
Your desktop probably has a bootloader to boot Ubuntu on your extHDD but not the laptop, that may be the probable issue.

---

### Post by harlan2 on 2014-01-28
thank you guys. it works now. Is it still worth it to get a live ubuntu over whatever i have currently?

---

### Post by fantab on 2014-01-29
> **harlan2 said:**
> thank you guys. it works now. Is it still worth it to get a live ubuntu over whatever i have currently?

If you want your Ubuntu to run on "ANY COMPUTER" then, YES Live Ubuntu is the solution. Live Ubuntu has support for plenty more hardware than an "installed" ubuntu on USB drive.

---

### Post by oldfred on 2014-01-29
It is another whole discussion but I use grub to loopmount boot an ISO file directly. So some of my smaller flash drives have several repair ISO. But my larger full install flash drive also has multiple ISO, so I can also boot a variety of install or repair ISO.

       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

