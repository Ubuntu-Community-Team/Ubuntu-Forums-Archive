---
title: "how to get wine1.4 installed in 14.04/mint17?"
date: 2014-05-18
forum: MINT
---

### Post by Baldrick_NZ on 2014-05-18
Everytime I try to install wine 1.4 into Mint17, 1.6 wants to be installed as well. Unfortunately, 1.6 crashes my app whereas 1.4 runs smoothly. 

How can I install 1.4 only?

Thanks in advance...

---

### Post by Elfy on 2014-05-18
*Thread moved to **Other OS/Distro Support**.*

---

### Post by keithcleaver2010 on 2014-05-18
Just checked the wine site, and 1.4 is available from their PPA. Head to your terminal, and add the PPA manually: ```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```

Then update your APT package information by ```
sudo apt-get update
```

You should then be able to install 1.4 with the following command in the Terminal: ```
sudo apt-get install wine1.4
```

Let me know if that works.

---

### Post by Tadaen_Sylvermane on 2014-05-19
Run wine through playonlinux. Then you can use any version of wine you want with zero difficulty. I love the command line but sometimes a GUI makes things 9000% easier and this is one of those times.

---

### Post by HiImTye on 2014-05-21
playonlinux is by far the easiest way to customize your wine sandboxes

---

### Post by Baldrick_NZ on 2014-05-24
Thanks for that guys!

PlayOnLinux did the trick!

---

