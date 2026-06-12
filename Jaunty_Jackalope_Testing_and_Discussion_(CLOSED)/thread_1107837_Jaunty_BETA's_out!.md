---
title: "Jaunty BETA's out!"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Leslie Viljoen on 2009-03-27
Hi people!

The beta testing images for the new Jaunty Jackalope are out!
Here's the page: [http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

If you can try these out, it will really help the community. I would like to make a special request for people to try the PowerPC releases since they often suffer from fatal flaws which are not corrected before the final release and the ISO image is set in stone.

Xubuntu PPC: [URL="http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/beta"]http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/beta
[/URL]Ubuntu PPC: [http://cdimage.ubuntu.com/ports/releases/jaunty/beta](http://cdimage.ubuntu.com/ports/releases/jaunty/beta)

---

### Post by conal on 2009-03-27
Thanks Leslie,

What about upgrading? Can we do this if we are brave? if so how? Is it just a case of amending the software sources to say Jaunty instead of Intrepid then running update manager? 

thanks in advance!

Conal

---

### Post by damis648 on 2009-03-27
> **conal said:**
> Thanks Leslie,

What about upgrading? Can we do this if we are brave? if so how? Is it just a case of amending the software sources to say Jaunty instead of Intrepid then running update manager? 

thanks in advance!

Conal

Fire up a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-manager --devel-release
```

---

### Post by perpetualcacophany on 2009-03-27
> **damis648 said:**
> Fire up a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-manager --devel-release
```

I just tried this, but I had to stop before actual installation started. Now when I try to upgrade it doesn't show the option in the update manager. I get this when in the terminal when I use the above command now:

```
current dist not found in meta-release file
```

The update manager still pops up, but the Jaunty upgrade isn't at the top any more. I know that it didn't install and I double checked and made sure that it still knows that it is in Intrepid.

Any idea how to get it to let me upgrade to the beta now?

Thank you.

---

### Post by damis648 on 2009-03-27
Try this
```
gksudo gedit /etc/update-manager/meta-release
```

and comment out all the lines currently in there (don't delete, just comment out in case we need to put them back) and paste this in:
```
[METARELEASE]
URI = http://changelogs.ubuntu.com/meta-release
URI_LTS = http://changelogs.ubuntu.com/meta-release-lts
URI_UNSTABLE_POSTFIX = -development
URI_PROPOSED_POSTFIX = -proposed
```
and save and quit. Try launching the upgrade again.:popcorn:

---

### Post by perpetualcacophany on 2009-03-27
> **damis648 said:**
> Try this
```
gksudo gedit /etc/update-manager/meta-release
```

and comment out all the lines currently in there (don't delete, just comment out in case we need to put them back) and paste this in:
```
[METARELEASE]
URI = http://changelogs.ubuntu.com/meta-release
URI_LTS = http://changelogs.ubuntu.com/meta-release-lts
URI_UNSTABLE_POSTFIX = -development
URI_PROPOSED_POSTFIX = -proposed
```
and save and quit. Try launching the upgrade again.:popcorn:

Nope, this didn't solve the problem. Thank you for the response though. Any other ideas?

---

### Post by damis648 on 2009-03-27
Maybe try this:
```
cd /var/lib/update-manager
sudo cp meta-release-development mrd.bak
gksudo gedit meta-release-development
```
and then clear the file (delete everything) and paste in:
```
Dist: warty
Name: Warty Warthog
Version: 04.10
Date: Wed, 20 Oct 2004 07:28:17 UTC
Supported: 0
Description: This is the warty warthog release
Release-File: http://archive.ubuntu.com/ubuntu/dists/warty/Release

Dist: hoary
Name: Hoary  Hedgehog
Version: 05.04
Date: Fri, 08 Apr 2005 08:18:19 UTC
Supported: 0
Description: This is the Hoary Hedgehog release
Release-File: http://archive.ubuntu.com/ubuntu/dists/hoary/Release

Dist: breezy
Name: Breezy Badger
Version: 05.10
Date: Thu, 13 Oct 2005 19:34:42 UTC
Supported: 0
Description: This is the Breezy Badger release
Release-File: http://archive.ubuntu.com/ubuntu/dists/breezy/Release

Dist: dapper
Name: Dapper Drake
Version: 6.06 LTS
Date: Thu, 01 Jun 2006 9:00:00 UTC
Supported: 1
Description: This is the Dapper Drake release
Release-File: http://archive.ubuntu.com/ubuntu/dists/dapper/Release
ReleaseNotes: http://changelogs.ubuntu.com/DapperReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz.gpg

Dist: edgy 
Name: Edgy Eft
Version: 6.10
Date: Thu, 26 Oct 2006 12:00:00 UTC
Supported: 0
Description: This is the Edgy Eft release
Release-File: http://archive.ubuntu.com/ubuntu/dists/edgy/Release
ReleaseNotes: http://changelogs.ubuntu.com/EdgyReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/dist-upgrader-all/current/edgy.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/dist-upgrader-all/current/edgy.tar.gz.gpg

Dist: feisty
Name: Feisty Fawn
Version: 7.04
Date: Thu, 19 Apr 2007 13:00:00 +0200
Supported: 0
Description: This is the 7.04 release
Release-File: http://archive.ubuntu.com/ubuntu/dists/feisty/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/ReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/feisty.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/feisty.tar.gz.gpg

Dist: gutsy
Name: Gutsy Gibbon
Version: 7.10
Date: Thu, 18 Oct 2007 12:00:00 UTC
Supported: 1
Description: This is the 7.10 release
Release-File: http://archive.ubuntu.com/ubuntu/dists/gutsy/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/ReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz.gpg

Dist: hardy 
Name: Hardy Heron
Version: 8.04 LTS
Date: Thu, 24 Apr 2008 12:00:00 UTC
Supported: 1
Description: This is the 8.04 LTS release
Release-File: http://archive.ubuntu.com/ubuntu/dists/hardy/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/hardy/main/dist-upgrader-all/current/ReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/hardy/main/dist-upgrader-all/current/hardy.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/hardy/main/dist-upgrader-all/current/hardy.tar.gz.gpg

Dist: intrepid
Name: Intrepid Ibex
Version: 8.10
Date: Thu, 30 Oct 2008 12:00:00 UTC
Supported: 1
Description: This is the 8.10 release
Release-File: http://archive.ubuntu.com/ubuntu/dists/intrepid/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/intrepid/main/dist-upgrader-all/current/ReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/intrepid/main/dist-upgrader-all/current/intrepid.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/intrepid/main/dist-upgrader-all/current/intrepid.tar.gz.gpg

Dist: jaunty
Name: Jaunty Jackalope
Version: 9.04
Date: Thu, 24 Apr 2009 12:00:00 UTC
Supported: 0
Description: This is the 9.04 release
Release-File: http://archive.ubuntu.com/ubuntu/dists/jaunty/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/jaunty/main/dist-upgrader-all/current/DevelReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/jaunty/main/dist-upgrader-all/current/jaunty.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/jaunty/main/dist-upgrader-all/current/jaunty.tar.gz.gpg

```
And try again, this might work.

---

### Post by perpetualcacophany on 2009-03-27
Awesome, that worked. Thank you so much. For some reason the meta-release-development was filled with a bunch of html from the website that is used to log in to my apartment's internet.

Thanks again.

---

### Post by damis648 on 2009-03-27
> **perpetualcacophany said:**
> Awesome, that worked. Thank you so much. For some reason the meta-release-development was filled with a bunch of html from the website that is used to log in to my apartment's internet.

Thanks again.

No problem. :popcorn:

---

### Post by carlf on 2009-03-28
Upgraded from Alpha. Nice that Amarok works now. On the minus Banshe does not.  I have been wanting to try it forever. 

What will be the default since Rhythmbox is not going to be upgraded anymore down the line?

---

### Post by Therion on 2009-03-28
> **carlf said:**
> Upgraded from Alpha. Nice that Amarok works now. On the minus ***Banshe does not***.
Confirmed.  

I also did a fresh install of Jaunty-Beta (over the previously installed Alpha).  

A fresh install of Banshee from Add/Remove froze on the first run and now it refuses to start *at all*.  Bummer.

Not a fan of Amarok and Banshee has been my Rhythmbox backup... Until now.

---

### Post by Unix-Man on 2009-03-28
I tried this off a live CD and it seems great i really like the new log in screen but other then that i didn't notice much new change. But i noticed the Drag Box bug was fixed. Anyway thanks for the link.

---

### Post by Chemical Imbalance on 2009-03-28
> **Therion said:**
> Confirmed.  

I also did a fresh install of Jaunty-Beta (over the previously installed Alpha).  

A fresh install of Banshee from Add/Remove froze on the first run and now it refuses to start *at all*.  Bummer.

Not a fan of Amarok and Banshee has been my Rhythmbox backup... Until now.

I installed a fresh partition of Jaunty next to Intrepid and Banshee works great in 9.04.

Perhaps it is an upgrade issue?

I recommend a new partition formatted with ext4 (my computer boots 10 seconds faster--and it used to boot in 20 seconds in intrepid!)
--of course though I'm running a Quad-Core with 1066mhz RAM, etc...:)

---

### Post by Therion on 2009-03-28
> **Chemical Imbalance said:**
> I installed a fresh partition of Jaunty next to Intrepid and Banshee works great in 9.04.

Perhaps it is an upgrade issue?

I recommend a new partition formatted with ext4 (my computer boots 10 seconds faster--and it used to boot in 20 seconds in intrepid!)
--of course though I'm running a Quad-Core with 1066mhz RAM, etc...
It _is_ a fresh install and I _am_ using Ext4 (one of the reasons I wanted to reinstall, plus I wanted to go back to a 64-bit distro).  

I dunno... Not having Banshee isn't the end of the world, I guess.  Rhythmbox not working, though, now that WOULD be the end of the world.

Currently getting a 42s boot on my 3.0Ghz Core2 Duo and 2GB of 1066.  Down from ~1m:10s on 8.04; so yeah, I'm happy!  Thinking a BIOS tweak or two might speed things up a bit as well.  Need to look into that.

---

### Post by Chemical Imbalance on 2009-03-28
> **Therion said:**
> It _is_ a fresh install and I _am_ using Ext4 (one of the reasons I wanted to reinstall, plus I wanted to go back to a 64-bit distro).  

I dunno... Not having Banshee isn't the end of the world, I guess.  Rhythmbox not working, though, now that WOULD be the end of the world.

Currently getting a 42s boot on my 3.0Ghz Core2 Duo and 2GB of 1066.  Down from ~1m:10s on 8.04; so yeah, I'm happy!  Thinking a BIOS tweak or two might speed things up a bit as well.  Need to look into that.

I have been *really* bad about not reading posts carefully lately ;)

:lolflag:

I couldn't believe the first time I booted Jaunty.  I mean seriously--10 seconds is awesome!

---

### Post by carlf on 2009-03-28
[http://cdimage.ubuntu.com/ports/releases/jaunty/beta/](http://cdimage.ubuntu.com/ports/releases/jaunty/beta/)

gonna try again.

---

### Post by carlf on 2009-03-28
in terminal su will not take my pw.

used synaptic downloaded alien so I could convert ibm java per instructions into a deb.
Once the instalation of Alien is finished we go to the directory where we have downloaded de java RPM package an in the console as root (su and password) we run "alien -i ibm-java-ppc-jre-6.0-1.0.ppc.rpm --scripts", and voila! when this process is finished we are going to have installed Java in "/opt/ibm/java-ppc-60/". (I'd make it -4 since is what ibm java is now if I could get that far.) Have ibm-java-ppc-jre-6.0-4.0.ppc.rpm on my desktop. 


Now we have installed Java we need to make it work for Mozilla Firefox, this is easy, we need to create a link to the to the plugin folder that firefox 3 use, not just mozilla plugins dir, so we go in the console as root to /usr/lib/firefox-3.0.1/plugins/ and inside this folder we create the link in this way "ln -s /opt/ibm/java-ppc-60/jre/plugin/ppc/ns7/libjavaplugin_oji.so", now we restart firefox 3, and go to Tools---Add-ons and there must be activated Java plugin, it appears like Java(TM) Plug-in 1.6.0-internal-root_10_....... or something like.

this is the guide link I'm trying to follow.
[http://kapsulax.blogspot.com/2008/08/java-plugin-under-linux-ppc.html](http://kapsulax.blogspot.com/2008/08/java-plugin-under-linux-ppc.html)

This is  one thing I miss about Fedora 10 because I knew how to get ibm java working with my powerbook.

---

### Post by Chemical Imbalance on 2009-03-28
> **carlf said:**
> in terminal su will not take my pw.



By default, Ubuntu's root account is locked down  and the only way to access it from a user account is to use the sudo command.  You can enable root and change the password yourself, but why do that when you have sudo?

---

### Post by carlf on 2009-03-28
> **Chemical Imbalance said:**
> By default, Ubuntu's root account is locked down  and the only way to access it from a user account is to use the sudo command.  You can enable root and change the password yourself, but why do that when you have sudo? guess that comes from me being used to Fedora.  I was just trying to follow that guide though so I could convert the rpm  to deb.  

any idea on banshee.  I have the same problem as on the banshe thread.

I loved the alpha version when I first tried coming from Fedora 10.  The beta version also.    

I love the fast boot up time.  I love not getting loading/lib/kdb/keymaps/i386/qwerty/us.map from Fedora 10.  Everytime rebooting I would spin what seemed like forever trying to get past that.

The first thing I did after installing the alpha and beta was the updates. After that I went and put a check mark for all the ubuntu studio stuff.  

I wanna get the ibm java only for playing yahoo games.  

I wanna get gnash or swfdec working for youtube online streaming sites.

---

### Post by Chemical Imbalance on 2009-03-28
Perhaps you guys should file a bug on launchpad if there is not already one there.

I'm listening to it right now on Jaunty, so I can confirm it works here.

---

### Post by Rog-Mahal on 2009-03-28
So Banshee is the new default music player for Jaunty? I'm going to miss Rhythmbox, hopefully someone will pick up that project. 

Has anyone tried to dual boot with rEFIt and ext4?

---

### Post by inphektion on 2009-03-28
> **Rog-Mahal said:**
> 
Has anyone tried to dual boot with rEFIt and ext4?

Yep worked fine.  The only issue i ran into was after having to force shutdown a few times cause of a wireless issue, the last time something was corrupted and I couldn't boot.  I didn't troubleshoot it cause I was testing stuff out anyway.
So at this point I'm on
/boot - 100mb - ext3
/ - 50GB - ext4
/home - 210GB - ext4

and even across bad shutdowns never saw that issue again with corruption.

---

### Post by cyberdork33 on 2009-03-28
> **Rog-Mahal said:**
> So Banshee is the new default music player for Jaunty? I'm going to miss Rhythmbox, hopefully someone will pick up that project. 

Has anyone tried to dual boot with rEFIt and ext4?
ext4 is backwards compatible with ext3... so ext3 drivers can read ext4 filesystems (you just don't get all the ext4-specific benefits).

---

### Post by Mlungu on 2009-03-29
Hello Everyone!
I am completely new to this so excuse me if I am posting in the wrong place or something like that.
I have one of the new MacBooks (late 2008 model, aluminum uni body). I would really like to try out Ubuntu. I was wondering: If I install the new version of Ubuntu (once it comes out), what are the chances that things will work straight away (trackpad, sound, network ...)? And if not how long will it take a beginner like me to get everything up and running?
Thanks for the help!

---

### Post by FrostBlue on 2009-03-29
Hello guys,
AM loving this new release.Jaunty is so much snappier that Hardy.I gave Ibex a skip as I had tons of issues.
Everything seems to work for me except I cant seem to add widgets to plasma.
The ones I compile and install dot show up even if I manually copy them to where used to be in Hardy.The select from file dialog doesn't even show .so files to select them.Anybody has any idea whats going on.

Help please.

Thanks .

---

### Post by MacBuntu1 on 2009-03-29
> **Chemical Imbalance said:**
> I have been *really* bad about not reading posts carefully lately ;)

:lolflag:

I couldn't believe the first time I booted Jaunty.  I mean seriously--10 seconds is awesome!

Wow!! I am getting 24 seconds on my Macbook, so I am happy!!! I love how fast it is, startup time is one of my (many) complaints against Windows, and Linux is even faster than Leopard!!!

---

### Post by cyberdork33 on 2009-03-29
> **Mlungu said:**
> Hello Everyone!
I am completely new to this so excuse me if I am posting in the wrong place or something like that.
I have one of the new MacBooks (late 2008 model, aluminum uni body). I would really like to try out Ubuntu. I was wondering: If I install the new version of Ubuntu (once it comes out), what are the chances that things will work straight away (trackpad, sound, network ...)? And if not how long will it take a beginner like me to get everything up and running?
Thanks for the help!
not everything will work straightaway...

Start here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

I think there is a page for your hardware and jaunty.

---

### Post by Mlungu on 2009-03-30
> **cyberdork33 said:**
> not everything will work straightaway...

Start here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

I think there is a page for your hardware and jaunty.

Thanks! That is exactly what I was looking for.

---

### Post by Leslie Viljoen on 2009-03-30
Ok, so which of you have a **PowerPC** machine, and have installed Jaunty successfully? I am really eager to try it but I haven't had the opportunity yet.

---

### Post by ELWisty on 2009-03-30
Upgraded from 8.10 on my Acer Aspire 5040 (clean install, got rid of the Windows partition at the same time). Couldn't be happier. Startup is about 30 seconds, a little under. In 8.10 I had to do a little tweaking to get wireless working with the Atheros wlan card I have, and even then I had to always manually reload the driver. Also, couldn't get the external USB sound card working with flash videos (laptop's internal sound card worked, the external sound card not). Now everything worked straight out of the box. No problem with anything I've tried on it so far.

When the final version of Jaunty is out next month, it will be possible to upgrade to that from beta from within the OS, right?

---

### Post by carlf on 2009-03-30
> **Leslie Viljoen said:**
> Ok, so which of you have a **PowerPC** machine, and have installed Jaunty successfully? I am really eager to try it but I haven't had the opportunity yet.
I have it on my G4 12 inch powerbook with 764 mb ram.

---

### Post by Fenris_rising on 2009-03-30
Hi all

I installed on a second HDD with the ext4 format. A massive 25 seconds has been shaved off my boot time :) I'm also looking at upgrading from my ATI X300 GPU as it seems the support for that particular family my be on the out if you want all the graphical knobs and whistles. Other than a few minor niggles, which you have to expect, everything seems that bit snappier in operation. Progress and login screens are also a bit more 'flashy' a good thing IMHO. I currently still use 8.04 as my primary work horse. 8.10 kept locking up on me.

regards

Fenris

---

### Post by Vorian Grey on 2009-03-30
I've been playing with the beta over the weekend and it fills like a winner to me. I don't have any major problems of any kind and it's really, really fast.

---

### Post by FrostBlue on 2009-03-30
Jaunty is fast...I love it.And very stable so far.

A couple of issues I have so far...just jotting them down here,
GTK styles in sys settings doesnt save any changes,reverts back to default on next login.
Network management applet cant really connect to secure wireless...Knetworkmanager does tho.
Cant add plasmoids like simple monitor and tun of compositing plasmoid for some reason.
Quick access applet doesnt work.

I know this is beta...so something like this shud b expected.

The rest of this release is simply amazing.

---

### Post by tiresia on 2009-03-30
> **Leslie Viljoen said:**
> Ok, so which of you have a **PowerPC** machine, and have installed Jaunty successfully? I am really eager to try it but I haven't had the opportunity yet.

Installed with the LiveCD Ubuntu Jaunty on my PowerMac G4 MDD (Dual 1,25 GHz), using ext4. I had not so much time to test everything, but as far as I know, I'm really impressed!!! Very stable and fast performances. 
I'm happy also because we have again a good reliable LiveCD.

I'm multibooting Ubuntu with Fedora and Debian. As expected no problems with ext4 for both other GNU/Linux Distros (Debian sees it as ext3 Fedora already as ext4)

---

### Post by Leslie Viljoen on 2009-03-30
> **tiresia said:**
> Installed with the LiveCD Ubuntu Jaunty on my PowerMac G4 MDD (Dual 1,25 GHz), using ext4. I had not so much time to test everything, but as far as I know, I'm really impressed!!! Very stable and fast performances. 
I'm happy also because we have again a good reliable LiveCD.

I'm multibooting Ubuntu with Fedora and Debian. As expected no problems with ext4 for both other GNU/Linux Distros (Debian sees it as ext3 Fedora already as ext4)

Fantastic! I have Xubuntu downloaded, I need to try that on my G4 MacMini as soon as I can get ppclinux.info on another box.

---

### Post by conal on 2009-04-02
Oh-no!

I just tried to upgrade to Jaunty. Stupidly I left the computer doing the upgrade and went off to bed. When I got up the power save function had switched the screen off. I managed to get the screen back on, but the keyboard and mouse were unresponsive.

There was only 20 minutes of the upgrade to go and there was a question about replacing a configuration file on the screen which I could not confirm or deny, eventually I had to switch the computer off.

Trouble is now when I switch on I get only the desktop background with a message saying my power save settings are not properly configured - (you don't say!). The mouse is working again, but I have nothing to click on - no panels or icons. 

Can anyone tell me how to resume the upgrade from a terminal?

Also should I file a bug report, or is this just what happens when you abandon an upgrade?

Many thanks

Conal

---

### Post by conal on 2009-04-02
Its OK, I worked it out

I found these commands which completed the install and now I have my desktop back:

> sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

Happy days.

---

### Post by spydouglas on 2009-04-02
I'm testing the beta on ppc--specifically, a Powerbook G4 5,8.
I upgraded from 8.10, so I cannot comment on the installer.

However, I am experiencing issues with the radeon driver.  DRI worked in 8.10, but doesn't any more.  Suspend/restore is also broken.  I've tried to look for forum posting and bug reports but haven't found anything on DRI problems.  Are any other PPC users experiencing these problems?  (my powerbook has a rv350 radeon card)

---

### Post by wingnux on 2009-04-03
I've just installed Xubuntu Jaunty Beta on my laptop, everything went just fine, the first boot worked perfectly but when I restarted it, there were no more panels, icons, wallpaper, nothing! I tried right-clicking and it didn't work either. Alt+F2 works tough, I launched the panel from there but even when I log out, save the session and log back in, the same problem occurs =/

Any help?


EDIT: After a system update the panels are back just like after installing but still there's no desktop background, icons and right-click menu =/ The desktop icons are VERY IMPORTANT since this is my dad's work laptop and it's really going to help him migrate from xp to linux. Thanks in advance.

---

### Post by conal on 2009-04-03
Did you try the commands I used to fix my problem?;-

> sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade 

Cheers

Conal

---

### Post by joshiss on 2009-04-04
Updating from 8.10 to 9.04 beta

I tried both the methods but still in my case after running 'gksu update-manager -d' the update window is launched but no line on top for 9.04 upgrade. I was trying the same 2 days back and it did show up but after partial download the update was cancelled for some urgent reasons. The cancel procedure only confirmed for cancellation but did not give any error.

Pease help
I am using UBUNTU 8.10
and the update version is 1:0.93.34

---

### Post by taavikko on 2009-04-04
> **joshiss said:**
> Updating from 8.10 to 9.04 beta

I tried both the methods but still in my case after running 'gksu update-manager -d' the update window is launched but no line on top for 9.04 upgrade. I was trying the same 2 days back and it did show up but after partial download the update was cancelled for some urgent reasons. The cancel procedure only confirmed for cancellation but did not give any error.

Pease help
I am using UBUNTU 8.10
and the update version is 1:0.93.34

Release upgrade were held back due to python issues, but archives are re-opened again.

Just type "update-manager -d" to upgrade.
If it states that there is no release found, check that
/etc/update-manager/release-upgrades 
file states that "Prompt=normal"

---

### Post by conal on 2009-04-07
Unfortunately I can no longer boot up Ubuntu, I don't know If this is a specific problem to the Jaunty PPC Beta but I filed a bug report with launchpad in case that is helpful, here is the problem, if anyone has any suggestions for a solution I would be most grateful, here is a brief description;-  

The computer went into hibernation, It would not come back on(screen remained blank despite trying keys and mouse) so I switched the power off. Now when I reboot I get past stage 2 of Yaboot, the screen says "please wait, loading.." then nothing happens, I just get a black screen with flashing cursor. If I press the apple key + f1 some text appears, reading:

Loading, please wait...
usplash: No usable theme found for 1024x768
screen init failed
19+0 records in
19+0 records out

I disabled usplash some time ago I understand that bit, the rest I do
not.

Many thanks

Conal

---

### Post by matthew.ball on 2009-04-07
Looks like it could be a similar problem to the nvidia ordeal, i.e. updated graphics driver and kernel but failed to update grub.

Are you able to log in? (i.e. Ubuntu loads, but doesn't start x)

If so, login and cd /boot - ls and view the available options (I believe they are available kernels).

There are 3 of these "kernels" on my computer for instance.

The update may have introduced a 2.6.28-11-generic kernel but grub is telling the system to boot the old 2.6.27-11-generic.

What you want to do is cd /boot/grub and open the menu.lst file (you'll want to use sudo and probably nano as the editor).

Just add a new boot entry (top of the available boot options so it gets first boot priority).

Following the same format as the previous entries.
> 
title           Ubuntu 9.04, kernel 2.6.28-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.28-11-generic root=<UUID>
initrd          /boot/initrd.img-2.6.28-11-generic
Where UUID is the same UUID as your previous entries.

If this doesn't work, I'm sorry I was unable to help you.

And I'll warn you, technically I *don't* know what I told you to do, it was what I found to do and worked for me.

---

### Post by conal on 2009-04-07
Thanks Matthew

I don't think I can get a command line unfortunately, it crashes just after yaboot. And would my machine even use grub? Does yaboot not replace grub for PPC machines?

I'm not near my computer just now so I'll look into your suggestion and get back to you later.

Kind Regards

Conal

---

### Post by wingnux on 2009-04-07
> **conal said:**
> Did you try the commands I used to fix my problem?;-



Cheers

Conal


Yes I did, the panels are ok but I can't get my desktop to work properly =/ There are no icons, menus nor wallpaper

---

### Post by conal on 2009-04-09
Sorry wingnux, as you can see from my posts my system is totally borked as well!

I am tying to fix it in recovery mode from the jaunty alternate install cd. I can mount the broken partition with a command line,  unfortunately, I have do idea what to do next! 

I think I'll make a fresh post to see if anyone knows of any useful commands to use here, I cant seem to find a guide for recovering a power pc - but there must be one somewhere!

Thanks

Conal

---

