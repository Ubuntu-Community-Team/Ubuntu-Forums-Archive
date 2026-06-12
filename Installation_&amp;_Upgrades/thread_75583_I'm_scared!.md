---
title: "I'm scared!"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by kudu on 2005-10-13
Do I dare risk it ?? I've tried Breezy 3 times now with the release candidate and killed my install each time necesitating a fresh re-installation of Hoary. I'm very happy with my current hoary setup and would prefer to dist-upgrade rather than do a fresh install from the CD. Will it work ? Or should I wait till Breezy gets ironed out a bit more ? I've tried both methods before and neither one produced a stable functioning breezy.

Regards,
kudu

---

### Post by Wandering Wombat on 2005-10-13
Its a dilemma aint it lol. I have been on breezy for quite a while now at least a month or 2 from memory. My Hoary install shit itself so I thought why not go to Breezy. So it was more logic than anything else. From one of the threads in these forums someone suggested to do a clean install of Hoary standard. Then use the Breezy CD I downloaded to upgrade. Apart from a couple of hiccups (very minor) my Breezy Install has been excellent. I honestly do feel for the people who have had problems with Breezy, it is bloody marvellous, I loved Hoary but Breezy is holding its own, in my situation anyway. :KS :KS :KS :KS :KS  (my Breezy rating lol). Backup everything you need and take the plunge!!!

---

### Post by codejunkie on 2005-10-13
[quote=kudu]Do I dare risk it ?? I've tried Breezy 3 times now with the release candidate and killed my install each time necesitating a fresh re-installation of Hoary. I'm very happy with my current hoary setup and would prefer to dist-upgrade rather than do a fresh install from the CD. Will it work ? Or should I wait till Breezy gets ironed out a bit more ? I've tried both methods before and neither one produced a stable functioning breezy.

Regards,
kudu[/quote]
i have found that the new release is pretty stable i've been using it for quite a while now without any major problems. but you asked is it safe to upgrade well that still depends on your setup most likely everything will be ok, but it's possible that something might still break because of some setting that was changed so backup before you upgrade.

---

### Post by kvidell on 2005-10-13
Well.. I tell ya what.
I tried to Dist-Upgrade a couple nights ago and completely fried my server...
This was after having done a fresh install on my laptop, which is running beautifully...

I personally am against dist-upgrade... It changes too many things at once for my taste and I'm quite frankly anyone has success with it (which is more points to the developers, but even more if it worked for me :-P).

What I'd recomend doing, is if you have multiple partitions, I'd save your home directory and some of the things you may have tweaked that live in /etc....

Other than that it's pretty much all going to get replaced anyway... Backup that stuff then go ahead and _try_ the dist-upgrade, and if that doesn't work I'd just bite the bullet and fresh install, then restore you backups of your home directories and configs (from /etc)...

I don't have a very hard time backing up my home directory... I only save my .*rc files anyway (pine, mutt, spam assassin, fetchmail, procmail, bitchx, screen, vim and tcsh). It's a several k backup procedure... From /etc I usually grab my host files, my resolv.conf, everything in /etc/network/ and anything else I know I changed by hand (smb.conf)..

It's up to you really, Hoary is nice but I'm completely blown away by Breezy. I've been using it for a little under a week now on three systems, no complaints what-so-ever. (Well... except that, and this is only for my server, it doesn't come with the SSHD or terminal-on-serial-port support enabled by default, I had to go in and jiggle some init scripts and agetty to get it working, but I can now drop a null modem cable on my server and kermit it from my laptop if the SSHD goes down or something.)

I'm also kind of a freak, I have _no_ problem with just flat out formatting, ditching all my configs, and reinstalling a server or desktop. It's kind of fun.
This poor laptop's had many fresh installs in the last little while... (Hoary, Breezy, back to Hoary a few times, Solaris 10, WinXP and now Breezy again)

Good times,
- Kev

---

### Post by tirian on 2005-10-13
I just tried to upgrade. It messed up my Kernal, X, drivers the whole works.

I backed up right before the upgrade but that backup was corrupted. Fortunately I was able to revert back to a previous backup but I lost about three weeks worth of data. It is going to take me at least a month to recreate all the data that I lost.

I really love Ubuntu, but this upgrade has me longing for my Mandrake.

I know that if I were a Linux god like the rest of you I'd have no problem. But why does it have to be so painful for mere mortals like myself?

---

### Post by angrykeyboarder on 2005-10-13
[quote=codejunkie]i have found that the new release is pretty stable i've been using it for quite a while now without any major problems. but you asked is it safe to upgrade well that still depends on your setup most likely everything will be ok, but it's possible that something might still break because of some setting that was changed so backup before you upgrade.[/quote]

I have no idea what happned but mine completely freaked out earlier today.  My symlinks disapeared and programs would crash.  I decided to completely reboot.

It wouldn't.  It froze when GRUB came up.  

I figured I'd have to start from scratch.    Then I left for a while and came back. I grabbed the DVD and was ready to start from scratch.  

I booted the PC and forgot to put in the DVD first and lo and behold, it booted normally and everything is working normally now.

I'm completely mystified as to what happned and how.

---

### Post by matthew on 2005-10-13
[quote=kudu]I'm very happy with my current hoary setup[/quote] Other than the natural desire to have the newest and shiniest it sounds like all is well with your computer. My advice, enjoy using it as is and don't worry about upgrading until you need to (i.e. when Hoary isn't supported any longer or there's some new feature you want that you can't get in Hoary). As an alternate, wait until you have a free weekend with enough time to work through all the pitfalls without feeling stressed for time...plan it in a few weeks when others have posted their solutions here to the problems you anticipate and when you have enough free time blocked off to make the work fun rather than a pain in the hindquarters.

For what it's worth, this is what I am doing with my laptop. I tested Breezy and got it working acceptably, but I didn't have time to really get my setup as I want it to be so I just restored from my Hoary backup and will use my own advice and wait a little bit. I do have a couple of desktops that upgraded in a couple hours or less with NO problems whatsoever, so in those sorts of cases I would recommend to do it now. For people like you and me with my laptop...waiting a little while won't hurt us.

---

### Post by professor_chaos on 2005-10-13
just backup important files and give it a try. If the dist upgrade doesn't work you can always go for the fresh install. 

I have done a dist upgrade on three seperate machines over the last 2 months, and while I had some small problems, all three sucessfully upgraded. I'm very glad I updated....Nice new features.

But then again, if you want to stick with what works...Or should I say what is currently working.

---

### Post by tirian on 2005-10-14
[QUOTE=tirian]I just tried to upgrade. It messed up my Kernal, X, drivers the whole works.

I backed up right before the upgrade but that backup was corrupted. Fortunately I was able to revert back to a previous backup but I lost about three weeks worth of data. It is going to take me at least a month to recreate all the data that I lost.

I really love Ubuntu, but this upgrade has me longing for my Mandrake.

I know that if I were a Linux god like the rest of you I'd have no problem. But why does it have to be so painful for mere mortals like myself?[/QUOTE]

I appologize for sounding so much like a whiner. I really do appreciate all the work that the Ubuntu team puts into this distro. I was just really fustrated. Fortuately I was able to recover some data from the bad backup and minimize my data loss.

Thanks again!

~Tirian

---

### Post by daschl on 2005-10-14
If you are happy with you current setup and if you have no problems: stay with hoary. there is no reason to upgrade i think :)

never touch a running system!

---

