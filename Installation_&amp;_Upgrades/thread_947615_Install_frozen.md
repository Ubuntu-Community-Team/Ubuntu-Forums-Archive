---
title: "Install frozen?"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by Scurge on 2008-10-14
I recently got fed up with windoze crashing and decided to nuke my hard drive and install ubuntu.  I ran DBAN and wiped the HD clean.  However when DBAN finished it said "finished with non-fatal errors.  this may be caused by bad sectors on the HD"  since there was nothing on the HD, I couldn't figure out how big or how many bad sectors there were.  Keep in mind I am a novice with computers as far as setting up an OS or the technicalities of such.  (a tech might say that i know just enough to seriously screw things up.) This is not to say that i dont know my way around computers at all, i've been computing since the days of the 286 and I was a DOS junkie all the way up till Windoze '98. (lol even then I fought the transitiion tooth and nail.) before I get to the problem I feel that I should say that I have limited C++ expierence, and have a general understanding of command syntax and very limited expierence using a unix shell.  Basically i can understand the gist of the tech speak, but I may ask for a more detailed explaination of some terms and techniques.  Anyway, on to my problem.  Oh yeah, and my box specs..  It's an older factory built HP pavilion with an intel 1.4 Ghz processor and a 60gig HD and 1 gig of ram (i think, or maybe 512Mb) I edited the bios to check the a: (floppy) drive then the d: (CD) drive, then the HD to boot.  The version of Ubuntu I am trying to install is: ubuntu-8.04.1-desktop-i386.  

I was trying to install again this morning to get what the command prompt said so I could post it here and decided to try some of the other options.  I selected "Install Ubuntu without changing system configuration" (i think that's what the wording was)and the CD drive and HD started to spin up as expected.  I got to the background image, I guess (orange and yellow bird shape), and an empty white text box in the upper right corner.  This was about an hour ago.  It's still spinning the CD drive and HD like it was in the begining, but it seems to be froze.  Is this normal or did my box lock up?  If it did lock up, will it possibly cause more bad sectors if I do a hard shutdown (not cutting the power, but holding the power button in till it cuts off)?

---

### Post by wpshooter on 2008-10-14
Scurge:

I believe that I recall the error message that you said that you received after running D-Ban on your hard drive.  I believe that this means that you "messed up" when you entered the parameters for running the D-Ban session.  As I remember when I made some type of mistake (and I don't recall the exact sequencing) when entering the session parameters that I got that same message at the end of the session.  When I later went back and made the correct entries the session worked perfectly with no errors.  

Do either one of 2 things.  Go back into D-ban and carefully study the parameters that you enter for running the session (and I think I would do that to make sure that I could get a clean run of D-ban and that there is not actually something wrong with the hard drive) or you could get [www.killdisk.com](www.killdisk.com) (which is a much simpler and faster way of WIPING your hard drive) and WIPE the hard drive and the try then installation of Ubuntu again.

My recommendation would be that you get the ALTERNATE Ubuntu CD for installation since it somewhat increases your chances of a good successful installation and also make sure that whichever version of the Ubuntu CD that you use, that you FIRST check the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu BEFORE trying to install the O/S.

Good luck.

---

### Post by Scurge on 2008-10-14
I did verify the disk before I tried to install, the disk is OK.  I guess I'm gonna run DBAN again, but im not sure about what the right parameters would be.  I do know, however, that when the box had XP running, something was wrong with it and it was extremely slow.  all tests for malware came back clean, so I was thinking that it could be bad sectors on the drive.  Thanks for the help.  As of fight now the Ubuntu disk is still spining in the drive and both the CD and HD lights are still blinking, and it's now been 4 hours.

---

### Post by wpshooter on 2008-10-15
> **Scurge said:**
> I did verify the disk before I tried to install, the disk is OK.  I guess I'm gonna run DBAN again, but im not sure about what the right parameters would be.  I do know, however, that when the box had XP running, something was wrong with it and it was extremely slow.  all tests for malware came back clean, so I was thinking that it could be bad sectors on the drive.  Thanks for the help.  As of fight now the Ubuntu disk is still spining in the drive and both the CD and HD lights are still blinking, and it's now been 4 hours.

Unless your computer is from the dark ages, 4 hours no way !!!

I would do the following:

Get the hard drive diagnostic software from your hard drive manufacturer's website.

If the drive comes up as O.K., then get [www.killdisk.com](www.killdisk.com) and WIPE the drive then install Ubuntu from the ALTERNATE CD version and I think you will be good to go.

---

