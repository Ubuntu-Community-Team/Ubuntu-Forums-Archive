---
title: "Ubuntu Won't update-says packages broken, but won't fix"
date: 2019-03-24
forum: Installation &amp; Upgrades
---

### Post by jwjones1979 on 2019-03-24
I typed sudo apt upgrade and got this:
[https://paste.ubuntu.com/p/Gjcz8hQkTw/](https://paste.ubuntu.com/p/Gjcz8hQkTw/)

Then I typed sudo apt --fix-broken install and got this:
[https://paste.ubuntu.com/p/YvyC9xpFcG/](https://paste.ubuntu.com/p/YvyC9xpFcG/)

what did I do wrong and how do I fix it?

---

### Post by again? on 2019-03-24
Post the output of...
```
lsb_release -a
```
and
```
sudo apt update
```

Have you installed or removed anything recently?

---

### Post by jwjones1979 on 2019-03-25
No, I just routinely update when I can.

lsb_release -a:
[https://paste.ubuntu.com/p/ChR8CXBgXb/](https://paste.ubuntu.com/p/ChR8CXBgXb/)
sudo apt update:
[https://paste.ubuntu.com/p/CgWtw3mXCv/](https://paste.ubuntu.com/p/CgWtw3mXCv/)

---

### Post by again? on 2019-03-25
Not sure what the exact error is.
The klaus-vormweg/bluefish ppa doesn't have a package for cosmic so that can be disabled.

Try disabling all third party repositories...
```
software-properties-gtk --open-tab 1
```
 and then...
```

sudo apt clean
sudo apt update
```

Still errors, try renewing your package lists...
```
sudo rm -r /var/lib/apt/lists/
sudo apt update
```

---

### Post by jwjones1979 on 2019-03-26
I did both of those, and this is what I got:

[https://paste.ubuntu.com/p/z9sRnzwdqB/](https://paste.ubuntu.com/p/z9sRnzwdqB/)

And how do you get that code box?

---

### Post by deadflowr on 2019-03-26
> And how do you get that code box?
[https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by Impavidus on 2019-03-26
You can get the code box by using [noparse]```
code tags
```[/noparse].

apt reports a lot of missing dependencies. apt even reports that apt is missing. I don't believe those packages are really missing. Many of those are essential, without which you wouldn't have a functional system. So, the database of installed packages is really messed up. Furthermore, you get input/output errors when apt tries to read the list of installed software, which indicates a filesystem problem. A filesystem check may help, but I wouldn't trust the list of installed packages even after you try to fix the filesystem. A filesystem check makes the filesystem consistent, but may not restore every file to the state that it's supposed to be in.

In fact, I don't trust your hard drive.

Boot from a live disk and make sure you have current backups of all your important files on an external drive. You're supposed to have such backups anyway, but check again. Run filesystem checks and check the health of your hard drive. If the filesystem check doesn't fix your problem (which I doubt it will), reinstall (or restore your entire system from a backup, if you have one). If the hard drive doesn't look healthy, get a new hard drive and reinstall.

[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by again? on 2019-03-26
Can you also post the ouptut from...
```
ls -al /var/lib/apt/lists/*
```

---

### Post by jwjones1979 on 2019-03-27
[**[COLOR=#000000]Impavidus[/COLOR]**]("https://ubuntuforums.org/member.php?u=1417721")

If all else fails, that's exactly what I'll do. Let's hope it doesn't come to that.

 	[**[COLOR=#000000]guber2[/COLOR]**]("https://ubuntuforums.org/member.php?u=2063040") 	 

[https://paste.ubuntu.com/p/ZKQxWvtdDr/](https://paste.ubuntu.com/p/ZKQxWvtdDr/)

---

