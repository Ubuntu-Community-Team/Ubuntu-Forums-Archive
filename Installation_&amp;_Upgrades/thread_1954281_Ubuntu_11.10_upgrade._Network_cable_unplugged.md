---
title: "Ubuntu 11.10 upgrade. Network cable unplugged"
date: 2012-04-07
forum: Installation &amp; Upgrades
---

### Post by paulcwatson on 2012-04-07
Hi, I recently inherited a desktop box (no wireless) with Ubuntu on from my son. It worked great until it invited me to upgrade to v 11.10. on about the second use. having done that - no network and the network panel on "hard wired" it says "Network cable unplugged" It is not, in fact it is very much plugged with both leds active at both ends.
 
I cannot ping the hub. My son tried a bunch of stuff to no avail. If it is not resolved tomorrow, hello windows - I need this machine to work!!

---

### Post by darkod on 2012-04-07
If you run:
ifconfig

what does it say?

Also, what does it say:
cat /etc/network/interfaces

You can also try this: download the 11.10 image, burn a cd with it (low speed, 8x or 10x) and boot into live mode with it. See if the wired network works in live mode. It usually should.

---

### Post by paulcwatson on 2012-04-08
Hi thanks. I did the disc, and it worked great, the I decided to do an upgrade install (v11.10 to 11.10) after it installed more problems, first no mouse would work (USB or PS2) even though it did during the install, and it justs asks me for my password over and over. I know its the right password because if i try a different one I get an "invalid password" message. 
 
I am now trying a full reinstall from the disk, I hope this works because I am loosing faith rapidly, I am trying to set this up for a business use and it has wasted an awful lot of time, I may as well cough up for Windows XP and MS office at this rate

---

### Post by darkod on 2012-04-08
Sorry for your troubles. All versions are generally stable but for serious business use you might want to consider using only LTS (Long Term Supported) releases. At this moment, they are released every 2yrs and have a 3yrs support term (5yrs for the server version).

The next LTS is actually around the corner, 12.04 LTS. The previous one was 10.04 LTS.

See how it goes with a new install of 11.10 and later think about using only LTS. You don't need to upgrade every 6 months and get into potential issues. With LTS versions you can upgrade from one to the next, for example directly from 10.04 to 12.04 (once it is released at end of April).

---

### Post by paulcwatson on 2012-04-08
Hey, thanks for your help. The reinstall seems to work, I logged on and hsve mouse & internet! would you reccomend that I go straight to 12.04 LTS as soon as it comes out, is there a good chance of a painless upgrade from 11.10?
 
Cheers  Paul,

---

### Post by darkod on 2012-04-08
Unfortunately, I don't think anyone can guarantee you a painless upgrade. I guess there are too many unknowns that can't always be covered. I do think the developers are doing their best for their part.

As you saw in this example, a clean install almost always works better than an upgrade.

What you could do is this: Once 12.04 is out, make a full backup of your data and try the online upgrade. If it fails, do a clean install of 12.04 and put your data back (since you had a current backup).
One more option for upgrade is to do it from a cd. I think it was introduced recently. If you are running 11.10 and put in a cd of 12.04 with ubuntu running, it should offer an upgrade to 12.04. Note that I haven't tested this, I have read people saying that option comes up.

As for me personally and upgrades, I never do them. Not because I had some bad experience, simply I believe clean installs are better. I have my ubuntu installed with separate /home partition which helps doing a clean install without losing any data or settings in the home folders. That's how I do it. When ever I want a newer version, I do a clean install reusing the existing /home partition.

---

### Post by paulcwatson on 2012-04-09
Great - Thanks

---

