---
title: "Ubuntu 10.04 freeze after a couple of minutes"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by jawaka. on 2010-08-26
Hello,

I've just installed Ubuntu 10.04 on a AMD processor with a nvidia graphic card in dual boot with windows xp.
First the live-cd was already freezing after a couple of minutes so I had to install Ubuntu with the alternate cd.
Now it freezes whatever I do after 2 or 3 minutes.
I had exactly the same problem with the 6.04 version but I had only to remove powernowd from /etc/init.d/ to make it perfectly working. But unfortunately this file seems not to be there in this version.

Thank you in advance for any help : )

---

### Post by jawaka. on 2010-08-27
Fresh news : in recovery mode (failsafe X) it doesn't freeze. So maybe it's a driver problem ?

---

### Post by sugam on 2010-08-27
jawaka: I'm having the exact the problem. Ubuntu suddenly freezes without warning shortly after booting. I have a few seconds to mess around then poof! If I run it in low graphics mode everything works fine.

Here is a link to my thread. Not too much headway, but at least it's something: [http://ubuntuforums.org/showthread.php?t=1561614](http://ubuntuforums.org/showthread.php?t=1561614)

I've been unsure about installing proprietary drivers, but EnvyNG doesn't seem too bad.

---

### Post by sugam on 2010-08-27
I fixed my problems by disabling KMS (Kernel Mode Setting). To try it do the following:

```
gksu gedit /etc/modprobe.d/nouveau-kms.conf
```

Now copy/paste this. Save & Reboot.
```
options nouveau modeset=0
```

---

### Post by jawaka. on 2010-08-28
Thank you ! it works ! :D

---

