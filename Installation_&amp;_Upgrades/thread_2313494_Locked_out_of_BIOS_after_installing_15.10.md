---
title: "Locked out of BIOS after installing 15.10"
date: 2016-02-13
forum: Installation &amp; Upgrades
---

### Post by Todd76 on 2016-02-13
I am interested in evolving from a Windows user to an Ubuntu user and have built a clean system from the ground up (all new HW, single boot Ubuntu) as a mechanism to learn the new operating system. I just completed installation of Ubuntu 15.10 (using UEFI) and have been exploring the operating system when I found I no longer have access to my BIOS menu during boot. Although the boot screen during POST indicates F2 or DEL to enter the BIOS, the system now seems to ignore the keys and always sends me to the Ubuntu logon screen.

Some additional info:
[LIST]
[*]I installed 15.10 on an unformatted drive (and have no intention of dual-booting at this point). 
[*]I have a new Q87M-E ASUS motherboard 
[*]I am booting from an SSD 
[*]I setup multiple partitions and mount points to support various directories such as /, /boot, /tmp, /var, /home, ... and a few others 
[*]I purposely made sure that secure boot was disabled to remove that level of complexity during my first install. I also disabled 'fast boot' due to some online suggestions I saw. 
[*]I can no longer access the BIOS through F2/DEL, although I certainly was able to when I first booted the system during installation. 
[*]I cannot boot from USB or optical drive ... not even the bootable thumbdrive I used to install the system. 
[/LIST]
 
Any help with resolving this is greatly appreciated!

Todd

---

### Post by grahammechanical on 2016-02-13
I do not think that the developers of Ubuntu have any intention of locking users out of the BIOS/UEFI boot system settings utility. I have put in many installs of Ubuntu over the years & I have never been locked out of my BIOS settings.

It might seem heavy handed but one way to get around this is to disconnect the hard drive. That may force the BIOS/UEFI to offer to open UEFI settings. As this is a self-built machine you can do this.

I also built my own machine. And to test that the motherboard was working I switched on without there being a hard disk connected. I am not suggesting this as a permanent workaround or even as a temporary fix. Just as a way of stopping the motherboard from loading an OS.

Regards.

Regards.

---

### Post by Todd76 on 2016-02-13
Thanks for the suggestion ... after disconnecting the boot drive I can now get into the BIOS using F2/DEL during boot-up.

I updated the firmware and started over with a less tweaked configuration, but continue to be 'blocked' from entering the BIOS when the drive is attached.

---

### Post by oldfred on 2016-02-13
I have an Asus Z97-AR.
And it has settings for UEFI fast boot which are totally different than Windows settings of fast startup or always on hibernation.
Fast Boot in UEFI is to make system boot quicker. Windows wants system to boot quickly as Windows takes forever with a normal boot.  It skips all system checks and assumes everything is the same, no hardware changes. But then that is so fast that you do not have time to press a key to get into UEFI. And most reboots are with no hardware changes so it may be good. And if changing hardware you should totally shut system down so a total cold boot should be a normal boot.

On my Asus I changed cold boot to normal (not fast) and while configuring system also had warm boot as normal, so I could easily get into UEFI to change settings. Once fully configured, I changed warm boot to 3 sec delay, so if I am quick I maybe can get into UEFI without cold reboot. Grub also now as an entry to get to UEFI, usually last menu entry. It may say System Setup and uses fwsetup in boot stanza.

---

