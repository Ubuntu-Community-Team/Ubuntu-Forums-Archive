---
title: "Dapper enumerating drives on PCI IDE 1st? or... If it aint broke dont fix it."
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by MetalMusicAddict on 2006-06-24
"If it aint broke dont fix it." are words I should have lived by.

I have a machine I use as a file/print server. I have 5 HDs in it currently (with space for 8) and a CD/DVD drive. Anyone who can add knows theres not enough spots to hook 'em all up so I need another IDE controller. I actually have 2. 1 extra for the future. ;)

So I *had* breezy runnin on it with no problems whatsoever. (refer to 1st sentence) With Dapper supposed to be a release thats supported for years so I wanted to run it. I also have fallen in love with Xubuntu. So I decided to run Xubuntu-Dapper on my server.

I have hit the biggest problem Ive ever had with Ubuntu and Dapper. (Ive had more little problems with Dapper that anything)

So my OS drive is hdc1. Master on the secondary chain. Breezy handled this no problem.

I installed Xubuntu-Dapper and now get this.

```
ALERT! /dev/hdc1 does not exist. Dropping to a shell!


Busy Box v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of commands.

/bin/sh: can't access tty; job control turned off
```
I have seen [THIS]("http://www.ubuntuforums.org/showthread.php?t=191885") thread but I wanted to bring it to everyones attention.

Now if I remove my PCI IDE controllers everything worked. *Untill* I booted up this morning. Now I get this bad block error that I couldnt get around. I decided to re-install to see If it would fix the block. Install hangs at varions points now. I also think that the drive is "F"ed from all the rebooting. Its a 20gig drive perfect for a OS. I really dont wanna go buy *another* way too big HD. My wife cringes everytime I tell her that. Ive bought tons. She hates it.

Im pulling my hair out, loosing faith in Dapper and am saddened by that.  :( I really do love Ubuntu.

ANY info on this is welcomed.

---

