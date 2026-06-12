---
title: "Ubuntu boots into dark blue screen"
date: 2014-02-27
forum: Installation &amp; Upgrades
---

### Post by Jasper_Haller on 2014-02-27
Hello everyone,

I am new to Ubuntu and just installed 13.10 a few days ago. Since this morning, I can no longer boot. Here's what happens:

1. I am prompted to enter the passphrase to my encrypted hard drive. I enter it and see a message confirming that I have successfully entered the passphrase. So far, so normal.
2. For a split-second, I see a message that my discs are scanned for errors.
3. I get a dark blue screen.

And this is where it ends. The screen is not black, just a very dark shade of blue, and I can adjust the brightness using my keyboard. I can also use the keyboard to put the computer to sleep. But this is all. I cannot log on (blindly typing my password has no effect) and cannot reach manual login by pressing ctrl+alt+f2.

So far, I have twice tried booting from a disc and running boot-repair. Each time, the program happily informs me that it has repaired whatever problem there was, but the dark blue screen still appears. It has also spit out a log file, but I have not been able to make sense of it. Here's a link to another such log file I just created: [http://paste.ubuntu.com/7007516/](http://paste.ubuntu.com/7007516/)

If anyone has any further ideas, I'd much appreciate it.

---

### Post by Dreamer Fithp Apprentice on 2014-02-28
I can't help you much but you've been 24 hours without reply so I'll throw in a few thoughts.

That part of the log that goes:
" . . . and looks      in partition 94 for ."

sounds like trouble to me. But I'm no booting expert. Sounds like there was supposed to be an expansion of a variable before the period and the variable didn't get set. But how to track it down precisely, and what to do about - I haven't the foggiest.

And anyway, "partition 94"? 94 ?!?!? That's a heck of a lot of partitions. You don't really have that many do you? Probably that's just something I don't understand. I'll be interested to hear more knowledgable comments on those things.

Anyway, the main thing I wanted to suggest is conditional. If you don't have any unbacked up data of importance in there, I'd just reinstall. If you do have important data there, I'd try booting from another device, like a live cd and attempt to copy it somewhere else. I believe when you use Ubuntu's built in method of encrypting home it gives you some string you're supposed to keep in a safe place in case you need to decrypt it without actually booting it. If you didn't save it I think there is also another method where you only need your login name and password but I don't recall the details. Maybe knowing what you are looking for may be of some use. For the future, if you don't already do it, you might consider keeping your data on a seperate partition and just leave home for config files and such. Makes life a lot simpler IMO, although it isn't the standard way. That way you don't have to worry about borking the installation - you can just reinstall. And if you want to encrypt your data also, there are standalone programs like truecrypt that are probably better. Good luck.

---

### Post by bedfordd on 2014-02-28
maybe try burning a live-disk and see if you can boot from it and get to your encrypted disk?

---

### Post by Jasper_Haller on 2014-03-01
Hi everyone, thanks for the replies. 94 partitions would indeed be a bit excessive :P Indeed, I haven't partitioned my disk at all. Just one of the many things that puzzles me about the log file.

Perhaps I should have mentioned that when I boot from a dvd, I can access the hard drive (it prompts me for my passphrase, I enter it, no problem), so I can easily recover all my data. So fortunately, I don't have to worry about that. I just didn't want to go through the pain of having to re-install Ubuntu if this was a well-known problem and there was a quick-and-easy solution. Seems like that's not the case.

---

### Post by Dreamer Fithp Apprentice on 2014-03-21
> **Jasper_Haller said:**
> I haven't partitioned my disk at all. ... I just didn't want to go through the pain of having to re-install Ubuntu . . . If you make a seperate partition for data and backup the installation with fsarchiver from another bootable medium (live disk or another hd partition) reinstalling the backed up installation is a snap. Much quicker than starting from scratch, and all your tweaks are preserved. Perhaps I'm too late in mentioning it, but bear it mind for next time perhaps.

---

