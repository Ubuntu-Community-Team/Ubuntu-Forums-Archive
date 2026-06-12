---
title: "DVD not working"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by daveguy on 2006-11-01
I recently upgraded my 6.06 Ubuntu box to 6.10, following the directions published. Everything works fine, except that I can no longer play DVD movies, which I could play before. The disks are not even mounted on the desktop.

Couple things that I found after digging around. 1) there is no mount point for the dvd drive in media, just one mount point for a cd drive. 2) in /etc/fstab there is no entry for a dvd drive.

What would the proper procedure be for putting support back in for the dvd drive?

Thanks for any help in advance!

---

### Post by jsandys on 2006-11-01
DVD drives are listed as cdrom.

What graphics card do you have?  If you loaded a restricted kernel for nvidia or ATI on 6.06 Dapper Drake, I believe you need to reload the restricted kernel for your graphics card after the upgrade.

---

### Post by daveguy on 2006-11-02
Nope, don't have an advanced video card, i.e. nVidia or ATI. I believe it's a built-in Intel i810 on the motherboard. I've forgotten to check if cd's mount on the desktop, but I know DVD's do not mount on the desktop, or appear anywhere mounted in the system.

This is starting to get annoying, I'm getting close to the point of doing a clean install of edgy. I would like to avoid that, however. Is there some sort of config script I can run to setup the drive so it will work?

Again, any help is very much appreciated! Thanks in advance!

Dave

---

### Post by PrinceArithon on 2006-11-02
IT's not your video card here this is from the Dapper Wiki

 How to install DVD playback capability

ironss: gstreamer dvd plugin is available as part of plugins-bad (or ugly?) and does not work reliably. However, Totem works with the xine backend to play back DVDs. This will keep you going until gstreamer gets dvd playback. Note that you do not have to install xine-ui or mplayer as suggested in

    * Read #General Notes
    * Read #How to add extra repositories 

sudo apt-get install libdvdread3
sudo apt-get install dpkg-dev fakeroot debhelper # If you have AMD64.  You need dpkg-source.  Otherwise skip.
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
sudo apt-get install totem-xine

Stubby: gstreamer dvd plugin not ported to dapper yet. following instructions will not work properly

    * Read #General Notes
    * Read #How to add extra repositories 


sudo apt-get install libdvdcss2


My suggestion is that you consult this Wiki first this thing has helped me move 90% away from Windows...to be honest I Haven't used windows in 3 weeks since I installed Ubuntu on my computer.  Anyway here is the link to the wiki

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

---

### Post by daveguy on 2006-11-03
Hate to tell you this, but all the stuff you wrote to do -- already done it. I am at my wits end (which wasn't very far, strangely enough), and I don't know where to go!! AAAaarrrrgggghhhhhh!!!!!!!!!!!!!!!!

Anybody else have any ideas? The DVD player worked fine under dapper, but when I updated to edgy it will not even recognize dvd's! But for some reason or other, cd's work fine! Explain that one for me!?!?

Thanks again in advance for any help!!

Dave

---

