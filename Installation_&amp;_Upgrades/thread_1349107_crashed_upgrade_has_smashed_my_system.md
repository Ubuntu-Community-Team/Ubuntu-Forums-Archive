---
title: "crashed upgrade has smashed my system"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by holiday on 2009-12-07
After googling, I've done this from a 9.10 XUbuntu live CD.

# mkdir /media/sda
# mount /dev/sda5 /media/sda

Verify that the contents of /media/sda are the root of the old system. See /dev and /proc and /home

# chroot /media/sda

Now

# apt-get dist-upgrade

Chug chug - fail

Following the prompt, I go

#apt-get -f install

Chug chug - fail


# apt-get --fix-broken

Blip - fail

The system keeps asking me "Is /proc mounted?" And well yes it seems to me that is because I see the directory but I see also that it is empty. Is this the problem? Maybe I should link /media/sda/proc to /proc? 

Can anyone explain this?

---

### Post by holiday on 2009-12-08
I think what's happened is that /proc is not populated because it is not the /proc directory from startup. So how do I point the chroot /proc at the physical /proc populated, probably, at startup.

Oh wait - this looks useful


[http://ubuntuforums.org/archive/index.php/t-1156240.html](http://ubuntuforums.org/archive/index.php/t-1156240.html)

I'll check it out tonight and get back. Looks like the instructions for chroot I read were over-brief.

---

