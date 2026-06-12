---
title: "Disk encryption not working"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by krzz on 2009-11-28
Hi,

I just downloaded 9.10 and decided to try the "require my password to login and to decrypt my home folder" but it didn't work.

All of my partitions are ext2 (one for /, other for /home/user1, other for /home/user2).

I'm assuming that it didn't work because I'm not being asked to "record my encryption catchphrase" after restart (as seen here for example [http://www.linux-mag.com/id/7568/2/](http://www.linux-mag.com/id/7568/2/)). And I can see the contents of /home/user2 when logged in as user1, and vice-versa.

Any ideas?

---

### Post by mt1234 on 2009-11-28
[http://ubuntuforums.org/showthread.php?t=1312672&nojs=1#usercptools](http://ubuntuforums.org/showthread.php?t=1312672&nojs=1#usercptools)

This may help. Take a look at entry #3. It may be that that plug in needs to be installed for any type of encryption. Good luck!

---

### Post by krzz on 2009-11-28
Thanks, I tried that (in my already installed ubuntu) but it didn't work. Should I reinstall Ubuntu instead?

Is that the program that is used for this kind of real-time home encryption?

---

### Post by shaggy999 on 2009-11-28
When you use home folder encryption it uses your login password that you type in when you log into your account and transparently maps the encrypted files to your /home/user folder. Do this:

Open up your terminal which should start out in your home folder. Type this:

```
df -h .
```

The '.' is important. Post the output.

---

### Post by krzz on 2009-11-28
I could solve it. I'm not entirely sure what the problem was, but I know the following:

- asking for mount told me that such partition wasn't being encrypted, now I can see that it's encrypted if I do "mount"

- I stopped using ext2 and started using ext4

- I was using three partitions /, /home/user1, /home/user2; now I did this instead: a partition for /, a partition for /home, and the third partition for /media/data... I think this was most likely the solution to the problem

Thanks!

---

