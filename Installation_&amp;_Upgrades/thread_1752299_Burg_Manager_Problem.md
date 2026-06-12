---
title: "Burg Manager Problem"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by Bobscrachy on 2011-05-07
I tried to install it, but while I was installing it I didn't hit the spacebar when selecting my grub boot hard drive. I've tried uninstalling burg and reinstalling it to see if I can get the same prompt, but no joy. Does anyone know how I can fix this?

---

### Post by colmeweb on 2011-05-07
Read the comments to this video

[http://www.youtube.com/watch?v=S_eT1OopS6U](http://www.youtube.com/watch?v=S_eT1OopS6U)

About half way down the full comments list the video maker gives some terminal commands that worked for me.

I made the same mistake, good luck buddy.

---

### Post by Bobscrachy on 2011-05-21
Thank you. Complete burg uninstall and reinstall. Pasting the solution here for other people. 

```
1- remove previous version :

sudo apt-get purge burg-manager

sudo rm -rf ~/.burg-manager

sudo rm -rf&#65279; /root/.burg-manager

2- Then reinstall it:

sudo dpkg -i burg-manager*

Or if you have the ppa installed use this command to reinstall it :

sudo apt-get update && sudo apt-get install burg-manager
```

---

