---
title: "Can't launch firefox"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by doskyis on 2010-07-23
I just upgraded to Ubuntu 10.04 and for some reason, firefox doesn't open. I click on the firefox icon and it attempts to open but it just doesn't. When I click repeatedly on firefox, an error message appears saying firefox is already running and i need to either close it or restart the system. 
PLEASE HELP ME!

---

### Post by ServerStorm on 2010-07-23
Hi doskyis,

Sometimes Firefox's executable process does not close, when a user has closed their Firefox. The easiest way to tell if this has happened is to:

[LIST=1]
[*]Go to System Administration (GNOME) or System on Kubuntu
[*]Open "Systems Monitor"
[*]Select the Processes Tab
[*]Select the header "Process Name" to alphabetically organize the processes
[*]Scroll down to see if the firefox-bin is running. If it is then, select 'firefox-bin' and at the bottom right select 'End Process'
[*]Finally relaunch Firefox.
[/LIST]
Regards, 
Steve

---

### Post by doskyis on 2010-07-23
Thanks for your help. I want to get as many potential solutions to take home with me since I won't be able to get on the internet if it doesn't work. The thing is I have not been able to open firefox since I upgraded to Ubuntu 10.04, so I'm not sure if it was ever running in the background. When I click on the firefox icon, it acts like it's loading, and sometimes, it even opens for a split second before it closes automatically.
I'd appreciate any other suggestions you might have. I can print them all and try each one. 
Thanks!

---

### Post by ServerStorm on 2010-07-23
Hi [doskyis]("http://ubuntuforums.org/member.php?u=1029887"),

If you try what I suggested earlier and it does not work, then I would uninstall and then reinstall firefox.

Use synaptic package manager and filter for firefox. The 'completely remove it'. Once the removal is complete then filter again for firefox and mark it for installation and select apply.

Your existing firefox bin maybe got corrupted during the update, so this has a good shot of fixing it.

Regards,
Steve

---

### Post by doskyis on 2010-07-23
I have a feeling I'm gonna have to reinstall firefox altogether. Thanks for the instructions of how to do that. I'll let you know how it goes.

---

### Post by Elmer Fudd on 2010-07-23
The FireFox re-install should solve your problem but...
Even if Firefox wont run that should not keep you off the internet. Use synaptic to install any of a number of browsers to use as a backup if an update of Firefox hicups your system. Midori,Chrome,Chromium,Opera. Then you will still have an avenue for online support.

Let us know

---

### Post by linux18 on 2010-07-23
ubuntu comes with a backup browser by default: w3m

---

### Post by doskyis on 2010-07-23
Thanks Guys!
I reinstalled Firefox but it didn't work. Problem remained the same, so I installed Chrome and Midori. They both work great! I'm not sure what the deal is with firefox on my laptop but I really don't care as long as I can browse the internet one way or another.

Thanks again.

---

### Post by brewmaster95060 on 2010-08-10
right after update to UBUNTU 10.04 
same problem
synaptic package manager
gives warning
while removing firefox, Directory
/usr/lib/firefox-addons/plugins/
not empty so not removed

try run firefox
claims another copy is running and exits.

---

### Post by brewmaster95060 on 2010-08-10
Well
read a tip here:
[http://www.webupd8.org/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html](http://www.webupd8.org/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html)
went here:
[http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

crossed my fingers and did this:
rm -r ~/.mozilla/firefox

1.2 - Deleting Profile Folder

Another option would be to simply delete the folder ~/.mozilla/firefox and start Firefox. This will force Firefox to create a new clean profile. Please keep in mind that this will completely delete all your Firefox settings, passwords, bookmarks, extensions, themes, cookies and other configuration files. 

To do that from a terminal, close Firefox and simply run the following command (you can't do that while Firefox is open):

rm -r ~/.mozilla/firefox
SIGH!

---

### Post by brewmaster95060 on 2010-08-10
runs longer before crash

---

### Post by ericlb on 2010-08-20
Hi,  I have the same problem.  Upgraded from 8.04 to 10.04. All seemed to work well until I tried to launch Firefox.  It started (saw it in the task bar) but then a message ...  Firefox is already running. Close it or restart.  I rebooted and then tried Firefox... same issue.
Firefox creates a .parentlock file just before it does not launch.  I delete the .parentlock and still no launch!
Tried  firefox -safe-mode    no launch!!
Tried firefox -P and created a new profile.  Same problem, could not launch the new profile!!!

Messages reports  

requested_mask="k::"  denied_mask="k::" and then creates the -parentlock file

HOW can I get Firefox to launch?

---

