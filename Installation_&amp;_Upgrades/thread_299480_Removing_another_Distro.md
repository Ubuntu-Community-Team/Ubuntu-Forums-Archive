---
title: "Removing another Distro"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by clucas on 2006-11-14
Installed Kubuntu 6.10 without any problems. Previously on my PC I had Suse 6.2 Beta 2. I thought that during the installation of 6.1 I would be asked if I wanted to delete Suse or leave it alone. I guess I was wrong. When the PC boots up, one of the options is to load Suse. How can I now get rid of Suse and free up some disk space?

---

### Post by Bachstelze on 2006-11-14
How is your drive partitioned ?

---

### Post by taurus on 2006-11-14
Applications -> Accessories -> Terminal

```
df -h
sudo fdisk -l
```

---

### Post by clucas on 2006-11-14
Love the quick responses! Unfortunatly I am at work so I cannot provide the requested info. I will reply as soon as I get home to check it out. I'd be guessing at this point.

---

### Post by clucas on 2006-11-15
I'm going to have to create another thread because I have new questions now. What I did was since I have 2 hard drives (both NTFS) I decided to move what was on the second to the first. I then went and installed 6.10 into the second drive. I had to "fixmbr" first and then did the install. It worked fine but as I said, I have other questions now.

---

### Post by taurus on 2006-11-15
Go ahead and start a new thread for your other questions.

---

