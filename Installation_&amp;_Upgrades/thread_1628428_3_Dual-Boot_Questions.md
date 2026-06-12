---
title: "3 Dual-Boot Questions"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by Dr Watts On on 2010-11-22
Hello all,
I am trying to restore access to Windows XP. I had installed Ubuntu 10.04 on friend's computer (grub in MBR), had trouble with his printer, so then installed XP on another partition of same hdd (sda3) to use his printer with mfr's Windows driver. Of course XP wiped MBR, so then restored MBR I had saved. 

Now I have Ubuntu back, but can't find grub.lst menu.lst grub.cfg, or whatever, to edit. So, 

**1)**: What file in Ubuntu needs editing?

**2)**: HOW do I edit that file?

I also can't remember whether to refer to boot.ini or ntdetect.com or ntldr or ??? in the Ubuntu boot file (if I ever figure out how to get that far). 

**3)**: To which XP file(s) (or folder(s)) should the new entry in the Ubuntu boot-file refer?

I logged in as root and tried running grub from console: grub isn't "installed" (??). 
The Ubuntu installation is standard 10.04, except I made sure to have a login account for root.

Any help would be appreciated, including links to relevant threads in UbuntuForums. I did find 
[http://ubuntuforums.org/showthread.php?t=1526269](http://ubuntuforums.org/showthread.php?t=1526269)

However I don't see the answers to my 3 questions above.

I would also be interested in the other permutations, since I will be messing with computers that have Windows 7 installed or to be installed, and boot.ini is not used. Then there are the same scenarios with other Linux bootloaders (grubs and lilos, etc). 

I have no idea how to determine [COLOR=DarkRed]***by examination*,**[/COLOR] which boot methods are in use on any particular Linux system, let alone how to modify them.

But FIRST, I need to deal with the immediate situation,
so I can return my friend's computer and get on with my own stuff (and life)!

I guess I need to get better with my site-search techniques, too.

Looking forward to any and all replies.
DrWattsOn [sidebar: SITE PROBLEM: the Post Icons selection of smileys do not all match their popup descriptions

---

### Post by oldfred on 2010-11-22
One of the real advantages of grub2 is that it is really good at finding other systems and including them. If you install a new system after Ubuntu:

sudo update-grub

That should add any new systems.

If you really want to know a lot about what is installed where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

I run the script before & after any system changes to 
 a - document what I had &
 b- to make sure I changed what I thought I changed.

General info:
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
/etc/default/grub
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by Dr Watts On on 2010-11-22
@oldfred:
Hello, I saw your posts in the thread I referenced above in my threadstarter. I logged on to that computer as "root", opened bash, ran update-grub, ... WOW, it worked, and works, just not exactly as I wanted. 
I wanted boot.ini to run, to show up per my edits to it (boot.ini), and instead it goes directly to the doggon logon. That IS functional. I explored the Ubuntu menu choices, but since I "gotta go" for now,
I will come back and explore the other info you gave me.
I will return and mark the thread solved after making a real attempt to get exactly the results I want, which aren't absolutely necessary, I just want what I want, is all.
So probably tomorrow or later tonight, I expect to be back here.
Thank you for your help.
DrWattsOn

---

### Post by oldfred on 2010-11-22
I thought boot.ini was like grub in that if you only have one system it just goes to login skipping any menu as it is not required.

Not sure in windows how to get its menu to come up.

---

### Post by Dr Watts On on 2010-11-23
Hello oldfred,
You are correct re boot.ini, I had forgotten. I accomplished my ends by simply adding a duplicate entry under [operating systems], wherein I changed the description to be as I wanted my friend to see it: ie, "Log Onto WinXP as 'printer', no Password". There is no "welcome screen" so he won't find other usernames unless he digs, and I hid most shortcuts not necessary for printing. So he won't accidentally get into trouble.
Meanwhile, all else is good. I didn't have time to change the menu titles provided by grub.cfg, although I will make time to read how, as well as the other links you provided.
So thanks for your time, effort, info, and the clarity you provided.
I'll be lurking when I find time.
DrWattsOn

---

