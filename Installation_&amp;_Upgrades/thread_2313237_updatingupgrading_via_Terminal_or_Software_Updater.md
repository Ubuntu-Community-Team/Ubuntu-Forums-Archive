---
title: "updating/upgrading via Terminal or Software Updater?"
date: 2016-02-10
forum: Installation &amp; Upgrades
---

### Post by David2009 on 2016-02-10
I had a problem downloading and installing updates via the Software Updater.  My problem was quickly resolved, but it brought up another installation issue.

After my cache was rebuilt (that seemed to have resolved my trouble) the last command I entered was sudo apt-get update. This downloaded a lot of information.  So, the next command I wanted to give was sudo apt-get upgrade, and this accomplished the installation.  All is great.  I rebooted the computer.

Next, I went back to the Software Updater to see if I'd get the message that the computer was up to date.  I didn't.  I received a message that there were new updates to download.  I did this, rebooted, and am here with my question.

Is it better (or preferred) to update and upgrade via the terminal or via the Software Updater?  Are they looking for the same information?

Also, I wonder if I got myself in trouble by removing old kernels using the Ubuntu Tweak program?  It is the only way I could figure out how to delete old kernels.  

Thank you.

David

---

### Post by newbie-user on 2016-02-10
I manage my linux boxes remotely, so I use the terminal all the time. That said, I just had a similar issue today where after the upgrade, there were more packages that needed to be upgraded. This is all in the command line, by the way. I suppose there were dependencies that needed to be resolved first before the latest packages could be installed. No big deal.

As for removing old kernels, first list what kernels you have installed:
```
dpkg --list | grep linux-image
```
Choose the kernels you don't want, then remove them (example below):
```
sudo apt-get remove linux-image-3.2.0-48-generic
```

---

### Post by grahammechanical on 2016-02-10
When we open Software Updater the first thing it does is check for updates. It does that by running apt-get update. And when we click to install updates it runs the apt-get upgrade command.

The difference between using Software Updater and the terminal is that in the terminal we have to authorise the action to complete the upgrade. But Software Updater has the authorisation to update the software sources list and to upgrade the software without requiring our authorisation except for certain kinds of software upgrade.

For example, a kernel upgrade will produce a dialog asking for authorisation. And there are a few other package upgrades that will prompt for authorisation. But mostly we can update/upgrade through Software Updater without needing to authorise the action.

Regards.

---

### Post by mörgæs on 2016-02-11
Removing old kernels is best done using **sudo apt-get autoremove**.

---

### Post by David2009 on 2016-02-13
Thank you very much.  I have written it down (in my cell phone notepad), so I will (hopefully) have it the next time.  

David

---

### Post by David2009 on 2016-02-13
Thank you for the explanation.  I appreciate your making the time to mentor new folks.

David

---

### Post by David2009 on 2016-02-13
Thank you for the help.  There is so much to learn.  (But, it is fun.)

David

---

