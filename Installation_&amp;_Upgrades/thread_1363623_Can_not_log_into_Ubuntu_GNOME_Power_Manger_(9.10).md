---
title: "Can not log into Ubuntu GNOME Power Manger (9.10)"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by chris_0076 on 2009-12-24
Hello,

When ever I try to log into Ubuntu up in the top right corner it says:

"The configuration defaults for GNOME Power Manager have not been installed correctly.
Please contact your computer administrator."

Then it semi-restarts and goes back to the login screen where everything starts over.

Can anyone please help me?


Thanks for any and all help,
Chris


EDIT

I tried removing and reinstalling it and it did not work.

I used:
 sudo apt-get remove gnome-power-manager
sudo apt-get install gnome-power-manager

---

### Post by ajgreeny on 2009-12-24
At login screen try Ctrl+Alt+F1 and login to the cli with your username and password (pw will not show on screen)

Now use command ```
mv /home/username/.gconf/apps/gnome-power-manager /home/username/.gconf/apps/gnome-power-managerbackup
```and then try going back to the gdm login screen with Ctrl+Alt+F7 and see if it works now.

---

### Post by chris_0076 on 2009-12-24
It says that the file is not there.

Should I just do a clean install to get all of this fixed? I have nothing saved on this computer. Or am I a simple fix from getting it working again? All that I have done with this installation so far is setting up everything to my liking (tablet install, theme, background, firefox addons ect).

---

### Post by chris_0076 on 2009-12-25
Meh... whatever I figure I don't have too much investing in this install so I'll just do it again.

Thanks anyways,
Chris

---

### Post by ajgreeny on 2009-12-25
I presume you used your own login username instead of actually typing "username" in that command.  If you did, there should have been a file of that name, I think, but either way, good luck next time.

---

### Post by gstanden on 2009-12-28
Hi, I hit this problem also about the gnome power manager and it prevented me from logging in to the GUI.

In my case, I had tried to update from Karmic Development branch and the updated had displayed "partial update only available".  After the partial update logging in to GUI was hosed.  

In my case, I did have a ton of files on the computer I needed so reimaging without getting my files off was not an option.  So here is how I finally got ALL of my ENTIRE disk image off of the harddisk without using the GUI.  It turned out to be simple, but I had alot of trial and error with other methods so I'm putting this here HTH.


0.  Plug in a USB drive to your computer with sufficient disk space to hold your entire ubuntu disk image.

1.  Turn on your laptop or desktop machine.

2.  Boot up with your Karmic distro install disk (download from ubuntu.com).  This means you have to boot from the DVD/CD drive.  You may have to find the Fn key which allows you to switch bootup to DVD/CD.

3.  Once you have the ubuntu disk GUI fully booted, open a terminal session and at the prompt type "sudo passwd".  Set a password for root in this way.

4.  Login as root using the password you just set using "su - root" then enter the passwd you just set.

5.  "cd /media"

6.  If you get same results as me, there you should see 2 (or more) very long strings (directory names) which are unique scsi_id's for (a) your harddrive, and (b) any plugged in external drives, eg. the usb drive you plugged in before you booted.  Figure out which is which.

7.  Now copy everything over from the hardrive to the usb.  first,

"cd /media/scsi-id-of-your-ubuntu-harddrive"
"cp -R dir1 dir2 dir3 dir4 /media/scsi-id-of-your-usb-external-drive"

Note, don't use a "*" because you DON'T want to copy the directory "cdrom" which is your ubuntu boot disk.

Otherwise, you copy EVERYTHING over in this way.  It will all copy typically without one single error because in this situation, your harddrive is just a dormant inactive filesystem, no different from a dormant external usb drive.

8.  Once this is done, spot check some of the copied files on your USB drive to make sure you got everything and that all was copied (check bytes counts here and there just to get a fuzzy about everything having copied ok).  Then unplug your USB.  You've now got your entire disk image.

9.  Now you can reinstall ubuntu and afterwards, you can cherry pick back into the image whatever you want, using the above procedure in reverse.

HTH Gil

---

