---
title: "Help, no gui or desktop after upgrade from 16.04 to 18.04"
date: 2020-11-25
forum: Installation &amp; Upgrades
---

### Post by worldwidejoe on 2020-11-25
I just upgraded from 16.04 to 18.04, cannot get a desktop or gui, cannot access home directory.

Upon rebooting I entered my password to decrypt my home directory,  then I am logged in at the terminal in my home directory. The only thing  in my home directory is:
 Access-Your-Private-Data.desktop README.txt .cache .ecryptfs .Private README.txt

 I am unable to start xserver, it resulted in various errors and does not start.

 I also cannot update, running sudo apt update returns errors:
```
 Err:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease Could not resolve 'us.archive.ubuntu.com'
 Err:2 http://archive.canonical.com/ubuntu bionic InRelease Could not resolve 'us.archive.canonical.com'
 Err:3 http://archive.canonical.com/ubuntu bionic-updates Inrelease Could not resolve 'us.archive.ubuntu.com'
 Err:4 http://archive.canonical.com/ubuntu bionic-backports InRelease Could not resolve 'us.archive.ubuntu.com'
 Err:5 http://archive.canonical.com/ubuntu bionic-security InRelease Could not resolve 'us.archive.ubuntu.com'
```


 Then it says: ```
4 packaged can be upgraded: Some index files failed to download. They have been ignored or old ones used instead.
 apt list --upgradeable Listing... Done

 gnome-session-bin/bionic-updates 3.28.1-0ubuntu3 amd64 [upgradable from: 3.18.1.2-1ubuntu1.16.04.21 
gnome-session-common/bionic-updates,bionic-updates 3.28.1-0ubuntu3 all [upgradable fro: 3.18.1.2-1ubuntu1.16.04.21 
qtchooser/bionic 64-ga1b6736-5 amd64 [upgradable from: 52-gae5eeef-2build1~gcc5.2] 
ubuntu-sesson/bionic-updates 3.28.1-0ubuntu3 all [upgradable from: 3.18.1.2-1ubuntu1.16.04.21

```

 Is it unable to update because my home directory is encrypted/locked in some way?  I'm not sure how to update those from the terminal yet, or if that's  even the next step..  Pretty far out of my knowledge zone here, thank  you for any help in advance!

---

### Post by ActionParsnip on 2020-11-26
The default is to not encrypt home. If you selected this then you know it is encrypted.
Can you ping 8.8.8.8 in the terminal?

---

### Post by CelticWarrior on 2020-11-26
Due to the huge change from Unity (16.04) to Gnome (18.04), an online upgrade was not recommended at the time and still isn't but most of times it worked without major hiccups. However, things change a lot if the 16.04 installation has encrypted home, a feature that was later removed due to safety concerns. Newer releases had the options of no encryption or full disk encryption only.

Knowing the above I would never try what you did in a 16.04 system with encrypted home. I would ONLY install 18.04 from scratch (with or without encryption) and then retrieve the backup from 16.04.

[https://askubuntu.com/a/743110](https://askubuntu.com/a/743110)

---

### Post by worldwidejoe on 2020-11-26
Thank you for the reply's folks It's a 16.04 install on a Samsung solid state drive, encrypted home directory. 

All I did was follow the upgrade dialog box during a normal software upgrade to do the distro upgrade that if offered me, 16.04 to 18.04. Why on earth is this offered if it doesn't work? ( obviously not the fault of people responding to my post here, I understand) This has completely locked me out of my computer..

I can ping 1.1.1.1 so I have internet connection. Something is very wrong with my repos/ppa's obviously and not letting me even install anything. Maybe because the home directory is encrypted I can't even make changes to the ppa/repos in the terminal..?

I put ubuntu 20.04 on a separate hard drive, plugged the 16.04 hard drive in to try and pull data from it directly. From the 20.04 deskop using Disks I can see my encrypted partition. and I can see the encrypted partition in my file manager with its locked icon. I installed ecryptfs, but opening the encrypted partition requires mounting the encrypted partition to access it. I am unable to mount the encrypted partition. When I attempt to, it asks me for the password, I enter it, and then it shows another partition on the drive in Disks, so it is accepting the password, but then the encrypted drive disappears from my file manager completely. If I try to run ecryptfs without the partiton being mounted, I get: 

user@computer:~$ sudo ecryptfs-recover-private
INFO: Searching for encrypted private directories (this might take a while)...
find: &#8216;/run/user/1000/gvfs&#8217;: Permission denied

I loaded up a new 16.04 on another hard drive and tried to directly pull the data from the encrypted drive/partition using that, when trying to mount it using Disks, same result as on 20.04, but if I try to mount it from the file browser (nautilus I think) a dialog box says 'The unlocked device does not have a recognizable flie system on it.


Why am I unable to mount the drive to use ecryptfs? Thank you for any help.

---

