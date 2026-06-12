---
title: "Grub Rescue&gt; problem dual booting"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by TeamRiddle on 2011-06-23
OK, so I've been searching the past few days on the forums, trying to figure this out on my own...

I'm quite a n00b to Linux. I have had it running on my old dell latitude for a year now with no problems, so i decided to dual boot my girlfriend's family's 2 year old desktop.

I installed the most recent live CD from the Ubuntu site alongside windows vista with what seemed like no problems. I restarted when I was prompted to do so, but then it loaded to GRUB RESCUE. I tried reinstalling to no avail. then i tried this:

[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

now i don't even have grub rescue. When it gets to the point where it used to say grub rescue, it does nothing. my monitor just goes into a mode waiting for a signal from the computer. I am currently running from the live CD (which is impressively fast and stable). 

Please help me with this. I feel like a complete jerk. I tried to install Ubuntu because i was sick of waiting 20 minutes for windows to load all of its garbage, just so i could use facebook.

Thank you for all your help

---

### Post by YesWeCan on 2011-06-23
Hi there. Don't worry, it is very easy to get into a mess when trying to do a dual-install. That tutorial looks ok so if it didn't work we'll need more details.
Would you download and run this: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
and post the RESULTS.txt file here inside code tags (use # button).

---

### Post by TeamRiddle on 2011-06-23
ok i think this is it

---

### Post by TeamRiddle on 2011-06-23
hmm that didnt work. did this?
```
[ATTACH]195830[/ATTACH]
```

---

### Post by YesWeCan on 2011-06-23
Well, it looks like Grub has been installed to both the MBR of sda and partition sda2. Is it possible when you re-installed Grub that you accidentally installed it to sda2?

Try this again from the CD (the Ubuntu version on CD should be the same as the version on HD).

[COLOR="Blue"]sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]

The distinction between sda2 and sda is vital. Report any errors. If none, reboot off the HD and if Ubuntu boots, run [COLOR="Blue"]sudo update-grub[/COLOR].

---

### Post by TeamRiddle on 2011-06-23
same problem still. this did not fix. any other ideas?

i really appreciate your help.

---

### Post by YesWeCan on 2011-06-23
Check the bios is set to boot sda and not your 2GB drive.
Hold the shift key while it boots - this should cause Grub to display its boot menu.

---

### Post by TeamRiddle on 2011-06-23
ok, sweet. so shift didn't do anything... BUT, now my display says something about the frequency being too high where it used to just say it was not getting a signal. i got frustrated so i sat and stared at my monitor display. Then ubuntu just magically started loading. 
My educated guess is that it was trying to give me an option to boot either ubuntu or windows then it timed out and booted ubuntu. if thats the case, how do i change the incoming frequency to my display for that screen?

---

### Post by YesWeCan on 2011-06-23
It is curious that no such problem occurs when you boot the live version. The live has a different boot system, tho. I don't know.

---

