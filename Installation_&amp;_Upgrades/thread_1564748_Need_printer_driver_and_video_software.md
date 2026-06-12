---
title: "Need printer driver and video software"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by anjan0deb on 2010-08-31
[SIZE=2]I have a computer running ubuntu without any internet connection.

I badly require a driver software for using my printer "Epson LQ-1050+" 
and also a video(.avi,.mkv) playing software for running in ubuntu. 

I want to download the softwares from a different machine and then 
take it in a pen drive and install it in the ubuntu comp.

Pls help me where can i download the softwares from and how to 
install it in the computer.

[/SIZE]

---

### Post by dhymalk on 2010-08-31
sorry, for this problem u must have package cd installation programme, if not..u must connect to internet to find the driver.thanks:popcorn:

---

### Post by varunendra on 2010-09-01
For media player, look for VLC if it is available in a single package.

Otherwise, the next easiest option is to

[LIST=1]
[*]make a Live USB flash drive with the same version you have, ([see how]("http://www.ubuntu.com/desktop/get-ubuntu/download"), follow step2 on this page)
[*]boot the computer (with internet conn.) from this Live USB drive,
[*]install **whatever you want + aptoncd **via synaptic,
[*]make an offline repository cd with aptoncd,
[*]use this offline repo cd as software source on your current computer (ubuntu will automatically recognize it as a software source).
[/LIST]
Alternatively, (if you don't want to use aptoncd, although I highly recommend it) you can just copy the **/var/cache/apt/archives** folder of the Live Ubuntu which you've used to download packages. All the downloaded packages are stored in this folder. You can manually install them on the target machine but among all those packages, manually determining & installing the dependencies in correct order may prove quite a headache.

If you live in India, another very good alternative for you maybe to get a complete repository of your version in form of 6 to 8 DVD package (depending upon version) in a very reasonable price (only INR. 240+Courier charges) from Zyxware ([http://www.zyxware.com/requestcd?title=ubuntu](http://www.zyxware.com/requestcd?title=ubuntu) , Phone: +91-471-2449495 (O), +91-9446-06-9446 (M))

There maybe better ways to work it out, but I don't know of any! :)

---

### Post by anjan0deb on 2010-09-04
> **varunendra said:**
> For media player, look for VLC if it is available in a single package.

Otherwise, the next easiest option is to

[LIST=1]
[*]make a Live USB flash drive with the same version you have, ([see how]("http://www.ubuntu.com/desktop/get-ubuntu/download"), follow step2 on this page)
[*]boot the computer (with internet conn.) from this Live USB drive,
[*]install **whatever you want + aptoncd **via synaptic,
[*]make an offline repository cd with aptoncd,
[*]use this offline repo cd as software source on your current computer (ubuntu will automatically recognize it as a software source).
[/LIST]
Alternatively, (if you don't want to use aptoncd, although I highly recommend it) you can just copy the **/var/cache/apt/archives** folder of the Live Ubuntu which you've used to download packages. All the downloaded packages are stored in this folder. You can manually install them on the target machine but among all those packages, manually determining & installing the dependencies in correct order may prove quite a headache.

If you live in India, another very good alternative for you maybe to get a complete repository of your version in form of 6 to 8 DVD package (depending upon version) in a very reasonable price (only INR. 240+Courier charges) from Zyxware ([http://www.zyxware.com/requestcd?title=ubuntu](http://www.zyxware.com/requestcd?title=ubuntu) , Phone: +91-471-2449495 (O), +91-9446-06-9446 (M))

There maybe better ways to work it out, but I don't know of any! :)
Thank you so much varunendra.I live in India and will try all the options to learn more.

---

