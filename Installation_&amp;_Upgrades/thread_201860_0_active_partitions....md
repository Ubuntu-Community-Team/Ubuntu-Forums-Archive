---
title: "0 active partitions...??"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by wtfm8 on 2006-06-22
I wanted to do a netinstall of the ubuntu 6.06 dapper release. I found this great site that showed how to [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows) 
So anyways, i setup grub perfectly, that was fine. Then I went about mounting the netboot install files (dapper release btw) and left it on downloading from the ubuntu archive. At one point, it was 83% close to finishing installing the entire thing (it downloaded from the archives for an hour prior and had just finished), and when it reached the 84% mark, the screen went black and it looked like the old school ping pong game from atari.. except without the ball. So I look over at my dsl and it shows that it's downloading something / active. I leave it on over night and wake up this morning to find out that the [ping pong]("http://betohora.terra.com.br/images/pingpong.jpg") screen is still there. I move the mouse, nothing, click on a bunch of keys, nothing... the processors not even working at all, the dsl's stable and i've been asleep for 5 hours...

What could I have done wrong?? I partitioned correctly prior to installation and set 8 gigs free for ubuntu, then in the ubuntu installer, I partitioned it as an ext3 and mounted on /

And now, when I boot it says **0 active partitions**
I hit f12 and choose "boot C:" but I still get 0 active partitions

like my nick suggests... so any help would be appreciated... GREATLY

---

### Post by wtfm8 on 2006-06-22
ok little update everyone, i unearthed one of my old knoppix cds and now i have access to my different partitions
i went through them, and nothing's deleted, in fact it looks like that partition that i installed ubuntu on last night made it. but if that's correct.. .then why am i getting this damned "0 active partition" message when i turn the computer on??
I guessed that it had something to do with my boot.ini (which if you click on the link in the previous post, you would see that you had to add grub for dos so that it would bootup /linux and you could do a netinstall) since it looks something like this:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
C:\GRLDR="Start GRUB"

so i was thinking maybe removing that last line would solve the trick, but now i don't have permission to edit boot.ini
i tried changing permissions but it didn't work out
i'm on my wits end, come on people please help :(

---

### Post by wtfm8 on 2006-06-22
ok I fixed it :) i was going to delete this thread but figured other people who had the same problem as me would benefit from it. What happened was that I unearthed an old Knoppix live cd and booted it up and rap qparted and found out that when installing ubuntu, all my harddrives were set to inactive. So solution: use qparted to set my hda1 active :) there we go have fun

---

