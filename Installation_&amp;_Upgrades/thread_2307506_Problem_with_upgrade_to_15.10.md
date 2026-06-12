---
title: "Problem with upgrade to 15.10"
date: 2015-12-25
forum: Installation &amp; Upgrades
---

### Post by Harry_Riley on 2015-12-25
I have a Lenovo T550 and I was running 15.04. 

I upgraded to 15.10 from the command line with the command:
sudo do-release-upgrade -d

In this version I do not have a taskbar or do I have Dash.  The only thing i have is a desktop.

My question is how can I upgrade to the appropriate version 15.10 without having to reinstall from the cd or usb?
Harry

---

### Post by Bucky Ball on 2015-12-25
You do have the appropriate version. There appear to be issues after the upgrade.

Open a terminal and:

```
sudo apt-get update
sudo apt-get upgrade
```

Report any and all errors. If none, reboot. Also provide the output of this command:

```
lsb_release -a
```

PS: I've changed your thread title for clarity as there is no 15.10 'developer's' version. You just have upgrade issues. :)

Few questions: 

Was this a standard, fairly vanilla, Ubuntu install you upgraded (not Xubuntu or another flavour)? 

Did you have any manually installed PPAs which were not disabled prior to the upgrade? 

Did you do a full update/upgrade (the first two commands I give here) prior to the upgrade? This is important.

---

### Post by Harry_Riley on 2015-12-25
I did not have any errors.

Here is the outpu from the command:
harry@harry-ThinkPap-T550:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

---

### Post by Bucky Ball on 2015-12-25
I have edited my first post. Please have another look.

---

### Post by Harry_Riley on 2015-12-25
Was this a standard, fairly vanilla, Ubuntu install you upgraded (not Xubuntu or another flavour)? 

This was a standard version.

Did you have any manually installed PPAs which were not disabled prior to the upgrade? 
No not that I know of.

Did you do a full update/upgrade (the first two commands I give here) prior to the upgrade? This is important.

no I did not do this before the uprgade.

---

### Post by Bucky Ball on 2015-12-25
> **Harry_Riley said:**
> Did you do a full update/upgrade (the first two commands I give here) prior to the upgrade? This is important.

no I did not do this before the uprgade.

Could have something to do with it. You really need to have an up-to-date system to upgrade to another release. A quick reflection on this and sure you will understand why. When was the last time you updated/upgraded the system you were trying to upgrade to the next release? If it's been awhile, that could be the culprit.

Sure there is a way of fixing this, but beyond my expertise. Hopefully someone can shed more light soon.

---

### Post by Harry_Riley on 2015-12-25
Well the plan was to do a clean install of 15.10 with a usb.  I am going through something of the same thing with Lubuntu at school so a clean install may be the answer.

---

### Post by Bucky Ball on 2015-12-25
Probably not a bad idea unless you have a day or two to work your way through this. You can boot from the Lubuntu install media, 'Try Ubuntu' and backup any valuable data to an external device using the desktop environment, then just hit the 'Install' icon on the desktop. :)

If you want to rearrange things, choose 'Something Else' at the partitioning section of the install and partition manually.

Good luck, and if you decide to go with the full reinstall, please mark this thread as solved and start a new one for future issues.

---

### Post by grahammechanical on 2015-12-25
So, Ubuntu loads to a login screen but from there it loads to a desktop without the launcher on the left or the top panel with app indicators. What can you do?

1) Right click the desktop wallpaper. That should bring up a menu with Open Terminal & Change desktop background among the options.

To shutdown - open the terminal & run

```
sudo shutdown -h now
```

to restart

```
sudo shutdown -r now
```

Changing video drivers might fix the problem. To change video drivers in this situation

Select Change desktop background. That will open system settings at the Appearance utility. From there we can get to the system settings main window & select Software & Updates>Additional Drivers tab. If we are connected to the internet and allow time for the utility to work we will get a selection of video drivers to experiment with.

Also, At the boot menu we can select the Advanced options for Ubuntu sub-menu & then select recovery mode. At the recovery menu we select Resume and that will attempt to load to the desktop using a fall back video driver. This is useful if the problem is caused by a proprietary video driver.

Regards.

---

### Post by Harry_Riley on 2015-12-25
Thank you all.

---

### Post by Harry_Riley on 2015-12-25
solved

---

### Post by Bucky Ball on 2015-12-26
How? Reinstall? Convention here is to share the solution with the community. Thanks. :)

Also, see the first link in my signature and mark the thread as solved.

---

### Post by Harry_Riley on 2016-01-05
I have completely solved this by making a USB for 15.10 and totally erasing the hard drive and reinstalling 15.10.  Now everything work except Google Chrome.  But that is not Ubuntu's fault.

---

### Post by Bucky Ball on 2016-01-05
Cheers. Enjoy! :)

Feel free to start a new thread to see if you can get some help with your Chrome issues. You could try Chromium from the repos. Good luck.

---

