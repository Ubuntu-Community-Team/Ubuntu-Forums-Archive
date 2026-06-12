---
title: "'error loading operating system' and many others"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by jon.reeve on 2007-05-24
I've been trying for the last few days to install ubuntu on my little Japanese Fujitsu Lifebook FMV-650MC laptop. There's no CD-ROM drive or floppy drive on it, and as far as I can tell the BIOS doesn't support booting from a USB drive (which is a shame, because I already have DSL installed on a 128M pendrive). So I tried doing a NetInstall, which worked pretty well until I started getting a whole lot of errors. Fatal errors, 'install failed', I wish I wrote them all down. I restarted, hoping I could go back into a partition editor in Windows and sort the whole thing out, but that gave me an "Error loading operating system" and absolutely no way to get around it. The only thing I could think to do (since there's no way to boot it from CD or floppy) was to take the HD out and put it in a box that will allow me to access it on my desktop via USB. Now I'm running the small (10G) laptop HD as an external HD on my desktop. So then I figured the best way to get ubuntu onto this laptop would be to try to install it onto this laptop hard drive using the desktop and a Ubuntu Live CD. I've managed to get through the installation successfully when I install to a preconfigured ex2 partition. It doesn't seem to want to boot to this system, however--keeps giving me the "error loading operating system".  I check out the config on grub and it all looks good. I figure maybe the BIOS was trying to load the old Win2K partition? So I decided to get rid of Win2K altogether. I backed up all my data and tried the install again, though this time choosing the guided install which formats the HD. Then, however, I started getting more errors, like "the ext3 file system creation in partition #1 of SCSI3(0,0,0) (sdb) failed." and the installation never got past partitioning. This can't be a problem with grub, I don't think, because it doesn't even seem to be getting that far. To make matters worse, this installation has somehow messed up my desktop's boot, so now my desktop loads a "Grub loading Stage 1.5 / error 21". Which leads me to believe that the install thought that my desktop's hard drive needed a boot loader, rather than my external drive which contains ubuntu. 

Here's the lowdown: 
newish DELL desktop with 80G internal HD that has one partition which contains WinXP, which doesn't load, and a USB external 10G HD jacked from a laptop which has: 
1st Partition: old Win2K partition that won't seem to erase or format or boot or anything
3rd Partition: ubuntu with grub and all the fixins which won't boot
5rd partition: linux swap

Ubuntu install can't format this USB drive. I figure if I could figure out a way to wipe it clean and start from scratch I'd have some luck. Does anyone know of a utility I can run or install from within the ubuntu live cd (currently my only working operating system) that could help me to format this external drive? Or some other way around this problem? 

I've been reading all the docs I can get my hands on but this has turned into a three-day affair, and it just keeps getting worse and worse! I could use all the help I could get on this one. Sorry it's so long-winded.

---

### Post by benanzo on 2007-05-24
I think one issue you might be having when you try to format that USB drive is that gnome-volume-manager keeps mounting it while gparted is trying to format it, causing it to quit and give you an error.  This is a common problem I have come across when formatting disks in Ubuntu.  You just need to disable automounting.

Go to **System** -> **Preferences** -> **Removable Drives and Media**
Then on the **Storage** tab, uncheck the first box **Mount removable drives when hot-plugged**

Then try to format it again.  Hopefully it will succeed.

---

### Post by jon.reeve on 2007-05-24
Thanks. I think it worked out. Now I have another problem on my hands with an X server not set up correctly.

---

### Post by benanzo on 2007-05-24
What problem are you having with the X server?

---

