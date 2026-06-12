---
title: "Power Failure during upgrade - blank desktop"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by luapekralc on 2008-05-22
Hi,

I was upgrading from 7.10 to 8.04 but during the last 20 minutes the power failed. So now I can log in (and the login screen looks like 8.04 (different than 7.10 anyway), but after that I just get a brown page - no toolbar, no activity. 

I suspect that I need to redo the upgrade. I tried to use the 7.10 CD to reinstall, but it looked like it was going to overwrite everything, which I would prefer not to do.

Any suggestions would be appreciated.

---

### Post by iaculallad on 2008-05-22
> **luapekralc said:**
> Hi,

I was upgrading from 7.10 to 8.04 but during the last 20 minutes the power failed. So now I can log in (and the login screen looks like 8.04 (different than 7.10 anyway), but after that I just get a brown page - no toolbar, no activity. 

I suspect that I need to redo the upgrade. I tried to use the 7.10 CD to reinstall, but it looked like it was going to overwrite everything, which I would prefer not to do.

Any suggestions would be appreciated.

If you still could see the GRUB menu option on startup (Select Recovery Mode), issue this command on your "Recovery Mode" terminal:

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

---

### Post by livefreely13 on 2008-05-23
I have a similar question.  I was in the middle of upgrading to Hardy and the coffeeshop I was at while my system upgrade was taking place closed before I could finish.  I have a wonderful looking login screen, but when I type in my username and password I get a similar looking brown screen.

Is there any way to bypass the login screen and do a reinstall from there?  It seems like if I was over-halfway through the upgrade process and on the way to installing many of the new packages, there should be a way to retrieve that within the computer.

---

### Post by iaculallad on 2008-05-23
> **livefreely13 said:**
> I have a similar question.  I was in the middle of upgrading to Hardy and the coffeeshop I was at while my system upgrade was taking place closed before I could finish.  I have a wonderful looking login screen, but when I type in my username and password I get a similar looking brown screen.

Is there any way to bypass the login screen and do a reinstall from there?  It seems like if I was over-halfway through the upgrade process and on the way to installing many of the new packages, there should be a way to retrieve that within the computer.

While on the booting process (Loading GRUB...), press ESC key to enter the GRUB menu then follow the step i posted above to resume your upgrade.

---

### Post by farhanali on 2008-05-24
I have a similar problem... i was upgrading to hardy from gutsy 7.10. before i starting the upgrade i installed all the upgrades that the upgrade manager suggested. during the downloading of packages the power failed.

After the system was rebooted the upgrade manager icon appeared in the the panel, and telling me that upgrades are ready to download. but when i asked it to upgrade it said that Not all updates can be installed, run a partial upgrade. when i clicked the partial upgrade during "preparing the upgrade" a popup cam up saying "could not calculate the upgrade, A unresolved problem occured while calculating upgrade. Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport."

Then i ask a friend to give me the alternate cd for upgrade from cd. during the upgrade from cd the power failed again :(.

now when i enter the cd it does not start automatically. i and i cant upgrade from network... what can i do???

Farhan

ps: the content of my /var/log/dist-upgrade/ folder is attached

---

### Post by iaculallad on 2008-05-24
> **farhanali said:**
> now when i enter the cd it does not start automatically. i and i cant upgrade from network... what can i do???

Try checking your system BIOS and try changing the boot order to CD/DVDROM first (BIOS sometimes fails when there's a power outage). 
Try rebooting to your CD again.

*- Then try the steps I listed on my posts above to recover your interrupted upgrade.

---

### Post by farhanali on 2008-05-24
> **iaculallad said:**
> 
.
.
.
 
Try rebooting to your CD again.
.
.
.


I did not boot from the cd... i just inserted the cd AFTER i logged into my system. a popup window came that a distro upgrade cd is detected .. and asked me to upgrade i replied yes...

---

### Post by iaculallad on 2008-05-24
> **farhanali said:**
> I did not boot from the cd... i just inserted the cd AFTER i logged into my system. a popup window came that a distro upgrade cd is detected .. and asked me to upgrade i replied yes...

Seems like you got messed up from the very beginning. Assuming that no important data had been saved in your drive, I suggest that you do a clean install to eliminate future problems caused by the failed installation due to power failure.

---

### Post by farhanali on 2008-05-24
[LIST=1]
[*] whats a clean install???
[*] i have a lot of data on my home folder? i want to save all that?
[/LIST]
1 more thing... at the moment my system is running fine ....doing all the things as it should do... still i was installing hardy to keep my system uptodate...

what should i do? i am really nervous now ? kindly help?

---

### Post by iaculallad on 2008-05-24
> **farhanali said:**
> [LIST=1]
[*] whats a clean install???
[*] i have a lot of data on my home folder? i want to save all that?
[/LIST]
1 more thing... at the moment my system is running fine ....doing all the things as it should do... still i was installing hardy to keep my system uptodate...

what should i do? i am really nervous now ? kindly help?

Clean install means you do the installation using the Ubuntu LiveCD. From booting to system files installation.

What CD are you using to upgrade your Gutsy? Is it the Desktop LiveCD or the Alternate CD. If you're planning to upgrade to Hardy, use the Alternate CD instead. Desktop LiveCD's are not for upgrade because it just copies itself on the existing HDD. Download and Burn the Alternate CD instead.

---

### Post by farhanali on 2008-05-24
i am using hardy alternate cd...

---

### Post by iaculallad on 2008-05-24
> **farhanali said:**
> i am using hardy alternate cd...

Try browsing the [page]("https://help.ubuntu.com/community/HardyUpgrades"), and look at the Alternate CD upgrade portion. Hope this could help with the situation.

---

### Post by luapekralc on 2008-05-25
Thanks for the suggestion. It started to work through the configure portion but then reached a point where there were errors in the open-office area. Actually it looked like there were a number of errors. Is there a file created where these errors are stored so that I can review them since I'm not in a terminal window I can't scroll up to find them, and since the system is not running I can't print them on my network printer.

It seems I have only one option - clean install. which would not be too bad since my files are backed up, but the various configurations and software installs would have to be done again. Is there a way to install the new version but retain the various configuration settings?

---

