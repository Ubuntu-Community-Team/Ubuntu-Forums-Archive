---
title: "cannot boot into ubuntu with CD or Wubi"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by Nycen on 2010-09-01
Hello folks,
   I am new to all this never having sought help in a  forum so forgive me if i goof up ..I have recently discovered ubuntu and  like it's elegance and simplicity and want to learn more about it  "hands on".  To this end I have tried to put it on one of my PC's  running the Vista SP2 OS...When i try to install it with the CD the  drive spins up then starts "hunting"..next the PC shuts down..black  screen monitor.no KB or Mouse..the monitor flashes a box saying "power  saving mode" then all is dead except for the power button being lit..I  have to manually turn the PC off to recover...Next i did a D/L of wubi  and rebooted as advised.Selected ubuntu on the BIOS and had the same  final result as B4 with the CD. I have D/L and burned 2 CD's, one with  my XP machine and the other with the Vista machine..Both CD's work as  advertised on my XP machine (i did the "live" install) but not the  Vista. The Vista machine is an HP with: AMD Athlon 64x2 3800+ CPU..3 GB  of RAM..250 GB HDD.  I do not like Vista ( i inherited the machine) it's  a pain in the posterior. IMHO ubuntu and it's ilk are the way to go and  i intend to do just that one way or the other.  I am a little long in  the tooth and not to swift with technical jargon or procedures so if you  can help me it would be more then a little appreciated..Hope ya do, :D

---

### Post by Rubi1200 on 2010-09-01
Hi and welcome :)

What graphics card do you have on the Vista machine?

Take a look here for possible workarounds for booting the LiveCD:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

If you have any questions, feel free to ask.

---

### Post by bcbc on 2010-09-01
> **Nycen said:**
> Hello folks,
   I am new to all this never having sought help in a  forum so forgive me if i goof up ..I have recently discovered ubuntu and  like it's elegance and simplicity and want to learn more about it  "hands on".  To this end I have tried to put it on one of my PC's  running the Vista SP2 OS...When i try to install it with the CD the  drive spins up then starts "hunting"..next the PC shuts down..black  screen monitor.no KB or Mouse..the monitor flashes a box saying "power  saving mode" then all is dead except for the power button being lit..I  have to manually turn the PC off to recover...Next i did a D/L of wubi  and rebooted as advised.Selected ubuntu on the BIOS and had the same  final result as B4 with the CD. I have D/L and burned 2 CD's, one with  my XP machine and the other with the Vista machine..Both CD's work as  advertised on my XP machine (i did the "live" install) but not the  Vista. The Vista machine is an HP with: AMD Athlon 64x2 3800+ CPU..3 GB  of RAM..250 GB HDD.  I do not like Vista ( i inherited the machine) it's  a pain in the posterior. IMHO ubuntu and it's ilk are the way to go and  i intend to do just that one way or the other.  I am a little long in  the tooth and not to swift with technical jargon or procedures so if you  can help me it would be more then a little appreciated..Hope ya do, :D
what graphics card do you have?

---

### Post by Nycen on 2010-09-01
Hello again
  TY for your replies to my problem. The graphics "card" is NVIDIA GeForce 6150 LE .It is not a card per se but is integrated into the mother board :(..I tried the workarounds as was suggested but got nowhere..The PC goes into a deep sleep/coma (as i described B4 ) moments after the CD is loaded into the drive and i can only recover by manually shutting down the PC. If i try to complete the ubuntu install by selecting it in the BIOS listings the same thing happens..PC goes comatose :(   Other then this goofy problem life is good :)

---

### Post by bcbc on 2010-09-01
> **Nycen said:**
> Hello again
  TY for your replies to my problem. The graphics "card" is NVIDIA GeForce 6150 LE .It is not a card per se but is integrated into the mother board :(..I tried the workarounds as was suggested but got nowhere..The PC goes into a deep sleep/coma (as i described B4 ) moments after the CD is loaded into the drive and i can only recover by manually shutting down the PC. If i try to complete the ubuntu install by selecting it in the BIOS listings the same thing happens..PC goes comatose :(   Other then this goofy problem life is good :)

You can override the wubi install (when it says press ESC for more options). Then press 'e' on the first entry, find inside (in a mess of stuff) the words 'quiet splash' and add nomodeset i.e. 'quiet splash nomodeset' (without quotes). Then CTRL+X.

If it looks like it's working then do the same after restart, press 'e' on first entry etc. 
After booting, look for an nvidia driver under System, Administration, Hardware drivers.

It's long winded - the live CD would be better usually to test your hardware - but if you don't even get to the point of putting in the override, not sure what you could do.

---

### Post by Nycen on 2010-09-02
Hello again & thanx 4 yur help
 following yur instructions..in boot manager,i select ubuntu ..get GNU GRUB v1.98-1ubuntu6..select Ubuntu,Linux 2.6.32-generic..hit "e" then enter ( if i hit enter 1st i get a drum roll and PC goes comatose )..next i get the GRUB window and type in "nomodeset" as suggested..hit Ctrl X...Voila! purple haze log in screen..log in and go System>admin>hardware drvrs...dialog box pops up "searching for available drivers" followed by a larger box with heading "no proprietary drivers are in use on this system"  there are 3 driver choices listed..i select the recommended one...No Go!  can't access the internet :(...i did untick the work off line entry under file...the only way i can access ubuntu on this dopee Vista machine is do the above every time...is there a plan B?  LOL....:)  Keep smilin'.peeps will think yur nuts but who needs normal:D

---

