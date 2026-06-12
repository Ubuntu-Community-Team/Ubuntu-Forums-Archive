---
title: "Installing Java, Generic Problem?"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by thomasthefinch on 2009-12-26
Morning.

After losing my Ubuntu virginity yesterday, and spending some time in these great forums getting my wireless to work, I have stumbled upon my second problem!

I downloaded Java (to play runescape... laugh at me, I know) and began to follow the installation instructions on the website. The first command is type su and hit enter.

Obviously (even I know with my limited knowledge of ubuntu) this requires you enter your password.  I enterted my password, and it says authentication failed.  Every time.  I've tried copying and pasting my password from a document and all sorts, but it still won't work.

Am I mistaking the password I use when I install anything else for another password that I should have set?

Thanks

Thomas

---

### Post by mprice on 2009-12-26
Try installing java this way it should work.

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by ajgreeny on 2009-12-26
You need ```
sudo command
``` to do things with root privileges in ubuntu, where command is the command you want to run, don't actually type "command".

Have a look at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for all the info you need.

---

