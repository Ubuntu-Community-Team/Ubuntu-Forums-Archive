---
title: "Live CD - Gnome keeps restarting..."
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by chris.zeman on 2006-12-19
I installed Ubuntu 6.10 on my laptop a few days ago, and it has been working great! I've never been this happy with a Linux distribution.

I decided to install it on a desktop machine I have dedicated to my ham radio activities and ditch Winblows. Well, Gnome starts, the desktop is shown (minus the files), and the toolbars show. Gnome immediately goes to the login screen and says that user ubuntu will be logged in. It logs in and the cycle restarts.

Ocassionally it will stop and sit there on the desktop with File Browser open, and something else but I'm not sure what. I move the mouse and the cycle starts all over again! Any ideas? I've tried acpi=off for the heck of it at startup, but that hasn't helped.

Thanks,
Chris

---

### Post by Cryophallion on 2007-01-15
I had the same problem. I was installing on an old Gateway with a P3 450, 256 megs of ram, and a voodoo 3 3000 video card. 

I luckily had the alternate install disk, and that installed fine. However, the problem of recycling to the login kept happening.

I would log in, it would load nautilus, etc, the bars would appear at the top and bottom of the screen, and then is would go back to the login screen. 

After 3 or 4 times of this, it would say something about a tab already being loaded, so it would restart (I was in a place with no internet connection at the time, and I was just testing to see if I could get it to run, so I didn't end up writing the exact message down).

I would still like to use ubuntu on that computer, and maybe make it a citadel server for work, but I couldn't resolve the problem and left the comp where it was (at my father-in -laws house 4 hrs away).

Any help would be nice.

---

### Post by ricklaw on 2007-01-15
I have the same problem with instralled Ubuntu 6.10.  I triople boot with windows and Suse.  Ubuntu has run flawlessly for 1 1/2 yrs without problems so i have not spent much time under the hood.  Everythibng was fine.  In my last session I browsed the web with Firefox and watched video on Democracy player.  I did not up date any of the system or add any programs.  Obviously, the system booted as I got to the Ubuntu Gnome login screen.  I know my user name and password are correct.  I have two users, default and unprivileged guest.  Both return to the login screen when i try to log them in.  The obviouis choices would be a broken graphical login file or a corrupted password file.  Could it be that Democracy player downloaded too many new files and the system has run out of memory.  I don't know if that would cause this problem.  I could use Suse to boot and remove Democracy files.  Any help will be appreciated.

Ricklaw

---

### Post by ricklaw on 2007-01-28
Never mind.  No one offered any help but I solved my problem.  Since I triple boot, I was able to boot into SuSE and mount my Ubuntu partitions.  Sure enough, my Ubuntu /home partition was 100% filled.  I freed up space and now I boot fine again.  Thought I would post this in case it helps anyone else.

ricklaw

---

