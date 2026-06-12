---
title: "Just tried out newly released Catalyst 11.10 with oneiric"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by alphacrucis2 on 2011-10-31
I have been running Cat 11.8 from the oneiric repos as Cat 11.9 was rubbish. I saw AMD have just released Catalyst 11.10 and I thought I would try it out with Oneiric 64bit. Well its a keeper.

---

### Post by ratcheer on 2011-10-31
I'm glad to hear it. I wonder when it will make it to the repos?

Tim

---

### Post by chazdg24 on 2011-10-31
> **alphacrucis2 said:**
> I have been running Cat 11.8 from the oneiric repos as Cat 11.9 was rubbish. I saw AMD have just released Catalyst 11.10 and I thought I would try it out with Oneiric 64bit. Well its a keeper.

How did you do it, exactly?

---

### Post by alphacrucis2 on 2011-10-31
> **chazdg24 said:**
> How did you do it, exactly?

Step 1. Download driver installer from AMD (64 bit version)

[http://www2.ati.com/drivers/linux/at...x86.x86_64.run](http://www2.ati.com/drivers/linux/at...x86.x86_64.run)

Step 2. Purge old fglrx

```
sudo apt-get --purge remove fglrx*
```

Step 3. Generate packages from installer (takes a while).

```
sudo sh ati-driver-installer-11-10-x86.x86_64.run --buildpkg Ubuntu/oneiric

```

Step 4. Install the three generated packages

```
sudo dpkg -i *.deb
```

Step 5.

```
sudo aticonfig --initial -f
```

Step 6.

Reboot. Will take longer than normal because ureadahead will be triggered to reprofile.


Notes. Step 3 requires some extra packages which you may or may not have installed. You need at least build-essential. I think the required packages are listed in the ubuntu ATI binary driver howto doc. Step 5 may or may not be necessary these days. I do that out of habit.

---

### Post by chazdg24 on 2011-11-01
> **alphacrucis2 said:**
> Step 1. Download driver installer from AMD (64 bit version)

[http://www2.ati.com/drivers/linux/at...x86.x86_64.run](http://www2.ati.com/drivers/linux/at...x86.x86_64.run)

Step 2. Purge old fglrx

```
sudo apt-get --purge remove fglrx*
```

Step 3. Generate packages from installer (takes a while).

```
sudo sh ati-driver-installer-11-10-x86.x86_64.run --buildpkg Ubuntu/oneiric

```

Step 4. Install the three generated packages

```
sudo dpkg -i *.deb
```

Step 5.

```
sudo aticonfig --initial -f
```

Step 6.

Reboot. Will take longer than normal because ureadahead will be triggered to reprofile.


Notes. Step 3 requires some extra packages which you may or may not have installed. You need at least build-essential. I think the required packages are listed in the ubuntu ATI binary driver howto doc. Step 5 may or may not be necessary these days. I do that out of habit.

I would do this on a clean install, so I assume there are other packages required.  Also, I have a 64 bit system.  When I have done this in the past, Oneiric would'nt boot.  I'm trying to learn this stuff, but I am somewhat frustrated by this process.  It wasn't pretty with 11.9.

Any other words of wisdom are appreciated!

---

### Post by FallenUnia on 2011-11-01
Just a note for anyone wishing to try this, I had to install dh-make, execstack and dh-modaliases

---

### Post by aeronutt on 2011-11-01
> **alphacrucis2 said:**
> I have been running Cat 11.8 from the oneiric repos as Cat 11.9 was rubbish. I saw AMD have just released Catalyst 11.10 and I thought I would try it out with Oneiric 64bit. Well its a keeper.

What hardware do you have (integrated and AMD GPU)?
(I keep waiting for Catalyst to work on my hardware, but it never has. Intel i3 graphics, and AMD Radeon HD 6630 discrete GPU.)

---

### Post by FallenUnia on 2011-11-01
I ran ```
 sudo sh ati-driver-installer-11-10-x86.x86_64.run --buildpkg Ubuntu/oneiric

``` that command. 

Succesfully generated three .deb files which I installed using dpkg. I think everything works, however I have no amdcccle installed. What is happening here? I'm quite sure I installed its .deb file and even re-installing it (it didn't say it was installed already) doesn't work: it won't show up.

Now that makes me doubt on whether or not I succesfully installed Catalyst 11.10. Is there any way to check this, and is there any way I can get amdcccle to work?

Thanks in advance guys!

**EDIT:** Fixed! See two posts below!

---

### Post by chazdg24 on 2011-11-01
> **FallenUnia said:**
> I ran ```
 sudo sh ati-driver-installer-11-10-x86.x86_64.run --buildpkg Ubuntu/oneiric

``` that command. 

Succesfully generated three .deb files which I installed using dpkg. I think everything works, however I have no amdcccle installed. What is happening here? I'm quite sure I installed its .deb file and even re-installing it (it didn't say it was installed already) doesn't work: it won't show up.

Now that makes me doubt on whether or not I succesfully installed Catalyst 11.10. Is there any way to check this, and is there any way I can get amdcccle to work?

Thanks in advance guys!

Do you have Compiz installed?  Once I install that for the FGLRX driver, Catalyst shows up.

---

### Post by FallenUnia on 2011-11-01
Well no, I am running KDE (Kubuntu). Anyways, I purged all the fglrx packages again and reinstalled my .debs, now it works! (:

---

### Post by chazdg24 on 2011-11-01
> **FallenUnia said:**
> Well no, I am running KDE (Kubuntu). Anyways, I purged all the fglrx packages again and reinstalled my .debs, now it works! (:

I don't understand that, but this entire issue is bizarre.

---

### Post by Mark Phelps on 2011-11-01
> **aeronutt said:**
> (I keep waiting for Catalyst to work on my hardware, but it never has. Intel i3 graphics, and AMD Radeon HD 6630 discrete GPU.)

It's not specifically an AMD driver problem.  It's a problem with switchable graphics PCs that have two very different graphics chipsets.

So, waiting for newer AMD drivers is not going to fix your problem.

---

### Post by chazdg24 on 2011-11-01
Shouldn't a tutorial exist for this sort of thing?  I found the Ubuntu tutorial at best, vague.  :confused:

---

### Post by aeronutt on 2011-11-01
> **Mark Phelps said:**
> It's not specifically an AMD driver problem.  It's a problem with switchable graphics PCs that have two very different graphics chipsets.

So, waiting for newer AMD drivers is not going to fix your problem.

Ahh..I didn't know that. Certainly, catalyst lets me switch/set default in Windows. But to be clear, Catalyst simply doesn't work for me in Ubuntu as the graphics driver, much less let me switch.

---

### Post by CowzRule on 2011-11-01
> **chazdg24 said:**
> Shouldn't a tutorial exist for this sort of thing?  I found the Ubuntu tutorial at best, vague.  :confused:

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by chazdg24 on 2011-11-02
> **CowzRule said:**
> [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Ya, know all about it.  Unfortunately, the installation of 11.9 did not go well, leaving me with a hosed system.  The tutorial wasn't much help.

---

### Post by ratcheer on 2011-11-02
I hosed my system following one of those tutorials once, too. From now on, I will just wait for the new fglrx to get to the official repos.

Tim

---

### Post by MAFoElffen on 2011-11-02
> **chazdg24 said:**
> Shouldn't a tutorial exist for this sort of thing?  I found the Ubuntu tutorial at best, vague.  :confused:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]Much credit to user "3602" for helping me keep this up to date with current workarounds:
**[Installing ATI Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10950714&postcount=334")**[/SIZE][/COLOR][/SIZE][/COLOR]

Also noted there is ATI's "switchable graphics" disclaimer and its related bug report. 

If you ever need to quickly find that link, Go to my sticky (link below). Post 2 is now a Table of Contents: 
**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

---

### Post by chazdg24 on 2011-11-02
> **MAFoElffen said:**
> [COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]Much credit to user "3602" for helping me keep this up to date with current workarounds:
**[Installing ATI Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10950714&postcount=334")**[/SIZE][/COLOR][/SIZE][/COLOR]

Also noted there is ATI's "switchable graphics" disclaimer and its related bug report. 

If you ever need to quickly find that link, Go to my sticky (link below). Post 2 is now a Table of Contents: 
**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

Wow, an excellent resource.  Thanks to you and user "3602".  I'm tempted to try again.

Anybody hear anything about and updated fglrx driver that would work with Gnome 3.2?  I would like to stick with Ubuntu, but I'm not a fan of Unity.  Not a big fan of Gnome 3.2 for that matter, but I really would like to get my hands dirty with it before I make a decision.
Thanks.  :)

---

### Post by ratcheer on 2011-11-02
@chazdg24 - There are several recent articles at Phoronix about the latest and future Catalyst releases.

[http://www.phoronix.com/scan.php?page=news_item&px=MTAxMDM](http://www.phoronix.com/scan.php?page=news_item&px=MTAxMDM)

[http://www.phoronix.com/scan.php?page=news_item&px=MTAwODg](http://www.phoronix.com/scan.php?page=news_item&px=MTAwODg)'

[http://www.phoronix.com/scan.php?page=news_item&px=MTAwOTM](http://www.phoronix.com/scan.php?page=news_item&px=MTAwOTM)

Tim

---

### Post by chazdg24 on 2011-11-02
> **ratcheer said:**
> @chazdg24 - There are several recent articles at Phoronix about the latest and future Catalyst releases.

[http://www.phoronix.com/scan.php?page=news_item&px=MTAxMDM](http://www.phoronix.com/scan.php?page=news_item&px=MTAxMDM)

[http://www.phoronix.com/scan.php?page=news_item&px=MTAwODg](http://www.phoronix.com/scan.php?page=news_item&px=MTAwODg)'

[http://www.phoronix.com/scan.php?page=news_item&px=MTAwOTM](http://www.phoronix.com/scan.php?page=news_item&px=MTAwOTM)

Tim

Interesting reading, but not what I asked.  Is an updated fglrx driver forthcoming so a newcomer to Ubuntu can easily install a driver that works?

I think that is a fair question.

---

### Post by ratcheer on 2011-11-02
Sorry. I was just trying to give some solid info on what the driver does and what is expected in the future.

Tim

---

### Post by chazdg24 on 2011-11-03
> **ratcheer said:**
> Sorry. I was just trying to give some solid info on what the driver does and what is expected in the future.

Tim

No, I'm sorry.  I was rude and did find those article quite informative.

Charlie

---

### Post by ratcheer on 2011-11-03
Thank you.

Tim

---

### Post by moteprime on 2011-11-03
I installed the 11.10 catalyst driver. Except for some missing pixmap lines, there was no errors.

> Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 9.


It seems to work fine, faster than 11.8, and the open source driver.
But it looks like i have some missing Unity functions.
The launcher seems to have broke somehow. the trash can is always on, the launcher scrolls ok, but cannot do that collapse thing where the icons are tilted or pressed together so that all the icons are shown. The alt+tab function is small and not so cool looking, and workspace switching also functions "oldstyle".

---

### Post by FallenUnia on 2011-11-03
Has anyone tested this driver with GNOME Shell? On several resources I read that it's fixed (one of them being the first link ratcheer/Tim posted), but on my most trusted source (Vi0L0, Arch Linux Catalyst packager) I read that window movement is still lagging. 

Can anyone confirm/elaborate on how it is on Ubuntu?

---

### Post by gigi17 on 2011-11-03
> **FallenUnia said:**
> Has anyone tested this driver with GNOME Shell? On several resources I read that it's fixed (one of them being the first link ratcheer/Tim posted), but on my most trusted source (Vi0L0, Arch Linux Catalyst packager) I read that window movement is still lagging. 

Can anyone confirm/elaborate on how it is on Ubuntu?

I can confirm that catalyst 11.10 works without problems on my Ubuntu 11.10-64bit.Spec of my comp is:amd a6-3650 with amd 6530hd grafic,asrock a75m-hvs fm1 mobo,8 gig corsair vengence 1600mhz ram,wd 1.5 tera 7200 sata2 hard disc.

---

### Post by FallenUnia on 2011-11-03
I'm not talking about just Ubuntu, I'm specifically interested in GNOME Shell :)

---

### Post by marin123 on 2011-11-03
> **alphacrucis2 said:**
> I have been running Cat 11.8 from the oneiric repos as Cat 11.9 was rubbish. I saw AMD have just released Catalyst 11.10 and I thought I would try it out with Oneiric 64bit. Well its a keeper.

How is 2D performance? I mainly watch movies and I hate video stuttering (or tearing). That is why I stick to xorg-radeon. It has way better 2D performance.

---

### Post by ratcheer on 2011-11-03
Well, I upgraded fglrx, fglrx-amdcccle, and gnome-shell from the repos, today, but gnome-shell still has the multi-colored bands across the top panel and some very squirrely fonts in the menus and dialogs. I guess they still haven't gotten together on anything that works, yet.

fglrx 2:8.881-0ubuntu4.1
fglrx-amdcccle 2:8.881-0ubuntu4.1
gnome-shell 3.2.1-0ubuntu1

Tim

---

### Post by FallenUnia on 2011-11-04
^ Thanks! That'll leave me with KDE for a while!

---

### Post by ratcheer on 2011-11-04
Is there any way to know which fglrx version is which Catalyst version? They never mention Catalyst versions on Launchpad, which is where I think it should be specified. And the AMD Catalyst Control Center just displays the Catalyst version from the first time it was installed, then it never changes with subsequent upgrades.

I read instructions for fixing the Control Center displayed version in the Archbang Linux forums, but it has to be done every time fglrx is upgraded. It hardly seems worth the trouble. It involves shutting down the display manager, deleting a particular file, and reinitializing the Catalyst Control Center. They were not very specific about how to do that last step, so I'm not messing with it.

Tim

---

### Post by FallenUnia on 2011-11-04
Fail, sorry. See below!

---

### Post by FallenUnia on 2011-11-04
> **ratcheer said:**
> 
I read instructions for fixing the Control Center displayed version in the Archbang Linux forums, but it has to be done every time fglrx is upgraded. It hardly seems worth the trouble. It involves shutting down the display manager, deleting a particular file, and reinitializing the Catalyst Control Center. They were not very specific about how to do that last step, so I'm not messing with it.

Tim

When I was on Arch (base of Archbang), it was just ```
sudo rm /etc/ati/amdpcsdb
```

from init 1 (sudo init 1 to get there)

**EDIT:** And the last step is just rebooting / restarting X

---

### Post by FallenUnia on 2011-11-04
Oh crap that should've been an edit, not a new post. Sorry fellas!

---

### Post by ratcheer on 2011-11-04
I guess my real question is, can something similar be done in Ubuntu to get Catalyst Control Center to display the current driver version?

Tim

---

### Post by FallenUnia on 2011-11-05
> **ratcheer said:**
> I guess my real question is, can something similar be done in Ubuntu to get Catalyst Control Center to display the current driver version?

Tim

I guess you can use the same instructions. Just try? It's not an essential file you're removing; it will automatically re-create it when you reboot / start X again.

---

### Post by ratcheer on 2011-11-06
> **FallenUnia said:**
> I guess you can use the same instructions. Just try? It's not an essential file you're removing; it will automatically re-create it when you reboot / start X again.

It did not work. Yes, the file was recreated when I rebooted, but the driver version is still reported as 11.6 in the Control Center. :(

Tim

PS - No, I neglected to do the init 1 part. When I try sudo init 1, my system hangs in the shutdown process. I thought I would be able to do a recovery mode reboot and delete the file from the root prompt, but when I do that, it tells me it is a read-only filesystem. What on earth is going on?

---

### Post by ratcheer on 2011-11-06
Ok, I got it fixed, for now.

First, a Google search shows that many people have apparent hanging problems when trying to "sudo init 1" from Ubuntu (and Debian). A bug on Launchpad goes on for months of posts with no resolution, then they just changed the status to Expired. I say "apparent" because it seems that you can type blindly and get the console terminal to do things, but it isn't very useful if you cannot see what is going on.

I did Crtl-Alt-F1 and ran "sudo service lightdm stop". Lightdm never really stopped, its status just changed to stop/waiting. But I deleted the /etc/ati/amdpcsdb file anyway, rebooted, and now the Catalyst Control Center shows the driver version as 11.8 instead of 11.6. Not what I had hoped to see, but I assume it is correct.

So, the latest fglrx in the repos from two days ago is still some version of 11.8, not 11.10.

Thanks,
Tim

---

### Post by chazdg24 on 2011-11-16
ATI 11.11 Drivers were released yesterday and they fix any residual issues that 11.10 did not.  I am very happy!  :D

---

### Post by ratcheer on 2011-11-17
I followed the instructions in post #4 and they worked perfectly. Thanks very much, alphacrucis2. I am now another happy user of Catalyst 11.11.

Tim

---

### Post by Lumsdoni on 2011-11-17
Has anyone tried gnome 3 shell yet? 11.10 drivers left me having to reinstall ubuntu.

---

### Post by ratcheer on 2011-11-17
> **Lumsdoni said:**
> Has anyone tried gnome 3 shell yet? 11.10 drivers left me having to reinstall ubuntu.

Yes, I am running gnome-shell, now. That is the main reason I wanted to get these drivers installed.

gnome-shell is much, much better with Catalyst 11.11, but still not perfect. One thing I have specifically noticed is that, if I hover the mouse pointer over an active graphic element, such as some buttons or smilies, I see a textual description of the element that is in that squirrely font that so many things were displayed as with earlier drivers.

But, the top panel and the system menu now look great.

Tim

---

### Post by moteprime on 2011-11-18
Arghh. Ended up uninstalling catalyst 11.11, maybe the graphics was faster but my hole computer got a lot slower. It's a relief now that i'm back on open source.

---

### Post by chazdg24 on 2011-11-19
> **moteprime said:**
> Arghh. Ended up uninstalling catalyst 11.11, maybe the graphics was faster but my hole computer got a lot slower. It's a relief now that i'm back on open source.

For me, 11.11 works much better than 11.10.  There are still a few bugs but I find Ubuntu faster than with the 11.10 driver installed.

Stay away from themes, Gnome will flicker with both drivers with themes installed.  Also, I have flickering if I don't log out from the most basic updates.  Otherwise, I finally got things working the way I want and am looking forward to 11.12 drivers.

---

