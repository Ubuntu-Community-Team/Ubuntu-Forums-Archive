---
title: "Upgrade to 15.10 from 15.04 Ubuntu-MATE"
date: 2015-10-26
forum: Installation &amp; Upgrades
---

### Post by wagb278 on 2015-10-26
I have Ubuntu-MATE 15.04 (64-bit) running and desire to test the Upgrade process. 

Instructions at [this article]("https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes/UbuntuMATE") 

The first step says to select System > Administration > Software & Updates.  That option does not exist in Ubuntu-MATE 15.04. 

However, doing System > Administration > Software Updater; and then Settings - The Notify me of a new Ubuntu version: is set to "For any new version". 

I get no notification that there is a new version (Ubuntu-MATE 15.10) available; thus cannot begin the upgrade process.  

Are the instructions in that article correct?  Has anyone else succeeded upgrading Ubuntu-Mate 15.04 to 15.10?

I have downloaded and tested a Ubuntu-Mate 15.10 ISO and the Try Ubuntu from the live DVD seems to run fine on that computer.  I will use that for a fresh install if need be, but would like to try the Upgrade option first.  

Thanks for any suggestions -

---

### Post by egeezer on 2015-10-26
Software and Updates is a different GUI application that enables you to choose the sources for Ubuntu or other software.  Does MATE have a choice of "Additional Drivers"?  If it does, clicking on that will bring up the panel you need.

But I would bet it won't be long before your regular update system lets you know about 15.10 anyway!

---

### Post by grahammechanical on 2015-10-26
I have to ask you a couple of stupid questions.

1) Since you checked that Update manager is set to "notify for any new version" have you updated Ubuntu Mate 15.04?
2) Have you tried this?

> Press Alt+F2 and type in update-manager to the command box.

Eliminate the obvious. I cannot test this as I am not running Ubuntu Mate 15.04. But the method of upgrading should be similar for all Ubuntu flavours although the menu options may have different labels.

That wiki page does directly refer to Ubuntu Mate 15.10 so I would assume that it is up to date.

Regards.

---

### Post by wagb278 on 2015-10-26
Thanks for the replies. 

Yes Ubuntu MATE does have "Additional Drivers" - and that does open the "Software & Updates" window.  Interesting!  But I also discovered that "Software & Updates" is available in the "Control Center; just not available in the System > Administration menu.  Again, interesting!  I learned something. 

I have tried the command "update-manager" and it just runs the "Software Updater" - same as on the System > Administration > Software Updater menu action.  And, yes I have updated Ubuntu-MATE 15.04 using that.  But no notification of the new release 15.10. 

I guess I will wait a couple of days and see if I get notified of the availability of Ubuntu-MATE 15.10.  I did read somewhere that the *Upgrades* are held off and not released the same time as the ISO images are released, maybe that is what is happening. 

Thanks again for your replies.

---

### Post by ken78724 on 2015-10-26
Wagb278, I have no idea what Ubuntu MATE means. Personally, I downloaded a Ubuntu Buzz 15.10 iso to help a friend with Parkinsons needing a PC. It wrote over whatever I had on a Dell PC sitting here and ran good; so I shipped it to the Ohio friend..

Then, if you will read my new post titled "10.04 to 15.10 upgrade logout problem," I believe you both have a source for a ubuntu 15.10 .iso and results showing though I have a small problem to solve, you see I was able to do ten hours of hard report writing. 

Good luck and thanks for all that you do. 

k78724

Wagb278: 

is the MATE matter a problem or means to explain the type of discussion you are leading?

---

### Post by Vladlenin5000 on 2015-10-26
ken78724,

Ubuntu MATE is a Ubuntu derivative/flavor running the MATE desktop.
[https://ubuntu-mate.org/](https://ubuntu-mate.org/)

---

### Post by Bucky Ball on 2015-10-27
Try this, an update, commands one at a time to check for errors, as suggested before, then see if you can see the 15.10 upgrade option anywhere:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

Please note that if you are intending to install things from the net during the install (third-party drivers, etc.) then use an ethernet cable. If your wireless goes down halfway through an install it might not be pretty (or should I say, it will possibly be pretty ... ugly!). :)

@ken78724: Easy enough to have a look for Mate if you're unsure what it is. It is an officially supported Ubuntu flavour which we cater for here. It was added to the family about six or ten months ago. Lightweight and lots of people like/love it. :)

Ubuntu Buzz? That's a blog by the looks. Best to download the ISO from[ the official Ubuntu repositories]("http://www.ubuntu.com/download/desktop").

---

### Post by wagb278 on 2015-10-27
UPDATE - Software Updater notified me of updates to MySQL and after those changes were installed it said "Software on this computer is up to date. However, Ubuntu 15.10 is now available (you have 15.04)".  I will try the Upgrade button that is now showing and report back with results.  Thanks.

Well, It worked! 

I guess I was just too impatient. 

After receiving the notice that I could upgrade 15.04 to 15.10 I ran that process - which took a little over two hours to run - the result was a fully functioning Ubuntu-MATE 15.10 with all my previous applications, configuration settings and data files.  Nicely done Ubuntu team. 

On the old 15.04, I had used Grub Customizer to change the Grub menu item name from "Ubuntu" to "Ubuntu-MATE 15.04" and that name change was retained by the upgrade process; so I will have to install that third-party app and change the name to reflect the new 15.10 version, but that is not a problem. 

Thanks All.

---

### Post by ken78724 on 2015-10-27
many thanks Bucky Ball

---

### Post by Mark Phelps on 2015-10-28
> **wagb278 said:**
> On the old 15.04, I had used Grub Customizer to change the Grub menu item name from "Ubuntu" to "Ubuntu-MATE 15.04" and that name change was retained by the upgrade process; so I will have to install that third-party app and change the name to reflect the new 15.10 version, but that is not a problem. 

Thanks All.

From what I've seen on 15.10, Grub-Customizer is not not available.  I checked recently, and the latest Ubuntu version was Vivid.  Don't think it has been updated for Wily yet.

---

