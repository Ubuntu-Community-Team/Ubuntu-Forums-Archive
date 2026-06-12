---
title: "Installation Issues - Freezing during boot"
date: 2010-07-29
forum: Installation &amp; Upgrades
---

### Post by DarthTeufel on 2010-07-29
Hi all,

I'm a newer linux user and am trying to install ubuntu 10.04 AMD64 version on my desktop computer.  The computer has an Abit motherboard with an AMD 64 X2 Athlon, Manchester style CPU.  2 gigs of ram, and a BFG geForce 7800 graphics card.

I've downloaded and burned the desktop AMD64 install to a CD.  When I try to boot from this CD on my desktop, the system freezes just as the ubuntu logo is about to disappear.  Then the screen goes a bit wanky with multi colors everywhere.   Then the computer is frozen and I have to reset power to do anything.

Currently, Windows XP is installed on the desktop.

If you need any other information, please let me know.  Looking to get ubuntu up and running and educating myself in teh world of linux.

---

### Post by AClark on 2010-07-29
You could try some different boot options to try and figure it out.

When booting from the CD hit escape when the two little icons first appear at the bottom of the screen.

Then choose your language and when you can see the "Try Ubuntu without installing" menu hit F6 for other options

A menu with several options will pop up - arrow down to "nomodeset" and hit the spacebar to put an X beside it then hit escape and it will go away.

You will notice a line of boot options near the bottom of the screen. If you left arrow until the cursor gets to the right end of "quiet splash" then you can backspace until it's gone (quiet splash that is).

Now if you hit enter it will start to boot without the Ubuntu splash screen and you can see what is being loaded and maybe get a clue as to what is causing it to hang.

The wonky colors might implicate the video driver and nomodeset will cause an older more basic driver to be used - if that works you have another clue.

Another thing you could try since you only have 2 gigs of ram and there is no advantage to using the 64 bit version unless you have more than 4 gigs - is to download the 32 bit iso and try that. 
[http://ubuntu.media.mit.edu/ubuntu-releases/lucid/ubuntu-10.04-desktop-i386.iso](http://ubuntu.media.mit.edu/ubuntu-releases/lucid/ubuntu-10.04-desktop-i386.iso)
 It's always possible that this particular problem only effects 64 bit Lucid.

Lucid 32 bit installer will even install a pae version of the kernel if it detects more than 4 gig ram that can take advantage of the extra ram.

You can experiment with other boot options if this doesn't help. You can try any or all of the ones in the popup to your hearts content.

Good Luck

---

### Post by DarthTeufel on 2010-07-30
I managed to get Karmic Koala installed ok.

But now I have a new issue.

Ubuntu loads up ok, and I get to the user login screen.  When I select the user I created during installation, the system freezes.  The screen gets distorted similar to what I described above.  I then have to reboot.

Reading through the forums, it seems like some people booted into recovery mode via GRUB, but I don't get a menu selection.  Is there some command to take you to a selection screen?

---

### Post by AClark on 2010-07-30
From the grub2 guide here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

"On a new install of Ubuntu 9.10 or 10.04 with no other installed operating system, GRUB 2 will boot directly to the login prompt or Desktop. No menu will be displayed. 
Hold down SHIFT to display the menu during boot (formerly ESC in GRUB legacy)."

---

### Post by DarthTeufel on 2010-07-30
Thanks for all your help.  I managed to get everything up and running tonight.  Bunch of little issues, but the main one was updating the Nvidia driver.  Once I did that, smooth sailing.

---

### Post by AClark on 2010-07-30
Glad to hear of your success.  Hope you have as much fun as I have had since I switched to Ubuntu as my main OS.

These little problems can be aggravating but somehow I get more enjoyment out of solving them than I do trying to keep Windows working.

Don't forget to mark this thread SOLVED using the forum tools at the top of the screen.  Enjoy.

---

### Post by DarthTeufel on 2010-08-02
It was a good deal of frustrating fun, but the payoff, of getting everything to boot smoothly was worth it.

I had messed around with a gentoo distro about 5 years ago, but ended up abandoning it.  Very happy I got Ubuntu up and running.  These forums were extremely helpful.  Just about every problem I encountered had a solution somewhere here.  Just a matter of thinking up better keywords to search with.

Thanks again for your help.

---

