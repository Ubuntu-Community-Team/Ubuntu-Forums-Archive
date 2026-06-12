---
title: "new in linux/ install xbasic"
date: 2012-04-24
forum: Installation &amp; Upgrades
---

### Post by maria41444 on 2012-04-24
Hi!! I am quite new in Ubuntu. The majority of my doubts I can solved looking into forums, but sometime installing is more difficult than that for me...
For instance now I have to install xbasic. To do it I have to follow the next steps, 
1. Put the xbasic-$(VERSION)-linux-i386.tar.gz file in
'      your / root directory.
'   2. Start an xterm window, then enter the following
'      lines:
'      cd /
'      tar xfz xbasic-$(VERSION)-linux-i386.tar.gz

But, how to "put" the xbasic in root directory?? Can someone help me? I would like to know what are the exact command I have to use for put xbasic in root directory. 
Thank you

---

### Post by corncob on 2012-04-24
Welcome to the forums!  What I would do would be to open a terminal (xterm) window and type
```
sudo nautilus
```
to open the file browser with root privilages.  I would then click on 'File System' and navigate to the file in the right hand pane (click on Home > username > Downloads or wherever it is), then drag it over to 'File System' in the left hand pane (what you clicked on initially).

---

### Post by jerrrys on 2012-04-24
*cough, gksudo, cough*

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gksudo&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gksudo&sa=Search&cof=FORID:9)

---

