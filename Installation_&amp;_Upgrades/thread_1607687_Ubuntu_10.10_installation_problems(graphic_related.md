---
title: "Ubuntu 10.10 installation problems(graphic related)"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by whitehorse13 on 2010-10-28
first of all sir this is my first post and i m totally new to linux(equivalent to zero knowledge in linux commands). i want to learn ubuntu but am facing quite a big problem while installing ubuntu on my laptop.
i have downloaded ubuntu 10.10 64bit and have also burned it to good disk at 4x speed.
when i boot it from cd everything goes simple and fine till it comes to a mixed orange colour screen and then nothing goes further, it just halts there with this full blank screen. 
so i have to do a hard shutdown.
then i tried wubi.it went good. after rebooting it asks for installation options. there are five of them. in the normal mode the same thing gets repeated again. but in safe graphics mode ubuntu gets installed but few errors are shown after installation.

[9.595838][drm]noveau 0000:02:00.0:couldn't find matching outscript table
[9.595844][drm]noveau 0000:02:00.0:couldn't find matching outscript table
[9.595863][drm]noveau 0000:02:00.0:couldn't find matching outscript table
[9.595885][drm]noveau 0000:02:00.0:couldn't find matching outscript table
ubuntu 10.10 ubuntu tty1
........
........
0 packages can be updated
0 updates are security updates
........
........
login..........:~$

there is no graphical screen and only this text screen comes again and again.
please help....please...ty

my laptop specs are as follows:
processor: intel mobile core 2 duo t6600@2.20ghz
chipset: nvidia nforce 730i
display: nvidia geforce 8200M G
ram: 4gb
present os: windows 7 ultimate 64bit
dual booted by wubi!!

---

### Post by whitehorse13 on 2010-10-28
please please help needed......!!!!!!!!!!!!

---

### Post by oldfred on 2010-10-28
I have nvidia and my monitor went to standby & had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader menu. (hold shift key from BIOS if not shown)
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by whitehorse13 on 2010-10-28
thank you sir
regarding nvidia drivers installation........
i have downloaded them from the website but dont have a single idea of how to install them and configure them!!
the file type is something ".run"
can anyone please tell me the proper steps for installing them.....(i dont have a single knowledge of linux commands)..

---

### Post by oldfred on 2010-10-29
I do not recommend the nvidia site downloads unless you have to have the bleeding edge drivers and know how to work with that.

The preferred choice is the version that downloads under system, administration, hardware drivers. 

A second choice is to find the site where they have created a ppa so it auto downloads.

---

