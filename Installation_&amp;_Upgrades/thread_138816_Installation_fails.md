---
title: "Installation fails"
date: 2006-03-02
forum: Installation &amp; Upgrades
---

### Post by WebbyBabe on 2006-03-02
I've burned a copy of Ubuntu many times and run into the same problem. It fails at the "installing remaining packages" part. What should I do?:confused:

---

### Post by Herman on 2006-03-02
How much time are you allowing that part of the installation to run for before you give up? 
And are there any error messages or other unusual behavior or symptoms/occurences?

That one is the second most time consuming part of a 'Breezy' install, taking around ten minutes on an average computer. It may appear to stop at times and pause for quite lengthy periods and it looks like nothing is happening. You hard drive led light might still be blinking though.

On an older computer (400mhz CPU), it takes twenty minutes for this progress bar to complete.

The most time consuming part of the install (for me at least) is the 'installing packages' progress bar after the GRUB boot loader gets installed and the system re-boots. That one takes fifteen minutes on a standard modern computer (3.0 Gz), and 40 minutes in a 400 mhz older computer.
Good luck, from (Herman) :-D

---

### Post by UbuntuPad1 on 2006-03-04
[QUOTE=Herman]
The most time consuming part of the install (for me at least) is the 'installing packages' progress bar after the GRUB boot loader gets installed and the system re-boots. That one takes fifteen minutes on a standard modern computer (3.0 Gz), and 40 minutes in a 400 mhz older computer.
Good luck, from (Herman) :-D[/QUOTE]

Well, THAT would have been an important bit of information to put into a message window.  My install's been on "Installing packages: Preparing for installation. . . " for like twenty minutes now.

---

### Post by stoeptegel on 2006-03-06
I have the exact same thing with a fresh reinstallation of (k)ubuntu 5.10, this DVD worked perfect a few months back. :confused:

---

### Post by cjj on 2006-03-06
I am having a similar issue with 5.10. The "copying remaining files" step failed after about 85%. Then when I continued, the computer rebooted, booted into Ubuntu, and started the "Installing packages" process. However, after over 30 minutes it is still on 0% progress. This is a P4 2Ghz processor, so not sure why it would be so painfully slow. I am letting it go, but suspect nothing is happening. Any ideas?

thanks in advance.

---

### Post by stoeptegel on 2006-03-06
I could skip that part> reboot at the end of procedure without DVD> put DVD back in and finish installation. Dunno why it still breaks at you, but i know the feeling.

---

### Post by cjj on 2006-03-06
uf....well, I haven't been able to reboot without that process. And I waited over 2 hrs and still had 0% progress. (this is a dell latitude laptop, a couple of years old). 

I just checked the CD I used to install and it seems to be good. Is breezy badger really stable? Or should I grab an older version?

---

### Post by cjj on 2006-03-06
just as an update...I put in a new CD on the reboot and it loaded. Amazing I already tried that half a dozen times and no results...now I am logged in. Though, in a separate bizarre issue, when I try to run the Gnome networking admin tools, it tells me my root pw is wrong (even though I can "su" on a shell).

---

### Post by stoeptegel on 2006-03-06
I'am not so a linuxguru myself, but does the breezy live-cd run smooth? I always try a live-cd first to make sure my hardware doesn't mess up a installation.

Yeah breezy is pretty stable for me, but you might wanna check the wiki: maybe your laptop is listed.
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=latitude&titlesearch=Titels](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=latitude&titlesearch=Titels)

---

### Post by plut0 on 2006-03-09
I had the same problem and this is what I did to fix it...

Load and mount the cdrom then reload apt-get:

kill -HUP `ps aux | grep apt-get | grep -v grep | awk '{print $2}'`

---

