---
title: "Reinstall 2.6.12-9 kernel"
date: 2006-05-07
forum: Installation &amp; Upgrades
---

### Post by bforbes on 2006-05-07
I installed Kubuntu 5.10, and in an attempt to install some sound drivers, I totally buggered the sound up, so now I don't have any at all. I would like to revert to the way it was when I installed Kubuntu, but I dont want to lose all my other settings. How do I reinstall the kernel that came with the CD? I've tried using apt-get remove kernel-image-2.6.12-9-amd64 and other commands like that, but it just says "Package not found". Can anyone help me?

---

### Post by confused57 on 2006-05-07
You could try entering the Grub menu when your computer is booting up by pressing "Esc" when prompted.  See if your old kernel is listed & if so, press "down arrow" to highlight it, press enter and your system will boot up into the old kernel.  If it's there, you can edit the default kernel that your computer boots to in your Grub menu.lst.  That way, you'll still have the newer kernel available, but your system will boot into the old one by default.

Sorry, didn't read your post closely enough...assumed you'd just installed a newer kernel.  Ignore what I wrote....

---

### Post by Sutekh on 2006-05-07
You should be trying ```
sudo apt-get *install* **linux**-image-2.6.12-9-amd64**-k8**
```

---

### Post by bforbes on 2006-05-08
Thanks, that worked.

---

