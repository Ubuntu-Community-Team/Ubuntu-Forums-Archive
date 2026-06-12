---
title: "synaptic error due to WordPefect install"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by 1of3 on 2010-08-26
error message when I try to add new software . . . 
_______
E: wp-full: subprocess installed post-removal script returned error exit status 127
_______

I had tried to add wordperfect 8.1 from a legit debian file I had on an old Corel Linux CD. [*Sorry but i would really like to have WP on my Ubuntu dist. (OpOff) just does not do it for me.*]
 command used          dpkg -i wp-full_8.1-nn_i386.deb

I used command line It partially installed, but required other legacy packages, these then failed completely when it tried to install incompatible font files. Ok . . so I try to back out, but when I try to remove the "wp-x-x-x" file it refused giving me the error above.

Any ideas . .?    Thanks

---

### Post by sikander3786 on 2010-08-26
Try removing the file from command line and post the complete results.

***sudo apt-get remove whateverfilename***

---

