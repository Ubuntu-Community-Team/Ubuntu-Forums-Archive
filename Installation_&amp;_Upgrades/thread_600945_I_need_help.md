---
title: "I need help"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by ChopperX on 2007-11-02
Ok i am currently running 7.04 fiesty fawn and i want to upgrade to the new gusty. I dont know how to do this since this is my first time upgrading a linux distro and i would like some help. If there a way i can download an installer or do i have to make a cd again and go trough that hassel?

---

### Post by Pumalite on 2007-11-02
If you have a working OS and are happy with it, I'd say keep it!. But if you insist, then I'd advise a clean install after saving /home and data. If you still insist on upgrade, you might want to try this:

sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list

sudo apt-get update

sudo apt-get dist-upgrade

---

### Post by ChopperX on 2007-11-02
i only have one os on this pc and thats linux and i fine with a clean install

---

### Post by Pumalite on 2007-11-02
You can download an iso from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by lyndaj70 on 2007-11-02
Watch doing clean installs, ESPECIALLY if you have an ATI video card....

If it works now, I recommend using update manager (system --> administration --> update manager) and at the top where it says there is a new version available, click "upgrade now."  Or burning an "alternate install" cd and using that.  I don't think you can upgrade using a regular Live CD, but I know you can just stick the alternate cd into the running computer and it will pop up asking you if you want to start the package manager or upgrade now.  

Personally on my computers with integrated ATI graphics, I have just burned the alternate install cd and used them to upgrade, to save on bandwith for multiple computers.  I was unsuccessful doing clean installs on any of my systems with integrated ATI video cards, though the one with an AGP ATI installed beautifully.

Regardless of which method you use, please make sure to back up all of your files, "just in case" your upgrade goes south and you have to reinstall.

Good luck!
~Lynda

---

### Post by Pumalite on 2007-11-02
A very good advise.

---

### Post by ChopperX on 2007-11-02
did it using update manager and got these errors

Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/binary-i386/Packages.gz](http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/source/Sources.gz](http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.beryl-project.org/dists/gutsy/main/binary-i386/Packages.gz](http://ubuntu.beryl-project.org/dists/gutsy/main/binary-i386/Packages.gz) 404 Not Found [IP: 195.114.19.35 80]
Failed to fetch [http://ubuntu.beryl-project.org/dists/gutsy/main/source/Sources.gz](http://ubuntu.beryl-project.org/dists/gutsy/main/source/Sources.gz) 404 Not Found [IP: 195.114.19.35 80]

---

### Post by Maestro23 on 2007-11-02
> **ChopperX said:**
> did it using update manager and got these errors

Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/binary-i386/Packages.gz](http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/source/Sources.gz](http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.beryl-project.org/dists/gutsy/main/binary-i386/Packages.gz](http://ubuntu.beryl-project.org/dists/gutsy/main/binary-i386/Packages.gz) 404 Not Found [IP: 195.114.19.35 80]
Failed to fetch [http://ubuntu.beryl-project.org/dists/gutsy/main/source/Sources.gz](http://ubuntu.beryl-project.org/dists/gutsy/main/source/Sources.gz) 404 Not Found [IP: 195.114.19.35 80]

Edit your** /etc/apt/sources.list** and delete those lines. You can use gedit.

> gksudo gedit /etc/apt/sources.list

Make your changes and save.  Then:

> sudo apt-get update

sudo apt-get upgrade

---

### Post by ChopperX on 2007-11-03
Let me make sure this is right. I edit the sources list then in put in the get-update command and after that i put in the get-upgrade command. 

Is that it?

---

### Post by PmDematagoda on 2007-11-03
Yes, just disable the entries for [www.tuxfamily.org](www.tuxfamily.org) and [www.ubuntu.beryl-project.org](www.ubuntu.beryl-project.org) by putting # infront of them. Save the file and then try upgrading again.

---

### Post by Pumalite on 2007-11-03
Fix sources.list
sudo apt-get update
sudo apt-get upgrade

---

### Post by cwrann on 2007-11-03
Does anybody else recommend that on a clean install you should put the OS and swap on relatively small partitions and leave the rest of formatted space as storage.

 I do this so that when I do a clean install I don't need to worry about losing my data because the only things that are getting reformatted are the OS and swap partitions.

---

### Post by PmDematagoda on 2007-11-03
This is not recommended as you could run out of space for installing applications, but it is a good idea to keep your /home partition seperate.

---

### Post by ChopperX on 2007-11-03
so then it would look like this for each line #[http://download.tuxfamily.org/3v1deb...86/Packages.gz](http://download.tuxfamily.org/3v1deb...86/Packages.gz)

just want to be sure im not screwing anything up :)

---

### Post by PmDematagoda on 2007-11-03
Yes, just type # in front of them. And don't worry, any mistake you do in the sources.list file is easily fixable and won't cause any serious problems.

---

### Post by cwrann on 2007-11-03
> **PmDematagoda said:**
> This is not recommended as you could run out of space for installing applications, but it is a good idea to keep your /home partition seperate.

I guess it only appropriate if you have a larger sized HD.

---

### Post by PmDematagoda on 2007-11-03
Yes, it would not be very efficient unless you have a good sized HDD.

---

### Post by lyndaj70 on 2007-11-03
If you have a decent sized hard disk it's supposed to make it easier, but I have no experience (yet)  in that area.. I have just always backed up my docs in the /home directory and went on, though I am planning to move my /home partition to another drive to try it....

According to my research, if you allow 7-10 GB hard disk space for /  then you should have enough room to grow for a bit.... I have tons of programs and stuff on mine with lots of educational stuff for my youngest, so I'm personally at the 10 GB limit right now, but I don't think the average user is going to install all the extra games and stuff.  If you think that you are, then just add  more space when you are paritioning. 

On this desktop, I have Vista on an 80GB drive and Ubuntu on a 30 GB drive.  I'm personally planning on wiping Vista, moving /home to that hard disk, so that we'll have plenty of room to grow.  It just depends upon how much space you have to spare....

Good luck!
~L

---

