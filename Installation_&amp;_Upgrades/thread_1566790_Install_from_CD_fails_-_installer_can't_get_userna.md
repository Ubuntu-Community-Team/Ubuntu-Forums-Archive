---
title: "Install from CD fails - installer can't get username or password?"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by Doomspark on 2010-09-02
I am trying to install Ubuntu as a secondary operating system on my Windows 7 PC.  

System specs as follows:
AMD Athlon II X4 620 Processor 2.6 Ghz
4.00 GB RAM
ATI Radeon 4600 series video card

I downloaded the 32-bit ISO image from ubuntu.com and burned it to a CD.  When I try to boot, I get a purple splash screen with a couple of icons on the bottom.  Shortly thereafter, I get another screen that says Ubuntu and has 5 dots on it that change color from red to white in sequence.  During this time, my CD drive is active.

After a very long time, the drive goes quiet and I get an error that the installer can't find the username or password.  I don't remember the exact text of the error message. The system was hung and required a hard boot to recover.

Reading these forums, I rebooted the computer and this time pressed the escape key once the display had changed to the Ubuntu with the dots.  The username/password error came up quickly and was followed by several "Bus error" messages.  I ejected the CD and restarted the computer in order to come here for enlightenment.

What other information can I provide that would help?  I'm reasonably good with Windows but a total neophyte when it comes to Linux.

I'm going to try it again and this time record the exact error message (which is what I should've done initially).

EDIT:
The initial error reads
process 396 Glib Warning  getpwuid_r() failed with error unknown user id

Then I got: (several times)
/scripts/casper-bottom/10adduser line 20  Cannot open /root/usr/share/debconf/confmodule

Then I got:  (several times)
chroot cannot execute debconf-communicate:  Input / Output error

Last line is:
Kernel panic - not syncing. Attempted to kill init.

---

### Post by Doomspark on 2010-09-03
Some more digging around on these forums found me a thread about the original error message. It's in the General Help forums. Apparently this message has begun showing up on systems that were previously working with no problems.  There is no clear consensus as to cause or solution.  It does seem specific to Lucid. 

At least one person states that the message can be bypassed, but that assumes that the installation has already completed.  In my case, I can't even install.

Ignoring that message for the moment, what would produce the "can't open..." messages that I'm getting?  Is my CD faulty?

---

### Post by Rubi1200 on 2010-09-03
Two things to try perhaps:

1. download and burn the ISO again at the lowest possible speed.
2. check the MD5SUM: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by sikander3786 on 2010-09-03
> **Rubi1200 said:**
> Two things to try perhaps:

1. download and burn the ISO again at the lowest possible speed.
2. check the MD5SUM: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Actually before downloading, I will recommend to check the MD5SUM and if the sums don't match, then you are going to download anyway. :p

And still if that doesn't help, try the alternate installer.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate)

---

### Post by Rubi1200 on 2010-09-03
> **sikander3786 said:**
> Actually before downloading, I will recommend to check the MD5SUM and if the sums don't match, then you are going to download anyway. :p

And still if that doesn't help, try the alternate installer.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate)
Yes, sikander3786 point well taken!
And I agree with the alternate install suggestion as another possible option.

---

### Post by CharlesA on 2010-09-03
Those error messages point to a bad burn or a bad ISO. You can verify the cd by hitting any key after booting off it and selecting "check disk for defects."

---

### Post by sikander3786 on 2010-09-03
> **CharlesA said:**
> Those error messages point to a bad burn or a bad ISO. You can verify the cd by hitting any key after booting off it and selecting "check disk for defects."

Agreed. Forgot to mention it in my previous post. If the MD5SUMs of already downloaded image match, then the next step will be to check the disc for defects. Otherwise rewrite at the lowest possible speed as Rubi1200 mentioned.

---

### Post by Doomspark on 2010-09-03
I will check the MD5SUM tonight when I get home from work.
 
As I can't boot from the CD, I'm not sure I'll be able to actually check the CD for defects. 
 
If the MD5SUM is correct, I'll reburn the CD and see what happens.

---

### Post by Doomspark on 2010-09-03
Burning a new CD at 8x allowed me to install.... now I have another issue, but I'll start a new thread for that.  Thank you to all who posted.

---

