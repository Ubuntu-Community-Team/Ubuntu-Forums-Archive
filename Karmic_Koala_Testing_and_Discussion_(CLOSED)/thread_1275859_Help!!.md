---
title: "Help!!"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jigglypuff on 2009-09-26
I have Recently installed Karmic Alpha Six and I did an update and restarted my computer. When I select to boot up into Karmic via GRUB It goes to a black screen but I can Tell my monitor is still on

---

### Post by rreese6 on 2009-09-26
First of all, Why would you install Alpha software if you don't know how the fix all the problems like Xorg (the problem you have now).
I would suggest that to stick to an LTS version until you understand Linux better.
On another note, if you just have to have this, you will need to supply more information, like video card make and model.
you will need to list your xorg.conf file.
you will also need to reboot your computer in recovery mode.
you could try the xorg fix in the recovery menu, otherwise you will have to do everything from the root prompt.
I really think you should probably go back to an earlier version such as 9.04LTS..
Alpha Versions are for well seasoned technical types to help work out the bugs....

---

### Post by jigglypuff on 2009-09-26
I know for shore that my video card is a Nvidia GeForce 7200

---

### Post by overdrank on 2009-09-26
Moved to Karmic Koala Testing and Discussion

---

### Post by howefield on 2009-09-26
> **rreese6 said:**
> I really think you should probably go back to an earlier version such as 9.04LTS..

Even though that would be impossible ?

;)

---

### Post by Regenweald on 2009-09-26
> **howefield said:**
> Even though that would be impossible ?

;)

How impossible is popping in the Cd ? ;)

---

### Post by todak on 2009-09-26
Using the search feature of this forum resulted in **[this]("http://ubuntuforums.org/showthread.php?t=1274795")** thread.

---

### Post by todak on 2009-09-26
> **Regenweald said:**
> How impossible is popping in the Cd ? ;)

Uh...there was never a 9.04LTS. The last LTS release was 8.04, hence the impossibility of installing 9.04LTS. ;)

---

### Post by howefield on 2009-09-26
> **Regenweald said:**
> How impossible is popping in the Cd ? ;)

Well, when you can find 9.04LTS, let me know......

---

### Post by novafluxx on 2009-09-26
> **rreese6 said:**
> First of all, Why would you install Alpha software if you don't know how the fix all the problems like Xorg (the problem you have now).
I would suggest that to stick to an LTS version until you understand Linux better.
On another note, if you just have to have this, you will need to supply more information, like video card make and model.
you will need to list your xorg.conf file.
you will also need to reboot your computer in recovery mode.
you could try the xorg fix in the recovery menu, otherwise you will have to do everything from the root prompt.
I really think you should probably go back to an earlier version such as 9.04LTS..
Alpha Versions are for well seasoned technical types to help work out the bugs....

Maybe he wants to use software thats come out in the past 6 months?
Just because someone asks a question about a problem they are having with the re-release version/alpha, doesn't mean they are stupid and shouldn't be running it.

This was posted on the incorrect forum, yes.

I frequently ask questions on the Karmic forum about issues I may be having, so just because one asks a question doesn't mean they shouldn't be running development quality releases.

I don't know how to fix half the things I may run into, and thats why I go to the Karmic forums and inquire why, and how, and to see if its a known bug already reported or not.

---

### Post by jigglypuff on 2009-09-26
So what do I need to do to fix this. Do I need to type something in when I boot up into recovery or press something on the keyboard when I boot regularly

---

### Post by lisati on 2009-09-26
> **howefield said:**
> Well, when you can find 9.04LTS, let me know......
:lolflag:
> **jigglypuff said:**
> So what do I need to do to fix this. Do I need to type something in when I boot up into recovery or press something on the keyboard when I boot regularly

As previously suggested, have a read of this information and let us know how you get on: [http://ubuntuforums.org/showthread.php?t=1274795](http://ubuntuforums.org/showthread.php?t=1274795)

---

### Post by jigglypuff on 2009-09-26
lisati I have already tried that. It didnt work

---

### Post by ronacc on 2009-09-27
try setting your xorg.conf to use the nv driver and see if that gets you into gdm . Then you can work on getting a working Nvidia driver .

---

### Post by jigglypuff on 2009-09-28
how do i get into my xorg.conf file

---

### Post by VMC on 2009-09-28
> **jigglypuff said:**
> how do i get into my xorg.conf file

its located at "/etc/X11/xorg.conf", if it's there. Use editor of choice with sudo.

---

### Post by miegiel on 2009-09-28
Can you get to a terminal (for example by pressing *Alt+F2* or *Ctrl+Alt+F2*)?

If you can, log into the terminal, update.
```
sudo apt-get update
sudo apt-get upgrade
```
Then reboot and see if you still have your problem.
```
sudo shutdown -r 0
```

---

### Post by jigglypuff on 2009-09-30
miegiel I cant get into terminal

---

### Post by archiesteel on 2009-09-30
> **jigglypuff said:**
> miegiel I cant get into terminal

Just a few questions:

- Is the screen completely black or does it have a prompt with blinking cursor?

- Have you ever used command-line Linux/UNIX before?

- What happens when you press the NumLock key? Does the NumLock LED toggle on and off?

- What happens if you try to boot in Recovery mode in GRUB? Do you get to a working prompt?

---

### Post by miegiel on 2009-09-30
In about 24 hours you can download the beta. Try the alternate CD if the beta desktop CD fails you too. You can't use it as a live CD and the installer isn't as pretty, But every time a desktop CD wouldn't properly install, the alternate CD saved me.

---

