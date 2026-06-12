---
title: "can't login after upgrade to 16.04"
date: 2016-04-23
forum: Installation &amp; Upgrades
---

### Post by headflux on 2016-04-23
I upgraded today from 15.10 to 16.04.  After the upgrade I cannot login in. 

I get to the logon on screen and enter my password, after a few seconds it just returns to the logon screen.

Please help!

Thank you.

---

### Post by kimble2 on 2016-04-23
I have the same thing after a clean install of Lubuntu 16.04 with encrypted home directory.
After the initial reboot, I was able to login and install some apps including Apache2 and pure-ftpd.
Then after another reboot the login screen appears.
If I type a wrong password it says "incorrect password",
but if I type the correct password the screen goes blank and reappears at login screen.

Using recovery mode (for single OS hold down shift to see menu) and choose "Drop to root shell prompt":
[COLOR=#0000ff]# mount -rw -o remount /
# ls /home
XXXX
# passwd XXXX
Enter UNIX password:
YYYY
Retype UNIX password:
YYYY
Password changed
# exit[/COLOR]

Choose "Resume booting"
result: same thing as above

The servers are running OK.

---

### Post by kimble2 on 2016-04-23
Using the Live Lubuntu 16.04 CD, I could mount the installed Lubuntu partition /dev/sda1
and as root see inside /media/lubuntu/nnnn...nnn/home/XXXX/
It has 2 files in it: README.txt and Access-Your-Private-Data.desktop
The .desktop file doesn't run.
From a terminal: sudo /usr/bin/ecryptfs-mount-private
It should now ask for the 32 hex string that encrypts /home/XXXX/ , but instead says "ERROR: Encrypted private directory is not setup properly".

That explains the login not working, but why is it not properly set up? - it looked OK when I was logged in the first time.
I can't see any option other than to reinstall without the encrypted home directory.
I'll wait a day for any help.

---

### Post by headflux on 2016-04-24
I got my logon working by disabling secure boot in the BIOS.

However I then found I had no desktop, so I had to disable the proprietary Nvidia drivers and reinstall the desktop via the terminal.

This seems to have fixed the problem.

---

### Post by kimble2 on 2016-04-25
Duh - the SSD I was installing to has just died.  It must have been stressed by all that filestore creation.  Replaced SSD with HDD, reinstalled OK.  Problem solved.

---

