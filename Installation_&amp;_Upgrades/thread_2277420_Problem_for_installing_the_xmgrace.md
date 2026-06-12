---
title: "Problem for installing the xmgrace"
date: 2015-05-08
forum: Installation &amp; Upgrades
---

### Post by zhangdashuang on 2015-05-08
Hi,

[COLOR=#000000]I am trying to install Xmgrace following $ sudo apt-get install grace[/COLOR][COLOR=#000000]. I get problem like:
*******************************************
[/COLOR][COLOR=#000000]...
[/COLOR][FONT=arial]Do you want to continue [Y/n]? Y[/FONT]
[FONT=arial]WARNING: The following packages cannot be authenticated![/FONT]
[FONT=arial] [COLOR=#ff0000] libgfortran3 libhdf5-7 libmotif-common libxm4 libmrm4 libuil4 libxbae4m xmhtml1[/COLOR][/FONT][COLOR=#ff0000]
[FONT=arial]  libnetcdfc7 grace xfonts-100dpi[/FONT][/COLOR]
[FONT=arial]Install these packages without verification [y/N]? y[/FONT]
[FONT=arial]Err [/FONT][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[FONT=arial] saucy-updates/main libgfortran3 amd64 4.8.1-10ubuntu9[/FONT]
[FONT=arial]  404  Not Found [IP: 91.189.91.13 80]
[/FONT][COLOR=#000000]...

*******************************************

I assume libgfortran, etc., are Ubuntu's default package? What is this authenticate package problem?

Nan[/COLOR]

---

### Post by oldos2er on 2015-05-08
Ubuntu 13.10 "Saucy Salamander" has not been supported since last July, so its repositories are no longer updated. It's best to install a supported version such as 14.04 LTS or 15.04.

---

