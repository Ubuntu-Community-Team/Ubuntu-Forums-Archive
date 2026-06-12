---
title: "cant get Adobe flash player to load in Ubuntu 11.4"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by leeper69 on 2011-06-02
Hi everyone:
 I am having problems getting Adobe flash player to load.
I went to there site and could only find the Linux download for Ubuntu 10.4 so I tried to load it using update manager to no avail cant seem to get it working in version 11.4, Works fine in version 10.10 . has anyone else had this problem? pleas let me know if you have and any help with this will be appreciated.

---

### Post by SeijiSensei on 2011-06-02
I use the 64-bit "[Square]("http://labs.adobe.com/downloads/flashplayer10_square.html")" beta which works quite well.  Download and unpack the compressed file. You'll get a file called libflashplayer.so.  Then run ```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
``` to make it available to all users.

---

### Post by lovinglinux on 2011-06-03
You can also use my [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) add-on. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance.

---

### Post by leeper69 on 2011-06-04
Hi lovinglinux I tried to install flash aid but cant get it to work I also tried to install flash installer using Synaptic but I get the following message [Pleas insert disk labeled Ubuntu 11.04_natty narwhal_-release amd64(20110427.1) in drive /cdrom/] I dont have this disk I downloaded a install disk from distrowatch and installed 11.4 with it but if I put it in the cd drive it is not recognized as the disk the system is looking for? I have never had so many problems getting things to work with Ubuntu the last two releases have just worked with no tweaking. I guess I am just getting spoiled If I look back to the old days of Linux this was the norm.

Hi Seiji Sensei I downloaded the file libflashplayer.so and copied it to the directory /usr/lib/mozzila/plugins/ but it dosent show up in my plug-ins list and I have checked to be sure it is in the proper directory? what am I doing wrong.

THANKS to both of you for answering my post!!!

---

### Post by leeper69 on 2011-06-08
Hi 
  I finally had some time to work on the problem installing Adobe flash player as it turns out the disk I downloaded from Distrowatch has all the necessary files on it but for some reason the system refuses to read them. this is how I got flash to work using Synaptic I tried to install the flash installer program which asked for the 11.4 disk it didn't work and gave me the following error message could not load cd/pool/main/e/eglibic/libic6_i386_2.13 oubuntu 13_amd64.deb so i quit Synaptic and opened the cd and went to the corresponding directory and clicked on the file which then opened with update manager and i installed it. then went back to Synaptic and tried to install flash installer again, it still wanted the disk so I quit the install and another error message popped up telling me that the file at cd/pool/main/a/alsa-lib/lib32asound2_1.0.24.1-oubuntus__amd64.deb was missing. so I quit Synaptic again and went to the corresponding file and manually installed it with update manager by double clicking on the .deb file.,then went back to Synaptic and installed flash installer. this time it no longer looked for files on the cd and finished loading the necessary dependences.  WOW FLASH PLAYER WORKS NOW! I am sure I will have more issues with this type of problem due to some glitch in my install of 11.4 but all is well for now.
Hope this will help some poor soul with similar problems!

---

