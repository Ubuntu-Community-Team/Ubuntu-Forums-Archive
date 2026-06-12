---
title: "installing tar.gz files"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by rballard on 2008-09-18
whenever i run ./configure to install a tar.gz file I get compiler could not create some executible files. And then the make command won't work after that. am i doing something wrong?

---

### Post by Pumalite on 2008-09-18
Do you have build-essential installed?
sudo apt-get install build-essential

---

### Post by rballard on 2008-09-19
ok the ./configure worked now it says

randy@Home-Ubuntu:~/Desktop/Documents/genecys-0.2$ make install
Making install in common
make[1]: Entering directory `/home/randy/Desktop/Documents/genecys-0.2/common'
make[1]: *** No rule to make target `install'.  Stop.
make[1]: Leaving directory `/home/randy/Desktop/Documents/genecys-0.2/common'
make: *** [install-recursive] Error 1

---

### Post by Pumalite on 2008-09-19
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Partyboi2 on 2008-09-19
> **Pumalite said:**
> [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
Monkeyblog seems to no longer be there.

---

### Post by Pumalite on 2008-09-19
Thank you.

---

### Post by Pumalite on 2008-09-19
[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

---

### Post by Partyboi2 on 2008-09-19
> **rballard said:**
> ok the ./configure worked now it says

randy@Home-Ubuntu:~/Desktop/Documents/genecys-0.2$ make install
Making install in common
make[1]: Entering directory `/home/randy/Desktop/Documents/genecys-0.2/common'
make[1]: *** No rule to make target `install'.  Stop.
make[1]: Leaving directory `/home/randy/Desktop/Documents/genecys-0.2/common'
make: *** [install-recursive] Error 1
When you ran ./configure did you get any errors?

---

### Post by rballard on 2008-09-19
No the./configure went through just fine.

---

### Post by Pumalite on 2008-09-19
Maybe this helps you:
[http://www.linuxforums.org/forum/suse-linux-help/50107-how-install-tar-gz-files.html](http://www.linuxforums.org/forum/suse-linux-help/50107-how-install-tar-gz-files.html)
[http://ubuntuforums.org/showthread.php?t=768148](http://ubuntuforums.org/showthread.php?t=768148)

---

### Post by Shazaam on 2008-09-19
```
sudo make install
```
should work.

---

