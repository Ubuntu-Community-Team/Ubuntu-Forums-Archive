---
title: "Dapper stalls / hangs on blank screen after entering login information"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by jlipps on 2006-07-31
Hello. I've been having some problems getting Dapper to run on my laptop. For context, I recently tried running/installing it the following ways:

[LIST]
[*]Installing from ship-it PC desktop CD
[*]Installing from burned ISO desktop alternative CD
[*]Running from ship-it PC desktop CD
[*]Upgrading from working Breezy installation
[/LIST]

In all of them, Dapper failed to start correctly (even though Breezy worked fine on my machine). Here is the symptom:

The install and boot sequences appear to go normally. Hardware is detected, the ubuntu splash loader works fine, network stuff is detected, and we get to the pretty login screen. I enter my username, hit enter, and then my password, and hit enter. The screen goes blank (to the brown background color), with a mouse pointer still there. After that, nothing happens. In Breezy, the little Mac OS 9 style app loader would appear, add icons for a second, and then launch the desktop. In Dapper, the screen stayed blank (brown), and I could move the mouse around, but nothing ever happened.

Thus, it didn't seem as much like a freeze as a strange hang--as if it's waiting for something that just doesn't happen.

Has this happened to anyone else? Is there any way around it? I really enjoyed Breezy on the laptop and it seems strange that all of a sudden things would not work--I'm figuring it could be a simple configuration problem, but I dunno. I tried some of the random troubleshooting techniques stickied at the top of this forum, but neither the PCMCIA hack nor the X-reset hack did anything.

Laptop specs:
Sager NP-5680
80gb HD
3.0 GHz intel 4
ATI 9600MP
(I'm running a Windows install on hd1, swap on hd2, and Ubuntu on hd3)

---

### Post by RedFive on 2006-08-07
Yes, I have the same problem.

Actually I downloaded and burned the ISO. Installed everything fine. Everything was working just fine and I was able to login and use the gui, etc, etc. But then I let the thing update itself and walked away from the computer.

I came back and it was frozen with the picture of a weird tunnel covering the entire screen. I figured it was just the screen saver that made it freeze. So I rebooted and now whenever I try to login to the default it hangs like you described above.

If I goto the options in the login screen and change it to Gnome, it's fine -- with the exception of the bottom bar not showing the applications that are open.

Help?!!

---

### Post by jlipps on 2006-08-07
Strange! Unfortunately for me, even if I select "gnome" at the login screen, the app loading still never takes place :-( Anyone else out there experiencing these things?

---

### Post by meatface on 2006-08-10
I am experiencing similar problems. I installed Ubuntu 6.06.1 this morning, which I downloaded and burned from the ubuntu site. When I boot up, I get throught the login screen. Then the little panel comes up that says stuff like, loading panel, loading desktop etc. But sometimes it gets partway through and the music stops and it will hang where it is. After rebooting 4 or 5 times it will boot up. I am really liking this distro and want to keep it, but if it does not boot right I cannot justify keeping it.

Meatface

---

### Post by tck on 2006-08-10
Woohoo this thread is for me, its so frustrating.

First tried using DVD 6.06 Dapper, was PAINFULLY slow like when I got onto the desktop it took 10 mins to open a terminal and the espresso didn't even start properly. Tried Desktop and the same issues.

Someone then recommended alternate version as they said this worked for them. So did a text install with Alternate and towards the end of installing packages it just hangs. I had turned off standy and all other power options beforehand in case this was the case.

Im installing this onto a Dell Inspiron 1300 256 ddr2 ram.

So I get the new Dapper 6.06.1 today, and same issue with the Desktpop, PAINFULLY slow and unusable.

Now trying to get the alternate 6.06.1 dapper.

:( :(

---

### Post by jlipps on 2006-08-10
I'll try downloading 6.06.1 and see what happens.

---

### Post by difranr on 2006-08-14
I am having the same problem.  I was performing an upgrade via get-apt and after the re-boot this occurred.  The bad thing for me is that I can not login or ssh into the box so I have no clue as to what is really going on.

---

### Post by difranr on 2006-08-15
This happened to me as well, and what I did was login in via the "Fail Safe Mode" of GNOME and ran **dpkg**. I forget the exact options, but I did a **sudo apt-get update** and it told me what the correct options were. Once I did that and re-started my server it worked like a champ.

---

### Post by jlipps on 2006-08-15
Well, I downloaded 6.06.1 and installed it on my system, but I'm experiencing exactly the same problem. Unlike difranr, I cannot even get into the "Fail Safe Mode" of GNOME--the same symptoms as always! Quite frustrating.

---

### Post by Heatwole on 2006-08-18
I am having the same problem after 8 install/restarts. Though it might have been automatix but am now not so sure. Could really use help with this.

---

### Post by difranr on 2006-08-18
Did you try the "Fail Safe Mode"?

---

### Post by onesojourner on 2006-11-22
I am having the same problem. I don't know how to boot into fail safe mode. if thats an option in grub its not showing up.

---

### Post by lowlight69 on 2007-03-20
i've also seen this, very odd.  for a couple of months my system was running like a champ, now after i login the system sits there for several minutes, then the GUI comes up and all is fine.  its very odd.  i have updated whenever i get the notifcation that new updates are available.  i think there was something in one of the updates that has slowed down the process down.  i'd love to find an answer to this problem.....

dell inspiron 8200
ati video card

any suggestions?????

---

