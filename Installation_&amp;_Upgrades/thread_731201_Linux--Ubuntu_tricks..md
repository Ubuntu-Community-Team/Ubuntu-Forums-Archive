---
title: "Linux--Ubuntu tricks."
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by ubuntoexpert on 2008-03-21
Sometimes I get a small box titled Öpen Files"but it contains empty space and I have no idea what to type in. SO:---

1.What do I put in it?

2.  When I am in Nautilis File Browser, under DEV" I have may executable files but the owner is root , so how do I overcome that?  Do I need to create a root account and how would I do that?

My usb stick with downloaded Linux exe files from Linux software, like clamwin,give me the above messages.  The USB stick popped up amazinly fast when I stuck it in,  then it dsappared. so how can I find it again?  Where did it go?  So I can try a .rar install of something.

I realize there is a lot of command typing, but I need to learn what to type and where. I am only a UBUNTU user for 4 hours so would you knowledgeable experts respond with simple language that I might EASILY understand and please be patient with me?  Because altho it really is a fantasic OS, so far I am really, really lost.

This is just the beginning of thousands upon thousands of points for somebody.

Why do they push exe downloads, when you need to be a magician to open them?
How can I get the dollar sign to change to  this #   in the terminal ?

Thank you,

---

### Post by k33bz on 2008-03-21
you dont need to log into root to take care of those files use sudo for that. As far as changing your $ to a #, with that pound there it represents that you are logged in as root. To do that all you have to do is 
```
su root
```
tyoe in your password, by default I beleive your root password is the same as your login password, which i would recomend changing. Since you already stated you have only been using Ubuntu for a few hours, I would strongly recomend against loging in as a root. You can do alot of damage to your computer if you are not careful while logged in as Root. Use sudo instead.

---

### Post by Pumalite on 2008-03-21
Try:
gksudo nautilus
That gives you root privileges in Nautilus.

---

