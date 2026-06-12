---
title: "Getting Rid of a Vista/Feisty Dual Boot setup"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by darussian12 on 2007-05-19
Browsing through the forums, i have been able to find lots of threads about how to get a dual boot installed and lots of threads about removing Linux and going to WIndows only. But for me at the moment I have Vista/Ubuntu and need to know that easiest way to 1) get rid of the Vista partition that in turn...2) I will not have to ever deal with Grub appearing and just automatically boot into Ubuntu as if there was nothing on the Hard Drive other then Linux since day 1 which leads me to part 3) I want to be able to use the free space to blow up my /home parition. Whats the easiest way to do the three above? Is there anyhing i need to know in regards with how the current partitions are arranged on the HD. Because i know the Vista one is the first one going from left to right on the HD diagram in partition magic. I have enough space on my / partition to back up anything in my /home parition if i need to delete it and just create a new and bigger one after deleting the vista ntfs parition, but i really dont know the proper way to go about this without screwing one of the paritions i dont need reformated. Im used ot being able to resize paritions as i please in the windows life, but i know its going to be a much bigger pain the the *** then simple click and drag and thats why Im asking the pros. thanks anyone that can help me out.

---

### Post by eapache on 2007-05-19
My suggestion is that you first use gparted to format your vista partition as ext3, then mount it as something temporary. Copy your home partition over to it (make sure to include hidden files), and set it as your home partition in fstab. Reboot, and make sure that it came up correctly as your home partition. Then use gparted to delete your old home partition and extend your root partition into the remaining space.

In theory your partition table would start as:
hda1 NTFS vista
hda2 ext3 /
hda3 ext3 /home

And end as:
hda1 ext3 /home
hda2 ext3 /

Is this what you were looking for?

EDIT: as for grub, after vista is gone, you can set the grub timer to 1 second, so that there is only a 1 second delay before booting ubuntu automatically. I don't know if you can remove it completely, but I wouldn't even if you could because its the only way to access recovery mode.

---

### Post by darussian12 on 2007-05-19
i am looking to make the 20 some odd gigs i left for bare bones vista and combine it with my existing /home partition. i dont need or want to make my root parition any bigger then what it is. so i guess my problem is how do i go about combining two paritions on the oppsite ends of the parition map...ignoring the swap space.... into 1 larger partition without having to reformat and lose stuff in my home and/or root parititions. This is my second competele reinstall of Ubuntu since trying out the linux life 2 weeks ago and not really feeling the back up all my files urge again :-)

> And end as:
hda1 ext3 /home
hda2 ext3 /

i thought the root parition had to be the first parition or something i thought i had read regarding Linux. then again ive browsed through way too much tech wiz speek to keep up correctly. how its physically arranged on my HD wont matter to me as long as it boots properly and that all the space that Vista is using is combined with my current /home parition and still be recognized when I logon.

---

### Post by eapache on 2007-05-20
Your root partition doesn't have to be first, but you cannot move the beginning of it because that is where grub looks for it's config. I don't think you can combine partitions at either end of the table because your root partition cannot be moved. When reinstalling, however, you don't have to back up your files (still suggested, but not necessary), just make sure that you don't format your home partition. What I would now suggest is the following:

- format NTFS as ext3.
- copy over current home partition (don't forget hidden files)
- in gparted, delete / and old /home, and extend new /home to desired size.
- reinstall feisty, keeping new home partition as-is, and thus all of your settings as well.

All you'd have to do would be reinstall a few programs. All of the settings, documents, menus etc. would be saved.

Your other option is to format the NTFS as ext3, and then mount it in fstab as a folder inside /home/username/. I have a second hard-drive for backup, and I mount it in /home/eapache/Backup, despite having my /home on a separate partition from /.

---

### Post by darussian12 on 2007-05-20
im assuming all the stuff i had to do to get my wireless, resolution and a few other issues working are stored in my root folder and not /home. because im assuming whatever i get through synaptic or the apt-get command ends up in root correct?

---

### Post by eapache on 2007-05-20
That depends. System-wide graphics settings (driver settings etc.) are stored in /etc/X11/xorg.conf. Wireless I really don't know. When you install something using add/remove or synaptic or apt-get (all really the same thing, regardless of permissions), it installs the executable in /bin/ and other things in other places. Program preferences that are user-specific end up in /home/username/.program. However, program preferences that are system-specific (such as wireless driver configurations) end up in various places. Installing the correct driver and then copying over your xorg.conf file will solve all of your graphics problems. For wireless, I don't know. You can look around to try and find the config file, or you can do it again (hopefully it will go faster the second time, since you know what you have to do). If you will list any other problems you had, and fixed, I'll try to point you to the proper config files.

---

### Post by darussian12 on 2007-05-20
after doing a second reinstall of ubuntu in a span of 2 weeks ive got all the important threads subscribed to on here...my biggest deal is the wireless after finally getting my beryl/compiz conflict with video playback resolved. no matter how well i follow the sticky about getting my broadcom 4318 card going, it always takes me a few go arounds with various methods so was wondting to avoid that but if i could do it twice i can surely do it 3x and hopefully for good. last question. copying stuff from my current /home to my new /home can i just right click and copy paste and that would solve the problem or is it some terminal method i need to do to make sure everthing goes like hidden files and such?

---

### Post by Kaptain Chaos on 2007-05-21
Hello,
Yes, you can just 'copy and paste'. All you need to do is open Places > Home Folder and then in the 'view' drop down menu click on 'Show Hidden Files' (Ctrl H). You'll see all of your hidden files as semi-transparent with folders having a full-stop before the regular name eg '.mozilla-thunderbird'. Create a 'username' folder in the new 'home partition. Copy and paste all the files into the 'username' folder in your new home partition. If there is more than one user (you) in your current home partition then the same thing needs to be done for each (I'm sure there must be a way to 'sudo' this from the terminal but I find this works). You could also burn the home folder to DVD to be on the safe side.

If you use the live CD to reinstall Feisty you'll be able to delete everything past your newly created home partition, increase it's size and create your 'root' and 'swap' partitions where and how big you want them.

---

