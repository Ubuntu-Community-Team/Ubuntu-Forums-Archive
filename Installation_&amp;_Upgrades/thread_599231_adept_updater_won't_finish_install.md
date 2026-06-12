---
title: "adept updater won't finish install"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by D_D_T on 2007-11-01
Hello! Can anyone help me please? I've been running Kubuntu Feisty for a while and things have been ok, but recently I tried to run adept updater and it came back with the message that "couldn't download or broken dependencies". I looked at this post as to what to do ([http://kubuntuforums.net/forums/index.php?topic=3087169.0]("http://kubuntuforums.net/forums/index.php?topic=3087169.0")) but the moment I tried
> sudo dpkg --configure -a
I was told that

> dpkg: parse error, in file `/var/lib/dpkg/available' near line 1170 package `login':
 EOF during value of field `Replaces' (missing final newline)

What can I do to fix this? The updates are backing up and I need to install some software!

Thank you!

---

### Post by por100pre1 on 2007-11-02
Try this:

```
sudo dselect update
```

you can also open Software Properties:

```
gksu software-properties-gtk
```

and change the repository server.

Let us know if this works. :-k

---

### Post by D_D_T on 2007-11-16
Hello!
Thanks for your reply. I Tried the "deselect update" option, but that didn't sort it, and my attempt to access Software Properties came back with 
> X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

I have also tried > sudo dpkg --clear-avail  followed by > sudo apt-get update but this doesn't work either. I managed to upgrade to Gutsy with this last set of commands, but then it went back to saying that there were broken packages again. 
I'm currently using Kubuntu Gutsy. 
Thank you for your help,
D_D_T

---

### Post by por100pre1 on 2007-11-18
Maybe the best solution is to backup your whole user folder to removable media or external hard disk drive and then do a fresh install. Sorry for the delay! :(

---

### Post by D_D_T on 2007-11-19
pants! I thought that may be the case, but was praying for another option. I think I'll leave this thread unsolved for a couple more days just to see if anyone else has an idea, but then I think I'll have to do a re-install. What a pain. How could Adept have destroyed itself so perfectly? 
Oh well, thank-you for your help anyway.
D_D_T

---

