---
title: "new to linux &amp; need suggestions"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by bradw on 2008-08-09
Greetings all.

Finally ready to make the switch to linux and I have chosen unbuntu. Have a ? about partioning my drive. It is 160gig. I would like a root, home, swap and var partion. laptop is hp dv9074cl with two gig of ram. Thinking of upping the ram to four gig before install. 
?1. I have read swap should be 2x ram so do I need to make swap either 4 or 8 gig?
?2. how large should the var partion be. I dont have a clue on this one.
?3. should more room go to root or home. I and my 2 daughters (5 & 7) will be using the laptop

Any suggestions would be most welcome. What I looking for is how you would carve up the drive and 
more important since Im trying to learn here is why would you carve it up the way you suggest. I will have no dual boot system

One last question, anyone running 8.04 on the hp laptop mentioned above. I was just wondering if there are any problems with the factory supplied hardware. Oh yea before I forget any recommendations on either a hp or epson wireless printer that works out of the box. I have a lexmark z1420 and many sites say this is a paperweight for linux. Darn nice little printer for xp and at 50 dollars at sams club not a bad deal but from what I read a dead horse for linux

thanks for any and all suggestions

brad

---

### Post by AlecJ on 2008-08-09
If it's a fresh install, then let ubuntu do the work, worry not about partitions.
Lexmark and linux do not work, I've tried. get an HP there well surported.

---

### Post by Pumalite on 2008-08-09
I would make 3 partitions:
15 GB for '/'
The rest minus the amount of your RAM for /home
The amount of your RAM for /swap

---

### Post by ad_267 on 2008-08-09
4 or 8 gig of swap is probably overkill. 2GB should be enough. Edit: 4gig if you're going to upgrade to 4gig of ram.
A home partition is a good idea but I'm not sure why you'd want a var partition. I'd say just stick to /, /home and swap.

You'll probably want more room for home. 20GB should be plenty for the root partition.

---

### Post by bradw on 2008-08-09
> **AlecJ said:**
> If it's a fresh install, then let ubuntu do the work, worry not about partitions.
Lexmark and linux do not work, I've tried. get an HP there well surported.

I want /home on seperate partition to preserve it should I need to reintall or want to try other distros. I read today to have a seperate partition for /var incase of a runaway something or other so my logs dont fill /root. 

Any way it is a fresh install. Thank you for your reply

---

### Post by Pumalite on 2008-08-09
If you want hibernation in your laptop; /swap should be equal to your RAM

---

### Post by bradw on 2008-08-09
thank you for the replies

---

### Post by Pumalite on 2008-08-09
This could be of interest to you:
[http://aldeby.org/blog/?page_id=87](http://aldeby.org/blog/?page_id=87)
[http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)

---

### Post by bradw on 2008-08-09
> **Pumalite said:**
> This could be of interest to you:
[http://aldeby.org/blog/?page_id=87](http://aldeby.org/blog/?page_id=87)
[http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)

thank you Im reading them now

---

