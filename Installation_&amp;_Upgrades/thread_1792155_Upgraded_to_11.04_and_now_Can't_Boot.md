---
title: "Upgraded to 11.04 and now Can't Boot"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by KrisB on 2011-06-27
Hi All,

Hoping Someone can help me.  I'm a relative newbie.  I've used Ubuntu for a couple of years, but I know VERY little about command line, and I pretty much don't know how to fix things.  :(  Sorry! 

I just did the "update manager" update to 11.04 and my system which is relatively new and worked perfectly until right after the upgrade suddenly won't boot after the restart.  I tried going to the recovery mode and "repairing broken packages" but it tells me that zero files will be downloaded or changed.   I tried using the USB to boot and reload the OS (which I used on another computer and it worked perfectly) but it won't boot to USB.  I tried an old version 9 CD but it won't boot to CD (yes I checked the boot order in BIOS and my HD was last in line).  So- I attempt to boot- and it starts to load.  I get the purple splash screen.  Then it goes black, and drops me into a list of errors and tells me all things that it's "starting/stopping" and says "0k" to each except one which in red says something about "stopping automatic crash report" which says "[COLOR=DarkRed]fail[/COLOR]".  The only thing it lets me do from there is Control-Alt-Delete.  I can sometimes get to the Recovery mode, and I did manage to use a "previous linux version" to boot- picked the first one on the list.  But it's a one time deal, then it goes back to not booting.  I tried the sudo apt-get clean, sudo apt-get update, sudo apt-get upgrade suggestion, but that didn't help either.  I **really** want to avoid wiping the drive if I can help it.  I just can't figure out how to make this thing boot, or why it refuses to boot to CD and USB.  

Anyone have any ideas that can help? Can I somehow get it back to booting to 10.10? It might be worth it at this point!?

Thanks to anyone who can help me. I need very clear instructions please.  I'm very clueless about any terminal stuff yet.  Thanks!

Kris

---

### Post by Quackers on 2011-06-28
To be honest it seems that you've done so much since the original error it's very difficult to help you now as it's unclear to me now what system is installed.
You may have just had a video problem which could have been fixed with a boot option. It could still be worth a try. If you have a Nvidia or ATI graphics card you can try the nomodeset boot option., Details in the thread below
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by KrisB on 2011-06-28
The only thing I've really done is boot to a previous version in the recovery mode- but it still comes up showing it's 11.04.  Nothing else every actually worked.  Honest.  I definitely have 11.04 It just won't boot on it's own.  I'll try your suggestion tonight and see what happens.  Thanks!

---

### Post by KrisB on 2011-06-28
Just skimmed through that page, and all I can think is wow! How do I find out which one might apply?  I don't want to permanently crash it! It doesn't hang at a black screen, it just goes black as it stops booting- then straight to that error screen with the crash report fail.  so I don't know that it is a video driver- but I'm too new at this.  What should I try first?  Please be detailed with any instructions. Thanks!

---

