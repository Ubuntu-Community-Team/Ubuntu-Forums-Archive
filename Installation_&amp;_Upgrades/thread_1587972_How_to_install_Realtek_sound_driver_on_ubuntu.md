---
title: "How to install Realtek sound driver on ubuntu?"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by HiTom on 2010-10-04
I want to install this [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)


How to? Because i downloaded the tar.gz2 format of it.

And i dont know what to do.

Please help me!

---

### Post by Naitsirhc Hsem on 2010-10-04
have you tried looking for restricted drivers, easier.  open System>Administration>Hardware Drivers.  if the driver is listed there, click on it and click install or activate.  that will solve your problem.  otherwise, follow these next instructions:


Extract the archive, right click extract here.
Open the terminal.
cd to the extracted folder,```
cd Downloads/foldername
```
and list the files in that folder, ```
ls
```
post the output here

from there I will tell you how to install the driver

---

### Post by andrewthomas on 2010-10-04
what sound card to you have?

post the output of 

```
lspci | grep Audio
```

and

```
cat /var/log/messages | grep hda
```

---

