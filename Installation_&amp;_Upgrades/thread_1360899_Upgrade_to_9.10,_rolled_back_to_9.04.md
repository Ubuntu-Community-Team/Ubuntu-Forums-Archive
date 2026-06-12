---
title: "Upgrade to 9.10, rolled back to 9.04"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by L a r r y on 2009-12-21
While I was setting this new swap meet computer up, I installed Kiwi 9.04, a flavor of Ubuntu 9.04, and decided before I got involved in production, I would upgrade to 9.10.

Firefox 3.0 in 9.04 has the same Preferences Privacy page as I saw in my Ubuntu 8.04 installation, and the same as Windows Firefox 3.5 has:

(I was going to insert a screenshot, but apparently I have to have it hosted somewhere on the Internet, so a word description follows:)

Title bar:  Firefox Preferences

**History**

[v] Keep my history for at least [   9 ] days
[ ] Remember what I enter in forms and the search bar
[v] Remember what I've downloaded

**Cookies**

[v] Accept cookies from sites      [Exceptions...]
.   [v] Accept third-party cookies
.   Keep until  [ I close Firefox ]   [Show cookies]

**Private data**

Here, a check box for "Always clear my private data when I close Firefox," and a Settings button.
A checked box for "Ask me before clearing private data, " and a Clear Now button, Help and Close round out the page.


I particularly like the method of handling cookies.  I place a list of sites where I want to stay logged-in in the Exceptions screen and allow them all to keep cookies.

I otherwise lose cookies when I close Firefox.


The Firefox 3.0 in 9.10 has an entirely different Privacy screen, and I did not take a screenshot of it while I had the chance.  No options presented except to clear cookies manually and something else, presented in a blue underlined link.


I also rolled back because I could not copy in my Firefox profile and see any of my stuff in there, same with Mozilla-Thunderbird profile and also with my gftp profile.

I was copying my 8.04 profiles into the newly installed 9.10 in my user folder.  I recall Firefox profile copied in some stuff and refused several JavaScript files.

910 has some nice looking features, but I had to get back up and running so I reinstalled 9.04.

Any thoughts?

The computer is a 1000 MHz AMD Athlon with 512 meg of memory and a 64 meg NVIDIA geforce video card.

---

### Post by Objekt on 2009-12-21
I tried a Kubuntu 9.04 to 9.10 upgrade over the weekend, but, like you, rolled back to my previous install (9.04 in my case) in short order.  Thank goodness I backed up an image of my system volume before running the 9.10 upgrade!  It took all of 5 minutes to restore my system to its former state, with the help of Clonezilla.

The 9.04->9.10 upgrade came very close to working, but there were two problems.

One, minor & an easy fix: the new kernel did not appear in the boot menu.  This one was a quick fix.  I merely had to edit /boot/grub/menu.lst to include an entry for the new kernel.  No big deal.  I'm used to the occasional probing of a *.conf file to get things working.

The second was major, and a showstopper.  Sound was freakin' BROKEN after the "upgrade."  I got sound when playing DVDs, but under no other circumstances.  Initially, I thought it was the old "No sound in Flash videos" bug again, which was frequently a problem for us 64-bit users until earlier this year, when Adobe finally fixed it.  I spent at least half an hour trying various Flash fixes & generally tearing my hair out in frustration, until I noticed sound was also not working in any other app, save playing DVD images in Kaffeine.
 
I tried to follow the "Ubuntu sound troubleshooting" thread, but the procedure to upgrade ALSA was no good.  At one point it wanted to download over 400 MB of miscellaneous files.  I'm not 100% sure, but I think it was installing TeX.  WTF?  Uh, no thanks, not going to do that.  I canceled and said to hell with it, I'll keep 9.04, thanks very much.  Then I reinstalled my 9.04 image.

I'm disappointed yet again.  This is at least the third time I've tried the "upgrade" feature in an Ubuntu variant, and the third time I've regretted doing it.  SO not worth the 2 hours of downloading new packages!

---

### Post by L a r r y on 2009-12-29
I recently compared notes with a friend who has installed 9.10 version of Ubuntu on his laptop, and he has Firefox 3.5.  His Privacy menu is the same as mine in Firefox 3.0 in Ubuntu 9.04, which is good news.  If I get hold of a spare hard drive that I can use to play with another version of Ubuntu, I will try 9.10 again.  And if I can dual boot between 9.04 and 9.10, I can see again if I can place my preferences over there.

Meanwhile my computer is up and running and I am getting my work done.

---

