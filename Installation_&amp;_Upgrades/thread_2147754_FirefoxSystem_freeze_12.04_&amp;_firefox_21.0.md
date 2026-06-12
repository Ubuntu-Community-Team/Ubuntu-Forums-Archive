---
title: "Firefox/System freeze 12.04 &amp; firefox 21.0"
date: 2013-05-23
forum: Installation &amp; Upgrades
---

### Post by xigen on 2013-05-23
Firefox 21.0 & Ubuntu 12.04.2 LTS (precise) 

I installed system upgrades - and now when I try to use FF for downloads (uploaded.com) they system freezes.

First - I suspected dust in the graphics card, so I cleaned the system.  Unfortunately, it did not solve my issues with Firefox.

Suggestions?

---

### Post by xigen on 2013-05-23
I have reinstalled Firefox.   This worked for a few (18+) hrs.    Then my system froze again.

Any suggestions as how to figure out what is causing the freeze?

---

### Post by xigen on 2013-05-29
I found a suggestion to upgrade the kernel.    

[http://partiallysanedeveloper.blogspot.co.uk/2012/05/ivy-bridge-hd4000-linux-freeze.html?m=1](http://partiallysanedeveloper.blogspot.co.uk/2012/05/ivy-bridge-hd4000-linux-freeze.html?m=1)

At the time of writing this article the latest stable kernel is 3.3.6

The kernel can be found at kernel.ubuntu.com or you can just ignore this and copy and past the commands below to the terminal depending on you installation

For Ubuntu (i386 / 32-bit) run these commands

 cd /tmp && wget -O linux-headers-3.3.6-030300_3.3.6_all.deb [http://goo.gl/zNlMy](http://goo.gl/zNlMy)  
 sudo dpkg -i linux-headers-3.3.6-030300_3.3.6_all.deb  
 cd /tmp && wget -O linux-headers-3.3.6-generic_i386.deb [http://goo.gl/TdBex](http://goo.gl/TdBex)  
 sudo dpkg -i linux-headers-3.3.6-generic_i386.deb  
 cd /tmp && wget -O linux-image-3.3.6-generic_i386.deb [http://goo.gl/osZhw](http://goo.gl/osZhw)  
 sudo dpkg -i linux-image-3.3.6-generic_i386.deb  


For Ubuntu (amd64 / 64-bit) run these commands

  cd /tmp && wget -O linux-headers-3.3.6-030300_3.3.6_all.deb [http://goo.gl/zNlMy](http://goo.gl/zNlMy)  
 sudo dpkg -i linux-headers-3.3.6-030300_3.3.6_all.deb  
 cd /tmp && wget -O linux-headers-3.3.6-generic_amd64.deb [http://goo.gl/Z9Ztt](http://goo.gl/Z9Ztt)  
 sudo dpkg -i linux-headers-3.3.6-generic_amd64.deb  
 cd /tmp && wget -O linux-image-3.3.6-generic_amd64.deb [http://goo.gl/jji3o](http://goo.gl/jji3o)  
 sudo dpkg -i linux-image-3.3.6-generic_amd64.deb 


Just reboot your system and done. 

... your mileage may vary ... however, so far - so good.     I put in the 3.3.6 kernel and pushed the system without issue.

---

