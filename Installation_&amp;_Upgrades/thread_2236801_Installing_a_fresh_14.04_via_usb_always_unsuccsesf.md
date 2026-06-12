---
title: "Installing a fresh 14.04 via usb always unsuccsesful"
date: 2014-07-29
forum: Installation &amp; Upgrades
---

### Post by omeraf on 2014-07-29
Dear forum I am very desperate for help.
I used yesterday unetbootin to create an Ubuntu 14.04.1 live cd on an Sandisk USB which I did use to install in the past so I know that the USB stick is okay, the [COLOR=#FF0000]installation progress completes with no errors [/COLOR]and I manage to boot to an unusable install. I [COLOR=#FF0000]cant see my cursor or use my touchpad in [/COLOR]my Asus laptop,[COLOR=#FF0000] the system is very slow[/COLOR] and unresponsive,[COLOR=#FF0000] I cant connect to any WIFI [/COLOR]or wired internet and the [COLOR=#FF0000]GUI is broken visually[/COLOR] as well. 
I am not able to download or create a new live cd with either disk utility or unetbootin 
I do not know what to do please help me

ASUS laptop  
Ubuntu 14.04.1 64 bit 
NVidia gt 520m

---

### Post by mastablasta on 2014-07-29
you didn't provide much data: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
if you actually boot to the OS you will have system logs available to show you what went wrong. if you can't get into the OS then you can hit esc while the OS is loading to see if there are any errors.

hold shift on boot to get the boot menu. try one of the boot options offered:[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
particulary nomodeset.

if it is not working and if you have NVidia Optimus technology you will need to install bumblebee.:  [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

also I assume live USB is still working well?  you did try it as live OS first to make sure all works on the notebook and hardware is Linux compatible?

I foyu haven't yet, oyu might want to drop to console and install NVidia drivers there. have a look at this: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by omeraf on 2014-07-29
thank you for the quick reply 
I will post more info from the logs as it will help us both later on. as for the optimus technology. I know currently the OS is using the Ubuntu driver not an NVidia one
and yes the live cd works perfect
I did try the recovery options like the check file system and the repair broken package 

I have been using elementary os luna with bumblebee for while now and I tried mint 17 with nvidia prime and works very good

---

### Post by mastablasta on 2014-07-29
means you have optimus. you need NVidia drivers and bumblebee I believe. live cd uses only intel probably which is why it works well. hard ot say since I do not have any experience with NVidia let alone optimus.

also use what works. 

run the rest in virtualbox :P

---

### Post by omeraf on 2014-07-30
I have no idea how to get the system logs out of my ubuntu.  I do able to boot to it
Plus when holding  shift to try for the boot menu dose not work
Im using my phone to reply

---

### Post by hoodbrothers2 on 2014-07-30
You should probably check if your bios needs updating.  I had a very hard time installing ubuntu on my pc, and updating the bios fixed my issues.

---

### Post by omeraf on 2014-07-30
I have no way to update it as it wont connect to internet

---

### Post by omeraf on 2014-07-30
Let give a little bit of history maybe it will help
I used mint17 and everything was great until i had gui problems and we thought its cuz of the nvidia driver so I tried to install the 340 version one and i did use the331 that u get through the driver manager,  but it ****ed it up i tried to reinstall. Mint with no success. So i said lets try ubuntu and now im here

---

### Post by hoodbrothers2 on 2014-07-30
Do you have another computer or something with a USB port?  If you don't know how to update the bios look up a tutorial.  But before you do that you should try to look up your laptop/motherboard to see if it needs an update at all.  However my problem was that I couldn't start ubuntu at all, whereas you can get at least a broken version.  Have you tried resetting the x org / x server?  It's been a while since I did but look up a tutorial.  I know it involves going into the grub repair menu.  When I screwed up my own x org it was when I was dealing with a new NVIDIA graphics card, so that could help.

---

### Post by hoodbrothers2 on 2014-07-30
This could help.  In the grub repair menu there is an option that gives you a command line like a terminal.  First you have to type a command that let's all other commands work.  I forgot what it is so search around on the web.  After that command, type

sudo apt-get remove --purge nvidia-*

To remove all things with NVIDIA.  Then try

sudo apt-get install --reinstall xserver-xorg

These should work but if they don't then don't blame me.  Finally, I found a tutorial that let me install NVIDIA drivers, and I'll look around for it.  If I find it I'll try to post it here.  Good luck!

---

### Post by hoodbrothers2 on 2014-07-30
This was on another thread.


Re: How to repair xorg without reinstalling ubuntu?

remove:

Code:
sudo apt-get remove xserver-xorg

install:

Code:
sudo apt-get install xserver-

reconfigure:

Code:
sudo dpkg-reconfigure xserver-xorg

---

### Post by hoodbrothers2 on 2014-07-30
Type all of these after the purge NVIDIA thing but still do it in the grub repair menu.

---

### Post by hoodbrothers2 on 2014-07-30
Here is the YouTube tutorial to install NVIDIA drivers.  His voice is REALLY weird, but this works.  Just remember to replace the driver version with the one you want.

[https://m.youtube.com/?#/watch?v=1oKn8DHvOrk](https://m.youtube.com/?#/watch?v=1oKn8DHvOrk)

---

### Post by omeraf on 2014-07-31
Well the real problem is that i cant connect to any wifi or wird Internet. So i cant reinstall anything

---

### Post by omeraf on 2014-07-31
A clean fresh install. With no usb no mouse no wifi nothing. And im stuck i cant make new usb stick with different distribution nothing

---

### Post by hoodbrothers2 on 2014-07-31
Ok, listen.  Boot up your computer.  Press the shift key over and over again until you boot into the grub menu.  Using the arrow keys, choose advanced options ubuntu.  Choose the latest version of linux that says recovery mode, i.e., 

Ubuntu, with Linux 3.13.0-32-generic (recovery mode)

Choose the option, root, and press enter.  You should see a command line.  Type, 

mount -o remount,rw /

Then, type

sudo apt-get remove --purge nvidia-*               (press enter after each line of code) (and thanks to NikTH for this bit)
sudo apt-get install ubuntu-desktop
sudo rm /etc/X11/xorg.conf
echo 'nouveau' | sudo tee -a /etc/modules

Then exit by typing: exit.  You might have to restart afterwards.  If this doesn't work, go back to the command line, type the mount command,  and proceed.  But ONLY if the above stuff doesnt work.

Next,

sudo apt-get remove xserver-xorg

Then,

sudo apt-get install xserver-

Finally,

sudo dpkg-reconfigure xserver-xorg

To exit type: exit.  Then press resume.  This should work!  But you might need to restart after pressing resume.  Good luck, and report back to tell me what happens.

---

### Post by omeraf on 2014-07-31
Thank you very much 
Well it did not fix any thing at gui the xorg commands
I think the real problem is that the os dont load any module. Even not for network or the touch pad
After ill be able to use my mouse and internet it will easier to fix the xserver issue

---

### Post by oldfred on 2014-07-31
What model Asus?

Some general info here:
 [https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)

---

### Post by omeraf on 2014-08-01
> **oldfred said:**
> What model Asus?

Some general info here:
 [https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)




Its an asus k53sj

---

### Post by oldfred on 2014-08-01
Asus seems to have a different model number for every system with different options.

Not sure if some of these are similar or not.
 ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Asus UltraBook - kernel comparisons K56CA
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI)

You first need to get Internet working using hard wired Ethernet. Then you will be able to run updates and get drivers for whatever needs new drivers.

---

### Post by omeraf on 2014-08-02
i solved my issue by geting a new usb disk and in the live cd session made a new usb disk and installed mint 17

---

