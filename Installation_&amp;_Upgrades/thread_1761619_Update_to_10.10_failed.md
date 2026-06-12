---
title: "Update to 10.10 failed"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by johnamcclintock on 2011-05-18
Hi Guys,
 
I am a relatively new Ubuntu user and was trying to upgrade my install from 10.04 to 10.10 which froze mid-upgrade and forced me to power off my machine. Now I cannot get into my Ubuntu at all, it boots as far as the login screen but nothing works. The mouse doesn't work and the login dialogue box does not show properly.
 
Is there anything I can do to roll my OS back to pre-upgrade or am I totally goosed and will have to re-install afresh?
 
Cheers,
 
John

---

### Post by dino99 on 2011-05-18
while you get the grub menu (hold "shift" key down at bios end process to unhide it), select "recovery mode" (second line choice) then "repair packages"

This will continue the installation

---

### Post by johnamcclintock on 2011-05-18
Does this recovery process take a long time as I've already run it a couple of times but powered off when there seemed to be nothing happening and also is it important that I installed my Ubunutu via Wubi rather than in a separate partition?
 
Thank you for the ultra fast intial response!
 
Cheers,
 
John

---

### Post by dino99 on 2011-05-18
how to make a real install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by johnamcclintock on 2011-05-18
Does this mean my current install is likely foobar'd? I have some work on it I would like to try to get off the disk before I do anything if possible. If it's not possible then there's not much I can do I suppose. The reason for the question about whether recovery takes time is because I can leave it running once I get home from work if I have to. Unfortunately I *have *to run Windows on my work laptop as it's the defacto supported platform. As a network admin I have a Linux install to allow me to play with tools like Rancid, Cacti etc before I do anything on the live network with them.
 
The team that is responsible for our laptops are not comfortable about us messing about with them too much so I try not to upset them too much! In short I can't easily re-partition and mess about with my machine too much without upsetting people so a proper install is perhaps not an option readily available to me :(
 
John

---

### Post by Joe of loath on 2011-05-18
I'm guessing this is a dual boot?

If so, you can simply boot into a live CD a live CD and pull off any data, config files etc you need, and stick them on a USB stick. Then just reinstall over the borked install, and you should be good.

---

### Post by johnamcclintock on 2011-05-18
Yes it is dual-boot. Thanks for the hint, can I use a USB stick to boot rather than a CD? I have a 4GB USB stick that I can free up to use for pretty much whatever I want if this is a possible option.

---

### Post by johnamcclintock on 2011-05-18
Apologies for the stupid questions, as I said I am pretty new to Ubuntu and using it in any great anger!

---

### Post by Joe of loath on 2011-05-18
Yup, USB is fine. Preferred, in fact, since it's faster and re-usable. On my Dell laptop, Kubuntu 10.10 boots faster from USB stick than it does from hard drive. Not sure why, but it does :lol:

---

### Post by johnamcclintock on 2011-05-19
Only problem with that being my laptop does not appear to allow me to boot from USB :( Back to the old-fashioned way of CD!!
 
Thank you both for your help. It's much appreciated!!

---

### Post by johnamcclintock on 2011-05-19
I've booted from the CD I created but I can only see the filesystem as NTFS. I cannot see anything within the Ubuntu partition added by Wubi beyond the stuff I would be able to see in Windows. I am beginning to think this might be a lost cause unless I am missing a trick here....

---

### Post by johnamcclintock on 2011-05-19
Accidental double-post, please ignore this post!

---

