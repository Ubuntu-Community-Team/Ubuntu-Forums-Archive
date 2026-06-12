---
title: "Wubi prevents installs from USB, know why need fix."
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by teebo63 on 2010-01-21
Wubi will prevent further installs via USB.

I have tried Wubi (should have read the fine print - once you do an update from within Ubuntu, you can kiss your Ubuntu bye-bye)

So anyway, tried to de-install Wubi from Windows, worked fine (no extra boot option afterwards) but still got the busy box sh instead of my shiny login screen after wubi re-install, so gave up and decided I should go back to Debian, but bear with me.

Debian or other Flash based installers can't find their iso file.
Why?
Well, when I dropped to a command line from the installer, mount produced (amongst other things):
/dev/loop0 /cdrom
/dev/loop1 /cdrom

What? Yes, my two previous wubi attempts will not die.
Although I have successfully run the uninstaller, and won't get any offer to boot into Ubuntu, the actual pseudo-disks are still there, with their iso's and wubi.exe (I know that because from the installer's shell, ls said they were there)

Now I have deleted c:/ubuntu from Windows, to no avail.

I tried to mount -o rw -o remount the two stupid mounts to at least try and rm the files in there, no luck: still can't rm on a read only fs. Hmmm.

So the question is:
*******************

How do I properly get rid of the pseudo disks wubi (contained rage) has so nicely (bitter sarcasm) created for me but won't go away? So that they won't mount as /cdrom in my installers?

Note that these pseudo disks or pseudo partitions do not show up in the windows disk management app.

I run a Toshiba Satellite T130-13L and sadly need to keep some sort of Windows for iTunes.

I saw plenty of unsolved error reports on the web where people could not install stuff after using wubi and I think this is related.

---

### Post by phillw on 2010-01-21
Hi, and welcome to the forums.

Sorry to hear you're having grief.

As you have, as far you can tell, removed Wubi - I'd go for remastering your MBR back to Win. That will give you back your Win system.

Head over to --> [Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

Once you have wrestled your system back - I'd suggest a dual booting system, as updates do seem to bork Wubi installations with regularity.

As for iTunes, the boyz and girlz over at WINE seem to getting better and better results with it --> [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

I'm not saying it's going to work 100% for you (it has a silver rating), but it may be worth a try having Win **inside** Ubuntu, and not the other way round ;-)

WineHQ is a great area for all things wine - as a little cheat, a lot of people have found the beta for wine to be running more apps than the current stable release - so do have a dig around on the subject.

Regards,

Phill.

---

