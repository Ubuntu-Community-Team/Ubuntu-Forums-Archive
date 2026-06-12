---
title: "installation freezes halfway through"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by daniel_a on 2007-02-03
I am installing 6.06 off of a live CD and the computer always freezes when the progress bar is at 48% and says "copying files ...".
I have tried setting the installer to erase the entire hard drive and again with setting up the partitions manually, it freezes with either of the options.  I checked the CD and it says it burned correctly and doesn't have any errors.  Could the CD still be bad and be causing the problem?

---

### Post by housam on 2007-02-04
Did you run the live CD before installing . Also check for the [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM"). maybe the CD still has some defects.
What is your pc specs?

---

### Post by daniel_a on 2007-02-05
Yes, I ran the live CD before installing.  I started the installer from the Ubuntu desktop while running on the live CD.
I checked the md5sum a while ago but I don't have the iso anymore so I will have to download it again to check that.  Is it possible to check the md5sum with the CD and not the iso?
My computer is a P3 1 Ghz with 1.3 GB of ram, it has an 18 GB SCSI hard drive.  I am putting Ubuntu on as the only OS, no dual boot.

---

### Post by meng on 2007-02-05
No, you can't really check the md5sum from the CD. It could still be that you have a bad burn, but without the original ISO you can't very well re-burn a good copy! What I would suggest is downloading the Alternate CD and burning that in order to install.

---

### Post by eapache on 2007-02-06
I'm having the same problem, only it's freezing at 65%. I believe it is caused (for me at least) by the fact that I modified my xorg.conf file to get it to work with my graphics card. I'm still looking for a solution. My thread about the problem is [here]("http://www.ubuntuforums.org/showthread.php?t=355033").

A few questions:

- What's your hardware like?
- Have you modified the xorg.conf file at all?
- What freezes(do you still have mouse, other tty etc.)?

My hardware and xorg.conf modifications are discussed in my own thread. When it freezes, my mouse still works, and gnome icons respond to mouseover, but x does not. When I click on anything controlled by x, the entire thing freezes (mouse included). If I go to another tty before clicking on x, it works ok, but returning to the graphical tty freezes it for good. Are there any logs I could access from a non-graphical tty that would help? My CD also appears to be burned correctly and without errors.

Hope some of this helps.

---

