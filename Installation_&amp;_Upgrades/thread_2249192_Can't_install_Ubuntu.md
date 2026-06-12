---
title: "Can't install Ubuntu"
date: 2014-10-20
forum: Installation &amp; Upgrades
---

### Post by exodus3 on 2014-10-20
Well i started with Ubuntu v12 a year or so ago but  life got in the way and i never got back to it again

i have been wanking about windows since XP came out ,after looking at windows 8.1 on the wife's laptop ,,the writing is on the wall 
and no way am i waiting around to get away from windows once and for all 

enough of why i am switching to anything but windows 

i forgot how i installed ubuntu 12 the last time :(  but i have DL'd and tried to install 14 twice and even went to 12 and gave it a shot 

have the same dam thing happen to me each time,after dl and unzip,when i click the application install icon i get a version\size\password and a few other things dialog box ,after filling those out when i click install,it will DL  ubuntu again,when it gets fully dl'd i get an error box [forgot to capture or write it down]

tried to make a USB install too,but can't find any iso file in the dl 

btw,,i want to run it along my current Vista OS  until i feel comfortable enough to dump windows

---

### Post by Impavidus on 2014-10-20
The thing you download *is* a .iso file. Maybe Windows offers you to unpack it, extracting the files that would come on the live disk, but the thing to burn is the downloaded .iso itself. For live usb, this may be helpful: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Don't use the wubi.exe that might still be included. It's old and no longer maintained. Create either a live dvd or usb and boot from that.

---

### Post by nerdtron on 2014-10-20
And here's a youtube video to create a bootable USB drive: [https://www.youtube.com/watch?v=Q7ZXA2Zedko](https://www.youtube.com/watch?v=Q7ZXA2Zedko)

---

### Post by Mark Phelps on 2014-10-20
> have the same dam thing happen to me each time,after dl and unzip,when i click the application install icon i get a version\size\password and a few other things dialog box ,after filling those out when i click install,it will DL ubuntu again,when it gets fully dl'd i get an error box [forgot to capture or write it down]
This reads like a WUBI install -- as in, installing while running Windows.  Do NOT do that!  WUBI is no longer supported and if it doesn't work, which is very possible, you won't be able to get much help.

> tried to make a USB install too,but can't find any iso file in the dlThat's because you need to download the ISO file of the Ubuntu version you want to install -- not the WUBI file.

> btw,,i want to run it along my current Vista OS until i feel comfortable enough to dump windows Then, the first thing you want to do is shrink down the Vista OS partition to leave room for Ubuntu.  To do this, download and burn a CD from the Minitool Partition Wizard Boot CD.  Boot from that, and use that to shrink the Vista OS partition.  Do NOT use GParted from the Ubuntu installer to do this, as that risks corrupting the Vista filesystem and rendering it unbootable.

Also, if you have an external drive available, it would be a good idea to install Macrium Reflect and use that to do an image backup of Vista -- which you could then use to restore it, if the dual-boot install goes badly.
> have the same dam thing happen to me each time,after dl and unzip,when i click the application install icon i get a version\size\password and a few other things dialog box ,after filling those out when i click install,it will DL ubuntu again,when it gets fully dl'd i get an error box [forgot to capture or write it down] 

---

### Post by exodus3 on 2014-10-20
wow guys ,,thanks for all the help,got more then i expecting but it just creates more questions for me 
i have not had time to keep up with all the PC  geekness to fully understand everything that is being said

this is the link i am using to get the ubuntu file ,,i am getting the 32bit version: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

windows DL's it as a zip file,the only other choice is to open it 

this is what i have after using winrar to open it :

[IMG]http://i.imgur.com/gIokf99.jpg[/IMG]


> Also, if you have an external drive available, it would be a good idea  to install Macrium Reflect and use that to do an image backup of Vista  -- which you could then use to restore it, if the dual-boot install goes  badly.

Edit:  i was able to find and run this program,,done deal and thanks

---

### Post by nerdtron on 2014-10-20
> windows DL's it as a zip file,the only other choice is to open it 

this is what i have after using winrar to open it :

Do not extract the file. You need to "burn" the file to a DVD or USB to make a bootable media. Then you'll be able to install Ubuntu.
See here how to: [http://www.everydaylinuxuser.com/2014/03/how-to-create-bootable-linux-usb-drive.html](http://www.everydaylinuxuser.com/2014/03/how-to-create-bootable-linux-usb-drive.html)

---

### Post by exodus3 on 2014-10-21
U so smawt grassa hoppa ,,well not really  :D

i had a flashback to the last time i tried getting an ubuntu iso file from a few years ago,,took close to 2 weeks and help from the local pc shop boys to make it happen

dl'ing from a different machine & even changing file extensions were useless !!

turns out that my winrar program is the culprit  for not being able to get the iso file 

i had to dis-associate winrar with iso's before i could get the correct format file 

so up next is how to create a partition for the ubuntu to run on,i am really gonna need help with this one since i have never partitioned a HDD with an OS on it  :doh:

---

### Post by nerdtron on 2014-10-21
> **exodus3 said:**
> 
so up next is how to create a partition for the ubuntu to run on,i am really gonna need help with this one since i have never partitioned a HDD with an OS on it  :doh:

You don't have to create it manually. If vista is already installed, you can boot into your USB installer and Ubuntu *should* detect that you have windows vista installed. On the installation of Ubuntu there will be an option to "Install side by side" with windows. Then you have a nice GUI to set how much you want to give Ubuntu. Then continue the installation.

---

### Post by exodus3 on 2014-10-21
> **nerdtron said:**
> You don't have to create it manually. If vista is already installed, you can boot into your USB installer and Ubuntu *should* detect that you have windows vista installed. On the installation of Ubuntu there will be an option to "Install side by side" with windows. Then you have a nice GUI to set how much you want to give Ubuntu. Then continue the installation.


i have 205gb free space,,i want to dedicate 150gb of that for ubuntu .idk  what numbers i will need to make that happen

---

### Post by exodus3 on 2014-10-21
continue  in this thread about the partitioning :   [http://ubuntuforums.org/showthread.php?t=2249298](http://ubuntuforums.org/showthread.php?t=2249298)

---

