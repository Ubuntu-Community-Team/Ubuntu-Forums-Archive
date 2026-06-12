---
title: "Licud Upgrade stops &quot;desktop ~~ removal blacklist&quot;"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by OzRattler on 2010-04-30
Hey All!

Hope you are all having gangs of fun!? 

Anyway, trying to upgrade from Karmic (9.10 / 64 bit) to Lucid on laptop to see how it flies prior to upgrading on my LAN server (8.10LTS / 32 bit)  and main work machine (9.10 / 64 bit).   I run aground with the message:

*"The package 'ubuntu-desktop' is marked for removal but it is in the removal blacklist.  This can be caused by ~"*

The three scenarios suggested do not apply to me or the software installed.  Namely, pre-release versions or unofficial software. Frankly, while I am not 100% noob - been using Linux now for 3 years - I cannot rule out the third complaint.  But I cannot workout what I might have installed to trigger such an error.

So far no luck with searches.  Efforts to upgrade at the command line yield no results.  Of course, all help welcomed!

Thanks in advance....

Rattler.

---

### Post by madmax1735 on 2010-04-30
it might have something to do with plymouth the new graphical bootloader

---

### Post by OzRattler on 2010-04-30
AH HA!!!!!

While waiting for a reply - and a special thank you to MadMax1735 - I stuffed around (technical term for tweak) with Software Source settings removing ones that I thought could be seen as a problem by an automated upgrade application and I am now upgrading.

So I will now allow the upgrade to complete, go back and re-enable those sources and see what happens.  I will post any other outcomes here as well.

Hope this thread helps someone.   A bit embarrassing I did not think of trying that previously..........

Have fun!

Rattler......

---

### Post by devzero on 2010-04-30
hi, i have that problem too, which software source did you remove?

---

### Post by devzero on 2010-04-30
so, 
I did an evil hack, it updates now too.

I did that in the shell with sudo do-release-upgrade
I attached strace till the error cames out then
I checked the log file from strace and found out, that
a file was created: /tmp/<folder_with_random_chars/removal_blacklist.cfg

So I let it restore to the old state, cleared the tmp folder,
restarted the tool and quick removed the *untu-dektop entries,
and saved.

Perhaps I nuked the rig, but lets see :D

---

### Post by OzRattler on 2010-04-30
OK - I killed Proprietary drivers as they are generally restricted.  I also decided to kill off multiverse.  This was done in the "Software Sources" dialogue box which can be found under System Menu.

Sadly, the video drivers are not working.  To be careful.  I am about to fix the video and resolution.

More in due course!

OzRattler

---

### Post by devzero on 2010-04-30
ah okay, I only removed the 3rd Party stuff and kept multiverse on, maybe that would have helped, but now i am currently in the upgrade progress. 
I use it on a atom netbook there are no proprietary drivers installed.

---

### Post by OzRattler on 2010-04-30
Continuing the Saga....

Multiverse seems to be the splinter under the nail.  

Mythtv [along with others] will not update through the regular Update Manager.  If I do check the Multiverse, then Update Manager suggests a Partial Upgrade since it claims that not all updates can be installed and to do so will install as many as possible.  BUT!!  It then stalls with the original error when I select Partial Upgrade.  

The only difference now is that rather then suggesting 'it' is a bug, it reports 'This is most likely a transient problem, please try again later."

I wonder how much later?

My machine is an HP dv5 tweaked to fly faster.

The graphics drives are now installed so I am now using the screen a little better than when first rebooted though resolution is very limited ~ 1280x720 rather than 1500+.  nvidia install is problematic.... Not happy - but will fix eventually.  Interestingly, GRUB still claims to be looking at 9.10!!

---

### Post by devzero on 2010-04-30
perhaps it helps if you hack the blacklist.cfg too.

---

### Post by OzRattler on 2010-04-30
OK  -  Went to /usr/share/update-manager and "#" ubuntu-desktop.   I reasoned that I can use the kubuntu-desktop.

So ran the "Partial Upgrade" which then went off and grabbed Mythtv; among others; and would you believe.....it has updated all those apps that previously were ignored.

For my next trick, I then tried to get the command "nvidia-xconfig" to work but it did not - well it worked but did not have the desired effect - resolution still low.  Next trick, hack the xorg.conf but that is proving tedious for me at this stage of night in Sydney.  My hack is generating errors in parsing the file.  I must have a typo or something included that is not liked.  Started working through it but need some sleep.

Also....Bananas to the window controls on the left!!

For one last throw....purged all things "nvidia" then asked it to install nvidia for me.  Did - but still at the same point.   Tomorrow or later, will purge nouveau drivers et Al.

Night for now!!

---

### Post by kcm on 2010-04-30
This bug may be what you are experiencing:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/571743]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/571743")

There is a conflict between libsdl1.2debian-alsa and libsdl1.2debian-pulseaudio.  So far, I know ubuntu-desktop depends on libsdl1.2debian-pulseaudio, and mythbuntu-desktop depends on libsdl1.2debian-alsa, so they cannot be mixed.  xubuntu-desktop only recommends libsdl1.2debian-alsa, so it can be mixed with ubuntu-desktop, but the upgrade won't work with both installed because they are listed in the wrong order in the metapackages.  I don't know about kubuntu-desktop, etc., but hopefully this info helps.

---

### Post by devzero on 2010-04-30
my hack worked and it updated, but now I have to choose every boot if I want to go to recoyery shell or skip mounting, if I skip it boots fine up.
ah ok that was an old hack for my netbook for something with /proc/bus/usb which got removed. perhaps it works fine without it, whatever that was....
Ha my key shortcuts works under xfce too YAY :D

BTW I dont use mythbuntu-desktop, but xubuntu-desktop and ubuntu-desktop so thats that bug, but it didn't got nuked and the sound still works.

---

### Post by OzRattler on 2010-05-03
Ripper KCM..............

I read the thread and all that goes with it.   Indeed on the 'test' machine both desktops are installed.  I have an old PIII flying Ubuntu with both and I will remove KDE and see how the upgrade goes tomorrow.

With some luck, it will go well and drivers for the video card will install cleanly too.    Once that is covered, I will retry with the unhappy machine and report back here.  I will also re-install KDE and see if that hurts anything.

Have fun!

---

### Post by OzRattler on 2010-05-04
A short fast reply............

Removed from the PIII Kubuntu Desktop ( ~ sudo apt-get remove kubuntu-desktop) and then started the upgrade.

Well...it installed, video looks good, mounts had some dramas which I have not totally investigated as yet but critical NFS and Samba mounts all flying.

Later, I will reinstall Kubuntu desktop and see what gives!

Having fun...............more now that I have a solution to upgrading but still no fix for my sick HP laptop.

---

### Post by OzRattler on 2010-05-13
Well....

Installed KDE and then pushed nvidia onto it and working well!

Hope this thread helps someone!

---

