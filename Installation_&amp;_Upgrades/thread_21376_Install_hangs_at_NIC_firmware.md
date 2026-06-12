---
title: "Install hangs at NIC firmware"
date: 2005-03-21
forum: Installation &amp; Upgrades
---

### Post by morpheen on 2005-03-21
I am very new to linux, a friend of mine suggested Ubuntu.  I am running an old Dell GX110 which is a PIII 800mHz, 512MB RAM, 40 GB Hard drive.  The Live CD works just fine, didn't have any errors.

During the install, it hangs at the "Loading components of the Ubuntu installer" section when it gets to "Retrieving nic-firmware-2.6.8.1-3-386-di".  The progress bar stops at 35% and the screen just flashes endlessly.

Has anyone come accross this before?  Is it s bad CD or maybe an incompatibility?

Thanks!

---

### Post by lao_V on 2005-04-08
Are you able to remove your NIC and try installing again? Or even, try with another CD? It would seem strange the installation hangs at "Loading stage".

---

### Post by satlurker on 2005-04-12
I have exactly the same problem with my gx110 ... goes through the entire install ... sets up the user passwords etc ... goes through the entire application upgrade process (apt-get upgrade I assume) and at the last moment hangs with a blank screen.

Very frustrating ... I don't know how many times I tried to get this to work ](*,)

I've given up and put SimplyMepis back on it and it works just fine ...

Sat

---

### Post by R.U.Sirius on 2005-06-05
i have the same prob with a dell latitude xpi think it's a dell specific prob, cause everyone who got this behaviour has a dell...

is there a workaround? i'd like to install kubuntu on that laptop


bets regards,
R.U.Sirius

---

### Post by roger6106 on 2005-06-17
I have this exact same problem with 5.04. I posted a [topic](http://ubuntuforums.org/showthread.php?p=216591#post216591)  about it there, maybe that will get some replies. 

[QUOTE=satlurker]I have exactly the same problem with my gx110 ... goes through the entire install ... sets up the user passwords etc ... goes through the entire application upgrade process (apt-get upgrade I assume) and at the last moment hangs with a blank screen.[/QUOTE]

Satlurker, that sounds like a different problem. This is during the loading before the install.

---

### Post by bunt on 2005-07-06
I have a similar problem with an old 200MHz Pentium from Quantex.  Not just a Dell issue.  The Quantex has no NIC or modem for that matter.  I tried several different CDs, all of which were pressed and shipped to me (not burned), and the install hangs at the SAME point on all of them.  Basically, after it can't seem to install the NIC driver, it just settles on a black screen with a text cursor on the bottom left.

---

### Post by carey on 2005-09-07
A friend is having the exact same problem.

To quote him:

"I boot the ubuntu cd using 'server'

It enters Low memory mode, I choose the language and keyboard. It 'Detects hardware to find CD-ROM drive'. It 'Scans the CD-ROM', 'Loads additional components', tries to load nic-firmware-2.6.10-5 or something, tries to do it about 10 times, then goes to a blank screen. I can type things in but nothing comes up."

It completely freezes with a blank screen.

Any ideas?

Also -- another thread about this problem: [http://ubuntuforums.org/showthread.php?t=42314](http://ubuntuforums.org/showthread.php?t=42314).

---

