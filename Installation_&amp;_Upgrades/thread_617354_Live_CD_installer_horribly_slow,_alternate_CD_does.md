---
title: "Live CD installer horribly slow, alternate CD doesn't boot"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by chapado on 2007-11-19
I downloaded the Live CD a few days ago and tried it on my current laptop, all the programs I tried worked perfectly. Yesterday I decided to install it on an old laptop I have so I can play around with it and see if I'm able to switch over from Windows XP. 

The laptop is a p4 1.8ghz with 256mb ram. Once it had booted, I noticed it was quite a bit slower than when I had tried it on the newer laptop. Understandable, I thought, this is a 4 year old laptop. The problems started when I tried installing onto the hard disk. I double clicked the install icon, but nothing happened. After double clicking again, and waiting 5 minutes, the install window appeared, but each screen took between 20 and 50 minutes to 'load'. After two and a half hours, while it was on screen 4 loading grub (IIRC) it gave me an error window that I didn't manage to read (it wasn't loading the full window, all I could see was the title) so I turned it off.

Today I tried with the alternate cd, but it doesn't boot, and in CentOS (the laptop's current OS) it can't read the cd. It can read the live-cd perfectly. MD5 hash is correct, and I verified the cd content after burning with nero. I also just re-burned it with infrarecorder and it's still not booting. My WinXP laptop reads the CD fine though :S

---

### Post by kwanbis on 2007-11-20
A friend of mine is having the same issue:

He has:
* AMD Sempron 3000
* 512 MB RAM DDR 333
* 30 GB Maxtor HD
* Mother Asrock
* Integrated Video

He burned at 4, 8 and 16x.

It takes 5 minutes to go from screen to screen. Any ideas?

---

### Post by kwanbis on 2007-11-21
bumped.

---

### Post by Pumalite on 2007-11-21
256 MB of RAM> Feisty Xubuntu Alternate CD:[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
Or smaller distro: DSL or Puppy.

---

### Post by kwanbis on 2007-11-21
my friend's PC has 512 MB of RAM. That shoudln't be an issue.

---

### Post by Pumalite on 2007-11-21
Your friend might have other problems. I'm answering your specific question. With 256 MB of RAM you cannot boot a Live CD unless you make a 500 MB /swap partition ahead of time.

---

### Post by kwanbis on 2007-11-21
What other problems do you think he could have? I never asked a question about 256 MB of RAM, so i don't understand how you are "specifically answerint it".

As previously stated, he has:
* AMD Sempron 3000
**[COLOR="Red"]* 512 MB RAM DDR 333[/COLOR]**
* 30 GB Maxtor HD
* Mother Asrock
* Integrated Video

---

### Post by Pumalite on 2007-11-21
You hijacked this thread.

---

### Post by kwanbis on 2007-11-23
Don't you have anything usefull to say? We are both having the same problem, only diference is memory. Do you rather have 15 threads about the same?

---

