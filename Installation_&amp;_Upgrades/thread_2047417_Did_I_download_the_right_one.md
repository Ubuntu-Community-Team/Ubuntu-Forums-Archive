---
title: "Did I download the right one?"
date: 2012-08-24
forum: Installation &amp; Upgrades
---

### Post by Darryl Jones on 2012-08-24
Sorry if I put this thread in the wrong place but...

I downloaded a version of Ubuntu; "Ubuntu 12.04.1 LTS 32 bit" the website says, which was good - it was faster than what I was previously using for instance - but it kept crashing all the time.

I'm using a pretty obsolete computer if that's the problem?; it's got an 2.8GHz Intel Pentium 4 CPU with 512MB of RAM and 37.2GB on the hard drive, 31.2 of which is free. I converted from Windows XP Home edition 2002 which I've went back to using for the time being.

Does anyone have any advice - is there another version that would be better for my computer or is there an update I should download or what?

---

### Post by vexorian on 2012-08-24
The crashes are not because of wrong version and your PC supports PAE.

So, better try finding out if the crashes are caused by a specific application and report the application.

Maybe using Unity-2D might fix things.

---

### Post by houseworkshy on 2012-08-24
It could be that you are squeezed on resourses, the 512 RAM is fairly low for Unity.  You could try an alternative GUI.  This is easy to do, a simple install from the standard repositories.  One which is good is LXDE. it's fairly simple graphically, though fully functional, but low on both power and resources.  If you install that you can choose to use it during the startup.  You will still have the Unity choice if you prefer.  Many mobile devise users have both anyway, Unity for when plugged in and LXDE when out and about to save on battery power.  
If that doesn't work there are many distro's aimed at lower spec machines, Slitaz still blows me away for how much is in so small a footprint but there are many others and many threads on this forum about such things.  The following is worth a read.
[http://en.wikipedia.org/wiki/Lightweight_Linux_distribution](http://en.wikipedia.org/wiki/Lightweight_Linux_distribution)
If you do hop be sure to go only to one which is still supported, also run it live to see if it picks up your hardware and have a look at it's repositories to make sure all the things you are likely to need are included.  The best site I know for distro's and reviews is distrowatch.com 
With luck LXDE will do the job.

---

### Post by Darryl Jones on 2012-08-25
> **houseworkshy said:**
> It could be that you are squeezed on resourses, the 512 RAM is fairly low for Unity.  You could try an alternative GUI.  This is easy to do, a simple install from the standard repositories.  One which is good is LXDE. it's fairly simple graphically, though fully functional, but low on both power and resources.  If you install that you can choose to use it during the startup.  You will still have the Unity choice if you prefer.  Many mobile devise users have both anyway, Unity for when plugged in and LXDE when out and about to save on battery power.  
If that doesn't work there are many distro's aimed at lower spec machines, Slitaz still blows me away for how much is in so small a footprint but there are many others and many threads on this forum about such things.  The following is worth a read.
[http://en.wikipedia.org/wiki/Lightweight_Linux_distribution](http://en.wikipedia.org/wiki/Lightweight_Linux_distribution)
If you do hop be sure to go only to one which is still supported, also run it live to see if it picks up your hardware and have a look at it's repositories to make sure all the things you are likely to need are included.  The best site I know for distro's and reviews is distrowatch.com 
With luck LXDE will do the job.

Can I get that without needing a blank disc or USB because last time I just downloaded it straight to the hard drive?

A link would be most appreciated.

---

### Post by Darryl Jones on 2012-08-25
I've started using Puppy Linux now. Hopefully that's sorted it.

---

### Post by houseworkshy on 2012-08-26
You can simply install LXDE to Ubuntu online through one of the package managers.  From the applications menu select the Ubuntu Software Centre.  That will open a window, type LXDE in the search box. go for the metapackage and install.  You will be asked for your password.  Once it's in reboot and after you enter your user name but before you enter your password you will have the choice of which desktop manager to use.

Puppy is good to have around whatever you use as it can rescue things.  It's not really designed for a hd install and it doesn't have password protection, though the "fat dog pupplet" is an exception.  Nice thing to have on a stick, a few mb down on a several gig drive in exchange for an installable to portable operating system which still functions for data storage is definately worth it.  I like the way one can remaster ones own bootable disc too.  Don't install it to the hd though, it can be done but the developers themselves don't recommend it.

---

