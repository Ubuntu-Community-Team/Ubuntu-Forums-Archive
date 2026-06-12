---
title: "Grub rescue mode?!"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Gamewiz on 2011-04-28
Hey there my computer is currently stuck in "Grub Rescue mode" I don't know how to get it unlocked. I tried installing the latest ubuntu from wubi after I deleted the partition for 11.04 beta I had already had (I had some issues with 11.04 so I went to windows (it's a dual boot machine) and cleared the partition)

After I got rid of ubuntu from there I don't think it automaticlly got rid of grub, which I was unaware of. So I continued to go through Wubi for to install 11.04 side by side Windows and to be used with the windows loader.

After I got thorugh all of that stuff I was instructed to restart my computer (as usual) and I did. But as soon as my computer came back on it came into "grub rescue>" with the error message at the very top of the screen "error: no such partition."

I am currently using a different PC to type this. I would like to know how to get out of the rescue loader and at least back into windows (I have windows 7). I don't care to much if I can make it into Ubuntu as I have most of my more important files on Windows.

I'm kinda scared atm, because I read somewhere earlier that I can't really do anything unless I have the windows boot disc, which I don't.

HELP PLEASE!!!! :(

---

### Post by bcbc on 2011-04-28
See the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198"), Problem #1, Solution #2. You can install a form of lilo that acts the same as the windows bootloader. You just need to boot an Ubuntu CD to do it.

(Even though this was not caused by Wubi the solution is the same - so you can ignore the background info).

PS these wubi problems are fixed with 11.04

---

### Post by utotmeh8 on 2011-04-28
This actually just happened to me when installing 11.04.  Unlike you, I had a windows 7 disc laying around and resolved the problem with 2 commands at the recovery Command Prompt.

```
bootrec.exe /fixboot
```

```
bootrec.exe /fixmbr
```

Here is the original post: [How to restore the Windows Vista or 7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

If you're having trouble finding a windows recovery disc, this page may help:  [Download Windows 7 System Recovery Discs]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

I really hope they work out the bugs

---

### Post by bcbc on 2011-04-28
The OP's problem isn't a bug (maybe yours is). If you dual boot (non-wubi) and give boot control to grub, then you need to know that grub has to load its modules from the linux partition. If you boot windows and format the partition then you break grub's chance of booting.

The wubi one is a bug and that's fixed in Natty. Fixes in lucid and maverick are ready, soon to be released.

---

### Post by Gamewiz on 2011-04-30
> **bcbc said:**
> See the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198"), Problem #1, Solution #2. You can install a form of lilo that acts the same as the windows bootloader. You just need to boot an Ubuntu CD to do it.

(Even though this was not caused by Wubi the solution is the same - so you can ignore the background info).

PS these wubi problems are fixed with 11.04


Oh my God, thank you SO MUCH. You're the best, thank you for linking me to that site. Sorry it took me so long for me to respond, I had a lot of stuff I had to take care of before I could get on my second computer (this one) I have just gotten everything fixed, and it looks like the wubi correctly installed the Ubuntu also. 

Thank you, Thank you, Thank you!:D

---

### Post by bcbc on 2011-04-30
> **Gamewiz said:**
> Oh my God, thank you SO MUCH. You're the best, thank you for linking me to that site. Sorry it took me so long for me to respond, I had a lot of stuff I had to take care of before I could get on my second computer (this one) I have just gotten everything fixed, and it looks like the wubi correctly installed the Ubuntu also. 

Thank you, Thank you, Thank you!:D

You're very welcome :)

---

