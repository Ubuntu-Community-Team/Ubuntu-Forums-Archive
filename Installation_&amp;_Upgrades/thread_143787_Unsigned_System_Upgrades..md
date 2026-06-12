---
title: "Unsigned System Upgrades."
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by GarethMB on 2006-03-13
Are these safe to install?

---

### Post by kaamos on 2006-03-13
Yes, and they are pretty important updates as well.

---

### Post by GarethMB on 2006-03-13
I can't install the base config update. Upddate manager just turns grey and does nothing. Do i have to remove the old base config manually or is this a bug?

---

### Post by kaamos on 2006-03-13
Close the update manager windows, open Applicatios->Accessories->Terminal and
```
sudo apt-get update
sudo apt-get upgrade
```

Hope that helps.

---

### Post by Klaidas on 2006-03-13
These are VERY important security updates
More info here: [http://ubuntuforums.org/showthread.php?t=143622](http://ubuntuforums.org/showthread.php?t=143622)

---

### Post by GarethMB on 2006-03-13
Thanks, i've installed them now. I was just cautious because unsigned security updates seemed strange.

Why did using sudo apt-get update/ upgrade make it work?

(I'm a newbie, incase you couldn't tell.)

---

### Post by bjweeks on 2006-03-13
[QUOTE=GarethMB]Thanks, i've installed them now. I was just cautious because unsigned security updates seemed strange.

Why did using sudo apt-get update/ upgrade make it work?

(I'm a newbie, incase you couldn't tell.)[/QUOTE]

The update notifier is not perfect yet.

---

### Post by nocturn on 2006-03-13
Yes, but they should be signed.

Try this to be sure:

1. backup your /etc/apt/sources.list file and replace with an empty file
2. apt-get update (or reload in synaptic)
3. Copy backup sources.list file back
4. apt-get update (or reload) again

This should show the packages as signed.

---

