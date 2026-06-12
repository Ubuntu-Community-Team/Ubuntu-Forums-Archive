---
title: "Ubuntu fails to boot after upgrade to 11.04"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by plugnplay on 2012-01-12
**Ubuntu fails to boot after upgrade to 11.04** 			
 			 			 		   		 		 		I just  upgraded to ubuntu 11.04 but now all the kernels fail to boot. The  resolution of grub changed and the older kernels are put into a  'previous kernels' folder. The most recent kernel halts at the message  '* Stopping userspace bootsplash [ OK ]' and the previous kernels fail  with the message 'Unlink after no-irq. Controller is probably using the  wrong IRQ', 
[IMG]http://i54.tinypic.com/15gcxhw.jpg[/IMG]
or show the background of the login screen with just a white box.
[IMG]http://i52.tinypic.com/2qiv1og.jpg[/IMG]
I think the cause is that I have an ATI graphics card (HD Radeon 3650),  because on my 2 other computers ubuntu upgrades fine and they have  NVIDEA graphics cards.

As a last resort I tried installing different distro's like Linux Mint but it also gived me the 'unlink after no-irq' message.

Do you guys know what the problem might be and how I can solve it? Thanks.

---

### Post by mastablasta on 2012-01-12
> **plugnplay said:**
> 
I think the cause is that I have an ATI graphics card (HD Radeon 3650), because on my 2 other computers ubuntu upgrades fine and they have NVIDEA graphics cards.

 
i think the problem is because:
 
A) you didn't uninstall the ATI graphics drivers known as fglrx (and disable any PPA) before upgrade
B) you did uninstall them, performed the upgrade but need to boot with certain boot parameter to get in GUI in order to install new drivers.
C) your upgrade failed (file error during download etc...)
 
if A is the case uninstall the fglrx via command line and then reboot using opensource drivers and once you are in the desktop you can install new proprietary drivers.
 
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by plugnplay on 2012-01-14
but i can't use command line yet .i have non access on my pc right now .is there a way to make system restore?

---

### Post by dino99 on 2012-01-14
boot in recovery mode (hold "shift" key down at bios end process to get the grub menu on single OS system), then you can use the terminal

---

### Post by plugnplay on 2012-01-23
that made a deference to me but how can i use the terminal to solve my problem ?

---

### Post by darkod on 2012-01-23
> **plugnplay said:**
> that made a deference to me but how can i use the terminal to solve my problem ?

Try the link posted in post #2. The commands are there.

---

