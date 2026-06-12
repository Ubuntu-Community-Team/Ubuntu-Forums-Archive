---
title: "Big Installation Panic/Crash problem *Video*/ Cannot boot live cd"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by werensgruner on 2010-05-13
Hello! I previously managed to install Ubuntu 9.04 using the regular  Live-CD by using the no-ahci option. Now I am trying to install Ubuntu   10.4 LTS with an alternate install CD but even tho when i use the same  options, I get a black screen then everything messes up and I get this:

This  is a video of what happens:
[http://www.youtube.com/watch?v=Ogmpo_D1Y1I](http://www.youtube.com/watch?v=Ogmpo_D1Y1I)

So I downloaded the regular installation CD and I had a big surprise again...The same thing happens  except that its not white but purple.

No  matter which option I select its still the same. Note that this did the  same thing when I tried to install Ubuntu 9.04 with the Alternate CD.

I have a SiS motherboard. I tried OpenSuse just for the fun of it and it works!!! But the things is I don't like OpenSuse I would really like to make it work with Ubuntu.

---

### Post by quixote on 2010-05-15
It looks like some kind of incompatibility with your monitor / video driver, but I must admit I have no good ideas on how to start troubleshooting if you can't even boot a livecd.  Could it possibly be a bad burn?  

If ubuntu is having video problems, it should default to an ugly old 800x600 with minimal colors that can be seen on just about anything.  It shouldn't act like a TV on the fritz.  That's why I'm wondering if maybe the cd is bad.  Can you test it in another machine?

---

### Post by pallanium on 2010-05-17
Hello! Thank you for the response. I test both CD and they worked perfectly on other computers. I must specify that I have a very shitty graphic card: SiS 740 . But well my Laptop works smoothly on OpenSuse but I'd rather have Ubuntu.

I can't even boot in console mode so I wonder whats happening. 

Thank you again!

---

### Post by pallanium on 2010-06-08
I still havent manage to solve my problems. If you have any idea, please tell me!

---

### Post by quixote on 2010-06-08
I did a search for [ubuntu sis graphics driver]("http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+sis+graphics+driver&ie=utf-8&oe=utf-8") and a number of links came up, including posts on forums about editing xorg.conf and installing sis-specific drivers and modules.  There's also reports of an ubuntu bug that sounds a lot like what you're seeing.  :(

Most of the forum solutions seem to be pre-Lucid, so they may not apply.  But it does sound like some customizing of config files is the only way to get that to work.  :( :(

If you want to give it a try and have further questions, just keep asking.  :biggrin:

---

