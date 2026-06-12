---
title: "The &quot;I'm scared to upgrade&quot; Thread"
date: 2008-11-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by danf_1979 on 2008-11-27
**NOTE: Please don't post messages like "This is alpha1, stay in hardy or intrepid. f you need to rely on a stable system don't use it". **

[B]This thread is for jaunty users, not for intrepid's dist-upgrades.
[/B]
Hi guys, I made this thread so we can discuss other people experiences when you're scared to upgrade because of some packages.

Today I see some xorg packages being synched from debian. Do these packages break jaunty?

```

The following NEW packages will be installed:     
  epiphany-browser-dbg{a} evince-dbg{a} evolution-data-server-dbg{a} evolution-dbg{a} 
  gimp-dbg{a} gnome-applets-dbg{a} gnome-dbg{a} gnome-panel-dbg{a} gstreamer0.10-esd{a} 
  gstreamer0.10-plugins-base-dbg{a} gstreamer0.10-plugins-good-dbg{a}                   
  gstreamer0.10-plugins-ugly-dbg{a} libatk1.0-dbg{a} libatspi-dbg{a} libdb4.6-java{a}   
  libdb4.6-java-gcj{a} libfontconfig1-dbg{a} libgail-gnome-dbg{a} libgail-gnome-module{a} 
  libgda3-3{a} libgda3-3-dbg{a} libgda3-bin{a} libgda3-common{a} libgda3-sqlite{a}        
  libgdict-1.0-6{a} libglib2.0-0-dbg{a} libgnomedb3-4{a} libgnomedb3-4-dbg{a}             
  libgnomedb3-bin{a} libgnomedb3-common{a} libgnomeui-0-dbg{a} libgnomevfs2-0-dbg{a}      
  libgoffice-0-6{a} libgoffice-0-6-common{a} libgoffice-dbg{a} libgsf-1-114-dbg{a}        
  libgsf-gnome-1-114{a} libgsf-gnome-1-114-dbg{a} libgstreamer0.10-0-dbg{a} libgtk2.0-0-dbg{a} 
  libgtkhtml3.14-dbg{a} libloudmouth1-0-dbg{a} libnspr4-0d-dbg{a} libnss3-1d-dbg{a}            
  liboobs-1-4-dbg{a} libpango1.0-0-dbg{a} libtdb1{a} libxft2-dbg{a} libxml2-dbg{a}
  nautilus-dbg{a} rhythmbox-dbg{a} totem-dbg{a}
The following packages will be REMOVED:
  libdb4.5-java{a} libdb4.5-java-gcj{u}
The following packages will be upgraded:
  app-install-data-commercial bug-buddy eog evince gnome-utils gtk2-engines-pixbuf hal-info
  libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libdrm2 libgnome2-0 libgnome2-common
  libgnome2-dev libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtk2.0-dev libgtk2.0-doc
  libgweather-common libgweather1 liblucene2-java libpango1.0-0 libpango1.0-common
  libpango1.0-dev libpango1.0-doc libphonon4 librsvg2-2 librsvg2-common linux-libc-dev
  monodoc-base monodoc-manual phonon phonon-backend-gstreamer python-gconf python-glade2
  python-gnome2 python-gnome2-desktop python-gnomecanvas python-gobject python-gtk2
  python-gtksourceview2 splix xserver-common xserver-xorg-core xserver-xorg-input-evdev
46 packages upgraded, 52 newly installed, 2 to remove and 0 not upgraded.
Need to get 108MB of archives. After unpacking 185MB will be used.
Do you want to continue? [Y/n/?]

```

```

xserver-common xserver-xorg-core xserver-xorg-input-evdev

```

So, if you've already upgraded this packages please tell your reboot experience, or X restart experience :)

---

### Post by Kevbert on 2008-11-27
Why upgrade when Hardy Heron is a long term release (and stable) ?  
Jaunty is currently only Alpha1 so if you need to rely on a stable system don't use it as it's still got a few bugs and is work in progress. If you want to help with development and finding bugs, by all means try it, but don't be surprised if you have a few crashes and need to re-install a few times.
Currently known bugs seen by me include no sound, no floppy or ntfs support, flash not working, (but there are some workarounds).

---

### Post by andrew.mckevitt on 2008-11-27
I'm not 'scared' to upgrade, I just don't want to. I'm using Hardy on my laptop and my desktop and everything just works. The LTS bit is a real bonus.
  I'm sure to 'break' one of them one day and then I'll consider moving up. It'll be 'clean' install too, I've been down the 'upgrade' path and it's very unpredictable.
  Until then, my heron will remain hardy.

---

### Post by danf_1979 on 2008-11-27
Why are you giving those kind pf replies? If I'm using jaunty is because I want to help. Its my decision, and I already know the risks. I accept them, but this time, I want to know other users experiences. Please don't trash this thread.

---

### Post by Gina on 2008-11-27
I think some people misunderstood your thread - I must admit, I did.  Were you referring to updating within Jaunty (or other development phase) rather than upgrading between a release version and a development one?  

Regarding upgrading bewteen versions, I don't.  I leave the working version and install the new one in a separate partition - with a separate home partition as well.  That way I can go back if breakage occurs (provided the breakage doesn't trash other partitions as well as the system one).  I have several older machines I use for testing plus a newly built one for that purpose.  I always leave one machine running a tried and tested Ubuntu and don't risk a development version on it until I'm quite satisfied a disasterous breakage won't occur.

As for updating a development version, I never do a partial update as that usually means some packages aren't yet ready and an update without them stands a good chance of breaking the system.  Better to wait a day or so until all the parts are uploaded and all the dependencies satisfied.  Apart from breakage, a partial update is not a proper test and not helpful to the development team.  "Of course it doesn't work abc is dependent on xyz and xyz isn't quite ready yet".

Now, after all that... to answer the original question (as I now read it).  I have installed Jaunty on two machines and have no issues ATM apart from sound which now works on one and I've yet to check again on the other.  At this stage there isn't a lot happening and little to cause any problems but I expect it will be different in a month or two.  I'm not expecting much change until after the developer summit.

---

### Post by zmir on 2008-11-27
Hi, danf_1979.
i just installed Jaunty a few days ago and so far it runs pretty well on my system. its not the first time iv'e installed a ubuntu alpha/beta since iv'e been playing around with it since 5.04, more or less.

I have tried to Install it three times because the first and second time falied to pass through the "package installation" phase. third time's a charm i guess :-) 

i had little time to play around with it since i'm only using it for testing and bug finding purposes but so far i have updated it twice.
first one i had 120 updates, and second one 60 updates, and all is well.
my system have not broken and crashed even once. but i have run into a few minor bugs which i intend to report. (mainly the muted sound bug and another bug which won't let me use prtscn shortcut to take screenshots.)

over all my experience thus far from jaunty is rather pleasing and i will continue to use it and test it further along its birth and mature stages.

PS: i'm including my system specs for anyone who is wondering about such things. (i do).

Pentium-3 600mhz (coppermine).
Unknown INTEL motherboard. (didn't really bother to check).
512 sdram.
radeon 9600XT 256mb ram (Running on AGPX4, while being an AGPX8 card).
20 GB hard drive + another 10 GB hard drive. 
1.5MB ADSL broadband connected to a Linksys WRT54GL running DD-WRT firmware.

that's all i guess :-)

---

### Post by danf_1979 on 2008-11-27
Gina: The thread case was like "I'm a jaunty user, and today I'm scared to upgrade 'this' or 'that' package. Has someone already updgraded those packages? and if so, did juanty break?"

So, the thread is now trashed :(. See ya next time folks.

---

### Post by jerrylamos on 2008-11-27
Hey, no problem, I double and triple boot on test machines and try whatever is newest, then I can boot back to the last version that sort of worked.

The upgrade to Intrepid a couple days ago killed audio.  That did get under my skin so I re-installed back to the Release Code where audio worked and I'm keeping a Hardy handy even where both audio and Compiz work.

This Jaunty was installed from a USB because the daily build needs to go on a diet to get back below 700 MB.  Only problem with USB is it will boot on only one of my three test pc's. 

Jerry

---

### Post by adult swim on 2008-11-27
i just made a spare partition and installed jaunty + updates.  the only problem i have ran into so far was libcanberra-gtk breaking, nothing serious.

---

### Post by Kevbert on 2008-11-28
Personally I'm taking the risk of using Jaunty on two machines. scared to use it, no, as I have backups of my important files. The most important thing is to backup all data as you never know when there's going to be a hardware or software failure.
If my previous post was a bit negative, I'm sorry, but just stating the obvious for any newbies who want an opinion.

---

### Post by Archmage on 2008-11-28
> **danf_1979 said:**
> Today I see some xorg packages being synched from debian. Do these packages break jaunty?

Long questions: Easy answer: Jaunty is already broken. There are so many things that don't work like they should. You can't breakt what already is broken. But you can make matter worse.

---

### Post by theozzlives on 2008-11-28
I've got my wed & print server running Jaunty and it works fine, I just can't figure out why I have sound with Jaunty. When I upgraded my laptop, I had a problem so went back to Intrepid (on the Laptop). so far Jaunty seems to printing and running my site fine.

---

### Post by Nullack on 2008-11-29
On my hardware currently Jaunty is relatively ok

---

### Post by DougieFresh4U on 2008-11-29
I am still having near 100% CPU usage. I haven't got the new .28 kernel installed yet, as I am waiting for updates to do it. I see .28 in Synaptic but apparently it's not ready comepletely. 
Updates this morning wanted to remove 'libcanberra-gnome' but I didn't go for it as not sure it would brake any thing. On the positive side, I do still have sound working :guitar:

---

### Post by Gina on 2008-11-29
I'm having trouble with the libcanberra thing - I get an error saying it can't overwrite the old one or something.  I think this is mentioned in other threads and has been reported on Launchpad.  It doesn't seem to cause any noticeable problem with my system except for error messages.

---

### Post by DougieFresh4U on 2008-11-29
> **Gina said:**
> I'm having trouble with the libcanberra thing - I get an error saying it can't overwrite the old one or something.  I think this is mentioned in other threads and has been reported on Launchpad.  It doesn't seem to cause any noticeable problem with my system except for error messages.

Did updates want to remove 'libcanberra-gnome' for you? Is it safe or should I leave it till further updates? Other than that I have no errors regarding 'libcanberra' issue.

---

### Post by Gina on 2008-11-29
I'm not sure - I just ran update-manager once I was no longer getting the "Partial Update" message.  The update did not complete and gave an error message that it couldn't complete the update.  I get the same error (I think) when I try again> E: /var/cache/apt/archives/libcanberra-gtk0_0.10-1ubuntu2_amd64.deb: trying to overwrite `/usr/bin/canberra-gtk-play', which is also in package libcanberra-gnome
E: /var/cache/apt/archives/gnome-session-canberra_0.10-1ubuntu2_all.deb: trying to overwrite `/usr/share/gnome/autostart/libcanberra-login-sound.desktop', which is also in package libcanberra-gnome  I also got an error about broken package so I looked for broken packages in Synaptic and it reported ubuntu-desktop.  So I tried reinstalling and got> E: /var/cache/apt/archives/gnome-session-canberra_0.10-1ubuntu2_all.deb: trying to overwrite `/usr/share/gnome/autostart/libcanberra-login-sound.desktop', which is also in package libcanberra-gnomeI'll have to look into this further when I have time.

To answer your question... it seems it was NOT a good idea to run this update.  I may see if a future update fixes it or if not, reinstall Jaunty.  Installing Ubuntu systems comes second nature to me now :lolflag:

---

### Post by Gina on 2008-11-29
I've just run Synaptic - done Reload then Mark All Upgrades. It wanted to remove gnome-session-canberra plus lots of updates.  Since I already had errors, I let it get on with it.  It all went through except for an error on flash-nonfree and I no longer have any broken package.

---

