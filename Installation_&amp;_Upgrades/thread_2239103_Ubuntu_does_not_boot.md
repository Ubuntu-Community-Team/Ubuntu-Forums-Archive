---
title: "Ubuntu does not boot"
date: 2014-08-12
forum: Installation &amp; Upgrades
---

### Post by em3raldxiii on 2014-08-12
Further to another post that I posted (which has not received any replies) that details how I could not get the system to boot after installing Ubuntu, I discovered this page:

[http://www.ubuntu.com/certification/hardware/201206-11396/](http://www.ubuntu.com/certification/hardware/201206-11396/)

which suggests that this particular machine (the HP Pavilion 23 All-In-One) is **certified to come with ubuntu preinstalled**.

So the one I am trying to install Ubuntu 14.04 on came with Windows 8 preinstalled.  After installing Ubuntu 14.04 64 bit (with no errors or trouble), the system wouldn't boot (it can still boot off the stick though).  I am wondering if there is something special about the version linked on the Ubuntu certification page above that will actually work on the PC.  Also, if that is true, I wonder if I can then upgrade it using the software updater.

Thoughts?

**Update:  This problem was solved here:  **[http://ubuntuforums.org/showthread.php?t=2238714](http://ubuntuforums.org/showthread.php?t=2238714) -- there does not appear to be any reason why one must use the version linked on the Certified Hardware page.  Go ahead and use the 14.04 64 bit image (or probably any subsequent newer ones, for that matter).

---

### Post by mörgæs on 2014-08-12
Have you tried [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) ?

---

### Post by em3raldxiii on 2014-08-12
Yep, I did indeed!  It seemed to go off without a hitch, and the output of the logfile was promising.  Unfortunately, upon reboot, it still says there is no OS (it doesn't even go to GRUB).

---

### Post by westie457 on 2014-08-12
Could you post a link to the logfile produced by Boot Repair please?
Some here might be able to spot the problem and suggest a solution.

Thank you.

---

### Post by em3raldxiii on 2014-08-13
UPDATE:

1.  I am not sure why, but the title of this thread was changed unbeknownst to me ... originally my question here was whether or not there was something special about the edition of 12.04 on the Certified Hardware page.  The new title essentially makes it sound like a duplicate of my original post, which was not the intention.  I am unsure who would change the title o.O

2.  The problem has been solved on the original thread:  [http://ubuntuforums.org/showthread.php?t=2238714](http://ubuntuforums.org/showthread.php?t=2238714) ... short version: I had to copy and rename one file in the EFI directory.  It was super simple, and Oldfred did an excellent job with the explanation.

@westie457:  Thanks for that, but as I mentioned, this thread wasn't originally intended for the purposes of analyzing the boot-repair log; I simply wanted to know whether or not there was something special about the release noted on the Certified Hardware page.  But thank you anyway, I am always humbled by just how generous everyone is with answering these questions. :D  Kudos, bro.

---

### Post by mörgæs on 2014-08-13
I changed the title, as the original 'Is it possible that Ubuntu 14.04 will not work on this PC?' was not helpful to people. What does 'this' mean? 

Anyway, good that you got it solved.

---

### Post by em3raldxiii on 2014-08-16
All good, [COLOR=#C61919]**mörgæs **[/COLOR]no worries.  I was just paranoid that someone would give me some flak for a duplicate thread.  But actually, back to my original question, was there originally something special about the release linked on the [http://www.ubuntu.com/certification/.../201206-11396/]("http://www.ubuntu.com/certification/hardware/201206-11396/") page?  I'm curious to know if the community/developers actually ended up generating a special image of the release for specific machines, and then when the new LTS edition came out, just incorporated the change or something like that.

---

