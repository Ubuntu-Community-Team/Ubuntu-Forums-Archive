---
title: "Trying to Install Ubuntu 8.04 on my Samsung R60"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by ashley99 on 2008-05-19
I have installed the OS, but when I re-boot and choose Ubuntu I get through to the splash page and that's it. After that the installation is supposed to ask me to choose a language, region, keyboard set-up, etc. The problem is that after the splash page it goes to a command-driven page discussing 'Root' and 'Sudo', with the command line reading ubuntu@ubuntu:~$ 
I've never worked with Linux, but have been told how easy the Ubuntu system is to get along with. Can someone help me out?

---

### Post by Pumalite on 2008-05-19
Tell me the name of your iso.

---

### Post by ashley99 on 2008-05-19
ubuntu-8.04-desktop-i386

---

### Post by Pumalite on 2008-05-19
Burn a new CD after doing md5sum on your iso; burn at 4x or less on CD-R, check CD integrity before install.

---

### Post by beN..87 on 2008-05-30
> **ashley99 said:**
> I have installed the OS, but when I re-boot and choose Ubuntu I get through to the splash page and that's it. After that the installation is supposed to ask me to choose a language, region, keyboard set-up, etc. The problem is that after the splash page it goes to a command-driven page discussing 'Root' and 'Sudo', with the command line reading ubuntu@ubuntu:~$ 
I've never worked with Linux, but have been told how easy the Ubuntu system is to get along with. Can someone help me out?


ashley this guide works perfectly for the samsung r60 plus -- i have the same laptop 


i dont wanna sound patronising but if yor an abosloute beginner -- when i write things like
sudo bash
cd mnt/usb

those are commands to be entered directly into the command line (or later when you have gnome up and running, by opening a terminal by opening it from applications>accessories)

first off you need to get installed and get your graphics running


get the ATI proprietry drivers from here   (for your radeon graphics card)

[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

put the file on a USB drive or similar

insert hardy 8.04 i386 (NOT the 64 bit) ALTERANATE CD (must be alternate CD)
F6 (opens boot paramater line to input)
noapic (add this to prevent I/O Bug)
<press enter> (Starts install process)
(Install to ones liking.)
(Reboot into system without cd in drive.)
(Press alt F2 and login.)
(Insert Install CD)
sudo bash
apt-cdrom add (adds the CD to the lsit of resources)
apt-get install build-essential (installs build environment)
(remove the CD)
mkdir /mnt/usb (mount point for external media)
(insert your USB flash drive or other media)
mount /dev/sdb1 /mnt/usb (your point may be /dev/sda1 or /dev/sdb2 or similar)
cp -R /mnt/usb /usb
umount /dev/sdb1 /mnt/usb
(remove flash drive)
mv /usb /ati-driver
cd /ati-driver
sh ati-driver-installer-x86.x86_64.run
(--- just accept all defaults for the install - literally its yes yes yes yes
after install is complete---
reboot

your Ubuntu should now boot into a full graphical gnome system

now for your wireless card - follow nicedudes guide here 

[http://ubuntuforums.org/showthread.php?t=795984&highlight=samsung+r60](http://ubuntuforums.org/showthread.php?t=795984&highlight=samsung+r60) TO THE LETTER ( also install wicd network manager is reccomended)

this worked for me on ATI Chipset /Aetheros wireless (Samsung r60plus)


any problems just ask - i have the same machine

---

### Post by beN..87 on 2008-05-30
i forgot to mention - the reason you cant get past the splash page is because you are using the i386 normal CD --- you need to get the 32 bit Alternate Install  (still i386 but Alternate CD)  -- dont use 64 bit or the one you're using now - or you're banging your head against a brick wall

once you have got the i386 alt CD - follow what i just posted -- make sure you add noapic to the boot paramater by pressing
F6
noapic
<press enter to start install>

then you should be away into the install process - follow the rest of my guide - and you should have a full ubuntu desktop---- then for your wireless-- follow nicedudes guide TO THE LETTER and you will have a working samsung r60 with ubuntu / vista dual boot!

ps also some tips for the install process if youve nevr done it before

dont worry about the network config - select option " dont configure network at this time"

 also be very careful and make sure you install an ext3 file system to a partition that is EMPTY - or your will wipe your vista

set bootable flag to OFF (or vista longhorn loader gets pissed off)



any problems give me a shout

---

### Post by ashley99 on 2008-05-30
Thanks very much, Ben..87. I'm going to give this a try tonight. 
Cheers,

---

### Post by haylun98 on 2008-06-07
Big Thank You to beN..87. I finally installed ubuntu 8.04 on my Samsung r60plus.
However I can only logon to ubuntu in failsafe Gnome mode to see GUI desktop. Normal Gnome session will only boot to a blank white screen with mouse cursor. I think the GUI desktop is behind the white screen. I was able to run Firefox with Fn+Home keys but unable to bring to front with Alt+Tab.
Has anyone seen this problem before?
I think this is still graphic driver problem. The driver filename i installed is slightly different with version number "-8-5-" in the middle of the it. I downloaded it via the link above in the guide.

Anybody help?

I am new to ubuntu forum and linux

---

### Post by beN..87 on 2008-06-08
> **haylun98 said:**
> Big Thank You to beN..87. I finally installed ubuntu 8.04 on my Samsung r60plus.
However I can only logon to ubuntu in failsafe Gnome mode to see GUI desktop. Normal Gnome session will only boot to a blank white screen with mouse cursor. I think the GUI desktop is behind the white screen. I was able to run Firefox with Fn+Home keys but unable to bring to front with Alt+Tab.
Has anyone seen this problem before?
I think this is still graphic driver problem. The driver filename i installed is slightly different with version number "-8-5-" in the middle of the it. I downloaded it via the link above in the guide.

Anybody help?

I am new to ubuntu forum and linux

i ran into the same problem on a couple of installs on the R60 -- i cannot figure out why as i did it the same way each time - sometimes it worked, sometimes it didnt and i got the white screen - anyway heres what finally worked  ( the reason i did it this way is that i remember doing some kernel and binary builds with Linux from scratch , and read somewhere that bash leaves certain files in RAM for easy retrival, which can hang around and cause problems when compiling kernels etc )

boot into vista and play around and then shut down (just to get rid of any temporary linux files in RAM that might be retreived by bash being lazy if you simply reboot from previously being in ubuntu )

insert the alternate CD and reinstall - during the partitioning stage WIPE the partition containing the previous ubuntu install (to get rid of any files that the fresh install will see as identical and get confused/ not install the new ones)

carry on with the install process and the ati drivers installation

reboot and pray that you see the heron smiling back rather than the white screen after you log in!!

-- this really confused me as i did it the same way each time and had differing results - i must have reinstalled it 5 times and kept getting the white screen until i tried this way and it worked! my guess is that bash and / or the installer recognises files either on the hard drive or in RAM (for easy retrival by bash) and some bugs happen during the install

hope it works out for ya

---

### Post by haylun98 on 2008-06-08
I tried it again last night and it work. This time I use a blank usb drive to save the ati driver. I also notice the first install when i run the cp -R command it took ages compare to the second. My initial usb key also contains other data adding up to nearly 2Gb. May be these other files got loaded in the memory prevent proper ati driver install.

---

### Post by naster on 2008-07-21
> **beN..87 said:**
> ashley this guide works perfectly for the samsung r60 plus -- i have the same laptop 


 As you're the owner of this laptop, can you tell me if you did manage to get all hardware working in ubuntu, such as WiFi, webcam, etc? And do Fn+key combinations work? If no, how do you adjust brightness of the monitor?
 I think I'll buy this laptop, so the answers for those questions are really important for me.

---

### Post by beN..87 on 2008-07-24
> **naster said:**
> As you're the owner of this laptop, can you tell me if you did manage to get all hardware working in ubuntu, such as WiFi, webcam, etc? And do Fn+key combinations work? If no, how do you adjust brightness of the monitor?
 I think I'll buy this laptop, so the answers for those questions are really important for me.


yeah ati graphics driver works - however it is proprietry not open source, so if you want 100% open source thats one thing to consider.... theres no webcam built in , wifi works great with madwifi

the hardware all works , so no problem with hardware - as for software the only problem i have encountered is Compiz Fusion 3d desktop has some video issues - though these are fixable

---

### Post by naster on 2008-07-25
> **beN..87 said:**
> ... so no problem with hardware

OK, thank you for your response.

---

