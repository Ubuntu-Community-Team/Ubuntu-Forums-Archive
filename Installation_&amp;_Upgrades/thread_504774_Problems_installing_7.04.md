---
title: "Problems installing 7.04"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by abrack08 on 2007-07-19
Okay, I am completely new to Ubuntu/Linux and I wasn't exactly sure where to post this between here and the newbie bored, but this is specifically for installation problems so I figured I'd give it a shot.

I have a 4-5 year old computer, not that great but should be able to handle Ubuntu (I'd get the exact information on it but I can't). A few months ago, my hard drive crashed, wasn't too big a deal, gave me an excuse to buy a nice 250 Gig one to replace my broken 17 GB. Well I went to install it in to my computer, and everything went great till it prompted me to put in my OS installation CD. Well we didn't have one, so I put it up assuming I'd buy a Windows XP or something in the next couple weeks. Well that never happened, and I ended up just using my Step Brothers computer instead. I finally got tired of his sucky computer a couple days ago though, and somebody told me about Ubuntu (honestly the main drawing point being that it is free) so I downloaded the CD Image iso and burned it to a CD. Well I pop in my old computer + new hard drive and run the installation CD for the hard drive again and I noticed that it asks what OS I plan on using, and ALL of the choices were Windows. I just picked Windows XP hoping it wouldn't matter. Well then it asks me to put in the OS installation CD and I put in the Ubuntu one I just made, and it brings me to this menu and I hit "Start or Install Ubuntu". I hit enter, and it goes to a loading screen, then it goes to this:

> BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter "help" for a list of built-in commands

/bin/sh: can't access tty; job control turned off
(initramfs)

Well I didn't know what to do, so I just turned the computer off, then I turned it back on, hit "Start or install Ubuntu" again, and this time **it went to that loading screen where it says "Ubuntu" and had the little orange bar that bounces back and forth. I assumed it was working, so I watched T.V. and waited for something to happen, but several hours later it was still nothing.** I turned it off, hooked up my step-brothers computer, and, well, it looks like that old old hard driveis finally fried too, because I hasn't messed with it at all and all of a sudden it can't seem to find the Primary Hard Disk. Of course I opened it up, switched some chords out to make sure that wasn't the problem, but no matter what I did, it wouldn't find it. I got frustrated, plugged up the Ubunutu PC again, hit "start or install" and I've been staring at that damn loading screen for about 16 or 17 hours now, and I don't have another computer to get on for myself other than this laptop, which I can only use when my parents aren't home =/

Help me? Sorry for the wall of text, I figured I'd be more likely to get help if ya knew exactly what was going on.

---

### Post by Wim Sturkenboom on 2007-07-19
Sorry, did not read last part of post

---

### Post by abrack08 on 2007-07-19
No harm no foul, any suggestions though? I was hoping something would come through fairly quickly, I'd like to have my computer up and running today.

---

### Post by dabl on 2007-07-19
Yep, you went wrong when you made that guess about the "other OS" thing.

Sticking with your "free" approach, I recommend you download the ISO and burn a GParted Live CD -- get the ISO here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

This CD has one mission in life -- to let you get that hard drive under control.  Boot your GParted Live CD, remove any partitions that may exist, then set 3 partitions as follows (since you don't have a Windows CD):

1 -- 10GB (set the "bootable" flag on this one)
2 -- 0.5GB (this will become the swap partition)
3 -- All the rest of it (this will become the /home partition)

You don't need to do formatting with GParted, just set up the partitions.

"Apply" your changes and let GParted do its thing.

Now boot your Ubuntu CD, choose "install", go through the language and time zone stuff, and then tell it you want "guided partitioning".  For each partition, set it up like I said above.  The 10GB partition gets mounted as "/" and formatted (either ext3 or reiserfs format), the 0.5GB partition is formatted "Linux swap", and the big partition is "/home" and is formatted.

Let it do the installation, let it install Grub on the root partition that you marked as bootable, and you should restart to a new Ubuntu system.  Should there be a video issue (like it restarts and you see a black screen with a blinking white "_"), post about that separately and you can get help. :)

---

### Post by lord lewix on 2007-07-19
get a older ubuntu then install that then upgrade from that...and if your installing from a windows computer format it then do what i said above.

---

### Post by abrack08 on 2007-07-19
> **dabl said:**
> Yep, you went wrong when you made that guess about the "other OS" thing.

Sticking with your "free" approach, I recommend you download the ISO and burn a GParted Live CD -- get the ISO here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

This CD has one mission in life -- to let you get that hard drive under control.  Boot your GParted Live CD, remove any partitions that may exist, then set 3 partitions as follows (since you don't have a Windows CD):

1 -- 10GB (set the "bootable" flag on this one)
2 -- 0.5GB (this will become the swap partition)
3 -- All the rest of it (this will become the /home partition)

You don't need to do formatting with GParted, just set up the partitions.

"Apply" your changes and let GParted do its thing.

Now boot your Ubuntu CD, choose "install", go through the language and time zone stuff, and then tell it you want "guided partitioning".  For each partition, set it up like I said above.  The 10GB partition gets mounted as "/" and formatted (either ext3 or reiserfs format), the 0.5GB partition is formatted "Linux swap", and the big partition is "/home" and is formatted.

Let it do the installation, let it install Grub on the root partition that you marked as bootable, and you should restart to a new Ubuntu system.  Should there be a video issue (like it restarts and you see a black screen with a blinking white "_"), post about that separately and you can get help. :)

Okay, well I got the GParted thing started, but it looks pretty confusing, I'm not really sure what I'm doing. I don't know how to set partitions or delete them or anything...

---

### Post by abrack08 on 2007-07-19
Okay, there's a problem... I found documentation on their site explaining how to set partitions, but... well the site explains how to do it with pictures like this
[IMG]http://gparted.sourceforge.net/larry/resize/big/chose-drive-b.gif[/img]

Which is kinda hard to follow, since the screen I'm staring at looks like this...
[IMG]http://i20.photobucket.com/albums/b230/abrack29/gparted.jpg[/IMG]

---

### Post by abrack08 on 2007-07-19
Okay, I'm retarded, it's obvious you have to run the thing and then it goes to the graphics mode. It asks for a video drive though, I went through trying each one of them, only one produced different results than the other ones, vesa, so I'm assuming that's it, but the problem is... it goes to a blank black screen and just stays there. This is pretty frusterating -_-

---

### Post by abrack08 on 2007-07-19
Bump...

---

### Post by confused57 on 2007-07-19
Maybe something in this thread will help you boot the Ubuntu live cd:
[http://ubuntuforums.org/showpost.php?p=2332270&postcount=5](http://ubuntuforums.org/showpost.php?p=2332270&postcount=5)

You could try the alternate cd, which might be able to install Ubuntu, but you wouldn't be able to test it first in a live environment.

---

