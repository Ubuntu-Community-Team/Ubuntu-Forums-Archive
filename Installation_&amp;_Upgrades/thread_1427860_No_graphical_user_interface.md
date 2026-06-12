---
title: "No graphical user interface"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by hbchrist1 on 2010-03-12
Hi,

I have ubuntu running as the only operating system on two computers, and thought it would be a fine idea to install it side-by-side with Windows 7 on my wife's new Sony Vaio laptop as well. This laptop actually has both windows 7 and some stunted version of vista installed by default, vista is accessible by pressing a "web" button instead of starting up the computer. This loads up vista with only a browser window available. 

Anyway, I tried ubuntu first on this computer by booting up a live cd, and all went well. I then installed using the wizard with everything set to default. There were no error messages.

When I start the computer, I get a choice of operating systems. If I choose ubuntu, it starts by showing the fancy fade-in-fade-out ubuntu logo, followed by a terminal login screen. If I do login using that login screen, all I get is a terminal prompt. There is no terminal window - the terminal covers the whole screen. 

So I have two questions: 
- What might be wrong and how could it be fixed?
- In a worst case scenario, is it possible to remove ubuntu and rezise the windows partition to cover the whole harddisk? I vaguely recall a warning to the contrary in the installation wizard. 

Thanks in advance!

---

### Post by Dayofswords on 2010-03-12
(i'm anoob, but i've seen a similar thing to get graphics to work)
start up and login in again,
then type ```
sudo startx
```
idk if sudo is required

you should see the login menu or desktop, not sure

---

### Post by hbchrist1 on 2010-03-12
I forgot to mention that I installed ubuntu version 9.10.

---

### Post by hbchrist1 on 2010-03-12
Apparently, sufficiently many others have had the same problem that there is a [sticky thread]("http://ubuntuforums.org/showthread.php?t=1305459") about it - the thread description was just not informative to me, hence I didn't find it before posting.

---

