---
title: "How can I burn my present Ubuntu on DVD/CD?"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by Tambooosh on 2010-08-05
Hey people, ):P what's up!
in short, recently I've started to use Ubuntu operating system.. the last version 10.04 LTS

I downloaded the .ISO image file from the site and burnt a CD to use it back, but I was wondering now after I installed my Ubuntu and made all updates and upgrades to the applications and added all packages that might be useful for me, can or can't I burn the present system with all the add-ons that I've added on DVD/CD??
instead of using the old CD that I made which is free of all packages and necessary programs.. :lolflag:
or at least, is not there downloadable files from the internet that allow me to install the packages and the programs offline!! considering that I might not be able to have an internet connection.. ;)

Thanks all :) :p
Peace

---

### Post by lemming465 on 2010-08-07
The short answer is that yes, there are ways of migrating a customized install to a new system, even if you are offline.  Which ones you use depends on your circumstances.

One option: backup and restore.  If you restore a complete system you might have to reinstall the boot loader (using chroot, grub-install, and update-grub) to get it working.

If you just want to keep track of packages you have installed, run *dpkg --get-selections* on the source system and *apt-get update; dpkg --set-selections; apt-get install* on the destination system.

You can also move .deb package files between systems and install them by hand (ok, probably scripted) with *dpkg -i*.

If you want to convert a live disk install into a live DVD, there are 3rd party tools like remastersys.

These are only a few of the options.

---

### Post by Tambooosh on 2010-08-09
Thanks alot lemming465 :) your answer is too shortened for me my friend, if you can explode it more.. I'm a beginner with Ubuntu.. so if you can please, explaine me how I can burn my present Ubuntu with all its conatins onto DVD/CD.. I apprciate it :)

---

### Post by ezsit on 2010-08-09
There is a program called remastersys that specifically does just what you ask. Look on their website, read the documentation, and follow the steps. Its relatively easy if you read, pay attention to what you are doing, and follow the steps correctly.

[http://www.remastersys.com/](http://www.remastersys.com/)

---

### Post by Tambooosh on 2010-08-10
The site [http://www.remastersys.com/](http://www.remastersys.com/) is refusing to be opened, dunno why!
I'm a newbie with Ubuntu, so please if you can explain it more or gimme more options I'll appreciate it..


Thanks

---

### Post by lemming465 on 2010-08-11
The site opens for me.  Do other sites open for you?  The three most typical reasons for inability to reach specific web sites are
1) you don't have DNS resolution
2) you don't have a network connection
3) the internet is broken (ISP problem, or site offline)

---

### Post by Tambooosh on 2010-08-17
please, when I'm trying to get the program remastersys it shows me a problem while getting the source of the program.. can't it be done manually? I mean downloading and installing the program just like in Windows..

Thanks

---

### Post by Elim_Garak on 2010-08-17
> **Tambooosh said:**
> 
instead of using the old CD that I made which is free of all packages and necessary programs.

This is what I do:

```
cd /
sudo tar cvpfz backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media /
```

It may give you an error message upon completing, but rest assured, it will work.  It's particularly important to use the exclude tag on the backup file, or you will wind up in an endless tar loop.  You can add other directories to be excluded.  With a basic install and a few of my favorite packages, I have no problems fitting the tarball on a DVD.

To restore:

```
cd /
sudo tar xvpfz backup.tgz -C /
```

Just ensure that you are pointing to the correct directory (i.e. the CD drive or a second hard drive) where the backup file is located.  After that, you can recreate any of the excluded directories.  You will likely have to adjust your fstab and grub list because the UUIDs will likely have changed.

I've used this method several times, particularly if I want to change something major and I'm not sure I'll be satisfied with the result.  It's a lot easier to restore it that way than trying to undo a bunch of packages, or, as you pointed out, reinstalling fresh, downloading new stuff, and putting all the old settings back.

---

### Post by lemming465 on 2010-08-17
> ... when I'm trying to get the program remastersys it shows me a problem while getting the source of the program.. can't it be done manually?
What are you specifically running, and what error message are you getting?  The easiest way to install it is probably:```

sudo -i
cat <<EOF > /etc/apt/sources.list.d/remastersys.list
# Remastersys
deb http://www.geekconnection.org/remastersys/repository karmic/
EOF
aptitude update
aptitude install remastersys
```
That should not be trying to pull any source .deb packages.
> [I mean downloading and installing the program just like in Windows.
The Ubuntu equivalent of downloading a windows .exe file and running it is downloading a .deb package archive file and running *sudo dpkg -i* against it.  If the vendor offers repository support, it's usually much easier to use that, particuarly since the repository version will track updates, which the direct install with dpkg will not.

---

### Post by ezsit on 2010-08-17
I believe that remastersys has a sourceforge account and repository. You can search sourceforge for remastersys and download the .deb file. 

Once downloaded, open the .deb file with Gdebi (right-click on the .deb file and choose to open with Gdebi installer - or something similarly worded entry). It will ask for your password and tell you there are many dependencies, so be sure to be online when doing this. Accept all dependencies and install the .deb file. 

Reboot and look in your System Menu under Admin and you should see an entry for Remastersys Backup. It is a straight-forward menu style app. Read all the info screens as you use the program, the info text will answer most common questions, like where the .iso file is placed upon completion.

Dist mode backup creates a live-cd or live-dvd that contains all the software you've installed or changed, but none of the user data from your /home directory. The Dist mode is great for customizing an installation and installing that same exact system on multiple computers.

The Backup mode will copy your /home folder contents, username and login. Make sure your /home directory does not have too much data stored, all this data will make the .ISO bigger (4 GB limit - MAX) and the more stuff you have in /home will require more RAM to boot the system. Best advice is to backup your static data (photos, music, files, etc) to some external device, flash, or DVD first and delete it from your /home folder before running the backup. Once you have backed up the system and restored it to another computer, copy your data back from its own backup. Keep data and system backed up separately and you will never go wrong.

---

