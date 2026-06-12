---
title: "Trouble installing Ubuntu on OS 9.2"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by JoeJoeMa on 2006-09-10
To put the situation in context, i barely know macs and i even know less about linux. But i'd like to learn. So when an imac was givin' to me a couple months ago, i figured i'd put linux on it. Well today i finally got around to putting it on. Except, the OS wont boot from the CD, i tried pushing C at startup but nothing happens. I really dont know anything else beyond that... I tried reading troubleshooting faqs but they all were using OS X. So im kinda stuck. I feel like not only a newb, but an incompetant one.

Any help would be greatly appreciated.

---

### Post by linear on 2006-09-11
First: what model iMac and how much memory? The answers may help.

Some items to look at:

1. Does the iMac boot other bootable CDs? (Like a Mac OS install disk.)

2. Was the downloaded iso file OK? (Compare MD5 checksum to that posted at download website.)

3. Was the iso burned to the CD as an image, and was it burned at a slow speed (4x or less)? (Bad burn is a common problem.)

4. If this is the Desktop CD, try the alternate install CD.

5. Is the keyboard an Apple keyboard, and is it plugged directly into the iMac (not a hub)?

6. Can you boot into Open Firmware? (Hold down Command-Option-O-F at startup.) If so, try typing **boot cd:,\\:tbxi**
and press Return.

Good luck.

---

### Post by JoeJoeMa on 2006-09-11
actually, yeah that woulda been good to detail some of that information.  it has 256 megs of ram, um model of imac... i dont know how to check that

1. i dont have any other mac OS discs.

2. i didn't download it i got it in the mail

4. i... dont know what desktop CD means... but i dont have an alternate CD

5. its an apple pro keyboard plugged directly into the computer

hm... alright i think this is the model number. I found it in the apple system profiler RN0329RWJV9

also the processor is a powerpc g3 450 mhz


ALSO it seems to have a dvd drive instead of CD, though i dont think that should make a difference. it might. i dont know much about macs.

---

### Post by linear on 2006-09-11
The Desktop CD (what you got in the mail) is a Live CD; it can (normally) be used to boot into Ubuntu without affecting the hard disk, and to install Ubuntu if you wish.

The alternate install disk is primarily for installation (though it has some other functions). It doesn't require booting into a gui, which can help in some situations.

You may still want to try downloading the alternate install CD if you can.
But it would be good to figure out if that iMac can boot from a CD at all...

---

### Post by JoeJoeMa on 2006-09-11
well from what i read, ubuntu should work on the imac.

---

### Post by JoeJoeMa on 2006-09-12
alright so i put the alternate install disk it. It's still not booting from startup. I tried pushing C and i tried pushing command-option-o-f at startup. still nothin.

---

### Post by linear on 2006-09-12
Hmm. Running out of ideas here.

The CD drive could be bad, or just finicky. Some of the older iMacs are particular about CD-R media.

You might want to repost in the [Mac forum]("http://www.ubuntuforums.org/forumdisplay.php?f=133"). Maybe someone there has more suggestions.

Edit: In fact, here's another possibility from that forum: [http://www.ubuntuforums.org/showpost.php?p=1426164&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1426164&postcount=3)

---

