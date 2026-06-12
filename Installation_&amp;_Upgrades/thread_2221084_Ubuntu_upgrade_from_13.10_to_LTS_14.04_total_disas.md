---
title: "Ubuntu upgrade from 13.10 to LTS 14.04 total disaster"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by ray_silva on 2014-04-30
After long working to get 13.10 working nicely, I did some reading on the supposedly stable 14.04 release and decided to do an upgrade. Well, now my Ubuntu is totally destroyed and not working at all. Sorry, this was not "via update manager."

I ran:
sudo apt-get -f dist-upgrade
During process that seemed to be running fine, I got a crash and have not been able to recover even back to 13.10.

This is where I wish there were a way to restore the entire system back to what it was before the attempted upgrade.

Is there any help, or am I completely screwed?

Please, no "you should have backed up your entire system before attempting the upgrade" - I don't need to be reminded of this failure.

---

### Post by deadflowr on 2014-04-30
If that's the command you ran, then you are still on 13.10.
dist-upgrade only upgrades packages for the existing install and DOES NOT upgrade releases.

Quite possible to resolve by running the fix broken packages command.
First though run
```
sudo apt-get update
```
this will bring the packages available for you up to date.
then try
```
sudo apt-get -f install
```
this will try to fix any broken packages you might have.


For the record, the command to upgrade releases is
```
do-release-upgrade
```
You may or may not need to use sudo with that.

---

### Post by ray_silva on 2014-04-30
OK, after pfutzing with possible solutions, I hit upon an advanced recovery start (holding shift key after BIOS boot). The old (13.10) install seemed to start up but I got errors and a red icon at top of desktop telling me there were errors and to run the package manager from right click. Tried but no such thing ran and the system again just locked and crashed.

At this point I'm just going to leave it alone and see if I get any suggestions before I make it even worse.

---

### Post by ray_silva on 2014-04-30
Thanks, I'm trying to see if I can get back to where I can get to a terminal window. Nothing yet.

---

### Post by ray_silva on 2014-04-30
Oops, that quick reply was meant for forum moderator deadflowr.

---

### Post by ray_silva on 2014-04-30
After seemingly dead for a very long period of time I held the power button to shut down and re-start but noticed that it was apparently doing something. I saw a message about Clam AV just before it shut down. I'll try restarting and let it do whatever it was trying to do. It may take a long time.

---

### Post by ray_silva on 2014-04-30
What if I download 14.04 iso, burn image to DVD, and use that to install it? Will that leave intact the files and configurations I had already installed? For example, my Samba server?

---

### Post by Ubi_one_2014 on 2014-04-30
suggestion is to download 14.04 iso, boot from that as a live dvd
backup all files you want, and do a fresh installation

---

### Post by ray_silva on 2014-04-30
Impossible. The problem is that the install crashed. I want to be able to recover my installs and configuration. Can't backup files if can't get the crashed system back up in at least some way.

---

### Post by ray_silva on 2014-04-30
OK, I installed 14.04 on a separate drive. Now, what I want to do is rescue what I had in the drive where 13.10 was installed. I'd like to begin by rescuing my pictures and documents. I would also like to rescue at least my configuration file for my Samba server installation. I'll figure out and rebuild everything else. I know that I should have backed up everything first. Maybe I was just too trusting to think that an Ubuntu upgrade would go smoothly. Really no difference from the headaches and disasters in Windows installs. In Windows at least if this had happened I could easily restore my system to a restore point before the install. BTW, I did precisely run this command and the result was a complete disaster -  [COLOR=#000000][FONT=Ubuntu Mono]do-release-upgrade[/FONT][/COLOR]

---

### Post by mörgæs on 2014-04-30
They often are. 
If you look around you will see most people here recommending a clean install.

---

### Post by ray_silva on 2014-04-30
OK folks, thanks for the suggestions of clean installs after the fact. Now, can anyone help me address the fact that I have data in that crashed disk that I need to recover?

---

### Post by deadflowr on 2014-05-01
> **ray_silva said:**
> OK folks, thanks for the suggestions of clean installs after the fact. Now, can anyone help me address the fact that I have data in that crashed disk that I need to recover?

Is the second drive big enough to copy the data over to it?
If so, then open the program "Files" and look for the original drive in the side pane(it should be under Devices).
Click on it and it will open.
Locate the Home folder, then go to you users folder and begin copying the files/folders.
You can copy/paste from one drive to the other.
rinse and repeat.

Sidenote, I'm confused about which command you ran that caused the breakdown.
Initially it was dist-upgrade, but you later on state it was do-release-upgrade.

---

### Post by ray_silva on 2014-05-01
deadflowr,


Sorry about the confusion I caused. Initially I had written that I did the attempted upgrade through the upgrade manager, but that was wrong. I edited to correct that. What I did was run the command "sudo apt-get -f dist-upgrade."


Yes, I had first run the two commands to get updates and install them, but realized (as you noted) that this does not upgrade from one version of Ubuntu to another.


I'm not sure where I got the upgrade command, but it is different than the one you mentioned: "do-release-upgrade."


Anyway, I used the first command mentioned above.


Everything seemed to be going fine for quite a while, then suddenly I got an error message and the whole system crashed.


I've tried connecting both the old drive (with 13.10) and the new one (14.04), but for some reason my computer tries to boot from the old one. Only when I disconnect the old one does the new installation boot and start up.


So, I'm trying to figure out how to boot up something that will allow me to read the old drive and get the data files out of it.


Thanks for your help.

---

