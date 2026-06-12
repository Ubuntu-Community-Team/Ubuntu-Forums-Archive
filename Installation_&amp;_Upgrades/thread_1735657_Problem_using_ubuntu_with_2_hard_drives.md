---
title: "Problem using ubuntu with 2 hard drives"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by supermallows on 2011-04-21
Greetings!


Problem is..

When I installed Ubuntu using the usb drive, I disabled the the other hard drive
So I have 2 hard drives on the computer

disk 1 - 250gb
disk 0 - 320gb

I disabled the 320gb that has windows 7 in the bios
I installed Ubuntu on 250gb

After it's done, it's not booting.
I tried checking in the bios and enable the 320gb
then the GRUB menu appeared.
I removed the sata cable from the 250gb and tried to boot only to 320gb
it is giving me an error about the GRUB
I then put back the 250gb then go to bios and enable both hdd
What happened was the GRUB menu appeared and the Win7 and Ubuntu is working

So what does  this mean?
I have to use 2 hard drive all the time?

I'll screenshot my disk management
[img]http://img191.imageshack.us/img191/4301/diskmanagement.jpg[/img]

I'm sorry it is my first time installing ubuntu.. 


thanks for your help, I appreciate it

---

### Post by Dutch70 on 2011-04-21
Hi and welcome to UF

Lets have a look at your boot info script with both hdd's connected.

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]

Then open a terminal (Cntrl+Alt+T) and run the following command...
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just click the # symbol in the toolbar & paste it between [CODE] [ /CODE] tags. Do not skip this step as many do.

---

