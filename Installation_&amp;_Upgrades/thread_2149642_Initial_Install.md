---
title: "Initial Install"
date: 2013-05-29
forum: Installation &amp; Upgrades
---

### Post by SlaneBoy on 2013-05-29
Good morning. Every now and then, I become curious about Ubuntu but it appears as if I need to call it a day with this poor excuse for an OS . I tried using Wubi and installing Ubuntu 13.10 onto my Dell Optiplex GX 260 w/ a SL6RZ P4 CPU . It uses the onboard Intel Extreme Graphics 82845 G/GV  Video chip.  Never seen anything so pathetic in a long time - After initial install, when I use my Password to Login, it completely clears the Display of everything but the Default Wallpaper. Nothing but that orange, reddish waveform. No Taskbar on top. no Unity menu items on left, NOTHING ! Those items ARE there before I Login, but quickly disappear and freeze that spinning wheel thing. My God - I'm a Tech and when you're faced with a glitch like this, it's rather pessimistic about the entire platform. Remarkable!  Glitched from Jump Street. What to do?

---

### Post by fantab on 2013-05-29
Are you sure you have 13.10 WUBI install? Perhaps you meant 12.10.
Can you tell us how much memory you've got? If its 1GB or less then I suggest you try [**Lubuntu**]("http://lubuntu.net/"). Its quite light on the system resources. It is Ubuntu but with LXDE desktop, unlike the default UNITY which requires more resources to run.

---

### Post by SlaneBoy on 2013-05-29
Yes, Sir - I've got 768 MB of RAM on the system and it ran 12.10 happily about a year ago. I downloaded/installed 13.04 but it called itself 13.10 assuming it would immediately update. I tried Lubuntu 13.04 and it didn't interest me the way that Ubuntu does. I've tried three (3) different installs of 13.04 and zero (0) has succeeded. Windows 7 runs smoothly on 768 Mbs and has a Min System Requirement of 1GB for a 32 bit application. I'm assuming that 13.04 will work the same way. It's close enuf to move forward and should, but Ubuntu is renegade as it gets. I remember what it took to get my Realtek CU 8188 WLAN operational last year and cringe. I'm a Tech and when this Accordion folds up from Jump St. that's not good. Launcher and Menu are present before Password is entered but not after. Ya gotta admit - stuff like this is EXACTLY why Linux is light-years away from the dominance that Microsoft enjoys.

---

### Post by fantab on 2013-05-29
Officially WUBI is not available in 13.04, since it has issues with Windows8. 13.10 is in [pre-alpha stage]("https://wiki.ubuntu.com/SaucySalamander/ReleaseSchedule"). So I wonder why your 13.04 calls itself 13.10. 
How does the Ubuntu 13.04 Live DVD/USB work? Have you considered 'true dual-boot', having Ubuntu on its own partition? 

I am afraid that I cannot be of much help... perhaps somebody else might be able to help you fix the vanishing unity.

---

### Post by SlaneBoy on 2013-05-29
Yes, I've read the same as you to the conclusion that Wubi was being eliminated because of conflict with W8. It made me wonder why all three downloads were loaded up with Wubi at the bottom of the list of Files. That's obviously where I install from for the sake of simplicity.  I feel like a Batter in a game of Baseball and I struck out.  The same thing happened with Linux Mint 10 and I can't remember how to solve it,all I remember was it was easy. Damn, this is gonna bother me. This MUST be a known issue. As soon as Password gets entered, the Screen is wiped clean like a BlackBoard. I'll bet this is gonna be harder than enabling a WLAN stick. That was double tough !

---

### Post by fantab on 2013-05-29
WUBI was included in the 13.04 *beta* but was dropped from the final release. Perhaps you have downloaded that version of WUBI and hence the issue. However, there are people who have successfully used that *beta* WUBI to run 13.04. 

I have a suspicion that the issue you have has something to with lightdm and/or permissions. What happens if you login as GUEST?

---

