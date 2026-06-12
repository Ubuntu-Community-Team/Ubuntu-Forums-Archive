---
title: "Eeek, Apt tried to remove lots of packages!"
date: 2008-12-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by durand on 2008-12-13
I saw the update icon flash "6 updates" so I just clicked through to install and suddenly I noticed that it was removing a lot of packages mostly from the base system. So I did a```
 sudo killall -9 dpkg
``` and then went back to the update dialog and it told me to
```
 sudo dpkg --configure -a
```
which I did and it cleaned up what it was doing.. However, / was set to have UID 0 and 999 permissions along with other folders and weird changes. I have absolutely no idea what could cause this problem!
I tried reinstalling the programs that were removed prior to killall-ing but that doesn't seem to help :(

I'm currently posting from a live cd since I can't use my installed desktop. Root is the only user that can login since I can't execute any programs with any other user including the shell...


Sooo, any ideas? I'd like to leave reinstalling ubuntu as my "if all else fails" option..
Thanks!

---

### Post by autocrosser on 2008-12-13
(standard disclamer posted here)---Really at this stage, unless you want to fix a broken system--I would reinstall Jaunty...Is this your only install (please don't say yes)???

Alpha2 is due this coming week & I would wait to do a clean install. My system is tri-boot--currently 2 installs of Jaunty (1 a week back from the other--sync'd once a week--at a "stable time") & 1 Intrepid install for fall-back in case of problems like the one you just had......I know it's more maintain work, but it will "save your a**" when a alpha blows-up on you.

I have redone permissions in broken systems before & in the long-run just reinstalled anyway--my 2 pence worth......

---

### Post by durand on 2008-12-13
Hmm...I suppose I should reinstall. I just like playing with unstable software so it is my only installation :P Ah well, I need it to be stable for my coursework so I guess I'll install Intrepid over this and then upgrade later.

Thanks for your input.

---

### Post by autocrosser on 2008-12-13
No problem!!!  Really, I would at least dual-boot for fall-back--makes life MUCH easier---are you setting a seperate /home for your installs?

---

### Post by durand on 2008-12-13
Yeah but won't there be problems if I don't wipe the home partition on reinstall?
Oh and I can't dual boot. My dad insists on using Windows so I can only really have one linux distro installed.

---

### Post by autocrosser on 2008-12-13
No--do not format your /home & that way you save your personal stuff....during install note where the partition for your /home is (this "assumes" you have a separate partition for /home) & do not format it---just tell the installer where it is.  If you didn't create a separate partition for /home---make sure you do it next install---I keep a separate /home for all 3 of my installs & sync them as needed.

**Reason**
I have had several harddrives die on me over the years & I REALLY hate loosing my personal stuff--by spreading the info over 3 drives I feel much safer--I also backup to DVD every couple of months just to be on the safe side.

Why don't you get a cheap drive & pop it in to the unit? Really makes life easier also!!!!

---

### Post by Gina on 2008-12-13
The only limit to how many systems you can have installed is hard drive space.  I often have 3, 4  or 5 systems to choose from at boot time.  This AMD64 has 3 - Jaunty (that I'm in now), Intrepid and Hardy normal 64bit Ubuntu.  The P4 has a lot more and is my main safe machine.  This has Intrepid, Hardy, Hardy Ubuntu-Studio and Interpid Ubuntu-Studio and Windoze XP - all available at start-up.  The P3 with just a 10GB hard drive has two versions of Ubuntu.  My laptop has Jaunty, Intrepid and XP.

As for /home, I like to have this on a separate partition.  I also have a separate /home partition from the main one for testing so that the test system has far less chance of deleting my personal files.

To return to the point in hand - if you have hard drive space you can have Windows and two Ubuntu systems installed plus home and swap partitions.

---

### Post by danf_1979 on 2008-12-13
durand: you can have two, three or more systems. Dualbooting is not a limitation, you can tripleboot too :P. And that is no limitation either :D.

---

### Post by durand on 2008-12-13
Yes I know about hard drive space but my point was that I don't use more than one linux distro simply because I would have to install all my programs on all of them to actually make them usable to me and I don't have enough space for 3 x 50GB linuxes. Plus I am too lazy to maintain more than one.

---

### Post by durand on 2008-12-13
Oh and I reinstalled. Clean system but now I have a lot of work to do getting it back to perfection.

---

