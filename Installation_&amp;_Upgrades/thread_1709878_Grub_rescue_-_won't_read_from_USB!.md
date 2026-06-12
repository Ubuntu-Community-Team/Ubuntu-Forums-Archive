---
title: "Grub rescue - won't read from USB!"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by altosk on 2011-03-19
Hi guys, really hoping someone can help me with this. I've tried reading other threads about grub rescue but it seems like it only works if the USB stick can actually be read. Sorry if I sound dumb, I'm really new to all of this.

I installed Jolicloud (it's based off Ubuntu, apparently) to dual boot with Windows 7 which I got with my netbook. When I tried to get rid of Jolicloud, I think I accidentally deleted a partition-- now whenever I boot up my netbook, I get the black "grub rescue" screen of death. 

I tried getting the netbook to boot from my USB but it won't do it. The USB light flashes but nothing happens. I know there's things in there because I can boot from the USB using my desktop. Jolicloud was initially installed from the USB so I don't know why it won't read it anymore.

Please help, I bought this netbook just a few days ago and am pretty shattered that I've messed it up so quickly.

---

### Post by Rubi1200 on 2011-03-19
Hi and welcome to the forums :-)

If Jolicloud was installed on the drive along with Windows and you got rid of it (intentionally or not), you will need to restore the Windows bootloader.

Trying from the grub rescue prompt won't help you since what you are seeing are vestiges of GRUB in the MBR.

Restore the Windows bootloader with the relevant Windows Recovery CD.
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you do not have a Windows CD, or are unable to get hold of one, you  can use an Ubuntu CD/USB to install a Windows-like bootloader.

From a terminal on the LiveCD/USB (Applications > Accessories > Terminal), run the following commands:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```This assumes that sda is the Windows drive. If not, change this to reflect the actual drive e.g. sdb, sdc, etc. 

Ignore any warnings and continue with the installation to the MBR. The  main point is to get lilo installed and allow the user to boot Windows.

If you want to make sure first before trying any of this, post the results of the  [boot info script]("http://bootinfoscript.sourceforge.net/")

---

