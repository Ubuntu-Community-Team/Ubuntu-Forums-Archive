---
title: "Installing in low graphic mode?"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by faceless-21 on 2010-01-20
I had a problem with Virtual Box and so I tried to do an update and part way through my internet connection failed and after I rebooted it says that it must go into a low graphic mode(console mode) and I can not seem to fix it...  I am not real sure how to fix it but figured if I could somehow revert back to previous graphics settings or drivers that would fix it but I cant figure out how to do that...  Any ideas what to do?

  Thanks for any help!

---

### Post by faceless-21 on 2010-01-21
Bump???

---

### Post by HugoSerrano on 2010-01-21
Hi.

Can you access the console? What graphical card you got?

---

### Post by faceless-21 on 2010-01-21
Yes I am able to log into a console, I have the Nvidia 6800go.

---

### Post by deadalus.globalnode on 2010-01-21
You could try repairing the packages. Reboot and when it asks whether you want to start ubuntu generic or ubuntu with recovery choose recovery mode. It should boot into a screen that will give you the option of repairing with dpkg along with some other options. Choose repair. After it has finished reboot.

---

### Post by faceless-21 on 2010-01-21
Hey deadalus I think I tried that but it needed me to be online and I have wireless only at the moment...  Should it beable to recover from the CD?

---

### Post by deadalus.globalnode on 2010-01-21
I don't think so. It sounds like what happened is the dependencies for your updates got broken due to the loss of Internet. You need to get the same version of whatever is broken for it to repair. I think that there is a way to remove the broken packages but I would have to look it up.

Edit:
You could try
sudo aptitude -f remove
but I suggest you read this first
- [http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)

---

