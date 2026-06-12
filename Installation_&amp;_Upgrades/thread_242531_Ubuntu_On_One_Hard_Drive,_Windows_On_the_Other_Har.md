---
title: "Ubuntu On One Hard Drive, Windows On the Other Hard Drive"
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by ThatKnicker on 2006-08-23
I am not sure if this is considered dual booting? I thought dual booting was two OS' on one hard drive. I want to do what I said in my thread title. I'm not sure how to do this, and this is the only thing holding me back from trying Ubuntu. So please if someone could give me directions or a link, I would greatly appreciate it. Thank you in advance!

---

### Post by scxtt on 2006-08-23
it's dual booting, booting any OS when more than 1 is present in your system is 'dual booting' -- but where do you stand as of now, what's your current HDD config, which OS(es) are installed already?

---

### Post by confused57 on 2006-08-23
See if this link is an option for you:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by ThatKnicker on 2006-08-23
Thank you both for replying so quickly! Wow thats awesome!

I think this is what I was looking for...
> The guide can be used to install on 2 different hard drives, but Windows would need to be the master drive and Ubuntu the slave drive. You would select "IDE drive hdb" to install Ubuntu onto and install Grub to Windows(hda) when prompted. Windows doesn't like it when it's not the first OS in a dualboot system, therefore, it has to be on the master drive when using this method. The menu.lst(Grub) Windows entry, provided in the links in my first post method, has a mapping command, which fools Windows into thinking it is the first OS.


^^Thats what I want to do, have Windows as my Master OS and Ubuntu to be my Slave OS. I just want to get my feet wet in Ubuntu. But my next question is, when I turn on the comp it will automatically run windows. Now how do I get my other Hard drive to boot Ubuntu when I want it to? I prolly use Windows the majority of the time, I just want to Boot to Ubuntu when I want to. This is possible, right?

---

### Post by scxtt on 2006-08-23
grub will take of all that ... i suppose your only decision is whether you want your master boot record to be left untouched ...

---

### Post by VirtuAlex on 2006-08-23
That statements about master/slave are not exactly true. Windows actually will be a slave OS if you're booting through grub installed on the master drive. If you want them to be separate but equal you install grub into ubuntu drive and go to bios to choose which drive you want to boot from. If you install grub into windows drive and then decide to remove ubuntu drive from the computer your windows would not boot at all.

---

### Post by ThatKnicker on 2006-08-25
Ah, Yes... thats what I needed. Can anyone else confirm this is correct?? Thanks by the way for helping. Some one should sticky a thread on "How to Dual Boot For Noobs". I would go there, happily, as a noob. :D

---

### Post by adds2one on 2006-08-25
Follow this link for as simple instructions as you will find anywhere on dual booting XP and Ubuntu.

This worked for me.

[http://www.hezardastan.org/breezy_xp_dualboot/en/](http://www.hezardastan.org/breezy_xp_dualboot/en/)

---

