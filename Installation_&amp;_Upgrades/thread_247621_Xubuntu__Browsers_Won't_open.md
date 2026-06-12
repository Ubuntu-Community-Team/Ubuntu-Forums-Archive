---
title: "Xubuntu:  Browsers Won't open"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by j-dub on 2006-08-30
Hi.

I just got xubuntu running as a LiveUSB installation, based on MadPilot's article.  Everything seems to be working except that I can't open a browser.  I'm connected to the internet, so that's not the problem.  But all three default browsers refuse to open.  I can see Firefox flash on for a second, and then disappear, with a message reading:  Failed to execute default browser; input/output error

If I try to execute firefox from the terminal, it tells me: Segmentation fault

Any help would be greatly appreciated.

Thanks!

-J

---

### Post by zxee on 2006-08-30
> Segmentation fault
 generally means the program is broken/not installed correctly. 
You could use apt-get to upgrade FF or perhaps install a lighter weight browser like dillo.

---

### Post by j-dub on 2006-08-30
Thanks.

I already reinstalled firefox, I'll try Dillo now...

---

### Post by zxee on 2006-08-30
If that doesn't work for you you might want to check out the official installation guides: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
There is a guide there for installing to a usb flash drive-I believe.

---

### Post by j-dub on 2006-08-30
OK,

So Dillo works. I'm using it right now.

But... It doesn't seem to support CSS... it's fine for quick and dirty stuff, but not for web development.

I tried "sudo apt-get firefox", and it had no idea what I was talking about, so I assume that's not the way to use apt-get.  

If you could instruct me on the command you had in mind, that would be great.  

Thank!

-J

---

### Post by zxee on 2006-08-30
> **j-dub said:**
> OK,

So Dillo works. I'm using it right now.

But... It doesn't seem to support CSS... it's fine for quick and dirty stuff, but not for web development.

I tried "sudo apt-get firefox", and it had no idea what I was talking about, so I assume that's not the way to use apt-get.  

If you could instruct me on the command you had in mind, that would be great.  

Thank!

-J

> sudo apt-get install firefox or
> sudo apt-get upgrade firefox
also check out > man apt-get

---

