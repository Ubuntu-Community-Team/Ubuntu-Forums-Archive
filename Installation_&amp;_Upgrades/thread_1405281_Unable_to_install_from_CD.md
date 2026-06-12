---
title: "Unable to install from CD"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by relkbycet on 2010-02-12
Alright, I've been having Windows licensing issues and decided that it would be a good time to upgrade to Ubuntu. I have used Ubuntu before but am not completely adept. Anyway, I downloaded the most recent(9.10 desktop) iso and burned it to a rewritable cd with two different iso software(Active @ iso Burner and ISO Burner)programs, but after both attempts, I began installation only to have it stop about a minute later with "I/0 Error: Error reading boot CD." I read that more expensive CD's had a higher failure rate than disposable CD's, but I am limited on options right now and gave it a try. Before burning, I checked the MD5Sum of the iso and it matched what I found on the Ubuntu hashes site linked in the installation guide. So I tried checking the disc for defects, with it stopping shortly afterward to display the same message. I tried a few boot command combinations, but figured that if it couldn't read the disc to check for errors(which probably meant that it had errors), the problem didn't lie there. I then tried installing from a USB flash drive, explicitly following the instructions on the official site and using Pendriver's USB software to write to my 2GB drive, then booting from USB. This seemed to work better, It brought up an install menu, which I navigated through to start installation. It had a list of processes for a while(the white lettering on the black screen that takes place when installing most things), and I left it alone. When I looked back at it about 20 minutes later, the screen only had a loading icon with an Ubuntu symbol in the center. I assumed that this was the next step in the installation, and left it on longer. When I next checked it, the icon was the same but in a different spot in the bottom left of the screen. Confused, I let it load longer. I checked it again, and the icon was at the bottom of the the screen in such a position that only half of the icon was visible, as the other half was offscreen. I can not get this to work and have no idea what I have done wrong, any help would be appreciated, and I can answer any questions about the system. Thank you.

---

### Post by khelben1979 on 2010-02-12
Well.. you can start by providing us with some hardware information and then we know a little better how the Ubuntu kernel have decided to deal with it.

I think that burning down Ubuntu Karmic on an DVD-R would be the best choice and letting the installer download more packages as they are needed from a ftp mirror somewhere.

---

### Post by dabl on 2010-02-12
Burn the CD at the slowest speed your burning software supports -- 4X if you have it, no faster than 8X.

---

### Post by relkbycet on 2010-02-12
Well, there are two different computers that I have tried installing it on. I'm not sure exactly what I need to tell you, but it has a Pentium 4 2.6G processor, and just over a GB of RAM. I honestly don't know enough about this process to judge what information is relevant. It is currently running XPSP3 on two partitions, maybe that is affecting it. And as for the burning speed, I set it for highest possible speed, but in the final report, it claimed to have used 4X. It will let me select 4x, so I will try that again and see if my results differ until I can get a DVD. I just need an OS right now, would a CD be more compatible with a less recent version of Ubuntu? And hopefully that significantly answered questions about the computer. I can find out any other specific information.

---

### Post by relkbycet on 2010-02-12
That was the main one, the other I am less worried about.

---

### Post by relkbycet on 2010-02-12
Also, if this makes a difference, the second burning software that I have used has said "Warning, DMA speed test has been skipped" every time that I have tried to burn something, but it notes the burn as a success. I stuck with this software after the first time because it was the first mentioned on the Ubuntu installation guide.

---

### Post by relkbycet on 2010-02-12
If I use Wubi on the one computer that still functions(to an extent), can I delete partitions and make Ubuntu the active OS after installation?

---

### Post by khelben1979 on 2010-02-13
In my opinion, skip Wubi and spend more time on concentrating on how Ubuntu works by reading some [more documentation]("https://help.ubuntu.com/community/Installation").

Also, try to solve your present problems with the help of patience, since it will otherwise just mess things up and you risk hating Ubuntu for all it's problems. Slow down the pace:
> I can not get this to work and have no idea what I have done wrong

---

