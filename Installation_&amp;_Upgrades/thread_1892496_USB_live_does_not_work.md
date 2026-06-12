---
title: "USB live does not work"
date: 2011-12-08
forum: Installation &amp; Upgrades
---

### Post by nookawarra on 2011-12-08
Hi folks
I have run Startup Disk Creator several times on 2 different USB sticks and on 2 different machines. Also used my normal install of 10.04 and a live CD of Kubuntu 11.10. Every time it seemed to work but it will not boot my machine - it skips over Boot from CD and goes straight to GRUB.. I previously had Puppy on one of the sticks and it worked fine so the BIOS does not appear to be a problem.
The only common thing I have done on each attempt is to install Kubuntu 11.10 on the sticks as that is the only iso I have hanging around.
I have checked with Gparted and the partition is marked boot,lba.
I can boot from a CD but I would much prefer to have a live USB stick so that I can help friends and relatives who still use Windows and occasionally catch viruses etc.
Help would be much appreciated.

---

### Post by WasMeHere on 2011-12-08
Hi nookawarra

I think there are a several other alternatives. Unfortunately USB booting is not (yet) standardized or stable, so you may need some different kinds of methods.

Often Startup Disk Creator works well, but there is also the option to use

Unetbootin, found on the internet, but also available from the repositories with
```
sudo apt-get install unetbootin
```

or MultiSystem [[COLOR="RoyalBlue"]_http://liveusb.info/dotclear/_[/COLOR]]("http://liveusb.info/dotclear/")

Other people may fill in with other alternatives, so in the near future you may have several different USB boot systems, and the chance that at least one of them works will increase. 

Have fun finding out :-)
Olle

---

### Post by c.cobb on 2011-12-08
With some USB sticks, I've found that the so-called "geometry" does not allow for the successful installation of Grub2 -- you get an error that "Your embedding area is too small," but it has already updated your MBR. 

I packaged up a version of Syslinux 3.86 that's in [a little 470 KB zip file]("http://ccobb.net/ubuntu/#download") you can try if you want and, so far, it's always worked (famous last words :) Don't click on the 1st zipfile link, but the 2nd one. You'll need to modify the "/boot/syslinux/syslinux.cfg" file to point to the Ubuntu subdir on your USB. Haven't tried Kubuntu yet; let me know if it works :)

Run the following script to install Syslinux bootloader to your USB.
```
 
X:\boot\syslinux\setup.bat                 # use on a PC running Windows
/media/YourUSB/boot/syslinux/setup.sh      # use on a PC running Ubuntu
```This won't boot directly from the ISO file, however, which is a nice point in favor of Grub2, so you need to copy the ISO contents to a subdir on your USB stick. 

BTW, there's also a zip file at the above link that can set up your USB to boot Ubuntu from either a PC or a Macbook. It works on my Macbook, but I'm looking for some feedback on this part.

---

