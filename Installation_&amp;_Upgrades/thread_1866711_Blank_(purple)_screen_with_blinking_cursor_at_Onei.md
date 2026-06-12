---
title: "Blank (purple) screen with blinking cursor at Oneiric"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by jalms on 2011-10-21
Hi there.

Although newbie to linux, I'm perfectly aware that this is a common issue in Ubuntu.
Things you should know first, don't know if they're relevant:
- I'm using Ubuntu through WUBI.
- My graphic card is Nvidia and both Natty and Oneiric worked just fine with proprietary drivers.
- Yes, I know what "Search" and "Google" are, it's despair after those both being unsuccessful that makes me yell for your help, I don't like to bother but really need you right now.

The story: I ran Natty perfectly for 3 months and then updated to Oneiric when available. Worked with Oneiric a couple of times successfully (I have the slight idea that, the last time, there was some update) but today I went to boot it and noticed immediately that it skipped GRUB and, then, halted in a blank purple screen.
I ran to these forums and into Google straight away and started to feel happy for finding lots of solutions, all of them quite simple. The most current one is to hold shift to get GRUB (successful) and then edit the entry and remove "quiet splash" and insert "nomodeset".
However, not only _"nomodeset" was already there_, but also removing "quiet splash" as now success at all, same result reproduced. Removing it and inserting "text" was unsuccessful also. Removing "nomodeset" didn't work either.
Trying to load a previous kernel was no help at all. It gave me a little bit more than 3.0.0 but just halted at hardware check and only reacted to Ctrl+Alt+Del.

Sorry but I'm noob enough to not know how to boot from recovery mode. It just prompts me for something I do not know what is.

Please do help me. I know you may find newbies boring, but I tried a lot to solve without bothering you.

---

### Post by LinuxFan999 on 2011-10-21
Using Wubi as a permanent installation is not recommended.
To do a dual boot with Windows, first defragment your Windows filesystem, then reboot with the Ubuntu CD inserted. Next, select "Install alongside Windows", then adjust the amount of space you want to give Ubuntu. Then, just follow the instructions, and after awhile, the installation of Ubuntu will be finished. Then reboot, removing the CD when Ubuntu tells you to, then a boot menu will appear. Select the menu item at the top of the screen to boot Ubuntu. Ubuntu will start up, then enjoy Ubuntu.
Don't forget that the option to boot into windows will be at the bottom of the boot menu.

---

### Post by jalms on 2011-10-22
Thank you a lot for your advice.
However, Ubuntu through WUBI is just a different bootloader, it's not supposed to be "that" different. Anyway, it should work, as it always worked, there's something wrong here that must be solved and me and whoever does have the same problem need to solve it other way...

---

