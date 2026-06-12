---
title: "[SOLVED] Installing totem-xine/packages on PC without internet"
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by Interestedinthepenguin on 2006-11-20
Hello.

Can anyone tell me how to enable DVD playback on an Ubuntu PC without internet access? 

(I believe) I've downloaded all of the dependency files for totem-xine, and they are stored in a folder on a fat32 partition; I just need to know how to go about installing these downloaded (deb) dependency packages.  

I've been at this for a couple of days.](*,) 

I am running Ubuntu 6.06 (i386)

Thanks.

---

### Post by aysiu on 2006-11-20
If it's a commercial DVD, you'll most likely need *libdvdccss2*, too, which you can download from [here](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/free/libdvdcss2_1.2.9-1plf4_i386.deb).

Once you have all the .deb files on your desktop, just type these commands in the terminal: ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by Interestedinthepenguin on 2006-11-20
Thanks for your help. :) 

I installed libdvdcss2 (and libdvdread3), but when I try to play a DVD, I get:  

Totem could not play 'dvd: ///media/cdrom0'. No URI handler implemented for dvd.

---

### Post by aysiu on 2006-11-20
[This](http://www.linuxforums.org/forum/ubuntu-help/70234-totem-could-not-play-dvd-media-cdrom0.html) is the only thing I could find on a Google search for your error. Hope it helps.

---

### Post by Interestedinthepenguin on 2006-11-22
Thanks, Aysiu.  

I really appreciate your help...but I still cannot play DVDs. :(  

I've run into some problems:  

Some of the packages are broken (and I've had to reinstall Ubuntu about a dozen times after removing the broken packs).  

There are certain versions that some packages depend on (and I can't seem to find the correct version(s) to download). :mad:  ](*,)   

I've had tons of patience with this (I've been at it for about a week), and I really want my Ubuntu installation to be up to par with (or better than) my Windows installation. :neutral:  

I really like this Linux distro, too. :-? 

Is there anything else I can do?

---

### Post by aysiu on 2006-11-22
Maybe forget about *totem-xine* for now and just focus on *libdvdcss2*? Try this: ```
sudo apt-get -f install
```

---

### Post by Interestedinthepenguin on 2006-11-22
I installed libdvdcss2 (_1.2.9-1plf4_i386.deb), and I still get:  

Totem could not play 'dvd:///media/cdrom0'.  No URI implemented for "dvd".  

I even re-followed the directions in the last link that you gave me, but libdvdplay0 (_1.0.1-7_i386.deb) won't install, due to dependency problems, and I know how that's going to go... :???:

---

### Post by aysiu on 2006-11-22
What about using something else to play DVDs? Xine? VLC? MPlayer?

---

### Post by Interestedinthepenguin on 2006-11-25
I now have DVD playback (in totem-gstreamer)! :-D 

Turns out, I was using the wrong packages.  

I recently found out that one isn't supposed to use "regular" deb packages with Ubuntu. :oops: 

The only minor problem is that the sound, when viewing DVDs, is a bit low, compared to totem-xine.  

...Totem-xine was the first one I managed to install, but the picture was washed out, for some reason, and when I uninstalled it, and put 'gstreamer back on, it was still washed out. :-s    I had to reinstall Ubuntu.  

I really appreciate your help, aysiu.  I still wouldn't have gotten this far without your help.  

Thanks a bunch!!

---

