---
title: "Compaq Armada 7400 - Old dog still keeping up"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by tracyapotter on 2008-06-11
I am going to pass along some info regarding my 3 years of success with (K)ubuntu and an aging Compaq Armada 7400 PII, 300Mhz, 256M ram machine.

This machine is basically used as an internet box (not video), OpenOffice, Gimp and QCAD.

Long post, end result:  Stripping out features did more for my limited HDD space than it did for my start-up times.  If you like ease of use - just do a full install and maybe Openbox windows manager. You can save 30 secs of system start-up and OOo start-up each with KDE-core and Openbox installed.  This gets the times down to match the vaunted Puppy linux with similar programs installed so I am quite satisfied that this is as good as it gets.  3 min vs 2.5 min system start = features vs ??faster??

I use this laptop to access the web and files on my peer-to-peer network.  It only has a 6G HDD, so since each release seems to get a little bigger I have had to set the partitions to 4.75 /, 1G /home, 256M /swap.

Good news is that hardware detection is getting better, sort of.  With pre-Gutsy releases I had to add snd-es1688 to the /etc/modules file.  Hardy detects the sound card with no problems or additions.

HOWEVER I have found two gotchas.  

Xorg.conf does not set up properly in Gutsy or Hardy.  If you upgrade you are fine.  If you fresh install you will not have graphics.  I always keep my samba, fstab, and now Xorg.conf files on my /home directory somewhere and back them up seperately.  Now when I do a fresh install, I only get a text log-in, then I replace the Xorg-conf and restart - video works fine, sound works fine.

ACPI=force has to be added to the grub menu.list to get the powering off to work.  I do not worry about hibernation, I could never get it to work with Windows when I got it in 1998.

So now I have some speed tests to tell you about.  I am not trying to list all the ways to speed the machine up.  The end conclusion is that it is a 300mhz machine, there is only so much you can do and you are going to have to live with it.

First, all tests done with these initial settings (KDE):

passive busy cursor OFF
no splash screen
localepurge - to clear space
1 desktop only
OOo Calc only - not the full suite

Turn ON times are from start to time KDE cursor disappears
I have to have Open Office - if you can live with lighter programs - good for you.  It will only help.


Fiesty full install -  start in 3 min 10 sec
                      OOo Cacl 2.2 in 44 sec

removed all unnecessary files down to KDE-core (see PsychoCats instructions for doing this)
added firefox, OOo Calc, OOo-style-crystal
did an apt-get autoremove

Fiest KDE-core         start in 2 min 20 sec
                      OOo Calc 2.2 in 40 sec

Upgrade to Gutsy       start in 2 min 28 sec
                      OOo Calc 2.3 in 41 sec

Upgrade to Hardy       start in 2 min 42 sec
                      OOo Calc 2.4 in 39 sec

added openbox, openboxthemes, obconf, menu
did and apt-get autoremove

Hardy w/Openbox        start in 2 min 40 sec
                      OOo Calc 2.4 in 31 sec

added OOoWriter, OOo draw, QCAD (basics for me)

Hardy w/Openbox      OOoWriter 2.4 in 40 sec



Hardy FULL fresh install from mini.iso (some kde4 components installed)

                passive busy cursor OFF
                no splash screen
                localepurge - to clear space
                1 desktop only
                OOo Calc only - not the full suite

                      start in 3 min 0 sec
                      OOo Calc 2.4 in 1 min 0 sec

removed kde4 and add openbox

                      OOo Calc 2.4 in 43 sec

Fresh Hardy CLI install

add kde-core, xorg, kdm, localepurge, adept OOo Calc, Write, Draw, QCAD
 (had to copy old Xorg.conf to /etc/X11/)
    KDE setup - fewer effects
                Plastic
                passive busy cursor OFF
                no splash screen
                1 desktop only
                

                       start in 2 min 25 sec
                      OOo Calc 2.4 in 43 sec

added openbox, openboxthemes, obconf, menu

Hardy w/Openbox        start in 2 min 25 sec
                      OOo Calc 2.4 in 34 sec



So as you can see going to KDE-core is about all that helped start-up and OOo is just slow.

I play around with Puppy linux so I thought I would do a comparison.

added OOo.sfs, network settings, Firefox, and QCAD  with CD+save file boot style

Puppy 3.01 or 4.00 (did not write down and can't remember which)

Puppy                start in 2 min 20 sec
                    OOo 2.2 calc in 32 sec

This is faster, but not that much, and puppy is a lot more work.  If you want to play with building your own distro, then by all means go for it, but if ease of use can stand a few more seconds, stick with (k)ubuntu.

---

