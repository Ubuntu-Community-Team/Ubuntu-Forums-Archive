---
title: "Upgrade from 14.04 to 16.04"
date: 2018-08-01
forum: Installation &amp; Upgrades
---

### Post by sophia.bobby on 2018-08-01
Hello,
Today I attempted upgraded Ubuntu from 14.04 to 16.04 using these commands. All appeared to go fine. I restarted the computer and now I cannot log into my account. Fortunately, I can go into a guest account. I see that it is still 14.04, but I have no permissions or limited ability to troubleshoot. Are there any suggestions to fix this mess I got into? or log files I can check to see if there is a partial upgrade?

thanks,
Sophia

Here are the commands I used for the upgrade
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install update-manager-core
sudo do-release-upgrade

---

### Post by TheFu on 2018-08-01
Earlier this year, I did the 14.04 --> 16.04 stuff on 6 boxes.  5 went cleanly.  1 failed in that I'd get logged in, but within 90 seconds, I'd be logged out and the system would reboot.  Took me a few hours to track it down to my personal perl version (only available under my account) which had broke that part of  the upgrade.  I removed perlbrew  (it is like rvm, rbenv, pyenv) and setup the normal perl environment and all has been fine.

I would boot off a flash drive, copy off all the log files, then restore from the pre-14.04 backup.   Then I'd go through all the logs looking for issues.  It could be a manually installed .deb file, 3rd party PPA, some environment variable, or hardware that chose to fail at the reboot.  Not much more we can guess with the information provided.

Booting off a flash drive is a common troubleshooting method for all Linux systems.  If you boot from the same release(14.04.x), then you can setup a chroot and actually run the OS on the HDD to see things from that perspective.

---

### Post by sophia.bobby on 2018-08-02
Great advice, I will give this a try.

Best,
Soph

---

### Post by TheFu on 2018-08-02
> **sophia.bobby said:**
> Great advice, I will give this a try.

Best,
Soph

If you don't have a backup, please,please make that the top of your todo list.  Lots of good methods depending on the factors involved.  I really need to make a Linux "Best Backups" Decision flowchart to help people get to the best setup for their needs/complexity/skills.

---

### Post by sophia.bobby on 2018-08-02
Unfortunately the usb ports do not seem to work...Will a DVD work similarly for booting?

---

### Post by sophia.bobby on 2018-08-02
In this situation with limited access to data and no root access, how do I make a backup?

---

### Post by Autodave on 2018-08-02
The DVD method will work.  Boot it up and choose TRY ?buntu.  From there, you should be able to access the hard drive. Get everything copied that you need: copy to an external hard drive, USB stick, whatever.  If you can manage to get everything copied, I would then bypass 16.04 and just do a clean install of 18.04.

---

### Post by TheFu on 2018-08-02
If you don't have a backup, then doing this now isn't all that useful.  Do you have a backup of the 14.04 data pre-16.04?

---

