---
title: "broken packages being hold"
date: 2013-06-25
forum: Installation &amp; Upgrades
---

### Post by rogerdv on 2013-06-25
I have just installed 13.04 today, and proceeded to update apt cache. When finished, it displayed some error related to amd-sometring.gz and stated that some repo could not be updated. I considered this unimportant as I plan to use catalyst 13.6 beta, and continued to install the relevant stuff I require. When I tried to install mc, I got an error saying that mc requires, mc-data, which can not be installed, and also mentions perl. Same for smplayer, audacious, etc. Many packages report the same problem and says that Im holding broken packages. Installed synaptic and checked if I had broken packages, but it doens list any. Any idea about how to solve this?

---

### Post by gifford on 2013-06-25
Try using synaptic to fix broken packages. It doesn't list them so under edit, click fix broken packages.

---

### Post by rogerdv on 2013-06-26
Already did that, didnt worked. As I said, synaptic doesnt list any package as broken.

---

### Post by Frogs Hair on 2013-06-26
Close all package management tools, run  the following terminal command, and copy and paste the output in code tags using # symbol in the reply box tools. There is usually instructions for further commands in the output or information to indicate the cause of the problem.```
 sudo apt-get update   
```

---

