---
title: "Ubuntu .04 freezes on boot AND when booting to Live CD! help!!!!"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by gruck1683 on 2008-08-16
Hello. 

I am stuck and need some help here!!

Yesterday when I first tried installing Ubuntu Hardy(booting from CD), my system would freeze after selecting "Install Ubuntu." The progress bar would start, then lock up. Unfortunately, this caused me to constantly do a hard restart on my PC :( Recently, I installed a Linksys Wireless card in my PC, so I opened my box and 'ripped' it out. After restarting without my wireless card, I was then able to install Ubuntu successfully, without ANY problem! Hmmm. It would be safe to assume that Ubuntu didn't like the wireless card, so I thought..

Now, I replaced the wireless card and rebooted and when I tried to boot to Ubuntu, it would freeze in the same place as before. At this point, I assumed the wireless card was the culprit, therefore I removed the linksys card altogether, hardwired my PC to my router and tried booting to Ubuntu again. After again trying to boot to Ubuntu, SAME THING!!!! I cannot get into the Ubuntu Generic at all. 

I tried X-server and repairing packages from recovery console, and no luck.

Windows Vista and Ubuntu Dual boot
Intel Quad Core 
Nvidia GeForce 8500
Realtek RTL8168c/8111c Ethernet card

Any suggestions?? I would really like to get this to work!!

---

### Post by Mister.Vash on 2008-08-17
So it was booting to disk and from CD without the card installed?  You put the card back in and neither one would boot, so you pull out the card and it still doesn't boot from CD or Disk?

You might have a loose memory stick in you machine.  Power down and unplug the system, then make sure that all of your memory sticks are firmly in place.  You may want to try reseating them as sometimes a connection looks good but the stick isn't connected all the way.

---

### Post by gruck1683 on 2008-08-17
Correct, it was booting fine without the card installed. I installed Ubuntu, added the card back in and it wouldnt boot. Then I removed the card and I cant get into the OS that is now installed NOR can I boot to the CD. It will crash at the progress bar everytime. Well, actually I just tried again to boot to the generic and it didnt even make it to the progess bar. My PC froze with a black screen. 

I will try reseating my memory sticks and will post the results. Thanks. Hopefully thats corrects the issue.

---

### Post by gruck1683 on 2008-08-17
Ughh. I reseated the sticks and experiencing the same thing! :confused:

Any other ideas? It must be hardware issue!

Heres a little about my system:

HP m8407c
Intel Core 2 Quad Q66004GB Ram
Realteck 8111c Ethernet card
NVIDIA GeForce 8500 GT
Vista 64-Bit

MotherBoard:

Manufacturer: Asus
Motherboard Name: IPIBL-LB

---

### Post by Mister.Vash on 2008-08-17
When you boot from the cd or hdd, does it get to the point where you can choose and run memtest86+?  If so, can you try running that.  If you can't get to that option, can you try downloading from [http://www.memtest86.com/](http://www.memtest86.com/) Then burn a cd from that site and test

---

### Post by gruck1683 on 2008-08-17
yes, I can get to the point where I can run the memtest. I will run that right now. 

So, just a bit ago, I went into the BIOS to disable the Onboard LAN and guess what? I was able to boot to the OS. Now, I have 2 kernels, the .18 and .19. I was able to boot to the .19 no problem. 

Lets see what happens after the memtest. 

Also, I want to point out after I choose the kernel to load (.19 for instance) I will see "starting up" then a screen that quickly appears that says "oem-device out of memory" or something along those lines. It moves too fast for me to catch exactly what it says...

---

### Post by gruck1683 on 2008-08-18
So it seems the issue has been narrowed down the onboard network card. When I disable the lan card via BIOS, I can boot to the OS. However, when the card is enabled, my PC lockes up during boot up. 

So what should I do now so that I can use my installed network card with the OS?? :confused:

All help is appreciated!!

Thanks!

---

### Post by Mister.Vash on 2008-08-18
If it is a hardware error, then you'll probably need to get the motherboard replace.  It could also be and issue with the bios, you could try updating to the latest version, it looks like they have an update from last month.  Looks like you will need to boot into vista to do the bios upgrade.  Just a piece of advice, make sure you backup your important data prior to doing and bios upgrade.  Most of the time the upgrade without and problems, but better to be safe that to lose anything important.  If the bios upgrade doesn't work, then contact HP and see if you can get warranty service.

[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv-61889-1&lc=en&cc=us&dlc=en&product=3686671&os=2093](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv-61889-1&lc=en&cc=us&dlc=en&product=3686671&os=2093)

---

### Post by gruck1683 on 2008-08-18
Well, I flashed my BIOS with the new version yesterday. Thought that may have been the issue, but no luck solving my problem. Sorry for not mentioning that. Hmm so you think its an issue with my motherboard? Thats unfortunate considering my computer is less than 2 months old :(

---

### Post by gruck1683 on 2008-08-18
I guess I'll try a fresh install..

---

### Post by gruck1683 on 2008-08-20
GREAT!! Now I need some serious HELP!!

So I deleted the 2 Linux partitions that were on my box using Partition Manager. There was the 1 partition with the OS on it and another 8GB partition which was the Boot partition!?!?

I deleted both of them, restarted my computer to boot back to windows. Then what happened was a screen came up that said "loading Grub Please wait....Error 5 and then nothing happens. So I did a hard restart AGAIN, booted to the Ubuntu disc and tried doing a fresh install. After choosing Guided-resize and creating  a new partition, it started resizing my patition and HUNG AGAIN. Of course, I had to reboot my PC YET AGAIN.

 Now I don't know what to do. I cant boot to windows because of this Error 5 and when I attempt to re-install Ubuntu now, it wont  allow me the same options for my partitions. I can only do a Guided-use entire disk!!

Someone please help :confused:

---

### Post by trash on 2008-08-21
do a search for 'fixmbr' that will restore your windows boot.

---

### Post by gruck1683 on 2008-08-28
so from the command prompt, I ran the bootrec.exe/fixmbr. Immediately after I hit the 'enter key, it says that its been performed successfully. The PC restarts and nothing changes. The computer hangs at Loading Grub Error 5. 

So obviously the Master Boot record isnt getting fixed using the Vista CD. I also noticed when click "repair computer" after booting to the CD, it will ask to select the OS to repair in the window, however theres nothing there. It gives me the ability to load drivers for the "device" IF the OS isnt present, but I am not sure of the directory where the drivers are...OR what device drivers they are even referring to.

---

### Post by knattlhuber on 2008-08-28
> **gruck1683 said:**
> Hello. 

I am stuck and need some help here!!

Yesterday when I first tried installing Ubuntu Hardy(booting from CD), my system would freeze after selecting "Install Ubuntu." The progress bar would start, then lock up. Unfortunately, this caused me to constantly do a hard restart on my PC :( Recently, I installed a Linksys Wireless card in my PC, so I opened my box and 'ripped' it out. After restarting without my wireless card, I was then able to install Ubuntu successfully, without ANY problem! Hmmm. It would be safe to assume that Ubuntu didn't like the wireless card, so I thought..

Now, I replaced the wireless card and rebooted and when I tried to boot to Ubuntu, it would freeze in the same place as before. At this point, I assumed the wireless card was the culprit, therefore I removed the linksys card altogether, hardwired my PC to my router and tried booting to Ubuntu again. After again trying to boot to Ubuntu, SAME THING!!!! I cannot get into the Ubuntu Generic at all. 

I tried X-server and repairing packages from recovery console, and no luck.

Windows Vista and Ubuntu Dual boot
Intel Quad Core 
Nvidia GeForce 8500
Realtek RTL8168c/8111c Ethernet card

Any suggestions?? I would really like to get this to work!!

Don't do a fresh install!! I'm having the same problem with a very similar setup. It's a known bug that'll (hopefully) be fixed with the next kernel update.

Here are the links to the bug reports:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227003](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227003)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/172563](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/172563)

After adding 'all_generic_ide' to /etc/grub/menu.lst stanza as suggested in the first link, the freezes appeared to occur less frequently. You could even add more restrictive boot options to GRUB as suggested to me by another forum member when I first posted my problem here:
> vga=normal ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off single

---

