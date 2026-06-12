---
title: "Server 9.10 Questions"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by Xaevo on 2009-11-28
I want to build a server, it's running windows XP Pro SP3 atm.

i have a 40 GB built-in HDD and i am going to buy an 1 TB internal HDD.

the setup i tought of was:
39 GB for OS (and where the applications get installed)
1 GB Swap
1 TB Storage

I want a few applications on it such as:
- Apache
- MySQL
- FTP
- IRCD
- uTorrent (for the web GUI)
- VLC

is this possible?
And how can i do this?
i am quite a beginner at server building...


Specs:
AMD Sempron 3000+ @ 1,95 Ghz
1 GB DDR RAM
Running 32 Bit OS atm

---

### Post by wojox on 2009-11-28
Sure just follow along [Karmic Server]("https://help.ubuntu.com/9.10/serverguide/C/index.html")

---

### Post by Xaevo on 2009-11-28
But how do i install said packages, and can i install via USB?

And is it possible to monitor my server via my Laptop, trough the desktop 9.10 ubuntu installed on there?
i do NOT want to pay for that other monitor app from canonical

---

### Post by Xaevo on 2009-11-29
Ok, installed and it works, but is there a way to edit all the files on my ubuntu laptop?
Configuration files ETC?

---

### Post by Dinodoc on 2009-11-29
If you want a GUI way to edit files I would suggest reading something like this thread:

[http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)

Or you could use the Remote Desktop.

If you just want to be able to login on a command prompt I would suggest grabbing Putty for your windows machine and using ssh on the linux box to login to shell.

---

### Post by Xaevo on 2009-11-29
i just want to edit the files on my laptop, and when i save it, it's saved on my linux server instead of on my laptop (think a network share, but then for the whole server system)

---

### Post by wojox on 2009-11-29
Just ssh into your server through your terminal and use 

```
sudo nano filename
```

is the easiest.

---

### Post by Xaevo on 2009-11-29
yeah, knew that trick already, but it's annoying...
well, i guess i just keep using that, tho

and how can i mount and setup an NFS share?
it's quite annoying to have to FTP my webserver files each time :/

---

