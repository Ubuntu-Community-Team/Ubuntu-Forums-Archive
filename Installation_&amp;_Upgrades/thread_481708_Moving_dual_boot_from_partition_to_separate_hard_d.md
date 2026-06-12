---
title: "Moving dual boot from partition to separate hard drive."
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by marpstar on 2007-06-22
Hey Everyone.  

Right now, I've got two hard drives.  An 80GB drive that I have both Windows Vista and Ubuntu installed on and a 160GB download/saved files HD.  With all of the audio editing I do, the 160GB hard drive is nearly full, and I just picked up a 500GB to replace that.  Now, the interesting part.  I want to move my vista install to the 160GB drive, leaving ubuntu with the 80GB drive.  I do not, however, want to have to reinstall both Ubuntu and Vista.  

I'm running Fiesty, if that matters, and have access to Norton Ghost if I need imaging software.  It seems that all I would need to do is image Vista to the 160GB drive and then reconfigure my GRUB to point to the correct Vista install point.  Am I missing something or am I safe to try it?

-Cody

---

### Post by logos34 on 2007-06-22
I believe that will work.  Since this is feisty we're talking about, then the UUID for the vista ntfs partition will (AFAIK) follow it when you ghost it to the 160gb.  You will need to change windows vista entry on menu.lst to /dev/hd**b**1 or sd**b**1 or whatever, and the 'root' line to (hd**1**,0)--the latter assuming that it stays second in the bios boot order after you add the new drive to the mix.  You'll also need to add mapping lines because you'll now be trying to boot vista on a non-first hard drive via grub on the 80gb. So you'll need 'map' lines like this:
[B]
map (hd0) (hd1)
map (hd1) (hd0)[/B]

But I really should fess up that I don't know how vista will handle it because I only know about XP...But if you're already successfuilly dual-booting vista and ubuntu on a single drive using grub then you stand a good chance of success,

---

