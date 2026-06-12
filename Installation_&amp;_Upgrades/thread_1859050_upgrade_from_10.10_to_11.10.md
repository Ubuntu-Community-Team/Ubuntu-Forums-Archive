---
title: "upgrade from 10.10 to 11.10"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by rummy77 on 2011-10-13
I've scoured the forum a bit, and, having not found precisely what I was looking for, would like to ask for a little bit of advice.

I installed 10.04 on my computer originally, dual-booting alongside Win7 (need it for one program twice a year).  When 10.10 was released I used the upgrade button in the update manager.  I did not upgrade to Natty because I did not care for Unity, but with GNOME 3 out I'm interested in moving to Oneiric.  

The dilemma is whether to do a clean install or whether to upgrade to Natty and then Oneiric using the upgrade button (twice).  I love ubuntu and use it 99% of the time, but I'm not very adept in the command line (yet).  The upgrade button seems easy, but I realize that there is an immense amount of changes happening to the system when I click that.  A clean install would be, of course, much cleaner, but I haven't had any experience doing a clean install over an existing linux install.

So I guess that what I'm asking, fundamentally, is: how difficult is it to do a "clean install" over my existing ubuntu install without destroying my dual-boot setup?  Will the process be akin to just popping in the new CD and letting ubuntu do everything itself?  Or will I have to worry about GRUB issues and lost Windows installs?

Thanks for any advice

---

### Post by mionescu on 2011-10-13
I have been doing updates for all my systems for a long time. Most of the times things went smoothly and you do not have to redo all the customization that you might have done and your files in the home folders should still be there (but make a back-up, just in case). Sometimes, however, things can get broken in an update. Since you want to upgrade from 10.04 to 11.10 I will advise you to do a fresh install. This way you can first check using the live cd that everything works. Please back-up your data before doing the install. When you install just select that Ubuntu takes over the previous Ubuntu installation and it should work just fine.

---

### Post by MG&amp;TL on 2011-10-13
You can usually choose the 'upgrade Ubuntu XX.XX to Ubuntu YY.YY' option. Boot a USB and find out.

It is worth learning the command-line, but I appreciate not all users will want to.

---

### Post by Devi 710 on 2011-10-13
I would recommend doing a clean install. I find upgrades feel bloated and slow.

Backup all your Ubuntu and Windows files.
Boot the live CD/USB and choose to install.
* When you get to the partition part, you might have to go the 'Advanced' settings and choose a Mount Point of "/" (this is what I have had to do in the past, though it might have changed)

I hope that helps

---

### Post by Slim Odds on 2011-10-13
> **MG&TL said:**
> You can usually choose the 'upgrade Ubuntu XX.XX to Ubuntu YY.YY' option. Boot a USB and find out.

It is worth learning the command-line, but I appreciate not all users will want to.

This not true.

You cannot skip a version except when going from one LTS release to another LTS release.

---

### Post by 23dornot23d on 2011-10-13
Although you say it cannot be done ...... someone has already done it ....

[http://ubuntuforums.org/showthread.php?t=1858960](http://ubuntuforums.org/showthread.php?t=1858960)

and I too was under the impression that it should not be done .....
although reading more threads that user is now having a few problems .... 

[**LINK**]("http://ubuntuforums.org/showpost.php?p=11338099&postcount=3")

I prefer a fresh install and its safer - retaining your old system too .......

---

### Post by rummy77 on 2011-10-13
I downloaded the image, put it on a USB drive, backed up all of my files, and am doing the upgrade now.

From the USB drive 11.10 booted fine, I selected the "try ubuntu" option, and had a chance to make sure all of my hardware was working.  

I clicked the "Install Ubuntu 11.10" icon, and was presented with four options.  I chose "upgrade 10.10 to 11.10."  It appeared to install the new OS with no problems.  Now the install dialogue states that it is "restoring previously installed packages."  It's been at this point for about an hour and my USB drive keeps flashing (is being accessed).  I'm assuming that this step is very slow because of the number of people upgrading today and the limited bandwidth of the repositories.  Hopefully in a little while it will be fine.

If for some reason everything crashes and doesn't complete, then I would presume I can just reboot with the USB and have it install 11.10 on the existing linux partition.  Here's hoping it doesn't get to that!

---

### Post by rummy77 on 2011-10-13
It's been at the same point for a while now, and the output in the terminal of the upgrade window is: ```
   	 	 	 	 	 	  ** (process:14742): WARNING **: Command line `dbus-launch --autolaunch=bd3837237c28b42b822afaad00000012 --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n 
  
 (ubiquity:4694): Gdk-WARNING **: The application 'ubiquity' lost its connection to the display :0; 
 most likely the X server was shut down or you killed/destroyed 
 the application. 
  
 Ubiquity 2.8.7 
  
 (ubiquity:15452): Pango-WARNING **: error opening config file '/root/.pangorc': Permission denied 
  
 Oct 13 16:57:02 ubuntu dbus[2791]: [system] Activating service name='org.debian.apt' (using servicehelper) 
 Oct 13 16:57:02 ubuntu AptDaemon: INFO: Initializing daemon 
 Oct 13 16:57:02 ubuntu dbus[2791]: [system] Successfully activated service 'org.debian.apt' 
 Oct 13 16:57:02 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1 
 Oct 13 16:57:02 ubuntu AptDaemon.Trans: INFO: Simulate was called 
 Oct 13 16:57:02 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/753e1f8aacfe4365beb5f4f4a96bf930 
 Oct 13 16:57:03 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1 
 Oct 13 16:57:03 ubuntu kernel: [  348.876141] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 35524, limit 35000 
 Oct 13 16:57:23 ubuntu ubiquity[15452]: Ubiquity 2.8.7 
 Oct 13 16:57:24 ubuntu ubiquity[15452]: log-output -t ubiquity laptop-detect 
                                     
 
```

Should I keep waiting?

---

### Post by Slim Odds on 2011-10-13
> **23dornot23d said:**
> Although you say it cannot be done ...... someone has already done it ....

[http://ubuntuforums.org/showthread.php?t=1858960](http://ubuntuforums.org/showthread.php?t=1858960)

and I too was under the impression that it should not be done .....
although reading more threads that user is now having a few problems .... 

[**LINK**]("http://ubuntuforums.org/showpost.php?p=11338099&postcount=3")

I prefer a fresh install and its safer - retaining your old system too .......

I wasn't saying that it can't be done, I was saying that it's not supported.

---

### Post by MG&amp;TL on 2011-10-14
Well...I'm sorry if I caused confusion, but i had a 10.04 desktop, inserted 11.04 CD, and it offered an option to keep all my files, still-supported programs and settings.

---

### Post by Slim Odds on 2011-10-14
> **MG&TL said:**
> Well...I'm sorry if I caused confusion, but i had a 10.04 desktop, inserted 11.04 CD, and it offered an option to keep all my files, still-supported programs and settings.

Which CD?

The LiveCD does NOT have an upgrade option. It has a "Test Ubuntu" which is runs from the CD or it has an Install option which is a clean install.

---

### Post by MG&amp;TL on 2011-10-17
See here:

[http://www.google.co.uk/imgres?q=ubuntu+partitioning+options+screen&um=1&hl=en&client=opera&rls=en&channel=suggest&tbm=isch&tbnid=VvKwd4t73ouydM:&imgrefurl=http://gnubyexample.blogspot.com/2011/05/ubuntu-install-cd-two-purposes-1-update.html&docid=BxDt-OSzwIvP0M&imgurl=http://2.bp.blogspot.com/-9itbEeZDv3M/TdVSpSHBQpI/AAAAAAAABto/vk9wLdouw38/s1600/ubuntuCDbootupMenu-ExistingInstallationDetected__2011Q2-19052011377optionsClear.jpeg&w=1600&h=1101&ei=b0ScTqrXJoiY8QOGo4TWBQ&zoom=1&iact=hc&vpx=601&vpy=361&dur=1421&hovh=186&hovw=271&tx=154&ty=113&sig=109761121294074381163&page=2&tbnh=134&tbnw=212&start=15&ndsp=15&ved=1t:429,r:7,s:15&biw=1304&bih=662]("http://www.google.co.uk/imgres?q=ubuntu+partitioning+options+screen&um=1&hl=en&client=opera&rls=en&channel=suggest&tbm=isch&tbnid=VvKwd4t73ouydM:&imgrefurl=http://gnubyexample.blogspot.com/2011/05/ubuntu-install-cd-two-purposes-1-update.html&docid=BxDt-OSzwIvP0M&imgurl=http://2.bp.blogspot.com/-9itbEeZDv3M/TdVSpSHBQpI/AAAAAAAABto/vk9wLdouw38/s1600/ubuntuCDbootupMenu-ExistingInstallationDetected__2011Q2-19052011377optionsClear.jpeg&w=1600&h=1101&ei=b0ScTqrXJoiY8QOGo4TWBQ&zoom=1&iact=hc&vpx=601&vpy=361&dur=1421&hovh=186&hovw=271&tx=154&ty=113&sig=109761121294074381163&page=2&tbnh=134&tbnw=212&start=15&ndsp=15&ved=1t:429,r:7,s:15&biw=1304&bih=662")

---

### Post by Slim Odds on 2011-10-17
> **MG&TL said:**
> See here:

[http://www.google.co.uk/imgres?q=ubuntu+partitioning+options+screen&um=1&hl=en&client=opera&rls=en&channel=suggest&tbm=isch&tbnid=VvKwd4t73ouydM:&imgrefurl=http://gnubyexample.blogspot.com/2011/05/ubuntu-install-cd-two-purposes-1-update.html&docid=BxDt-OSzwIvP0M&imgurl=http://2.bp.blogspot.com/-9itbEeZDv3M/TdVSpSHBQpI/AAAAAAAABto/vk9wLdouw38/s1600/ubuntuCDbootupMenu-ExistingInstallationDetected__2011Q2-19052011377optionsClear.jpeg&w=1600&h=1101&ei=b0ScTqrXJoiY8QOGo4TWBQ&zoom=1&iact=hc&vpx=601&vpy=361&dur=1421&hovh=186&hovw=271&tx=154&ty=113&sig=109761121294074381163&page=2&tbnh=134&tbnw=212&start=15&ndsp=15&ved=1t:429,r:7,s:15&biw=1304&bih=662](http://www.google.co.uk/imgres?q=ubuntu+partitioning+options+screen&um=1&hl=en&client=opera&rls=en&channel=suggest&tbm=isch&tbnid=VvKwd4t73ouydM:&imgrefurl=http://gnubyexample.blogspot.com/2011/05/ubuntu-install-cd-two-purposes-1-update.html&docid=BxDt-OSzwIvP0M&imgurl=http://2.bp.blogspot.com/-9itbEeZDv3M/TdVSpSHBQpI/AAAAAAAABto/vk9wLdouw38/s1600/ubuntuCDbootupMenu-ExistingInstallationDetected__2011Q2-19052011377optionsClear.jpeg&w=1600&h=1101&ei=b0ScTqrXJoiY8QOGo4TWBQ&zoom=1&iact=hc&vpx=601&vpy=361&dur=1421&hovh=186&hovw=271&tx=154&ty=113&sig=109761121294074381163&page=2&tbnh=134&tbnw=212&start=15&ndsp=15&ved=1t:429,r:7,s:15&biw=1304&bih=662)

I've never seen this before. Ubuntu has always had the policy to upgrade from one release to the next or to upgrade from one LTS to another.

Those were the only supported options.

Also, that shows 10.04 LTS -> 11.04, not 10.10 -> 11.10

---

### Post by MG&amp;TL on 2011-10-17
Meh. I would have said so too, but I'm just talking from what the USB menu says to me. :)

Never mind, if the OP got what they wanted...

---

### Post by michael.b.broussard on 2011-10-17
> **MG&TL said:**
> Well...I'm sorry if I caused confusion, but i had a 10.04 desktop, inserted 11.04 CD, and it offered an option to keep all my files, still-supported programs and settings.
I got the same thing when I upgraded 1 of my machines. Went from 10.04 to 11.04, but it didn't save it even when I clicked keep files.

---

### Post by alphacrucis2 on 2011-10-17
> **Slim Odds said:**
> Which CD?

The LiveCD does NOT have an upgrade option. It has a "Test Ubuntu" which is runs from the CD or it has an Install option which is a clean install.

There's been an upgrade in place option in ubiquity for some time now. I upgraded 10.10 to 11.04 that way. It worked but uninstalled all apps that weren't on the CD. That was because some sort on error occurred but I never bothered to try an figure it out. I just manually installed the apps that went AWOL.

Edit. Came in with the 11.04 Live CD. Here's a webupd8 blog showing screen shots.

[http://www.webupd8.org/2011/03/ubuntu-live-cd-will-let-you-upgrade-to.html](http://www.webupd8.org/2011/03/ubuntu-live-cd-will-let-you-upgrade-to.html)

---

### Post by vendar13 on 2011-10-18
The dilemma is whether to do a immaculate put or whether to upgrade to Natty and then Oneiric using the elevate switch (twice). I love ubuntu and use it 99% of the indication, but I'm not really sensation in the enjoin piping (yet). The upgrade secure seems undemanding, but I create that there is an immense turn of changes occurrence to the system when I dawn that. A weightlifting lay would be, of teaching, such tradesman, but I haven't had any experience doing a fresh position over an existing linux lay.


      [Computer   Store](http://www.computervalley.ca/)       [Online   Computer Store](http://www.computervalley.ca/)

---

