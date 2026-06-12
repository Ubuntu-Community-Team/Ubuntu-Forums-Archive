---
title: "Back up home and then new installation"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by tea for one on 2008-10-10
Good evening

I intend to install Intrepid Ibex during November after some inevitable undiscovered bugs are fixed.

This will be a new installation from a CD not an upgrade via the internet which I understand is sometimes imperfect.

I intend to back up my home directory to an external device, install a clean version of 8.10 and then restore my back up. I use Gnome if that is important information.

I have added other software to my existing 8.04 such as Wine, Thunderbird, Grsync, VLC etc and I am unclear if these applications will reappear when I restore my back up or do I have to visit the repositories to download and install them again.

Thanks in advance

---

### Post by lonniehenry on 2008-10-10
Sounds like a good plan.  When you install Ibex  (8.10) and get the connection to the net running, then all of the programs you mentioned are in the add remove programs.  Just enable the repos and just install them and use them.  I have found Ibex to be stable and my hardware works well with it. I have had minor hiccups in the updates but no show stoppers. Good luck.

---

### Post by tea for one on 2008-10-10
I realise that the software is in the repository and that I can reinstall them anytime, but I am trying to ascertain what exactly is in the "hidden" files of my home directory.

I would rather burn intrepid to a CD and test it in live mode before installation because I have had failures in the past. For example:-

7.04 worked flawlessly
7.10 failed dismally
8.04 worked flawlessly except for "log in" screen

---

### Post by lonniehenry on 2008-10-10
After you try out the live CD and if you have space on your harddrive, you could partition your free space and install Ibex next to your Hardy install.  In the installation you have the option of moving over your preferences, bookmarks, etc. from your hardy install.  I did that as I wanted to retain my Hardy install as I was just testing Ibex.  You will be able to mount your Hardy drive partition and move files to Ibex home. You will get the benifits of a fresh install and the ease of transfering your files.  Backing up your hardy /home  to an external drive or dvd just to make sure is recommended of course.

---

### Post by tea for one on 2008-10-10
Yes, I do have some space to install Intrepid next to Heron and I will certainly give this due consideration.

However, do you know if the "hidden" files in my home directory contain my added applications such as Wine & Grsync or do I have to download them again?

Time for bed now, I will be up with a lark tomorrow.

---

### Post by sokopok on 2008-10-10
All the hidden files in your home folder are your personal configuration. No applications are installed in your home. If you want to backup some of this configuration (like firefox history/bookmarks, you kde settings, emails, ...) make sure you keep these files at hand.

---

### Post by tea for one on 2008-10-11
Thanks for the reply, it is becoming a bit clearer now.

Therefore, I back up my home directory, perform a clean installation of Intrepid (after testing in live CD mode), restore the home data and then visit synaptic via add/remove to download copies of applications that I had added to my previous Hardy OS.

Is there a simple method of backing up applications before installing Intrepid so that I do not have to download them again. 

I am not averse to downloading again but it seems that the 'phone companies benefit from additional usage which could be avoided because the user has existing copies of applications that have been wiped with a safe method of installation.

I suspect that I'm missing a trick here?

---

### Post by woodenbrick on 2008-10-11
It's pretty likely that most of the packages you have installed at the moment will have been upgraded in Ibex, meaning you have no choice but to download them again. If you wanted, you could backup /var/cache/apt/archives on your current install, and dump it back in after. Anything that doesn't have a different version wont be redownloaded, but I doubt it will save you an amazing amount of bandwidth.

---

