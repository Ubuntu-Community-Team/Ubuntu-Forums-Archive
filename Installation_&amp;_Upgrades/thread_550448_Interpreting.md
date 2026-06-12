---
title: "Interpreting"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by celtic426 on 2007-09-13
Need some help interpreting what exactly to do with this.  I have been having problems using Ubuntu (with wubi) with my HP laptop (nvidia drivers).  Ubuntu loads, but then the screen goes totally blank and I think it is resorting to the CRT which I don't want.  I found this site where this problem was fixed but I'm not sure how to do what the solution is.

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109414]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109414")

One of them says: "Does adding
Option "UseDisplayDevice" "DFP"
to the Screen section of /etc/X11/xorg.conf make any difference when you are using nvidia-glx?"

And then they responded that that worked.  I can get to some sort of menu thing when I press ctrl alt f I believe.  I also can alter the boot string.So can someone help me out with what that means and how I do that?  How do I get there and how do where do I add it? 

Please and thank you,

Tim

---

### Post by avik on 2007-09-13
Press Ctrl-Alt-F1, and log in.  Type:

```

sudo cp /etc/X11/xorg.org /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.org

```

Type in the mentioned code in the correct place.  Press Control-x, then y and enter.  Finally, type in:

```
sudo /etc/init.d/gdm restart
```

That should do it.

---

### Post by Pumalite on 2007-09-13
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
gksudo gedit /etc/X11/xorg.conf

---

### Post by avik on 2007-09-13
> **Pumalite said:**
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
gksudo gedit /etc/X11/xorg.conf

Oh yeah.  I'm so used to using the command line whenever I do anything related to Xorg, I forgot about this. :)

---

### Post by Pumalite on 2007-09-13
He ask to interpret; nothing more. I'm glad you helped him so completely.

---

### Post by celtic426 on 2007-09-14
Thanks for your responses guys.  I must be doing something wrong tho cause every time I try to type those I get command not found or directory doesn't exist and once I got a GTK warning that cannot open display.  

I am supposed to be typing those things after "tim@vanm-213:~$" right?

Am I supposed to be putting a / before sudo?

I tried for like 10 minutes all different combos of stuff but nothing worked.  And actually after giving up on that I tried to boot into Vista again and it gave me an operating system error.  I had to use HP's system recovery option and use the check disk function which repaired some files which is kinda scary...

So unless someone can tell me defintly something I'm doing wrong I've pretty much given up especailly now that I almost lost my whole C drive.

Thanks

---

### Post by Pumalite on 2007-09-14
Copy and paste the command and the output in your post.

---

