---
title: "Update Manager doesn't show Hardy Update"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by scbash on 2008-05-23
Hi all-

I'm new to the forums, but I've been using Ubuntu at home and work for a little under a year now (all systems are running 7.10).  Last week my home system went through the Hardy upgrade with no problem, but for some reason on my work machine Update Manager doesn't show the Hardy update as available.  The upgrade instructions imply the Hardy update won't show if the machine doesn't have all the 7.10 fixes, but I can't figure out why this machine wouldn't...

A few details:  the machine is an 8-way quad-core AMD Opteron workstation.  I currently have 7.10 Desktop 64-bit installed on it.  Because of the number of cores, I have both the original desktop kernel and a custom 32 core kernel available.

At first I thought Update Manager wasn't happy with the custom kernel, so I rebooted using the standard desktop kernel, but that hasn't changed the situation.  I've refreshed the repository both from Update Manager and Synaptic -- neither program shows any updates available and "Fix broken packages" didn't do anything.

Am I missing something obvious?  Are there any tools I can use to find out why Update Manager isn't showing the upgrade?  I'm not new to Linux, but as I said I'm fairly new to Ubuntu, so I'm not very familiar with diagnosing problems like this.

Any help will be appreciated.  Thanks for your time!

Stephen

---

### Post by housam on 2008-05-23
Try sys. >> admin >> software sources >> check all the boxes in the first 3 categories.then check for the updates through the update manager. this may help.

---

### Post by scbash on 2008-05-23
> **housam said:**
> Try sys. >> admin >> software sources >> check all the boxes in the first 3 categories.then check for the updates through the update manager. this may help.
Following that procedure, the new boxes checked are "pre-released updates" and "unsupported updates" (all others were previously checked).  The new boxes do give me updates to apply, but do I want to introduce pre-release and unsupported updates to my everyday work machine?

Thanks,
Stephen

---

### Post by housam on 2008-05-23
> **scbash said:**
> Following that procedure, the new boxes checked are "pre-released updates" and "unsupported updates" (all others were previously checked).  The new boxes do give me updates to apply, but do I want to introduce pre-release and unsupported updates to my everyday work machine?

Thanks,
Stephen

No, you don't have to do so. but just to confirm that all boxes are checked. also check that you download from the main server.

---

### Post by scbash on 2008-05-27
> **housam said:**
> No, you don't have to do so. but just to confirm that all boxes are checked. also check that you download from the main server.
Finally getting back to this -- sorry for the long dead time...  I checked and the machine was pointing at "Server for United States" rather than "Main server".  I changed it and forced a refresh, but still no Hardy update.  Any other thoughts?

Thanks,
Stephen

---

### Post by gnr on 2008-06-03
Hi stephen, try..

gksudo gedit /etc/apt/sources.list
change every word gutsy to hardy (be sure to leave the # in front of cd)
sudo apt-get update
sudo apt-get dist-upgrade


^^^ ok probably shouldn't try this, use it as a last resort before formatting.

---

### Post by tgrimley on 2008-06-03
> **gnr said:**
> Hi stephen, try..

gksudo gedit /etc/apt/sources.list
change every word gutsy to hardy (be sure to leave the # in front of cd)
sudo apt-get update
sudo apt-get dist-upgrade

I'd try ```
gksu "update-manager -c" 
``` before that

---

### Post by scbash on 2008-06-03
> **gnr said:**
> gksudo gedit /etc/apt/sources.list
change every word gutsy to hardy (be sure to leave the # in front of cd)
sudo apt-get update
sudo apt-get dist-upgrade
So I did the first two steps and then ran the update-manager.  Update-manager reports over 500 updates available, but says it can't perform several of them (including packages like apt, dpkg, cupsys, eog, ...).  It worries me that system-critical packages like apt and dpkg aren't "upgradable".  What do people think I should do?

Thanks,
Stephen

---

### Post by tgrimley on 2008-06-03
I'd revert your sources to gutsy and rerun update-manager until you're clean, doing update-manager -c and waiting for it to pop up.  In my experience it's not good to just change all the repos.

---

### Post by scbash on 2008-06-03
> **tgrimley said:**
> I'd revert your sources to gutsy...
In other words undo the two steps I did above?  (in which case, yes, I've already done that)
> **tgrimley said:**
> ... and rerun update-manager until you're clean, doing update-manager -c and waiting for it to pop up.  In my experience it's not good to just change all the repos.
Well that's just the problem...  update-manager isn't showing any pending updates, and doesn't show the Hardy upgrade as available.  I just tried another AMD64 system and it doesn't show the Hardy update either.  Talking with coworkers, their x86 machines do show the update as available.

All these machines are behind a proxy server, but are configured to fetch updates and packages through the proxy server (just got a few packages in Synaptic this afternoon).  Are there any other common problems that could be causing this?

Thanks,
Stephen

---

### Post by tgrimley on 2008-06-03
Yes, did you run it with the -c flag tho?  You didn't say you did or I am blind..

---

### Post by scbash on 2008-06-03
> **tgrimley said:**
> Yes, did you run it with the -c flag tho?  You didn't say you did or I am blind..
I thought I had, but to double check I just did it now...  And it worked...  I must be crazy.  So that problem has been solved.  Thanks!

But out of curiosity: why did the AMD64 systems not automatically show the update?  Is there a difference in how update-manager runs on 32- and 64-bit systems?

Thanks,
Stephen

---

