---
title: "kubuntu hell"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by yonkman on 2008-05-08
Well, upgrade went fine, for the last month I have been growing accustomed to all the "issues" with the new version.  I have been using ubuntu for about 3 years as a very important workstation.

I have used the advice in the forums very sucessfully over  that time.

Now, after an aptitude update last night I can't get my computer to boot.


If I can get to the command prompt that would be awesome, but I can't.

Also, neither the lastest Kubuntu CD nor Knoppix will recognize my sata harddrives.

Motherboard is abit ib9
cpu dual core 1.3
3 gb ram


When selecting from grub the recovery boot, I get the famous ata failed or revalidation failed

It just fails at ATA...... and dumps me into busybox

ata6: EH complete is the last line then the box hangs.

I am ONLY looking to get back to command line for now, I hope I can take it from there.

Peace

---

### Post by lemming465 on 2008-05-10
Have you tried reseating the drive cables and or checking the BIOS settings?  This smells more like a hardware issue than a software one, in spite of the apparent coincidence of the update.  I assume you've tried powering the box down and then up already to no effect; if not definitely try that first.

---

### Post by yonkman on 2008-05-11
SOLVED()

for some reason the rescuse mode FINALLY let me in 8hrs later and I was able to get to command line and reconfigure x which seemed to be the issue.

I am still unable to sucessfully shut down from KDE menu, but I have my workstation back so i consider it a success.

One thought, the lack of hardware support is the SINGLE biggest isssue facing all *NIX distos/versions in my opinion.

if it isn't dumbed down more, then linux users will just be IT employees or the adventurous.

---

### Post by Pumalite on 2008-05-11
The adventurous are more numerous than you think.

---

### Post by Zorael on 2008-05-11
Linux needs corporate support; they need to see that it's a viable platform and there's a large enough userbase that developing drivers - and applications - is worth their effort. As it is now, a hardware manufacturer that doesn't supply Windows drivers is *dead*. Depending on what kind of hardware it is, he's likely in for some serious flak if he doesn't supply Mac ones, too. But Linux? "Nah, they're just nerds."

---

### Post by Pumalite on 2008-05-11
Whoever wants to use Linux; will use it no matter what. I don't think we'll ever be a majority.

---

### Post by yonkman on 2008-05-12
There is a potentially HUGE market available for linux today, especially with the costs of MAC and MS.

However, it is very difficult to break that barrier with all the current problems of open source today.

Here is one small suggestion.  SmBuntu (Small Business Ubuntu) a branch that has most applications a small business might want and plenty of help documention for when your business grows.

Get that wave going and the tons of surfers will paddle for it!!!

---

