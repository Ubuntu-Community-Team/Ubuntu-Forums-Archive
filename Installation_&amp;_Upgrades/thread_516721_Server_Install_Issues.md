---
title: "Server Install Issues"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by ctlw83 on 2007-08-03
Processor: Athlon 64 X2 3800+ 65w
Motherboard:  MSI MBOX K9N6SGM-V 
Video Card: Onboard Nvidia GeForce 6100 64MB
Sound Card:Onboard Realtek Sound
Ram: 2GB Dual Channel GEIL DDR2 800 mhz
Hard Drive: 2 SATA Western Digital 80 GB with possibility 0f using Hardware RAID 1
Network Card: on board realtek
DVD ROM: Sony

Hey All,

Just built my machine today and everything seemed to run smoothly until I tried to run the OS after install.  The hard drive wouldn't boot.  When I went back into the install CD and selected "boot from first hard disk" it simply says BOOT Failed, with no reasons. Note: this was with just the main SATA drive, not in RAID setup.

Then I tried configuring my on-board RAID as a RAID 1 setup and tried the install again.  Both SATA drives showed up in the setup and I selected the one on SATA 1.  Finished the LAMP install again and this time a single line that said GRUB came up after install but, nothing after that.  Note: Tried the "boot from 1st disk" on CD again and it gave me an error of some sort

I have tried both the LVM and non LVM installs and neither seems to work.  However, the hard drive does get partitioned and does have the data on it, so I know I don't have a DOA drive.  Any ideas??

God Bless,
Chris

---

### Post by prodezigner on 2007-08-03
Hopefully I can put in my two cents...

Try using a GUI based flavor of Ubuntu. See if you can install it successfully that way. I had a guide on setting up an Ubuntu Server with XFCE as the window manager (lightweight and VERY useful for configuration, setup something simple... with your system it should smoke).

I'll dig around and find that tutorial for ya.

Just post back results on the standard install of Ubuntu though. We'll use that as a building block.

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06]("http://www.howtoforge.com/lamp_installation_ubuntu6.06") it's for 6.06, but you can easily omit any packages you don't want. When it gets to the point of the: SUDO APT-GET INSTALL UBUNTU-DESKTOP part simply use the command: SUDO APT-GET INSTALL XUBUNTU-DESKTOP for a more lightweight server interface (if you prefer an interface). Your server should push the standard GNOME desktop just fine though however.

---

### Post by ctlw83 on 2007-08-03
Actually, the install isn't the problem.  I can get through the install fine.  It just won't boot...  I will DL a gui once it IS booting though.  I am nto running a command line server....

---

