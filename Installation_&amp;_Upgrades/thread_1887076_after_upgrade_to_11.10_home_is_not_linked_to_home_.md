---
title: "after upgrade to 11.10 home is not linked to /home anymore"
date: 2011-11-26
forum: Installation &amp; Upgrades
---

### Post by zaatlob on 2011-11-26
I did a upgrade from 10.04 to 11.10. First time i did it manual, but had some flows. I did the partion manual, because i have a seperate home partition. 
Because of the problems with the instalation i decided to install 11.10 again. I did this with the options install over 11.10.
This time it created a new home partition. Is it possible to redirect the home to the old home partition?

---

### Post by BC59 on 2011-11-26
Well one solution would be using Ubuntu Tweak. 

```
sudo add-apt-repository ppa:tualatrix/next
sudo apt-get update
sudo apt-get install ubuntu-tweak-0
```

(with the command -0 you will install the previous version, because the last is not yet full working)

From ubuntu-tweak now you can scroll down and find the button to change default folders.

---

### Post by zaatlob on 2011-11-26
Thanks for the suggestion, but when i look at i still loose all my settings.
I want to tell ubuntu that home is the home partition and not the part that's left over on the root.
Is it possible to merge the free part of the root with my old home.
Or is it far more simple to reinstall 11.10.

---

### Post by ajgreeny on 2011-11-26
It might be simpler to reinstall, but you can try editing your /etc/fstab file first by adding lines in the format
```
# /home was on /dev/sda2 during installation
UUID=e2554df2-7e16-4864-97c9-834d8bebecda /home           ext4    defaults        0       2
``` for which you will need to know your /home partition UUID from the command ```
sudo blkid -c /dev/null
``` After the edit you can try running command ```
sudo mount -a
``` and you may find all your old /home is now in place.

It is possible that ubuntu-tweak can do this for you automatically, but I have never seen it, so am uncertain about that.

---

