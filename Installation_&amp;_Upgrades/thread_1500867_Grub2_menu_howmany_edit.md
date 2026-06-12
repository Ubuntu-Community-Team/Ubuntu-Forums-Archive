---
title: "Grub2 menu howmany edit"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by lifespurpose on 2010-06-03
I have Koala with Grub 2, working fine. Just did some updates and now the boot menu is getting long, too many kernels. Want to reduce to the last two kernels plus Win XP, so got online and looked for instructions in English. News flash: Nobody seems to care about this issue, there is absolutely nothing to be found on it for Grub 2. There is a SIMPLE command for Grub, "howmany", in menulst. Menulst is not used in Grub 2, so that's out. OK I give up, after searching for over an hour for Grub 2's equivalent. Maybe someone here knows how it's done? IN ENGLISH please, not "sudo !@#$%^&*()_+" !!! I am an intelligent BEGINNER.
The Grub 2 page says: "GRUB 2 allows users to create customized menu selections which will be automatically added to the main menu when sudo update-grub is executed." Note the word ADDED. What about REMOVING? Does anyone want to bother themselves with addressing this issue?
I read somewhere StartUpManager can do this. Application Finder doesn't show StartUpManager on my machine, and reading about it at [https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager) has me worried, as it seems to be Grub-1 related. I don't get the impression it will do what I want for Grub 2. If it does, they should say so, right??
I could remove the older kernels, but would rather just edit the boot menu. I found this for removing kernels:
*Open synaptic, do a search for "linux-image" and then remove the older kernels from your computer. Removing them via synaptic will remove them from the boot menu as well. Keep the kernel you are currently using plus one older one you know works. To find your current kernel: uname -r*
OK so I open synaptic and do the search. It comes up with maybe 200 files, some of which start with linux-image, scattered throughout the list. Oh boy, let a newbie loose on this. Just select and delete them all, why not? I can't tell one from another, the only difference is a cryptic number that means not one whit to me. There has to be a better way!!!!
OK so I got brave after editing etc/default/grub and doing update-grub, which reported the kernels by number, which I had forgotten. Then went back into Synaptic and hit the 'Sort By Installed' divider, which brought all the installed kernels to the top, where they make sense. Then I selected the two lowest-numbered and shot them in the head. They are gone. Now I will reboot and if you don't see me again.....

---

### Post by oldfred on 2010-06-04
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

---

### Post by lifespurpose on 2010-06-04
Followed your link and read the incomprehensible gibberish, thanks, I am now much better educated. If you guys are really serious that editing code like that is the best way to get a mundane task done, this explains the slow adoption of Linux as a viable replacement for Windows in the real world (outside the inside). Somebody should think about what nongeek users (and I don't mean boneheads) are likely to want to do (and correcting a boot menu growing out of control is very likely to be high on that list, since it will be seen every time the computer is booted) and make sure there is an intuitive way to do it. Grub 1's "howmany" parameter, while not drag-n-drop, was at least easy to understand. It would make even more sense to allow the user to create the menu himself in plain English, then let Linux try to translate that to the names it needs to work. For example, say I wanted the menu to read:

Linux [or Ubuntu, or Koala]
Recovery mode
Memory Test
*Windows [or XP, or Vista, or Windows 7]

The asterisk would mark the default choice. Braindead easy.
I would simply write that into a file, call it "grubmenu" and put it in the appropriate location. On update-grub that list would be translated so that "Linux" would point to a submenu (created by grub config or prober or whatever), listing the installed kernels. (The default there would be the most recent kernel.) The other items similarly. "Windows", [or its variants] being a trademark, would be easily interpreted to point to the installed Microsoft OS, if found. If not, it would simply say, "invalid menu item, OS not found" and redisplay the menu, with a suggestion as to what to do next, such as by displaying a list of OS's that were found. And a list of the shorthand names that are recognised as pointing to them.
Surely this would not require a lot of work for coders and would save tons of grief by newbies. 
As for removing older kernels, I found synaptic to be easy to use once I guessed for myself that re-sorting with the "Installed" column would bring all the kernels together at the top. I did not remove "headers" files since that instruction didn't wander by until a day later. Which is another problem Linux suffers from: scattered instructions. Of course, what is worse is that the instructions are written for geeks, which is fine for geeks, of course, but useless for those who merely want to get-er-done and get back to work. Linux is like the early cars before the Model T, where you had to be an engine mechanic to be a driver. If you like it that way, so be it, but it will never overtake Microsoft that way. Granted that all drivers should know how to do basic maintenance, but requiring them to be able to rebuild the engine is unreasonable. But thanks for listening to the rant anyway.

---

### Post by oldfred on 2010-06-04
You can have a total custom menu.

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

---

