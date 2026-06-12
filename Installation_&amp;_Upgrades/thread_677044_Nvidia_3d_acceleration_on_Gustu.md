---
title: "Nvidia 3d acceleration on Gustu"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by kacike76 on 2008-01-24
Please Help.....
after countless hours behind my newly installed Gusty machine i seem to can't figure out what i need to do to enable the Nvidia-glx driver for 3d and 2d acceleration.  I am using a GeForce 3 Ti 200 running on a Dell Dimension 8200 desktop.  I only have 256MBytes or RDRAM installed :( and a 1.7GHz processor

[B]I've followed several threads to do this, and this summarizes my attempts to get this working.  

1) made sure all repositories are enabled
2) typed "sudo apt-get install nvidia-glx" as i think this is the proper driver for my card 
3) typed "sudo nvidia-glx-config enable" and get no error messages
4) reboot my machine [/B]

Note: i've also used Envy to install this driver

After rebooting with this driver enabled i don't get login screen and my monitor just remains blank.  I am using a Dell E151Fpb with a VGA connection.  I am forced to then to power down and run "dpkg-reconfigure xserver-xorg" from recovery mode and reconfigure the graphics driver to the open source NV.  :(

I would like to be able to play around with advanced desktop effects (i am a newbie!), but can't seem to get this driver enabled.  I may also add (in case it matters) that i have a dual boot machine with XP on a separate drive.  I was a little curious about seeing two instances of Ubuntu 7.10 on the GRUB screen.  One appears as the first item on the list and the other choice is under other operating systems.  Dunno if this matters any

Thanks in advance!

---

### Post by jeffus_il on 2008-01-24
You need to install the restricted-drivers package using Add/Remove Software on the Menu or Synaptic Package Manager.

---

### Post by kacike76 on 2008-01-24
I believe i've already installed this package, but could you please tell me how to check.  I've looked at my xorg file to see that the driver updates from nv to nvidia.  Am i missing something? would i still be able to get the restricted drivers without this package you are referring to? Again, newbie to Ubuntu

Thank you

---

### Post by jeffus_il on 2008-01-25
From the System Menu run the "Restricted Driver Manager" and enable the ATI graphics driver.
 Afterwards the driver in the xorg.conf file should be "nvidia", not "nv"

---

