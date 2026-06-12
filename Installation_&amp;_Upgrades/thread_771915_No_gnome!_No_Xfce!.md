---
title: "No gnome! No Xfce!"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by Vash on 2008-04-28
Hello i have a huge problem and would appreciate some advice. I had 7.10 running perfectly for a while, i decided to upgrade to hardy i did it a bit early maybe 4 days before the actual release everything went fine. my problem started when i tried to add the xubuntu desktop and have it in addition to gnome but it didnt work out so decided to remove it. I ran a command from a page i found (bad idea) and it unistalled gnome and Xfce now im stuck! i can login and access apt from the command line only but it says it cant retrieve info from the sources and keyring manager is broken so it cant be installed when i run sudo apt-get gnome-desktop-environment or gnome base or even nautilus. I know it is completely my fault it was my ignorance or negligence rather but i have 4 gigs of important photos and 8 or 9 gigs of music. Im on the 7.04 live cd i can see the partition and mount it but the pictures cannot be accessed due to read and write privileges. Please help me my system was heavily customized. Thanks so much in advance. I really dont want to go back to windows. . .eww

---

### Post by tamoneya on 2008-04-28
you should have plenty of privileges to mount your drive when you are running the liveCD.  What commands are you using and at what points are they failing?
Just so that it is easier for me to tell what you are doing could you post the result of ```
sudo fdisk -l
```This way when you reference /dev/sda1 or something i will know what partition you are talking about.

---

### Post by Vash on 2008-04-28
ok here it is 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60092   482688958+  83  Linux
/dev/sda2           60093       60801     5695042+   5  Extended
/dev/sda5           60093       60801     5695011   82  Linux swap / Solaris

I have no problem mounting sda1 just click on it in nautilus (from live cd) and i can see my files correctly but the pictures folder cannot be opened i want to copy them to a drive or reinstall gnome (preferably) now this is all from the cd. The only commands i have ran is without the cd after grub i get a command prompt asking for my user name and password and i login but then i try to run sudo apt-get install gnome-desktop-environment but it cannot install.

---

### Post by tamoneya on 2008-04-28
what do you mean you cant get into your pictures folder.  You should have unlimited permissions while running the liveCD since there are no passwords.  There should be no lack of permissions. The only thing i can see as a problem would be if you had encrypted them for some reason.

---

### Post by Vash on 2008-04-28
Yes it only shows the owner as the one with permission to read and write the files. :( im screwed i dont know what to do but thanks anyway

---

### Post by tamoneya on 2008-04-28
just do ```
sudo chmod -R 777 /my/directory/of/pictures
```

---

### Post by Vash on 2008-04-28
WOW! you're a genius! Thanks so much that did the trick.

---

