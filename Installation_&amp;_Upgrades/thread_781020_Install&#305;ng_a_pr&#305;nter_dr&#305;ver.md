---
title: "Install&#305;ng a pr&#305;nter dr&#305;ver"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by R2D2! on 2008-05-03
H&#305;, I'm new to Ubuntu, so &#305;t may be a bas&#305;c quest&#305;on.

I've just downloaded a dr&#305;ver for Phaser 7760.

I read the “readme” and says:
> run setup within the install directory as root to install the driver.


What does that mean?

—[COLOR="Silver"]R2D2![/COLOR] **Ilhu&#305;témoc**

---

### Post by Partyboi2 on 2008-05-03
enter the directory of the file you downloaded. So if I downloaded a file called abc to my desktop I would need to enter the directory by 
```
cd Desktop/abc
```then type
```
sudo -s
``` to run as root for that terminal session. (After installing return to normal user)
or if you are wanting root privileges for just a few commands you can type sudo before the terminal command to gain root privileges.

You can find out more about sudo by typing 
```
 man sudo
```
or 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Patb on 2008-05-03
> run setup within the install directory as root to install the driver.
What does that mean?

It means you should start a terminal and go to the directory where Phaser is installed.  Most likely that directory is the very directory where the readme file is so check the path to that. Then, in a terminal type:
```
cd </full/path/to/readme/>
```
Then check whether the setup file is present 
```
ls ./setup*
```
If the output includes "setup" or "setup.sh" you are probably in the correct directory.  Then, still in that directory, run setup as root (sudo) to install the driver:
```
sudo ./setup
```
That should work.  If you get lost, post more details. 

Cheers, Pat.

---

### Post by R2D2! on 2008-05-04
Thank you for your help

—[COLOR="Silver"]R2D2![/COLOR] **Ilhu&#305;témoc**

---

