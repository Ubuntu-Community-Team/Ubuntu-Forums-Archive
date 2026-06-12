---
title: "USB install 10.10 got no GUI"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by attilab on 2010-12-30
this is not funny,
from the same USB 10.10 desktop edition I've installed to 2 laptops days ago it was all OK (beside minor issues), now installed to my older PC, 
- couldn't even run the live ubuntu session before install, didn't had checkboxes or the usual questions, anyway,
- create the partitions, 
- finished the install, restarted, but got no GUI or called desktop environment?
- the black screen, asks me for username and password and stays there
- I am not good with typing (since DOS it was some sort of evolution to windows style), I don't know what to do
- HOW TO get back to desktop interface?

---

### Post by ghostborg on 2010-12-30
Just a guess, but it looks like a graphics issue.
You could try an older version say 10.04 LTS and see if the "Try" option works. If it turns out to be a graphics problem you could try a different card if this is a desktop and you happen to have one lying around.

I believe the command to start the desktop GUI from command line is "startx"

If your desktop did not install as you indicated that there was an unusual install with no check boxes you could try "sudo apt-get install ubuntu-desktop" from the command line.

---

### Post by robbiemacg on 2010-12-30
When installing Ubuntu on older systems, many of which might have limited graphics capabilities, I have had the best success using the alternative install. Consider this option.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by attilab on 2010-12-30
on that PC the last good working installation was the 9.x
the 10.4 stack right after the boot, I didn't had a keybord or mouse working, so I didn't bother with it for a while, just ran XP
so, yesterday installed 10.10 what again didn't gave me results what I would be satisfied with
:(

---

### Post by robbiemacg on 2010-12-31
Did you try using the alternative install image? 
An older desktop system might require some tweaking, but I'd be surprised if the alternative install image didn't get you most of the way there.

---

### Post by robbiemacg on 2011-01-02
Have you come up with a solution that's going to work for you, [attilab]("http://ubuntuforums.org/member.php?u=775561")?
If so, please share it and mark this thread solved.
If not, share some more information regarding the errors you've encountered and the things you've tried so far to overcome your problem.

R.

---

### Post by attilab on 2011-01-03
no luck yet, here is what I've tried just recently:
- downloaded a new image file, checked for integrity, burned CD (since the USB didn't worked)
- installed ubuntu 10.10 same smooth as on my other machines, at the end want to REBOOT in order to finish the installation, eject the CD
- forward to reboot screen and hang with a message:
"The system is going down for rebot NOW"
remember forcing shot down before (USB installation) with power button, but that just gave me hang on @ the start blank black screen (without desktop envirenment) and as I sad before I don't know the linux typing business...:(

---

### Post by attilab on 2011-01-03
> **robbiemacg said:**
> Did you try using the alternative install image? 
An older desktop system might require some tweaking, but I'd be surprised if the alternative install image didn't get you most of the way there.
older yes, maybe 2 y old, but it was running 9.x just fine :(
maybe I can try to put back the previus known working version, 8.x or 9.x ??

---

### Post by attilab on 2011-01-03
so, the grub (dual boot) is working, but boots to a non graphical interface. I enter the username and password. Here my knowledge stops and Im confused how to go further.
I might be able to dig further once Im in desktop envireonment :(

---

### Post by robbiemacg on 2011-01-07
Apologies for the brief absence.
I don't believe I can help you take things any further based upon the information you've shared. Perhaps someone with greater experience or a different perspective will be able to help solve this puzzle.

---

### Post by darnir on 2011-01-16
Try this thread.. Is on a similar problem and the issue was resolved for the concerned user..
[http://ubuntuforums.org/showthread.php?t=1650100](http://ubuntuforums.org/showthread.php?t=1650100)

---

