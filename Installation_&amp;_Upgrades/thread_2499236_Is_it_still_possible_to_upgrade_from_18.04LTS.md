---
title: "Is it still possible to upgrade from 18.04LTS?"
date: 2024-07-19
forum: Installation &amp; Upgrades
---

### Post by Engineeringtech on 2024-07-19
I've been dealing with a host of health problems the last year, and because of that, never proceeded with any of the updates from 18.04LTS.   Just a few weeks back I was getting notices offering upgrades to 20..??LTS.    Or was it 22.??LTS?   Now I get no upgrade notifications and when I open up the software updater, I see the message, "Failed to Download Repository Information".   Does this mean I no longer have any chance of upgrading my machine?   

I'm a novice user, 69 years old and in poor health.  I'm just looking to update my machine so I can get on the internet safely.  I am not interested in spending the next six months learning all about the intricacies of Ubuntu or the command line syntax..   It's a neat operating system, and I appreciate all the effort people have made creating it.  But frankly, I have my doubts that I will live long enough to get educated... 

Is there a place where I can download an ISO image for 20.??LTS or 22.??LTS?  And will it allow an upgrade, instead of a format and install that will destroy my data and the few applications I have added (mostly Windows programs running under Wine)?  I'm ashamed to admit I don't even have a good way to backup my computer.  I'd like my relatives to be able to access my files should I pass.

---

### Post by grahammechanical on 2024-07-19
When a Ubuntu version reaches end of life support its software repositories are moved to a different internet address. That is why you are getting the "Failed to Download Repository Information" There is a file that is called <sources.list> that has the addresses of the repositories. That file still has the old 18.04 repository addresses.

As you do not want to mess with the command line it is not possible to help you any more than I have already. Yes, we can download an ISO image of Ubuntu 20.04 LTS, 22.04 LTS and 24.04 LTS, but we cannot upgrade from it. We can only re-install from these ISO images. It should be possible to install to the existing partitions without marking the partition to be formatted. That should leave the personal files in the /home/username folder untouched. 

It would also be possible to run the Ubuntu Try Ubuntu mode of the installer and access the files on the hard disk and copy them to another place. As you can tell, your options are getting complicated and complicated is not what you want.

By the way I am 76 years old and 14 years ago I had a serious heart operation. So, I understand that when you are ill - you are ill. But I have also been using Ubuntu since 2007 and visiting Ubuntu forums even before I first installed Ubuntu, So, I have learnt one or two things.

I cannot decided which is the easiest option for you. This link will explain how to update the sources.list file to the present location of the 18.04 repositories. That will allow you to update 18.04 and then do an online upgrade to 20.04.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

You decide which option you wish to go for and we will try to help get the job done.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

P.S. I have just thought of another option. Does you machine have a USB port? Purchase a pre-formatted USB memory stick and use 18.04 to copy your personal data to the USB memory stick. If the stick is formatted with a Windows format then your relatives with Windows machines will be able to access what you have put on the USB stick.

Regards

---

### Post by Engineeringtech on 2024-07-19
> **grahammechanical said:**
> When a Ubuntu version reaches end of  life support its software repositories are moved to a different internet  address. 
As you do not want to mess with the command line it is not possible to help you any more than I have already. 

How have you "already" helped me?   I already knew the  repositories have been moved.    I never said I objected to entering  some commands at a prompt.   But I prefer not to spend days or weeks  learning some arcane process about how Linux upgrading works.  Right now in particular my free time is in short supply.    I'm only  interesting in using my PC for browsing and writing documents.   I followed the link you provided with the instructions  about editing the sources file.  It is NOT self explanatory to a novice like me.    This seems to be the case every time I'm force to "look under the hood" of Linux.   The mechanic demands that I learn all about the operation of the motor before helping me.   He can't just say, "you flooded it" and tell me how to start the motor.  It feels like an initiation to a fraternity.  

Sorry about your heart problem.  But rather than brag about your  experience with Linux, and belittle my lack of knowledge, why don't you  actually TRY and help me upgrade?   I would appreciate it, and pray for you.

---

### Post by Dennis N on 2024-07-19
>  Just a few weeks back I was getting notices offering upgrades to 20..??LTS. Or was it 22.??LTS? Now I get no upgrade notifications and when I open up the software updater, I see the message, "Failed to Download Repository Information". Does this mean I no longer have any chance of upgrading my machine? 

It seems to be possible, but maybe only in some cases (see below). I do get the upgrade notice to 20.04.5 LTS with Software Updater. (see screenshot, from 18.04 today, Jul 19).
Also, do-release-upgrade also tells me that this upgrade is available:
```
dmn@Sydney:~$ do-release-upgrade -c
Checking for a new Ubuntu release
New release '20.04.5 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

```
By saying some cases, I wonder if this only works when the system is enrolled in Ubunto Pro. Mine is enrolled and gets updates to the OS. 
You might see if you can enroll your 18.04 in Ubuntu Pro, let it upgrade the system, and then see if the upgrade to 20.04 is offered.

If you manage to enroll in Pro, security updates are then provided until 2028, so you would not need to upgrade to 20.04.5 if you don't care to.

---

### Post by yancek on 2024-07-20
To download Ubuntu go to their site.  For a specific release, do an online search wit the name of the release version (24.04, 22.04).  Links to both below.

 [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

[https://releases.ubuntu.com/jammy/](https://releases.ubuntu.com/jammy/)

If the instructions for changing the sources.list seem to complicated, you could install a newer version over the older version and if you already have a separate /home or data partition, selecl to use it during the install but do NOT format it.  If your hard drive is large enough, you could create another partition or partitions for a new install of Ubuntu.  You could post the output of either command below and someone could make a suggestions.

```
sudo parted -l
sudo fdisk -l
```

---

### Post by Tadaen_Sylvermane on 2024-07-20
It is possible to upgrade from that all the way through assuming the old-releases repositories are still valid. This is my sources.list that I upgraded via the Debian method from jammy directly to noble before it was available for standard upgrade.

```
#deb http://us.archive.ubuntu.com/ubuntu jammy main restricted universe multiverse
#deb http://us.archive.ubuntu.com/ubuntu jammy-security main restricted universe multiverse
#deb http://security.ubuntu.com/ubuntu/ jammy-security main restricted universe multiverse 
#deb http://us.archive.ubuntu.com/ubuntu jammy-updates main restricted universe multiverse

#deb http://old-releases.ubuntu.com/ubuntu kinetic main restricted universe multiverse
#deb http://old-releases.ubuntu.com/ubuntu kinetic-security main restricted universe multiverse
#deb http://old-releases.ubuntu.com/ubuntu kinetic-updates main restricted universe multiverse

#deb http://us.archive.ubuntu.com/ubuntu lunar main restricted universe multiverse
#deb http://us.archive.ubuntu.com/ubuntu lunar-security main restricted universe multiverse
#deb http://security.ubuntu.com/ubuntu/ lunar-security main restricted universe multiverse
#deb http://us.archive.ubuntu.com/ubuntu lunar-updates main restricted universe multiverse

#deb http://us.archive.ubuntu.com/ubuntu mantic main restricted universe multiverse
#deb http://us.archive.ubuntu.com/ubuntu mantic-security main restricted universe multiverse
#deb http://security.ubuntu.com/ubuntu/ mantic-security main restricted universe multiverse
#deb http://us.archive.ubuntu.com/ubuntu mantic-updates main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu noble main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu noble-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ noble-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu noble-updates main restricted universe multiverse
```

Notice the Kinetic lines. Assuming 18.10, 19.04, 19.10 are still online in that location you can upgrade one step at a time although there are no guarantees with this method as it is not supported by Ubuntu officially. The process is simple and not hard to understand.

Make sure current system fully updated and upgraded to whatever is available.

```
sudo apt update && sudo apt upgrade && sudo apt full-upgrade && sudo apt clean
```

Then comment out the current 18.04 repos in this case, and uncomment 18.10. Then the same command as above. Repeat in series until you hit 24.04, or 20.04, or 22.04 depending on your goal. 22.04 would be the minimum as 20.04 will stop being supported next year unless you enable Ubuntu Pro.
Again there are no guarantees with this method. In my case I upgraded a fresh chroot installation from Jammy > Noble one step at a time and have no problems. A fully installed system may cause some issues. Make sure to backup before doing it. In the future you should always try to keep on the current LTS before it goes offline / EOL. Any third party repositories or PPA's will likely cause issues with this method. Repair or fix any issues as you go, before moving to the next upgrade process.

> But I prefer not to spend days or weeks  learning some arcane process about how Linux upgrading works.

There is no arcane process. Rather the process isn't arcane unless you don't upgrade in time. They won't keep the easy mode upgrade around forever. So you put yourself in this situation. Your computer told you to upgrade, you chose not to. Happens every day. Your frustrations are misplaced. Don't be pissed at people here trying to help you. In the future keep up to date and you won't have problems like this again. Many folks have this idea that they can install it once and never touch it again. To a degree true but like anything it requires maintenance. Nothing can be left alone to it's own devices, at least when it's on the internet.

---

### Post by aljames2 on 2024-07-20
ditto all.  As mentioned throughout.  Just doubling down on the "backup your stuff first".  Then you have the peace of mind if it blows up, a fresh install is quick & simple.
Probably your /home directory is all you would need, unless you also have some custom configs, scripts, or other that you made yourself in some system location like /etc /usr/local /opt  etc.

Let us know if you need help backing up your /home directory.

I think we all would like to see you succeeed.  Be well

---

### Post by guiverc on 2024-07-20
I'll respond, but apologies if this detail is already understood, or repetitive.

Yes you can *release-upgrade* UNTIL the release you want to upgrade is itself EOL, for Ubuntu 18.04 LTS, the upgrade path is to 20.04 which is still OPEN thus you can upgrade.

Ubuntu 18.04 LTS is EOL or EOSS depending on *architecture*, which I didn't see mentioned.

EOSS releases may NOT require you to use [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) so do NOT make changes unless necessary.  If using a country mirror, you may need to switch manually to the main archive or another mirror though (*that handles EOSS*).

However not all MIRRORS may provide support; so some of your sources may no longer exist, or have been moved, so correct these manually (*if corrections are required*).

Other complications can also exist; eg. if your system has *outdated* security certificates, you'll need to fix those yourself, or if using ESM just apply security fixes normally and the issue will resolve.

EOL = End of Life; eg. 18.04 *i386* and *armhf* are now EOL
EOSS = End of Standard Support; eg. *amd64* has ESM or extended support

FYI:   I'm a desktop user, and if a *release goes EOL or EOSS, *I often just *non-destructively re-install* a *supported* release, as it allows me to *jump* to whatever release I want to, but there can be complications with this method (*esp. if you're using lots of 3rd party software*), and its not intended for Server apps/installs. I also tend to use this method if I lack disk space, or am just in a hurry; as this is actually rather fast. It's an option anyway (*if you're using Desktop*).

---

### Post by Engineeringtech on 2024-07-26
Thank you both.  I've been wanting and  trying to reply, but have been sick and my computer has been frozen.  Type a letter and it takes 3 minutes to appear on screen. Click on a button or link and it takes multiple clicks and multiple minutes for the computer to act.  This is going on at the desktop, and all applications.   I don't know how to fix it.   Another reason why I want to upgrade.   I will see if I can follow your code and do the update.   I don't have Ubuntu Pro.  Can you tell me what it is and how to update it?

---

### Post by Engineeringtech on 2024-07-26
Thanks, but, some of your instructions are over my head.    I feel so stupid sometimes.  69 years old an in poor health.  I just want my computer to work for my family should I become hospitalized.

---

### Post by Dennis N on 2024-07-26
>  I don't have Ubuntu Pro. Can you tell me what it is and how to update it? 
You can subscribe here:
[https://ubuntu.com/pro/subscribe](https://ubuntu.com/pro/subscribe)

When you click "Buy" at the bottom (I can't check what happens, since I've already did this years ago), but I believe that you get a token (a string of characters to copy), and the page tells you how to use it to enroll your machine.

Once it's enrolled, do an update in the normal way with Software Updater. After everything is up-to-date, you get the offer to upgrade to 20.04. See attached screenshot from today, Jul 26.

---

### Post by Engineeringtech on 2024-10-10
I've been dealing with complications from cornea surgery, and the problems I mentioned earlier (freezes, slowdowns, etc. )   It is hard to post questions and do anything when the letters I type appear on the screen 3 or more minutes after I hit the key.    Which is why I wanted the upgrade in the first place.   

Anyway, I managed to figure out how to get the subscription to Ubuntu Pro.  And since doing that, I now occasionally get offers to upgrade to 20.04.  But the upgrades always fail, either telling me the repository is missing, or the following message:   
Maybe you can make sense of it.



                        W:GPG error: [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F, E:The repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' is not signed.

---

### Post by yancek on 2024-10-10
If you do not use wine then commenting out that entry or any entry relating to wine in your /etc/apt/sources.list file by placing a # at the beginning of those lines would eliminate that problem.  If you use wine a lot, not much point in doing this.

How old is your hardware?  If it is 10 plus years old, trying to install and use current Ubuntu releases may not help.  Backing up your data and installing to the same partitions WITHOUT formatting them would also work.  If an older computer, you might try Xubuntu, Lubuntu or Bodhi or a non-Ubuntu like MX or AntiX Linux.

---

### Post by Engineeringtech on 2024-10-16
Yancek,

Sorry for the delay in replying.  As I said earlier, I have health problems and also my computer keeps slowing to a crawl or freezing requiring a hard shutdown.  Before seeing your reply, I uninstalled wine.   There is no entry in the sources.list file to comment out.    I will try again to see if the computer will upgrade and get back to you.  The computer is about 8 years old by my estimation.

---

### Post by Engineeringtech on 2024-11-23
I have had seen several offers to update my system to Version 20.04.  Every time I tell it to proceed, it downloads most of the required files, excepting a problem with a couple "third party sources".  It tells me these can be fixed at a later date. Then it presents this error message:

**[COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., W:GPG error: [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F, E:The repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' is not signed.[/SIZE][/FONT][/COLOR]**

  

How do I fix this?

---

### Post by Norm24 on 2024-11-25
Remove the wine repo and try again.

---

### Post by yancek on 2024-11-25
I explained the way to eliminate that error above in post 13.  Go to your /etc/apt/sources.list file and the sources.list.d directory and comment out any entries relating to wine.
You might make a backup of these files before making the change.

The link below gives a very long and detailed explanation of updating 18.04 to 20.04 which is dated August, 2024.  Haven't used it so I have no idea if it will work.

[https://www.cyberciti.biz/faq/upgrade-ubuntu-18-04-to-20-04-lts-using-command-line/](https://www.cyberciti.biz/faq/upgrade-ubuntu-18-04-to-20-04-lts-using-command-line/)

Another thing you could to is to reinstall a newer version, 20.04, 22.04 or 24.04 and install to the same partition on which you currently have the filesystem.  The important thing if you do this is to select NOT TO FORMAT the partition.  If you have other partitions such as /home or /data do NOT FORMAT them either when you create the mount points.

---

### Post by Engineeringtech on 2024-12-02
> **Norm24 said:**
> Remove the wine repo and try again.

"Repo"?  I removed the wine weeks ago.

---

### Post by Engineeringtech on 2024-12-02
> **yancek said:**
> I ...Go to your /etc/apt/sources.list file and the sources.list.d directory and comment out any entries relating to wine.......Another thing you could to is to reinstall a newer version, 20.04, 22.04 or 24.04 and install to the same partition on which you currently have the filesystem.  The important thing if you do this is to select NOT TO FORMAT the partition.  If you have other partitions such as /home or /data do NOT FORMAT them either when you create the mount points.

I commented out entries relating to Wine in the sources.list file back in October.  There is a file called winehq-bionic.sources in the sources.list.d directory.  It is read only and contains a web address for wine builds.  Should I delete this file, or just remove the web address.  HOW if it is read only?

The link and instructions you pointed me to before describes a very involved process for SERVERS.  I have a desktop, not a server.  And not sure if I can handle the detailed list of instructions.

---

### Post by yancek on 2024-12-03
>  "Repo"?  I removed the wine weeks ago. 				

Yet in post 15 from one week ago you again report a message regarding problems with 'wine'?

You can either delete  the file winehq-bionic.sources in your sources.list.d directory or comment out the line in it.  I doubt it will matter as your problem is due to the fact that your desktop version of Ubuntu reached end of life in April, 2024 and you should have updated before that.  The simplest solution is to reinstall to the same partitions on which you currently have 18.04.  If you have data you want to keep then do NOT format the partition.

If your hardware is old, you may want a lighter version of Ubuntu such as Lubuntu, Xubuntu, Bodhi...

---

### Post by Engineeringtech on 2024-12-04
> **yancek said:**
> Yet in post 15 from one week ago you again report a message regarding problems with 'wine'?

You can either delete  the file winehq-bionic.sources in your sources.list.d directory or comment out the line in it.  I doubt it will matter as your problem is due to the fact that your desktop version of Ubuntu reached end of life in April, 2024 and you should have updated before that.  The simplest solution is to reinstall to the same partitions on which you currently have 18.04.  If you have data you want to keep then do NOT format the partition.

If your hardware is old, you may want a lighter version of Ubuntu such as Lubuntu, Xubuntu, Bodhi...


YES.  Even though I uninstalled all apps with the name "Wine", I continued to get the error message I reported a week ago.   

I was, and still am dealing with health problems and never got the chance to update.

How / where do I get a DVD copy of the installer for the latest LTS version?   Will the installer know on which partition 18.04 is installed, and whether I want it partitioned?   Isn't my data (on the desktop, documents folder, etc.) in the same partition?  Should I move it to an external drive?  (I don't currently have a drive to use.

---

### Post by yancek on 2024-12-04
I've never used wine so can't speak specifically about it but uninstalling the apps is not the same as commenting out or deleting the entries in the /etc/apt/soures.list file or the sources.list.d directory.

Better to make backup to a second drive.  Making a backup to the same drive is just making a copy, not a backup.  The purpose is if the drive fails so having two copies of data files on a failed drive won't help.

I'm not sure the latest Ubuntu will work for you, it depends upon your hardware.  The link below gives the system requirements for the latest Ubuntu.  If they are too much for your hardware you might try a lighter version such as Lubuntu, Xubuntu or Bodhi.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

You can download Ubuntu at their site at the link below.

[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

> Will the installer know on which partition 18.04 is installed, and whether I want it partitioned?   I 

The installer will see your partitions but it isn't telepathic so it won't know how you want it installed/partitioned.  I looked back through your posts and don't see any information on your drives or partitions so I don't know if you have separate /home or data partitions.  When you boot the Ubuntu installer, you should be able to use a terminal to run sudo fdisk -l or sudo parted -l to see partitions/drives.  Or if you prefer graphical, you can see the same information with sudo gparted.  If you do this and don't understand the output you can post it here and I expect someone will be able to point you in the right direction.

---

### Post by Engineeringtech on 2024-12-10
I appreciate your help.     

As I said before, I commented out the entries in the sources.list file referring to Wine.  But I have a FILE in the sources.list.d directory that I don't know how to delete.   I'd like to delete it and try to update, but it tells me I am not owner.  I'm not very good at using the terminal.  How do I log on as owner and delete the file?  Not very good at navigating from the terminal.   

I'm sorry this has dragged on for so long.  However as I stated before, I have health problems and rarely get on my computer.  I never wanted to dig into the innards of Linux.  I just wanted to use it, like so many people use Windows.

---

### Post by Tadaen_Sylvermane on 2024-12-10
In your applications you should have a Software and Updates program. Open that, then one of the tabs allows you to check  / uncheck source files. Go there, find the offending wine repository and uncheck it. It will very likely ask for your sudo password.

If the file is disabled you can ignore it and leave it there, won't hurt anything. Later on if you feel up to it you can remove it properly.

---

### Post by Norm24 on 2024-12-11
> **Engineeringtech said:**
> I appreciate your help.     

As I said before, I commented out the entries in the sources.list file referring to Wine.  But I have a FILE in the sources.list.d directory that I don't know how to delete.   I'd like to delete it and try to update, but it tells me I am not owner.  I'm not very good at using the terminal.  How do I log on as owner and delete the file?  Not very good at navigating from the terminal.

```
*your file manager* admin:/

sudo *your file manager*
```
Either command will give you root access to your files.Just replace *your file manager* with whatever you use,in my case it would be Caja.

Having root access can potentially be very dangerous so be aware and BE CAREFUL what you do.You can navigate to the specific file you want to delete but again deleting flles as root can have unintended consequences!

---

### Post by yancek on 2024-12-11
'm not sure what the purpose of post 25 is but in post  23, you stated "I have a FILE in the sources.list.d directory that I don't know how to delete".  That file is root owned so you need sudo to remove it.  You can open a terminal and change to that directory:  cd /etc/apt/sources.list.d  the do sudo rm nameoffile (enter the actual name of the wine file you have.

---

### Post by Engineeringtech on 2024-12-12
Thank you.  I checked the Software and Updates Program.  No source files were selected.   I then finally figured out how to use the terminal to browse to the \etc\apt\souces.list.d directory and delete the file named wine-*-*.list.

Now if I could figure out how to force the update to V20, I could see if it works.    Previously I waited for the OS to offer me the update.

---

### Post by yancek on 2024-12-13
>  \etc\apt\souces.list.d directory 

A problem with the above is that you have it backwards and that you are using backward slashes when you should be using forward slashes.  You can get to that directory from anywhere in the system with the command below;

```
cd /etc/apt/sources.list.d
```

You are having problems because you waited too long to upgrade 18.04.  Support for it ended well over a year ago which means that when you try to do an update/upgrade from either the terminal or software manager, that software will be looking for a specific location, an IP address and the files needed are no longer there.  When support   ends, the software/files are moved to a different server location and the usual commands will not work usually with an error similar to file not found.

There really isn't much point in upgrading to 20.04 in any case as support for it will end in April, 2025.

If you want to try going to the archives and updating/upgrading that way, the link is below but you will not likely be successful.  If you don't mind frustration and have a lot of time on your hands to mess with it, good luck.  Otherwise, depending upon the age of your computer, you might be better off simply reinstalling, maybe a lighter version such as Lubuntu, Xubuntu or Bodhi.  You should back up personal data to another drive but you could reinstall to the same partitions and choose NOT to format them.

---

### Post by Engineeringtech on 2024-12-13
> **yancek said:**
> 'm not sure what the purpose of post 25 is but in post  23, you stated "I have a FILE in the sources.list.d directory that I don't know how to delete".  That file is root owned so you need sudo to remove it.  You can open a terminal and change to that directory:  cd /etc/apt/sources.list.d  the do sudo rm nameoffile (enter the actual name of the wine file you have.


Thanks.  I was able to remove the file that referenced the Wine source, by working from the terminal window.  My fear and trepidation comes from the fact that I'm not familiar with terminal commands and navigation.   I assume there is some way to temporarily give root access to the windowed file manager, but don't know how.  I did not post comment #25, and I am not certain how one changes the file manager, or why it would be advantageous to me.

Now if I could only figure out how to trigger an update to see if the removal of the Wine source fixed the problem with my upgrade to V20..  Previously I waited for the system to offer me an upgrade.

Numerous people have told me I should backup my data and install V20 or V22 from scratch.  I assume they mean using a DVD created from a downloaded ISO.  I have resisted doing that because I have a history of backing up data, and the backups failing.  That was true from Windows and my other Linux installs.  It is almost like I'm cursed in this regard.  I realize eventually my hard drive will fail, but so far, it has been good.   I'm old and in very poor health.  Although there are some family pictures and documents on the computer that I would like to keep, Mostly I just want a working computer to access the internet.   Perhaps Linux isn't the right platform for someone such as myself, but my luck with Windows has actually been worse.

---

### Post by yancek on 2024-12-13
>  Now if I could only figure out how to trigger an update to see if the  removal of the Wine source fixed the problem with my upgrade to V20.

That won't work as I explained in my previous posts since the 18.04 files to upgrade have been moved and the update/upgrade commands will fail as will using the software manager.  You would need to find the archives for 18.04 and find a method of using it to update/upgrade.  Chances of doing that and being successful are poor because very few people do it.

You could try installing another version and selecting to NOT format your partitions which should save personal data.  I've done this multiple times but I would always suggest a back up first.

---

### Post by Irihapeti on 2024-12-13
> **Engineeringtech said:**
> Thanks.  I was able to remove the file that referenced the Wine source, by working from the terminal window.  My fear and trepidation comes from the fact that I'm not familiar with terminal commands and navigation.   I assume there is some way to temporarily give root access to the windowed file manager, but don't know how.  I did not post comment #25, and I am not certain how one changes the file manager, or why it would be advantageous to me.

Now if I could only figure out how to trigger an update to see if the removal of the Wine source fixed the problem with my upgrade to V20..  Previously I waited for the system to offer me an upgrade.

Numerous people have told me I should backup my data and install V20 or V22 from scratch.  I assume they mean using a DVD created from a downloaded ISO.  I have resisted doing that because I have a history of backing up data, and the backups failing.  That was true from Windows and my other Linux installs.  It is almost like I'm cursed in this regard.  I realize eventually my hard drive will fail, but so far, it has been good.   I'm old and in very poor health.  Although there are some family pictures and documents on the computer that I would like to keep, Mostly I just want a working computer to access the internet.   Perhaps Linux isn't the right platform for someone such as myself, but my luck with Windows has actually been worse.

If you can't get a backup to work, could you just copy the family pictures and documents to an external disk that you plug into a USB port? That would be vastly better than nothing.

---

### Post by ActionParsnip on 2024-12-16
Just do a straight file copy. You don't have to use fancy backup software to make a backup. A backup is just a second copy of your data.

---

### Post by Engineeringtech on 2024-12-20
> **yancek said:**
> ......

  	 	 	 	   Yancek,
 
 
 I believe I may have success with some reservation, thanks to you and others who helped me.  After commenting out the entries relating to wine in the sources.list file and deleting the winehq-bionic.sources file,   I waited patiently for the upgrade manager to offer me another chance to upgrade to V20.04.    (I did not know how to manually force the offer.)   Well today it offered the upgrade, and THIS TIME, the upgrade did not fail for lack of a proper Wine source.  I now have V20.04 running on my machine.  

One possible bugaboo.   I had enabled Ubuntu Pro Support for V18.04LTS earlier.   If I look at the Livepatch settings, it tells me Ubuntu Pro Support is still enabled.  Does this mean I have two versions of the OS running on my machine (18 and 20), or does it simply mean Ubuntu Pro Support is now enabled for V20.04?

 
 
 One last question… My machine was used when a co-worker gifted it to me 4 years ago.  I don’t know how old it is.   The settings window tells me it has 7.7 GB of memory, a Core I3-4170 3.7 Ghz processor, an Intel® HD Graphics 4400 (HSW GT2) card, and a 1TB rotating hard drive.   
 
 
 Should I just run V20.04 for the time being or attempt the update to V22?  

When is V20.04 End of Life?

 

Thanks again to all who helped me, a total novice to get this far...  Merry Christmas & Happy New Year

---

### Post by deadflowr on 2024-12-20
> One possible bugaboo. I had enabled Ubuntu Pro Support for V18.04LTS earlier. If I look at the Livepatch settings, it tells me Ubuntu Pro Support is still enabled. Does this mean I have two versions of the OS running on my machine (18 and 20), or does it simply mean Ubuntu Pro Support is now enabled for V20.04?

Indeed a bugaboo.
A few users have posted that they too have had erroneous listings in the pro dashboard showing more attached machines than actually attached.
See: [https://discourse.ubuntu.com/t/how-do-i-find-machines-which-have-esm-enabled/47272/11](https://discourse.ubuntu.com/t/how-do-i-find-machines-which-have-esm-enabled/47272/11)
scroll down toward the bottom to see others with the issue.

---

### Post by Irihapeti on 2024-12-20
Each LTS release is supported for 5 years, so 20.04 will be out of support next year, around April, I think. That gives you a month or two to think about it.

At this point, may I suggest that you join us on Discourse and continue the conversation there.

---

### Post by Engineeringtech on 2024-12-23
> **deadflowr said:**
> Indeed a bugaboo.
A few users have posted that they too have had erroneous listings in the pro dashboard showing more attached machines than actually attached.
See: [https://discourse.ubuntu.com/t/how-do-i-find-machines-which-have-esm-enabled/47272/11](https://discourse.ubuntu.com/t/how-do-i-find-machines-which-have-esm-enabled/47272/11)
scroll down toward the bottom to see others with the issue.

Thank you.  I will move over to discourse and check it out.  However, for the time being at least, my system seems to be operating correctly.

---

### Post by Engineeringtech on 2024-12-23
Thanks.  Yes, I did a search and EOL is May.  I just got a notice to upgrade to V22, so will ask again if my hardware will support it.

---

### Post by Engineeringtech on 2024-12-23
> **Irihapeti said:**
> Each LTS release is supported for 5 years, so 20.04 will be out of support next year, around April, I think. That gives you a month or two to think about it.

At this point, may I suggest that you join us on Discourse and continue the conversation there.

Thanks.  Yes, I did a search and EOL is May.  I just got a notice to  upgrade to V22, so will ask again if my hardware will support it.

---

