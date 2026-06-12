---
title: "My System and Ubuntu just don't mix"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by KharmaPolice on 2007-08-21
Hey guys,

  I've been pouring over these forums for hours now and can't seem to find anyone with my exact problem.

I've been trying to install Fiesty for about 4-5 days (I really don't remember anymore, it feels like forever) and thus far have only been met with frozen machine for all my efforts.

I'm trying to dual boot Fiesty with Vista (which is what I'm writing this from now).  Every time I try loading the live install (both the cd and dvd - check sums are good and I did write them pretty slow) I keep getting these weird error messages.  They're never quite the same.  Rather than typing them all out, I decided to do some pictures with my digi cam.  Here's one if I just boot normally from the disk (Run or Install Ubuntu option): 
[[IMG]http://img514.imageshack.us/img514/6324/dsc00050ca8.th.jpg[/IMG]](http://img514.imageshack.us/my.php?image=dsc00050ca8.jpg)

followed by this one:
[[IMG]http://img514.imageshack.us/img514/1869/dsc00051dq3.th.jpg[/IMG]](http://img514.imageshack.us/my.php?image=dsc00051dq3.jpg)

Which (at first, I've seen them before) led me to believe that all would go well anyway.  Lies, all of it, because here where it ultimately leads:
[[IMG]http://img512.imageshack.us/img512/924/dsc00052xh1.th.jpg[/IMG]](http://img512.imageshack.us/my.php?image=dsc00052xh1.jpg)

So, I'm stumbling around and find Wubi.  I figure, "Shoot, it can't hurt" and give it a whirl.  Wouldn't  you know it, everything seems to work out.  It downloads the latest installer iso (even though I had it already, but I figure I'd let it work on it's own), reboot, even manage to go through the entire installation process, right down to importing accounts from other os's.  I start to get a little excited.  I can see the light at the end of the tunnel.  When it finishes install, it tells me it's killing process' and will reboot.  After all is said and done, I get this screen:
[[IMG]http://img211.imageshack.us/img211/426/dsc00047ym1.th.jpg[/IMG]](http://img211.imageshack.us/my.php?image=dsc00047ym1.jpg)
Note the time stamp.  That's 45 minutes after I rebooted.

I'm simply at a loss.  I've read of similar problems with people installing.  I've tried turning off acpi and a couple of string variables in F6, but I always end up with the same result.  Screens full of incomprehensible code and no way of entering anything.

Here are the specs for my computer:
Intel Celeron 2400Mhz
768 DDR SDRAM (512 slot1 256 slot2)
GeForce FX 5200 (with 128mb)
Running Win Doh's Vista Ultimate

If there's already an answer to this question, I'll be more than happy to go to that thread.  I just never found it anywhere I looked.

Thanks in advance.

---

### Post by wpshooter on 2007-08-21
This may or may not have anything to do you your problem but have you tried doing scandisk and defrag on your windows O/S several times prior to trying to install Ubuntu ?

---

### Post by maybeway36 on 2007-08-21
Press Ctrl+Alt+F1 then Ctrl+Alt+F8 during the splash screen.

---

### Post by KharmaPolice on 2007-08-21
Thanks guys.  I'll try your suggestions and and let you know how it goes.

---

### Post by KharmaPolice on 2007-08-24
Hey folks,

Still no go.  I defragged the computer 4 times, I think. (only because the new Vista defragmenter gives you no clue as to what it's actually doing), then tried rebooting to Wub with and without the ctrl+alt keysi.  That didn't work, so reset and tried booting from the cd, same as wubi.  Still no dice.

Unless anyone just has an amazing answer that will fix it, I think I'm just going to wait until I get a different system and try again.  Thank you to those that did try to help!

KP

---

