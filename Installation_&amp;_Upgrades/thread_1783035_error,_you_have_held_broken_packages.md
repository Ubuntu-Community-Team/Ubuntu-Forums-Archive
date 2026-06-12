---
title: "error, you have held broken packages"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by 28s on 2011-06-15
Hello,
I am using ubuntu 8.04LTS Hardy Heron.
I sometimes play runescape, but havn't played it for a while; though I recently started trying to play again. I found that I needed to install the new icedtea plugin in order to play, but when I try I get an error message saying something along the lines of:
E: error, you have held broken packages. And I cannot therefore install it and play runescape. I have also checked, and cannot find any broken packages, so I am confused. 
Any help would be much appreciated, thank-you.

---

### Post by oldos2er on 2011-06-15
Run ```
sudo apt-get install -f
``` or in Synaptic, Edit, Fix broken packages.

---

### Post by 28s on 2011-06-15
Thank-you so much for replying. 

I have tried both of your suggestions, and have now tried to install java runtime environment 1.6, but it says not available? 

any help would be appreciated. Thank-you

---

### Post by oldos2er on 2011-06-15
Have you enabled the partner repository? That's where sun-java6-jre is, along with the other sun-java6-* packages. openjdk-6-jre is in main, so if that's the version you want, run ```
sudo apt-get update && sudo apt-get install openjdk-6-jre
```

---

### Post by 28s on 2011-06-15
Thank-you for replying, I tried this and it partly worked but partly didn't, as some of the files didn't install, and so old files were used it said.

---

### Post by oldos2er on 2011-06-15
Can you post the output from the command?

---

