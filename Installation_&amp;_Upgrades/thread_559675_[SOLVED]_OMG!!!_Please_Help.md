---
title: "[SOLVED] OMG!!! Please Help"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by S.S.S.P5 on 2007-09-25
well, Im sure you experianced users are used to hearing this by now, but surprise surprise I cant get desktop effects, beryl or my sound card to work, Ive had feisty installed for about a week now and have managed to get a bunch of software to work jackd- ect, ive installed the "low latency" kernel, beryl, emerald, the usual, that took a bit of work but i got it up and running succesfully, so I know with a little help I should be able to get the sound and video cards up and running

I have followe all of the resources on the internet that i could find, but alas, i get half way with the instructions and every time one seems to fail, or crash the desktop making me have to reboot. Ive also had the GUI not open a dozen times and have to reset the xserver- so Im learning, and am too proud to quit due to frustration.  This is not going to "beat" me.

I digres,  I got the original kernel running from the live Cd, liked it,  and reformatted the drive so going back to XP is not an option either way oops :) 'bah well, and I actually went out to buy stuff for this box so I could create music and videos and have a really cool GUI (as depicted in YouTube) and so far all i have to show for my money/time, is a huge mess d'oh

the system is a..
asrock motherboard
genuineintel p4 @1.6
ati radeon rv280 (i know)
creative labs live! 5ch sb0200
1.5 gig of ram
dvd burner
dvd drive
multicard reader
basic adi provista monitor E75

any help at all would be greatly appreciated, as I really want to be "linux saavy"

---

### Post by Seisen on 2007-09-25
Have you tried this link to get you graphics card working?

[https://help.ubuntu.com/community/Radeon_9200/9250_(RV280)_and_DVI]("https://help.ubuntu.com/community/Radeon_9200/9250_(RV280)_and_DVI")

---

### Post by bliffle on 2007-09-25
I think your problem is that you've rushed ahead too quickly.  I can only guess, but I'm going to suppose that you didn't lose any of your important data when you re-formatted your HDD and that you can start over and proceed methodically to develop your target system. It is near impossible for an outsider, no matter his experience with linux, to come in now to your worksite and solve your problems without doing that very thing. And it is even worse trying to do it remotely, like this.

My suggestion is:

-commit yourself to rebuilding your system methodically from scratch.

-commit yourself to allocating 3 weeks to the project. If you proceed methodically you may be able to trim that to 2 weeks, but if you go off helter-skelter it will expand to 4 weeks, 5 weeks, 6 weeks, even longer. Haste is the enemy of schedules.

-make a choice between 7.04 feisty and 7.10 gutsy. I recommend 7.04 because it has been very stable and gutsy is an unknown quantity. Yes, it's heartbreaking to reject the attractions of Gutsy, but you can revisit the issue and ugrade in a few weeks. Fortunately, that is pretty easy.

-reformat your HDD and plan a new partition layout. As a starter you can use the layout that LiveCD or AlternateCD will volunteer. 

-Install Feisty from the LiveCD. I recommend LiveCD over AlternateCD for the simple reason that Live is the only one I've used and I've had no problems. 

-devote the rest of the day to solidifying your position. Get your network hooked up (this may take you a couple of days, depending on hardware). Make sure your ethernet (cat5, J45 connector) system is going, even if you will be using wireless, because you may need it in a pinch. Every ethernet is supported by every OS and every wireless AP/ router.

-exercise every pulldown in the pulldown menus, even if you just cancel them immediately. this will provide valuable cues to your future efforts.

-make sure you understand the Synaptic GUI and Aptitude and apt-get commandlines.

-get Xchat going, you may need IRC for live group meetings.

-exercise the ready-installed apps, like Gimp, mediaplayer, movie player, gnome Baker, etc., to create a baseline of knowledge. Even with more sophisticated studio apps you will find this lore useful.

-study and exercise "ffmpeg" from the commandline. In any studio work you do you will find this powerful weapon to be a lifesaver.

-spend a little time learning 'dd' and 'pcopy' since you will eventuall want to create new partition layouts for the purposes of data sharing and data security, especially with large multimedia files.

-give yourself a few days to repeatedly use the common tools and thoroughly exrcise updates through Synaptic and Aptitude (you will end up using both).

-When you feel comfy with this stuff, start adding the fancy stuff in one step at a time so you can test as you install.

You will find that your queries here to the forum will be better targeted to enable specific solutions. You will also find that you can help other folks.

---

### Post by S.S.S.P5 on 2007-09-25
ok so far so good....

james@james-desktop:~$ sudo apt-get install build-essential fakeroot
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
fakeroot is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
james@james-desktop:~$ sudo apt-get build-dep xserver-xorg-video-ati
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
james@james-desktop:~$ apt-get source xserver-xorg-video-ati
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 1010kB of source archives.
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main xserver-xorg-video-ati 1:6.6.3-2ubuntu6 (dsc) [1218B]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main xserver-xorg-video-ati 1:6.6.3-2ubuntu6 (tar) [979kB]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main xserver-xorg-video-ati 1:6.6.3-2ubuntu6 (diff) [30.5kB]
Fetched 1010kB in 31s (31.6kB/s)                                               
gpg: Signature made Wed 11 Apr 2007 04:53:25 AM EDT using DSA key ID 76682A37
gpg: Can't check signature: public key not found
dpkg-source: extracting xserver-xorg-video-ati in xserver-xorg-video-ati-6.6.3
dpkg-source: unpacking xserver-xorg-video-ati_6.6.3.orig.tar.gz
dpkg-source: applying ./xserver-xorg-video-ati_6.6.3-2ubuntu6.diff.gz
james@james-desktop:~$ 

then it says this....

This downloads three files and unpacks the sources into the directory xserver-xorg-driver-ati-version. In this directory is the file, src/radeon_bios.c what we need to edit. Towards the end of this file is a comment saying:

        /* revision 4 has some problem as it appears in RV280,
           comment it off for now, use default instead */

And after this comment follows a code block that has been commented out. We need to re-enable this code by removind the commenting-out. In my case deleting lines 574 and 561 did the job.

the last time i tried to do this i ended up with a src/radeon_bios.c., src/radeon_bios.c.~,src/radeon_bios.c.~~, plus the lines it says to delete are not the ones listed above, Im sorry Im brand new to this, but a fast learner- lil help plz!

---

### Post by S.S.S.P5 on 2007-09-25
i fully see what your saying about learning more basic stuff first, but im the type of person to jump in with two feet first, and thats the way ive ever learned anything, so this is the approach i want to take rather than recompiling the kernel and starting again for the fourth time, being that ive been through that twice already, and am sattified with the current setup except the following 

I have absolutley everything on the mother board enabled and working, perfectly, i might add, including my little windows button, internet, dvd drives, internal memcard  reader, jackd, jack server (that was an ordeal) the only two things i cant get to work are my pci cards, 

ATi Radeon R9200 se (visible in lspci)
Creative Live! SB0200 (not visible in lspci)

I have found both of their drivers in linux format, and have followed multiple install guides and how to's but they either freeze the OS, not work correctly, or cause the GUI to not start, forcing me to reconfigure xserver back to vesa. 

so Im not completley ignorant to whats going on on my feisty system, I just want my RealTime support for midi to work and to have the cool graffix i saw on youtube on my linux system

---

### Post by S.S.S.P5 on 2007-09-25
Got desktop effects enabled- most likely by fluke, not even sure what it was lol!

---

### Post by bliffle on 2007-09-25
Oh. You just want to shift the work to somebody else. Like George Bush: make a big mess then get someone else to fix it. Oh.

---

### Post by S.S.S.P5 on 2007-09-25
i bet you'd rather me be dragged off and tasered like the sniviling coward John Kerry, for speaking up tho, right?

---

### Post by bliffle on 2007-09-26
Coward? You mean like the guy who dodged his duty in the TANG? Or the guy who charged the source of fire?

I think you're a Champagne Corps kind of guy. Nowhere in sight when there's work to be done, but right on the scene at harvest time. First guy in the payroll line. A cream-Skimmer, high-rider, credit-ripper, parasite.

IMO If we solved your problem, you wouldn't be back until you had another problem. Would you return to help others solve their problems? I don't think so.

I told you how to find the solution to your problem.

Bye bye.

---

### Post by S.S.S.P5 on 2007-09-27
> **bliffle said:**
> Coward? You mean like the guy who dodged his duty in the TANG? Or the guy who charged the source of fire?

I think you're a Champagne Corps kind of guy. Nowhere in sight when there's work to be done, but right on the scene at harvest time. First guy in the payroll line. A cream-Skimmer, high-rider, credit-ripper, parasite.

IMO If we solved your problem, you wouldn't be back until you had another problem. Would you return to help others solve their problems? I don't think so.

I told you how to find the solution to your problem.

Bye bye.

oooOOOHhhh, sounds like some ones got a dirty diaper!

   Way to psyhco-analize a person in one paragraph, two can play at that, here's what I get from you..
  
 your a cowardly internet "tough guy" who can't say what he really wants to people on a day-to-day basis, so to fulfil your need to be a complete jackass, by being ignorant and rude to people who don't even know you, and can otherwise no way inflict pain or hardships on your life, you degenerate.

  What was it? did your dad not hug you enough when you were little, huh? 
  Very little parental guidance, was it?
  Let me guess, you a little less than well endowed , aren't you. 

 Get a life , you pathetic excuse for a human being

---

