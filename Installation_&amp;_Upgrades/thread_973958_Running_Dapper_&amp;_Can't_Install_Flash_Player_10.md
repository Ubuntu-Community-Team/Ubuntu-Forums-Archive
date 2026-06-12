---
title: "Running Dapper &amp; Can't Install Flash Player 10"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by *Zebedee* on 2008-11-07
Hi I am hoping that somebody out there can help...

Since the web upgrade to FlashPlayer 10 I have not been able to use any FlashPlayer facilities online including YouTube etc.

I am running Ubuntu Dapper Drake 6.06 LTS with Firefox 2.0.0.17
I am super happy with my computer system, it's great and very customisable, so don't want to upgrade, but I can't install flash player 10 on my machine.

When I download it from adobe, it arrives and sits neatly on my desktop, there to stay! I click to extract and click to run the installation package, it seems to install fine but when I visit a flash site I find myself in the same predicament.

I have tried the direct 'install plugin' buttons online, they seem to download properly and tell me that flash has been installed, yet when I hit youtube, there are no videos visible!
I have tried turning off my machine after the install and restarting fresh, but no joy...

I've checked add/remove and synaptic package manager and can't find anything relevant to install, and now I'm quite stuck!

If any wise Linux users out there could spare the time to explain the problem and the process i need to use to rectify my very annoying issue I would be very greatful... :-)

Many thanks for your time in advance.
Zebedee :-)

---

### Post by rexmundy on 2009-02-06
I too am trying desperately to find out if there is ANY WAY WHATSOVER to get Flashplayer to work on Dapper. I must have read 500 posts by now and followed at least 100 different instructions, and as USUAL it still doesn't work.

So one last try.

Is there anybody out there that can tell us HOW to get WHICH Flashplayer plugin to work in Dapper? And no, I will not just upgrade to Hardy or some other Bloatbuntuware because they do not work well on my system. I run Xubuntu Dapper because it does work better and faster than any other Linux OS and I would like to stay with that.

---

### Post by dougalkerr on 2009-02-06
Did any of you guys get Flash to work yet as I can't either. I am running Dapper coz any upgraeds on this old machine knock hell out of my graphics and I usually end up with more of a mess than an upgrade.
So any help is DEFINITELY appreciated...

---

### Post by rexmundy on 2009-02-10
I finally accidentally did it. I'm a bit unsure of all the things I did, but here's my latest theory on how to get Flashplayer 9 (because 10 won't work for some reason) on a UBUNTU DAPPER system.

Many thanks-for-nothings to all the people out there who didn't tell me anything useful for months, leaving a complete novice to muddle through yet another Linux quagmire.

First you will need a live CD of some other Linux that will let you edit things you're not "allowed" to edit with your Ubuntu. Personally I use a Slax 5 live CD that does this, but you may also be able to use Mepis, or Mepis Antix (Spartacus is still my favorite of these) or Knoppix or some other live CD I don't know about. But like I said, I have a Slax 5 that does the job.

On a normal install of your Ubuntu there are many repositories not included for downloading things with Synaptic that you might want but don't have. If you know how to edit your sources.list and update Synaptic then do it. If you're not comfortable with that then leave it alone and this Flashplayer tweak will probably still work.



======================================

For anyone interested here is my own Xubuntu Dapper sources.list which seems to keep my machine happy:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) dapper free non-free

deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) dapper free non-free

deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) dapper-commercial main

===========================================

I have a huge amount of extra things added in Synaptic, such as most of the gstreamers and lame, lame0, mplayer, vlc, etc.

I also ran this in terminal as well:
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs


NOTE: In Synaptic make sure you do NOT have the flash plugin-nonfree thing ticked. You do not want to upgrade because Flashplayer 10 apparently won't work with Dapper but 9 will.

============================================

Search the internet for a download package of Flashplayer 9. I found it in various places as "flash-plugin-9.0.124.0-release.i386.rpm" and similar things. You need to extract the package somewhere like on your desktop so you get an unpacked Flashplayer file. Within this main file you will find another file somewhere called "libflashplayer.so" or similar. This is the important one so remember where it is.

Now close down your Ubuntu system and restart it with the other live CD (as I said in my case this was Slax 5).

Go to wherever that "libflashplayer.so" file was and copy it. Then go to "/usr/lib/firefox" and look for the plugins file, and then copy the .so into it. I found another .so file there already so I knew this was the right place.

Close everything down and then restart your computer as normal on Ubuntu and if you're lucky you will finally have a flashplayer working. No telling how long this tweak will last since the evil Flashplayer people keep putting out new versions all the time but it should be good to go for some time yet.

I may have accidentally done some other things along the way in my frustrated tweaking, but as far as I can tell the main point is that you get the Flashplayer 9 .so file into the Firefox plugins folder. That seems to be the basics of it.

Good luck, hope it works for you. I am glad to finally have Xubuntu Dapper running on a weak old box with Flashplayer.

---

