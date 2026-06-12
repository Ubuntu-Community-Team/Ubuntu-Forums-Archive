---
title: "Can't install Ubuntu 12.04 in MSI X320"
date: 2012-06-25
forum: Installation &amp; Upgrades
---

### Post by serwwweb on 2012-06-25
Hi friends, i'm having a problem that i can't resolve trying to install **Ubuntu 12.04** on a **MSI X320**.
Booting to a live session or trying to install directly gives me the following error:
**mmc0: controller never released inhibit bit (s)** and then only a black screen.
I tried the following distros: **fedora, mint y opensuse** (the latests versions), with the same result as ubuntu. The only ones that works were **Puppy y PCLinuxOS** also the latests versions, and **Ubuntu 10.04**, that already worked, but after upgrading to 12.04 gave the same problem.

Apparently the problems are associated to the hardware, and/or the kernel.
**SD/SDHC/MMC card reader** seems to be a problem, also the sata controller **sis 3531**, or **chipset Intel® US15W (Poulsbo)** with **video Intel GMA 500**.
I come to you as a last resort before getting rid of the machine, which is very comfortable to work.
Thak you very much, and sorry, my english is horrible, i hope you understand.

---

### Post by darincb77 on 2012-06-25
Hi,

I have also suffered with this machine for a while. When attempting to install a distro, I normally would avoid the many errors due to the SD card reader by blacklisting at boot, adding to the boot parameters:

```
sdhci.blacklist=yes sdhci_pci.blacklist=yes sdhci-pci.blacklist=yes mmc0.blacklist=yes mmc_core.blacklist=yes mmc-core.blacklist=yes
```

Apologies - I do not know if the correct syntax is '-' or '_' so I use both above. Similar, when it is installed, I add to the /etc/modprobe.d/blacklist.conf:

```

blacklist sdhci
blacklist mmc0
blacklist sdhci_pci
blacklist mmc_core
blacklist sdhci-pci
blacklist mmc-core

```

HOWEVER, I have never gotten 12.04 to work. I get a black screen and can't get a tty or anything after it. I've never diagnose the problem. I've never gotten a distro based after 11.04 to work. I typically use Zorin OS and the EMGD driver ( [https://wiki.ubuntu.com/PoulsboObsoleteDrivers](https://wiki.ubuntu.com/PoulsboObsoleteDrivers) ).

Cheers,
Darin

---

### Post by serwwweb on 2012-06-25
> **darincb77 said:**
> Hi,

I have also suffered with this machine for a while. When attempting to install a distro, I normally would avoid the many errors due to the SD card reader by blacklisting at boot, adding to the boot parameters:

```
sdhci.blacklist=yes sdhci_pci.blacklist=yes sdhci-pci.blacklist=yes mmc0.blacklist=yes mmc_core.blacklist=yes mmc-core.blacklist=yes
```

Apologies - I do not know if the correct syntax is '-' or '_' so I use both above. Similar, when it is installed, I add to the /etc/modprobe.d/blacklist.conf:

```

blacklist sdhci
blacklist mmc0
blacklist sdhci_pci
blacklist mmc_core
blacklist sdhci-pci
blacklist mmc-core

```

HOWEVER, I have never gotten 12.04 to work. I get a black screen and can't get a tty or anything after it. I've never diagnose the problem. I've never gotten a distro based after 11.04 to work. I typically use Zorin OS and the EMGD driver ( [https://wiki.ubuntu.com/PoulsboObsoleteDrivers](https://wiki.ubuntu.com/PoulsboObsoleteDrivers) ).

Cheers,
Darin

I've made the changes that you suggest to booting from live with no luck. The same black screen comes in the end. I thought that the video driver is the main problem, because while booting it says that the sdhci is blacklisted. So i'm running out of options i think. Probably i should stick with 10.04 or try the 11.04 instead.

---

### Post by darincb77 on 2012-06-25
Yes, I can never get around the black screen problem. 

It is well known that there is a black screen problem, especially with gma500 machines, but I can never get the standard solutions to work. 

I have found a site: [http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/](http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/) with some ideas and I will try some of their suggestions.

---

### Post by darincb77 on 2012-06-25
I can use the method below to boot the live usb. 

Modify the boot options:
 
Remove:
```

quiet splash

```

Add:
```

sdhci.blacklist=yes sdhci_pci.blacklist=yes sdhci-pci.blacklist=yes mmc0.blacklist=yes mmc_core.blacklist=yes mmc-core.blacklist=yes console=tty1 acpi_backlight=vendor noplymouth psb_gfx.blacklist=yes

```

Takes a few minutes to get to the live screen. Screen will glitch and go black with backlight for a few moments but then goes to live screen with bad resolution.

Note that this disables the new fancy gma500 pdb_gfx driver. I have no idea which of those above are necessary and which aren't - when your screen doesn't turn on it's hard to diagnose a problem. 

Perhaps after install psb_gfx can be replaced with emgd. I will try an install and see what happens.

---

### Post by serwwweb on 2012-06-25
Excellent news!!!
I will try what you said later when i get home and i will post the results. :D

---

### Post by serwwweb on 2012-06-25
Hi, i tried what you post, and i can say that boots flawlessly.
Tried different variations and i realise that just with the addition of
```
psb_gfx.blacklist=yes
```
boots into live and let me use everything, including network right out of the box. The only thing that it seems to not work correctly is wireless lan. It detects wireless networks but won't let me connect to none of them.
I will try to install and see what happens.

---

### Post by darincb77 on 2012-06-25
I think I might know how to fix the wireless, but I am focusing on the screen resolution for the moment. 

Here is my roundabout means of installation. psb_gfx still needs blacklisting, hopefully we can find a workaround. 

here are the full details of installation:

I can use the method below to boot the live usb.

Modify the boot options:

Remove:
```

quiet splash

```

Add:
```

sdhci.blacklist=yes sdhci_pci.blacklist=yes sdhci-pci.blacklist=yes mmc0.blacklist=yes mmc_core.blacklist=yes mmc-core.blacklist=yes console=tty1 acpi_backlight=vendor noplymouth psb_gfx.blacklist=yes

```

Takes a few minutes to get to the live screen. Screen will glitch and go black with backlight for a few moments but then goes to live screen with bad resolution.

Note that this disables the new fancy gma500 pdb_gfx driver. I have no idea which of those above are necessary and which aren't - when your screen doesn't turn on it's hard to diagnose a problem.




For the install - seems a little slow and clunky but it will work. I turned off the wifi hardware switch and connected to LAN to download updates while installing. I installed on the whole disk.

DO NOT RESTART AFTER INSTALL - do the following first. 

Then i open the home folder from the left hand unity menu. Under "Devices" in the top left, click on your hard drive to mount it. 

Open a terminal and do:
```

cd /media/NAME_OF_YOUR_HARDDRIVE

```

Then I do:
```

sudo gedit /etc/default/grub

```

Find the line that looks like "GRUB_CMDLINE_LINUX_DEFAULT="[some options here]" "

Remove the following:
```

quiet splash

```


And add the following:
```

sdhci.blacklist=yes sdhci_pci.blacklist=yes sdhci-pci.blacklist=yes mmc0.blacklist=yes mmc_core.blacklist=yes mmc-core.blacklist=yes console=tty1 acpi_backlight=vendor noplymouth psb_gfx.blacklist=yes

```

Shut down and restart.

For the first boot you will need to hit 'tab' at the purple screen and edit the boot options just as you did above (remove quite splash and add all the other things), then when it boots you need to do: 
```

sudo update-grub

```

Run update manager then restart to make sure everything is OK until this point. This should include an update of the linux kernel. While restarting you will probably need to change the boot parameters by hand again, I'm not sure why. 

 Now we will fix that. Do the following:

```

sudo gedit /etc/modprobe.d/blacklist.conf

```

And add the following:

```

blacklist sdhci
blacklist sdhci-pci
blacklist sdhci_pci
blacklist mmc0
blacklist mmc_core
blacklist mmc_core
blacklist psb_gfx

```

And to make sure these blacklists work in the future, do:

```

sudo update-initramfs -u

```


Then once again do this (I'm not sure why it didn't stick the first time):


Then I do:
```

sudo gedit /etc/default/grub

```

Find the line that looks like "GRUB_CMDLINE_LINUX_DEFAULT="[some options here]" "

Remove the following:
```

quiet splash

```


And add the following:
```

sdhci.blacklist=yes sdhci_pci.blacklist=yes sdhci-pci.blacklist=yes mmc0.blacklist=yes mmc_core.blacklist=yes mmc-core.blacklist=yes console=tty1 acpi_backlight=vendor noplymouth

```

And do:
```

sudo update-grub

```


Now you should finally be able to do a clean restart. 

Note that we don't yet have the correct resolution. I am pretty sure the bug affecting us is: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/944929](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/944929)

You can try to see this with "sudo modprobe psb_gfx" - that will cause the screen to go black.

---

### Post by serwwweb on 2012-06-26
Thank you, i did all that you said and works perfectly! including wireless lan :p
Tomorrow i will begin to try to get acceleration and/or the proper resolution from one of the sites that you told:

[http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/]("http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/")

and from here:
[http://ubuntuforums.org/showthread.php?t=1229345&highlight=gma500&page=541]("http://ubuntuforums.org/showthread.php?t=1229345&highlight=gma500&page=541")

and here:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#A12.04]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#A12.04")

and here:
[http://ubuntuforums.org/showthread.php?t=1984236&page=5]("http://ubuntuforums.org/showthread.php?t=1984236&page=5")

Thank you so much
Regards

PD: Tomorrow i will post the results of my tests.

---

### Post by serwwweb on 2012-06-26
Well, i tried a few workarounds with no success. The video resolution is still the same.

Tried the **915 Resolution** thing and even to installing the **kernel 3.4.4**, that leaves me with a black screen no matter what i did, and tried all the steps that worked with the default kernel of 12.04.
Now i am back with the default kernel and uninstalled the 3.4.4.
I will keep searching options.

---

### Post by darincb77 on 2012-06-26
Great! I am very interested to see if we can get the resolution better, I've had this machine stuck on an old distro for a while. 

Let me know if you have any progress. I've been trying to circumvent the bug with kernel updates, but no progress so far.

---

### Post by darincb77 on 2012-06-27
Well, I've had no luck with 12.04. But honestly, I was getting the feeling that unity might be a bit clunky on this machine. 

I've installed xubuntu 11.10 from alternate, which is snappy and nice. 

If you do that, you can blacklist poulsbo and psb_gfx and install emgd110 from : [https://wiki.ubuntu.com/PoulsboObsoleteDrivers](https://wiki.ubuntu.com/PoulsboObsoleteDrivers)

I've done the standard blacklists of the sd card. 

I've also installed compiz from [http://www.howtoforge.com/enabling-compiz-on-xubuntu-11.10-oneiric-ocelot](http://www.howtoforge.com/enabling-compiz-on-xubuntu-11.10-oneiric-ocelot) and emerald from [http://it-diary.com/tutorials/install-compiz-emerald-xubuntu-11-10/](http://it-diary.com/tutorials/install-compiz-emerald-xubuntu-11-10/) . It is fast and nice.

I think I might stick with this for now. It is nice to have a functional computer even if the distro is not ideal.

---

### Post by serwwweb on 2012-06-27
Ok, i think i will keep on trying to find a solution, as this machine is not my primary one. I might try fedora 17 first, i've heard that might work. I'll keep briefing my results and i thank you for your assistance.

---

### Post by darincb77 on 2012-06-27
Sounds good. Keep me informed. F17 might be good because it is a later kernel 3.3.4 which comes with gma500_gfx, still 2D but worth a shot. 

Let me know if you are interested in xubuntu 11.10 - it took a few tweaks but it is really nice now with 3D + compiz - much better than gnome ever was with 3D. Cheers.

---

### Post by serwwweb on 2012-06-28
Ok, Fedora doesn't work either, Ubuntu 12.10, same result: "Black Screen". Even with all the blacklist devices and options.
I'm getting tired, and i don't want to install windows on this machine, first i will sell it!
So, i am willing to accept your offering on how to install xubuntu as a desperate last effort :-P

---

### Post by darincb77 on 2012-06-29
Ok, well I used the xubuntu alternate for a usb install, with a blacklist of the sd card. Then on the first startup I made permanent the blacklists of the sd card and psb_gfx. Then it should boot stable.

Then install emgd110 from : [https://wiki.ubuntu.com/PoulsboObsoleteDrivers](https://wiki.ubuntu.com/PoulsboObsoleteDrivers) - you shold now have good resolution

If you want compiz and emerald, you can use the instructions on:  [http://www.howtoforge.com/enabling-c...oneiric-ocelot](http://www.howtoforge.com/enabling-c...oneiric-ocelot) and emerald from [http://it-diary.com/tutorials/instal...xubuntu-11-10/](http://it-diary.com/tutorials/instal...xubuntu-11-10/) . It is fast and nice.

I am working on getting suspend to work now. Everything else seems OK. I hope I haven't missed anything. 

I also removed "quiet splash" and "vm.something=7" from the grub line to be safe, and changed the swappiness to 10 and did 'sudo apt-get install preload' to make things a little faster.

The wireless is also weird, with "mcu" errors. To be safe I installed the rt3090 deb from here: [http://ubuntuforums.org/showthread.php?t=1669283](http://ubuntuforums.org/showthread.php?t=1669283)  and I blacklisted the rt2 drivers. I'm not sure how necessary that is. 

Let me know if you have any questions.

---

### Post by serwwweb on 2012-06-29
How did you do to make it work the alternate from USB? It keeps me asking for the cd.

---

### Post by darincb77 on 2012-06-30
I just used the ubuntu startup disc creator on another computer, with the alternate i336 iso: 

[http://cdimage.ubuntu.com/xubuntu/releases/oneiric/release/xubuntu-11.10-alternate-i386.iso](http://cdimage.ubuntu.com/xubuntu/releases/oneiric/release/xubuntu-11.10-alternate-i386.iso)

You could probably just use the live disc with the proper blacklists (sdhci,sdhci_pci,mmc0,mmc_core,psb_gfx). If you want to give that a try: [http://cdimage.ubuntu.com/xubuntu/releases/oneiric/release/xubuntu-11.10-desktop-i386.iso](http://cdimage.ubuntu.com/xubuntu/releases/oneiric/release/xubuntu-11.10-desktop-i386.iso)

---

### Post by darincb77 on 2012-06-30
Alternatively, if you have no luck with the ubuntu startup disc creator, you could use unetbootin and point it to your downloaded iso file.

---

### Post by serwwweb on 2012-06-30
At last i'm writing from Ubuntu 11.10 installed via usb prepared with unetbootin, but the only way to install it was via network installation.
Right now i'm just about to install gma500 graphics and look what happens. I was able to install the system without any tweak and boots fine with the exception of the drivers for graphics card wich results on a screen resolution of 1024x768.
I will try what you've done for xubuntu and i will post later.

---

### Post by serwwweb on 2012-06-30
Ok, i've got native resolution 1366x768. Installed EMGD driver 1.10 from ppa and only works for unity 2d, and i must say a bit chunky. The worst is that the youtube videos are horrible, even the sound cracks and pauses randomly. Can't get 3d acceleration. I'll keep on searching.

---

### Post by darincb77 on 2012-07-01
Ah, I think we had some misunderstanding. I installed Xubuntu 11.10, you seem to have installed regular ubuntu with unity.

Either should work I guess, but xubuntu is quite snappy. Youtube videos are ok in chrome, the mplayer vaapi in the emgd ppa works well.

---

### Post by serwwweb on 2012-07-03
Ok, my mistake, i'll try it.
Thank you so much. Unity runs very poorly in this machine.

---

