---
title: "Deletion of system files. HELP!"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by nortada on 2011-10-05
Hello,

I accidentally executed the following command "sudo rm -R ./fonts /*", and because of the typo (extra space between "./fonts" and "/*"), massive deletion of my system files started. I know, it was a very negligent and stupid mistake. =D>

Before I could press Ctr+C, the folders: /bin, /boot, /etc and /home, had been deleted. At least, it's what I could perceive from the error messages of impossible to delete files. I think the catastrophe stopped in my /home folder. 

My desktop crashed, with  bars on windows disappearing, keyboard doesn't work, ... hopefully music is still playing. I think it prevented me from destroying the keyboard ](*,), and just laugh about the situation. Bottom-line, I think the system is unusable, but haven't tried to reboot it yet.

So, I request your help and advice, on what's the fastest way to recover it. Ideally without having to install a fresh new system, and applications.

I don't have much time, since I have a master thesis to deliver in two weeks. And  this was my best computer for working on it, although not the only one.

Thanks in advance,

PS- sorry for all the talk. But I think you'll be sensible to my current need to tell people how much I'm stupid. Oh well... Live and learn...

---

### Post by lcman on 2011-10-06
> **nortada said:**
> Hello,

I accidentally executed the following command "sudo rm -R ./fonts /*", and because of the typo (extra space between "./fonts" and "/*"), massive deletion of my system files started. I know, it was a very negligent and stupid mistake. =D>

Before I could press Ctr+C, the folders: /bin, /boot, /etc and /home, had been deleted. At least, it's what I could perceive from the error messages of impossible to delete files. I think the catastrophe stopped in my /home folder. 

My desktop crashed, with  bars on windows disappearing, keyboard doesn't work, ... hopefully music is still playing. I think it prevented me from destroying the keyboard ](*,), and just laugh about the situation. Bottom-line, I think the system is unusable, but haven't tried to reboot it yet.

So, I request your help and advice, on what's the fastest way to recover it. Ideally without having to install a fresh new system, and applications.

I don't have much time, since I have a master thesis to deliver in two weeks. And  this was my best computer for working on it, although not the only one.

Thanks in advance,

PS- sorry for all the talk. But I think you'll be sensible to my current need to tell people how much I'm stupid. Oh well... Live and learn...

There's still hope because you haven't rebooted the system yet. You need to switch to single user mode and recover the files you've deleted.

Here's a good tutorial:
```
http://www.cyberciti.biz/tips/linuxunix-recover-deleted-files.html
```

---

### Post by nothingspecial on 2011-10-06
> **nortada said:**
> 

So, I request your help and advice, on what's the fastest way to recover it. .

The fastest way to have a working computer to write your thesis with is to reinstall.

---

### Post by nortada on 2011-10-29
I ended reinstalling the system. Hopefully I had my /home in a separate partition, which permitted me to keep all my data, configurations and some applications.

Also I noticed that Ubuntu11 already looks for existing home partitions during installation process, what is a really nice feature. 

Thanks for the help.

---

