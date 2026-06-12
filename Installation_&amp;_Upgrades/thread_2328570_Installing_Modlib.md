---
title: "Installing Modlib"
date: 2016-06-22
forum: Installation &amp; Upgrades
---

### Post by ksd2 on 2016-06-22
Hi.
Can some one please tell me how to install the Modlib package in ubuntu 15.10 ? I am new to Ubuntu.
I have a tar file (for deb file) and extracted it on my desktop. But what next ? 

Thanks in advance.

---

### Post by ajgreeny on 2016-06-22
What do you mean by "I have a tar file (for deb file)"?

Did the tar archive extract to a .deb file?  If so, you can double click on that, and it should install with software-centre, (or gdebi if you've installed that).

If it is a tar archive containing a lot of different files and folders look for a **readme** or **install** file and see what that contains.

---

### Post by ksd2 on 2016-06-23
Hey ajgreeny
Thanks for the reply. So I went into the folder and opened the README file. Attaching a screenshot. I am totally a noob and did not understand what I am supposed to do. Can you help me with this ? Just explain me what this means.
[ATTACH=CONFIG]269731[/ATTACH]

---

### Post by ajgreeny on 2016-06-23
So this is a source archive which means the many files you see have to be configured and built into a package and then installed by running the commands shown in that README file.

I have never yet had a reason to do this even in my 11 years of using Ubuntu so I am not the best person to try and help, but there are some packages you will need to install before trying any further which you can get by running ```
sudo apt-get install build-essentials
```
Now in terminal navigate to the folder that you extracted from that archive and run the commands as shown in the README file except that you will need to run **./configure** as user, then **sudo make install** as root, hence the sudo prefix.

Try that, then come back again if you can not get it to work and I'm sure someone will be more able to assist than I am.

---

### Post by ksd2 on 2016-06-24
I did and it did install. I checked for dependencies and it shows all okay. But when I configure the file, it says Fatal error and says modbus.h - no such file or directory.
I consulted a friend of mine and he suggests I might not have some packages related to Python which prevents gcc from accessing the library. But what package, he does not know.

---

### Post by steeldriver on 2016-06-24
What "Modlib package" did you download exactly, and from where?

---

### Post by ajgreeny on 2016-06-24
> **steeldriver said:**
> What "Modlib package" did you download exactly, and from where?

Good point!!

I should have asked, but did not think about it at the time.

---

