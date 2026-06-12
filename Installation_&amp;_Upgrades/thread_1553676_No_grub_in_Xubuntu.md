---
title: "No grub in Xubuntu?"
date: 2010-08-15
forum: Installation &amp; Upgrades
---

### Post by Squigglebird on 2010-08-15
Hello!

I'm playing around with my old Dell Dimension 4300, trying to turn it into a daily use/game machine using Xubuntu 10.04 and Puppy Arcade. Xubuntu is installed on my first harddrive and works fine, and I put Puppy on my second harddrive. Thing is, I can't figure out how to get to choose which one to boot when I start the computer, it just boots straight to the Xubuntu desktop without a single line of text being displayed. Puppy works fine if I boot from the live CD, but it would be cool if I could skip the CD and just have a frugal install on the harddrive instead.
I'm not experienced enough with linux to have a clue where to even start here. I've used Ubuntu before, but there was always a grub that you could edit by modifying menu.lst. That doesn't seem to exist in Xubuntu...? :confused:

Anyone have any advice? My computer doesn't really have anything on it, so I don't mind starting over from scratch if need be.

---

### Post by drs305 on 2010-08-15
Squigglebird, welcome to the Ubuntu forums.

First, see if you can display the menu by holding down the SHIFT key during the early stages of the boot. That should display the Grub2 menu.

It probably isn't finding your second OS, which is why it doesn't give you a menu. After booting, open a terminal and run "sudo update-grub" to see if Grub2 picks up the other OS. If it does, you should get the menu to appear if the settings in /etc/default/grub are correct.

I have various links in my signature line about how Grub2 works. One that would be easy to review would be the "G2 Tasks" link, which covers some of the most common settings.

---

### Post by Squigglebird on 2010-08-16
Hello, and thanks!

Well, I've made some progress, I think. The links you provided definitely pointed me in the right direction. Update-grub didn't find Puppy at all at first. But I got the grub menu to appear and I managed to add a menu entry for Lucid Puppy so I can boot it from the grub menu. I still can't get Puppy Arcade to show up in the menu. I added an entry for Arcade in the 40_custom file, and if I start the startup manager in Xubuntu, the entry is visible there, but it doesn't show up in the grub menu when I start the computer. I don't really know what to try next. Both Arcade and Lucid Puppy have their own folders on the same partition of the same harddrive, and I added the entries the same way, just changing the folder names in the paths. Still, only one shows up in the menu. Hm.

---

### Post by drs305 on 2010-08-17
> **Squigglebird said:**
> I added an entry for Arcade in the 40_custom file, and if I start the startup manager in Xubuntu, the entry is visible there, but it doesn't show up in the grub menu when I start the computer. I don't really know what to try next. 

Did you run "sudo update-grub" after adding the entry into 40_custom? It won't be incorporated into the Grub2 menu until this is done.

Is 40_custom executable? I don't think this is your only entry in 40_custom, but make sure the executable bit is set:
```
sudo chmod +x /etc/grub.d/40_custom
```

To have visual confirmation that the file content is being added, you can add this line to the top section of the 40_custom file. When you run "sudo update-grub" in a terminal, you will see a message as the file is read into grub.cfg:
> 
#!/bin/sh
**echo "Adding 40_custom." >&2**
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.


If you have more than one entry in 40_custom, but only one is showing up in the menu, check to make sure the menuentry is correct (punctuation, etc). If you aren't sure, post it here.

---

### Post by Squigglebird on 2010-08-17
Yup, I ran sudo update-grub, and checked everything in the 40_custom file, spelling, punctuation, etc. several times. It's all correct, but for some reason the Arcade entry just doesn't show up. The other entry, Lucid Puppy, did show up, so the 40_custom file does seem to be executable. After scouring the puppy linux forums as well and trying everything I could think of, I finally got fed up and just downgraded to the old grub. It took about five minutes to get everything working perfectly. I guess my computer just doesn't like Grub 2... So now everything works exactly the way I want it to, and I can live without a grub menu background picture. :D
Thanks for all the help!

---

