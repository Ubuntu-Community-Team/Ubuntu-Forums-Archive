---
title: "Trouble With Installing Packages"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by chughes27 on 2012-02-05
So, I've been trying to install a few apps, and when I try to install them I get an error saying "Please insert the Ubuntu 11.10 Oneiric Ocelot cd" or something along those lines. So pretty much I can't install them without a CD, which I do not have and I cannot burn one. I've never had this issue before and I would love for it to go away.

---

### Post by mikewhatever on 2012-02-05
In the Software Center, click Edit->Repositories, and uncheck the CDROM box.

---

### Post by chughes27 on 2012-02-05
Thanks!! That was really helpful!

---

### Post by Bucky Ball on 2012-02-05
If it solved your problem please mark thread as 'Solved' from Thread Tools to help others. ;)

---

### Post by chughes27 on 2012-02-05
Not solved anymore.

Now, when I try to install something, it just sits there and loads and says "waiting for apt-get to close". How do I fix this??

---

### Post by Old_Grey_Wolf on 2012-02-05
I have never had that problem. However, after a reboot try these commands
```
sudo apt-get update
sudo apt-get upgrade
```

If that doesn't work then maybe the errors from those command will give someone an idea for fixing the problem.

---

### Post by chughes27 on 2012-02-05
Just used the update and upgrade commands, everything seems to be working fine now. Thanks!

---

### Post by Old_Grey_Wolf on 2012-02-05
Please mark thread as solved

If you do not know how to do that, near the top of the webpage (scroll up) there is a menu "Thread Tools". Select "Mark this thread as solved". It lets other people searching the forums know that this had a working solution and they don't need to provide additional help.

Thank you.

---

### Post by chughes27 on 2012-02-05
Done!

---

