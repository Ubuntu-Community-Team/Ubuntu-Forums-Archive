---
title: "Incomplete upgrade 9.10 -&gt; 10.4"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by johnsd on 2010-07-14
Hi

I have just upgraded from 9.10 to 10.4 on line. I went out and left the PC to the job - when I returned the screen was locked on 4 minutes of installation to go then the cleanup phase. No action could be coached out of it - so I rebooted and all seems to be fine. I manually restarted the install from the CLI and now hopefully all the upgrades have been installed. However the cleanup phase has not happened.

So my question is - is it safe to use the Computer Janitor to do a cleanup under these conditions?

Thanks
John

---

### Post by hansdown on 2010-07-14
Hi johnsd.

Please hold off on using the janitor, for now.

Is your system working?

Are there any problems, that need to be fixed?

I ask you to wait, before using the janitor, because it has a problem, with removing key components, that may make your system unusable.

---

### Post by johnsd on 2010-07-14
Everything does seem to be OK - but I will hold off using the Janitor.

---

### Post by DougieFresh4U on 2010-07-14
This should tidy things up:
[B]```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get autoclean
```[/B]

---

### Post by hansdown on 2010-07-14
Post back, if you do have any trouble johnsd.

It could just be one of those strange things that happens with installs.

I'm crossing my fingers.

DougieFresh4U has some good tips.

---

### Post by johnsd on 2010-07-14
> **DougieFresh4U said:**
> 
sudo dpkg --configure -a

Thanks - had already done the line above which seems to have installed the outstanding packages. So have now done the autoclean too - there is about 94 packages in the Janitor but I think I will just leave them in the meantime.

Thanks
John

---

### Post by DougieFresh4U on 2010-07-15
Please do not use **Computer Janitor**

---

