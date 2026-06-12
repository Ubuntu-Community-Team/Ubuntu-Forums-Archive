---
title: "/home directories not being created"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by static0verdrive on 2010-01-23
Heya guys,

Hopefully someone can lend a quick hand here. The problem is when a user logs into my Ubuntu x64 Server 9.10, their home directory doesn't get created.

Here's some background FYI:

Bought new RAM and right after popping it in, my previous ssh/samba "server" on 32-bit kubuntu-desktop 8.04 stopped working. Like a moron I never suspected the new RAM despite the timing, because it would boot part of the way before dropping to command line with errors (and I've never had bad RAM before, lucky me I guess). 

It took a few tries for the copying to work, but I managed to save my /etc/passwd, /etc/shadow, and a few mp3's I wanted. Tried to reinstall the OS using x64 9.10 (kubuntu-desktop, ubuntu server, you name it) but the discs were always failing the integrity check. Wasted about 10 blank discs before realizing I should try it in VirtualBox on my other PC, in which the discs passed the check. Thinking the issue was the DVD-ROM drive I swapped them and still had the same problem. Scouring the internet I came across a post regarding the same Debootstrap warnings and failed integrity checks that ended with "my problem turned out to be bad RAM" and THEN it hit me - the timing of the weird problems was too good to be a coincidence...

So in the end I wouldn't have had to format - I could have removed the new RAM and all would have been fine; however, on the plus side I'm now running Ubuntu x64 Server 9.10 with LVM and loving it.

I restored the /etc/passwd and /etc/shadow files, but now when a user logs in they get "Could not chdir to home directory /home/username: No such file or directory" and they're left in /

I presume there's a flag that tells the system the user had already logged in in the past so it doesn't bother creating it, but I couldn't find it. Any ideas how I can retain their login and password but fix it so it will create their home directory upon first login?

Sorry for the long post - I'm hoping someone finds this useful if they bump into the same issue. Any help would be greatly appreciated!

---

### Post by static0verdrive on 2010-01-23
<bump>

---

### Post by arubislander on 2010-01-23
I have zero experience with samba and such.. but my experience with Linux is that the user's home directory is created at the same time the user is created, never at log on. So it would seem to me that all you would have to do is create empty home directories for all the users in your /etc/passwd file and all should be well.

Don't forget to chown them to the right user.

---

### Post by static0verdrive on 2010-01-24
Thanks for your reply. Sorry I should have been more clear - Samba is only configured for one /public folder not for the /home directories... I was hoping to avoid manually creating and chown'ing 50 directories, but if I have to then here's where a little perl magic may be nice!

---

