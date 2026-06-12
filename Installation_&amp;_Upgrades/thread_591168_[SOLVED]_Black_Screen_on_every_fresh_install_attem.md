---
title: "[SOLVED] Black Screen on every fresh install attempt (64bit with GeForce 8800)"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by cowrecked on 2007-10-25
I've heard a lot about Ubuntu, so I decided to try it on my system.  However, I've had no success in installing.

Each time I boot off of the installation CD and choose any option (Install or Start Ubuntu, Graphics Safe mode, OEM, CD check, memory test, etc) it displays a progress bar of loading the linux kernel, then goes to a blank screen (sometimes briefly showing a line of text at the top of the screen and a line at the bottom).  I've downloaded multiple copies of the .iso's, burned multiple CD's at different speeds, and I even downloaded the FULL dvd and burned that, all with the same results.

I'm trying to install the 7.10 AMD64 version (which I've read should be no problem with an intel Core2Duo).

I've seen a few similar threads, and searched for solutions, but I've been unable to find a clear answer.

System Specs:
intel Core2Duo E6750 @ 3.5GHz
eVGA GeForce 8800GT 640MB
4x1GB G-Skill DDR2 @ 4-4-3-4
500GB Samsung SATA HDD, 120GB Seagate SATA HDD (intended install path for ubuntu, if I can get that far), 400GB Seagate SATA HDD
Samsung IDE CD burner, Samsung IDE DVD burner
Creative Sound Blaster X-Fi XtremeMusic
Samsung SyncMaster 206BW @ 1650x1080

I currently run Windows Vista Home Premium with no issues, and have run Windows XP with this configuration.

---

### Post by cowrecked on 2007-10-25
Any help is appreciated.

---

### Post by cowrecked on 2007-10-25
bump

---

### Post by TheBigBentley on 2007-10-25
okay newb here offering some advise based on my current problem. I get this same problem when I either update my ATi drivers or try to use any driver other than the defaut 7.04 drivers. and try to post your xorg file so everyone can take a look. second while I know your anxious to solve your problem it may annoy some people when you bump your thread after only 50 minutes :)

---

### Post by cowrecked on 2007-10-25
Perhaps I should have made it more clear, I dont currently have any linux installed, this is a completely new, fresh install of ubuntu.  I'm not sure how to get to any linux files to show you, including the xorg file, as I havent been able to install in the first place.

(oh, and I'm only trying to get a reply before I go off to work for the day :D )

---

### Post by TheBigBentley on 2007-10-25
I use an app called wubi that makes installing and dual booting from within windows a cinch. Not sure if you currently have windows installed but it does all the complicated work for you. I highly recommend it. While I don't have a 64 bit PC i just read that wubi will detect a 64 bit cpu and download the correct version for you. If your new like I am, I suggest starting there.

---

### Post by cowrecked on 2007-10-25
thanks, I'll give that a try

oh, does this work for 7.10? The installer is "Wubi-7.04-04.exe"

---

### Post by cowrecked on 2007-10-25
yeah, looks like this is just for 7.04

---

### Post by dmonkey on 2007-10-25
Did you try the alternate install cd?

---

### Post by cowrecked on 2007-10-25
can you clarify what exactly the alternate install CD is?

---

### Post by dmonkey on 2007-10-25
Hi,

look here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

At the bottom of the form is a checkbox to get the alternate download. This allows you to install ubuntu without booting into a GUI (which might be your problem).

Once ubuntu is installed you will be able to boot into recovery mode and perhaps fix the issue from there.

---

### Post by cowrecked on 2007-10-25
turns out all I needed to do was in the additional options menu (F6) change **splash** to **nosplash**, and I could install from there

since then I've had a few other issues, including the Grub error 17 preventing me from booting into either vista or ubuntu, which I've only now fixed for vista

but anyway, thanks for your help

---

### Post by cowrecked on 2007-10-28
followup, I've set up ubuntu and vista to work exactly as I want

thanks again for the help

---

