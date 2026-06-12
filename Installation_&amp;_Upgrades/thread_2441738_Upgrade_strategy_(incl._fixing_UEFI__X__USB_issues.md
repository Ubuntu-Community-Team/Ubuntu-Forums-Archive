---
title: "Upgrade strategy (incl. fixing UEFI / X / USB issues)"
date: 2020-04-26
forum: Installation &amp; Upgrades
---

### Post by T_Jo on 2020-04-26
Hi 

I have been updating my system for a few years now - currently on 19.10 and like to do a clean install of 20.04
Reason is I like to keep using an LTS version. My main use of the system is for browsing, multimedia and have a VM image of 16.04 Ubuntu that I also like to upgrade to 20.04

My desktop has issues automatically starting X (always hangs and I need to select a new session and startx). 
Also another more annoying issue because of an UEFI problem I always need to start with a rEFInd boot disk. A while ago I deleted some apparently important boot information and are not able to automatically boot Ubuntu anymore. 
rEFInd boot disk has the UEFI boot information stored that is needed to boot.
Another issue is with USB drives that are not always automatically recognized, sometimes I need to reconnect them or switch to another USB port. 

So my backup strategy will be:

1. Backup my home directory 
2. Backup my Browser profiles 
3. Backup some of the most important files and directories (including terminal history - contains some very useful CLI)  
4. Back-Up my VM image 

Then 

1. Fix the UEFI issue if needed. I assume a clean Ubuntu install not fix it  
2. Install 20.04 (hope this fixes the issue with X and USB)
3. Restore browser profiles
4. Restore files/directories/terminal history
5. Upgrade VM image from 16.04 - 18-04 to 20-4 

So no questions yet but when I run into issues I will use this post. Feel free to comment on my strategy.

Edit [some comments about the process]

Tried to copy my home directory with tar but got a "file changed as we read it" error. I assume that happens because i am actively using my PC. Content of /home can of course change during copying. 

changed that method and now using rsync (hopefully that will work)

rsync -avz /my/home/ /somebackupdir/

after using this method got "rsync error: some files/attrs were not transferred"
Most files are transferred but still a pretty large chunk didn't copy - I think most of them are read only files. Good enough for me but next time I think I will use "sudo rsync -avz /my/home/ /somebackupdir/" 

- didn't wait for a next time, wanted to be sure I didn't miss important files so used rsync with sudo and indeed added a lot of data in the backup directory

Currently doing some reading on EFI.  I think my problem was that I removed /boot/efi with Gparted and never managed to fix it (also didn't really try) 
Looks like installing ubuntu will fix it and automatically partitions the HDD correctly and add the necessary files.

Backup browsers

[https://www.fossmint.com/backup-and-restore-google-chrome-profile-on-linux/](https://www.fossmint.com/backup-and-restore-google-chrome-profile-on-linux/)
[https://www.fossmint.com/backup-and-restore-a-firefox-profile-on-linux/](https://www.fossmint.com/backup-and-restore-a-firefox-profile-on-linux/)

---

### Post by oldfred on 2020-04-26
All your user files are in /home. Does not hurt to back up some data in addition, but it should be in /home.
You may have some settings in /etc that are system wide. I edit some grub files, but so few in /etc, I just copy into /home so my backup of /home includes those.
You should export a list of installed applications. But may want to manually edit it (it is text, but long). It may have old kernels or apps you do not want to reinstall.
I periodically export history to a text file so that is in backup also.

Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[https://ubuntuforums.org/showthread.php?t=2368992&](https://ubuntuforums.org/showthread.php?t=2368992&) 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) & 
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

My backup includes this also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by T_Jo on 2020-04-27
Thanks oldfred for the tips.  

Just upgraded and installation worked pretty well. UEFI boot was fixed during install so that's nice. 
My problem with X is not fixed though. Ubuntu is always seeing two displays - a built in display and the correct (external) display. Unfortunately the built in (virtual) display is always the preferred and primary display. 
The screen I am presented with after installation is a secondary screen without the applications. So I then usually go to command line and start gnome-control-center display. Choose clone screens and it is fixed. 

After installing 20.04 the first screen I am presented with is a purple screen and have access to the mouse and like usual no applications. Unfortunately CTRL-ALT-T doesn't work to enter some commands in a terminal. Needed to start a new session and stop gdm3 (sudo systemctl stop gdm3)
After that I could startx and am able to start gnome-control-center display from terminal. So not perfect, but there is a workaround.

---

### Post by oldfred on 2020-04-27
Do not know screen issues as I have desktop with only one monitor.

You may want to start a new thread with that issue in title, and see if anyone has suggestions or fixes.

---

### Post by T_Jo on 2020-04-27
I also have a desktop with only one screen - Ubuntu just thinks it has two :) It is a bit annoying, but has an easy workaround and I have this problem since 16.04 so I am used to it and not on my priority list to fix. Looks like a software issue, Puppy Linux works fine. Will start a new forumpost later. Thx!

---

