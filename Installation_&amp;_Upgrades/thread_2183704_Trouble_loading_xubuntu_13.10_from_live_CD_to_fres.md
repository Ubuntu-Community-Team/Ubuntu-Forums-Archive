---
title: "Trouble loading xubuntu 13.10 from live CD to freshly formatted hard drive"
date: 2013-10-25
forum: Installation &amp; Upgrades
---

### Post by HumN on 2013-10-25
Okay, so I had a hard drive failure on one of my computers, an HP Compaq nc6000. I got a replacement hard drive that was freshly formatted but has no OS on it at all. I installed the replacement drive and of course got a "non-system disk" error when I turned the machine on, so I placed an xubuntu 13.10 live CD (DVD, actually) in the optical drive and powered the machine up to get another error, saying the disc is unbootable because it lacks pae. I tried it with a Linux Mint disc and got a screen with the LM logo and a 10-second countdown to an auto-boot, but then once the countdown was completed, it just sat there with the LM logo and no further activity. Is there an interim step or some other trick that I need to perform? Given my druthers, I would really prefer to load xubuntu on the machine.

---

### Post by fantab on 2013-10-26
Do you have a 64bit processor or 32bit? PAE is what 32bit uses to identify and use more than 4GB RAM.
How much RAM do you have?
Did you replace the HDD yourself?

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by HumN on 2013-10-26
I'm pretty sure it's a 32bit processor. It's a Centrino. I've got 2GB of RAM, which is the max that machine will take. I did install the hard drive myself.

> **fantab said:**
> Do you have a 64bit processor or 32bit? PAE is what 32bit uses to identify and use more than 4GB RAM.
How much RAM do you have?
Did you replace the HDD yourself?

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by fantab on 2013-10-26
Perhaps your .iso didn't burn properly to the DVD/USB. Do a [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") on the downloaded Xubuntu.iso and BURN it again.

---

### Post by HumN on 2013-11-04
Okay, I haven't yet gotten Xubuntu 13.10 installed, but I finally found an old installation disc the machine would accept--Ubuntu 11.10 i386. So that installation is finishing up now. It's kind of late, so I won't try to upgrade tonight, but at least the machine officially isn't dead. And that's progress. I am hoping now that the machine has an operating system, albeit an old one, on its hard drive, the upgrade process will be relatively smooth.

Live coverage here--the machine is now booting on its own from the new hard drive as I type. And success! The nc6000 has now been brought back to life!

I'll keep you posted as I attempt to upgrade to a supported OS.

---

### Post by fantab on 2013-11-05
Not Bad. Since 11.10 has reached its 'End Of Life' you wont get any updates for it. However, it is possible to upgrade it to the next ubuntu version which is 12.04 [supported upto 2017]. That should be good news.

I suggest you follow instructions [HERE]("https://help.ubuntu.com/community/EOLUpgrades").

12.04 CODENAME= precise
11.10 CODENAME= oneric

EDIT: If the above method doesn't work out then:
Try installing 12.04.3 32bit which is the latest version of 12.04, if that doesn't work, because of new hardware enablement stack can cause issues on older PC,
then download older version of 12.04 from [HERE]("http://old-releases.ubuntu.com/releases/precise/ubuntu-12.04-desktop-i386.iso") for regular download or download [TORRENT]("http://old-releases.ubuntu.com/releases/precise/ubuntu-12.04-desktop-i386.iso.torrent").

---

### Post by HumN on 2013-11-05
That's precisely what I did. Almost immediately upon installation, I received a warning that the OS had reached end of life and would not be updated, but instead of prompting me to upgrade, it directed me to a semi-informative Web site showing the life cycle for various versions of the OS. While mousing around before going to bed last night, I finally stumbled upon the Software Updater app and was prompted upgrade to 12.04. I didn't have to be asked twice, so I got the process started, went to sleep, and then finished the last couple of steps (removing obsolete files and restarting) when I woke up this morning. 

I'm thankful to have the machine running again, even if it has the annoying Unity interface. I much prefer Xubuntu and run it on my other Linux laptop. Someday when I'm really, really bored, I may decide to undertake the switch to Xubuntu. For now, I'm just thankful to have it up and running again.

> **fantab said:**
> Not Bad. Since 11.10 has reached its 'End Of Life' you wont get any updates for it. However, it is possible to upgrade it to the next ubuntu version which is 12.04 [supported upto 2017]. That should be good news.

I suggest you follow instructions [HERE]("https://help.ubuntu.com/community/EOLUpgrades").

12.04 CODENAME= precise
11.10 CODENAME= oneric

EDIT: If the above method doesn't work out then:
Try installing 12.04.3 32bit which is the latest version of 12.04, if that doesn't work, because of new hardware enablement stack can cause issues on older PC,
then download older version of 12.04 from [HERE]("http://old-releases.ubuntu.com/releases/precise/ubuntu-12.04-desktop-i386.iso") for regular download or download [TORRENT]("http://old-releases.ubuntu.com/releases/precise/ubuntu-12.04-desktop-i386.iso.torrent").

---

### Post by fantab on 2013-11-05
> **HumN said:**
> That's precisely what I did. Almost immediately upon installation, I received a warning that the OS had reached end of life and would not be updated, but instead of prompting me to upgrade, it directed me to a semi-informative Web site showing the life cycle for various versions of the OS. While mousing around before going to bed last night, I finally stumbled upon the Software Updater app and was prompted upgrade to 12.04. I didn't have to be asked twice, so I got the process started, went to sleep, and then finished the last couple of steps (removing obsolete files and restarting) when I woke up this morning. 

I'm thankful to have the machine running again, even if it has the annoying Unity interface. I much prefer Xubuntu and run it on my other Linux laptop. Someday when I'm really, really bored, I may decide to undertake the switch to Xubuntu. For now, I'm just thankful to have it up and running again.

So did your upgrade to 12.04 went well and successful?
Installing Xubuntu on your current setup is as simple as:
```
sudo apt-get install xubuntu-desktop
```
This will give the complete Xubuntu desktop.

OR

```
sudo apt-get install xfce4
```
This will only install the XFCE4, minus all the xfce-goodies.

Another option will be to install Cinnamon... whose interface is similar to older gnome2 and xfce.

You can change from Unity to Xfce (or any other desktop) from the Ubuntu login dialog. You will have to click on the Ubuntu circle in the login box to select the xfce session.

---

### Post by HumN on 2013-11-06
Yes, the 12.04 install went without a hitch. I'm actually typing on that machine right now. Thanks for the tip on installing Xubuntu. I'll give that a try. The command line is always a bit mysterious to me.

UPDATE: I just tried 'sudo apt-get install xubuntu-desktop' and it seemed to install, but now when I restart the computer, I get the Xubuntu splash screen but it still boots into Unity.

---

### Post by fantab on 2013-11-06
You have to choose the session from Login Screen, where you type your password, Do you see a 'white gear-circle' in the login box? Well, click on it and select xubuntu.

---

### Post by HumN on 2013-11-06
Thanks. I found it. That's what I get for messing with this stuff when I'm tired. I have things set up right now so it goes directly to the (unity) desktop without entering a password, so I didn't see that dialog box until I logged out and back in. Guess I need to make an adjustment there. Is there a way to set the system to boot into Xubuntu by default? Thanks again for all your help!

---

### Post by fantab on 2013-11-06
You have to edit the lightdm configuration to set up Xubuntu as default. If I remember it correctly:

```
gksu gedit /etc/lightdm/lightdm.conf.d/10-ubuntu.conf
```

Gedit (Text-editor) will open the file 10-ubuntu.conf as root.. the content of the file will be something like:

> [SeatDefaults]
user-session=ubuntu

just change '=ubuntu' to '=xubuntu' and save the file. Restart.

---

### Post by HumN on 2013-11-08
Okay, I got it, but I'm not sure how I did it. The procedure you outlined above yielded only a blank document with that filename. I then opened the ubuntu.conf file directly in a text editor and made the necessary edit, but it wouldn' save, presumably because I wasn't logged in as root. Mildy frustrated, I started mousing around in the Settings Manager to at least come up with a way to automatically bring up the dialog box to manually choose Xubuntu at login. Under the General tab in the Session and Startup control panel, I checked the box next to "Display Chooser on Login", thinking that might do the trick. Along about that time, the Upgrade Manager informs me I have updates that need installing, which amount to an update of the Linux kernel itself. After that process was complete, I was prompted to restart, which I did, and instead of displaying the chooser, it booted directly into Xubuntu. LIke I said, I don't know how I did it, but I'll take it nonetheless.

---

### Post by fantab on 2013-11-08
I don't have 12.04 to check where, in which file it has 
> [SeatDefaults]
user-session=ubuntu

You can check in /etc/lightdm/lightdm.conf.d folder and check files to which file it is...

But since you are booting to XUbuntu, it may not be necessary. Yet you MUST have an option to switch between Ubuntu and Xubuntu sessions.

Perhaps someone with 12.04 can explain better.

Anyway, I am glad you are booting to Xubuntu... enjoy.

---

