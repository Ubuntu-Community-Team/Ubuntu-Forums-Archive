---
title: "Booting multiple linux OS..."
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by eggchess on 2008-05-06
OK, I want to compare PCLinux and Ubuntu, so I came up with the idea of dual booting these two OSs. ( I know, I'm nuts) My question is, will I need two swap partitions, two /(root) partitions and two /home partitions, or what? I can imagine that either Linux OS would use the same swap and maybe even the same /home. I can also imagine that only one could use /. So, where does the other root go? HELP!

---

### Post by macaholic on 2008-05-06
Yes, in theory they could share a home directory, the way I know how to do it is through /etc/fstab/. They cannot however share a / as you said, you would need to partition your hard drive during isntallation.

---

### Post by lswb on 2008-05-06
It's not too difficult to run 2 or more versions of linux or other operating systems on the same computer. I have been running dapper for some time on my laptop and recently installed hardy on a separate partition. I have windows XP also, but about the only time I boot that up is to run income tax software. The different versions of linux can all share the same swap partition. Whichever version is currently booted will have its own /, i.e. the "root" of the partition it is installed in. 

Many people do share /home among different installed distributions, but it can be problematic because of the . configuration files that are in your home directory. (Don't confuse the /home _partition_ with your /home/username directory) I have a /home in each distribution. I keep music files, pictures, etc, in diectories on the windows partition and make symlinks to them as needed. There are pros and cons and lots of ramifications to whichever way it is done.

If you google for "grub multiple linux boot" or similar you will find some good information. One of the best sites I have seen is 

    [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by JawsThemeSwimming428 on 2008-05-06
I'm no expert on the subject, but I would be a little worried about doing that. Different OS's save things in different spots and use different configurations. Sharing /home directories between similar distros is safe(r) but I don't know if I would want to try that.

---

