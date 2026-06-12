---
title: "help running QEMU-0.8.0 win2k image with new QEMU-0.8.1"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by barmaley on 2006-06-17
Hallo, people

After I successfully upgraded from Breeezy to Dapper, I did not manage to run win2k image created in Dapper with QEMU-0.8.0. I installed a new QEMU-0.8.1 and KQEMU-1.3.0pre7 with the help of a great script described in this thread:
[http://ubuntuforums.org/showthread.php?t=187413](http://ubuntuforums.org/showthread.php?t=187413)
but still no success with running the windows image.
The error that windows shows can be seen in the attached screenshot.
I badly need the data stored in that image.
Please, help.

---

### Post by catlett on 2006-06-17
Did you try uninstalling QEMU-0.8.1 and then re-installing QEMU-0.8.0? This may not be a long term solution but hopefully it will allow you to access the data you need from that image and archive it somewhere.

---

### Post by barmaley on 2006-06-17
Thanks, catlett, for a fast response.
I don't know how to un-install qemu, I think there is only one option of make clean, but it is possible when you install from the source, not with the help of the script. Do you know how to unistall it?
Any way thank you, I'll try it.
Ubuntu people are great :)

---

### Post by catlett on 2006-06-17
It isn't cut and dry sometimes but the comand to issue is ```
make uninstall
``` It's just like when yoiu use make install. You have to cd to (in the uninstall case) the directory the application is compiled in (as opposed to the folder that you unzipped the atr into). If you still have the original folder with the configure and make files, go to it and check the READ ME and the INSTALL  for any information on uninstall.

A way to avoid this in the future is to use checkinstall instead of make install. When you use checkinstall that application makes a deb package out of it so you can uninstall it later like a regular deb. Here is the checkinstall homepage [http://asic-linux.com.mx/~izto/checkinstall/](http://asic-linux.com.mx/~izto/checkinstall/)  Here is the "man" page for checkinstall [http://manpage.willempen.org/1/checkinstall](http://manpage.willempen.org/1/checkinstall)

To install checkinstall use Synaptic Package manager or run```
 apt-get install checkinstall
```

When you go to compile run it like this```
 ./configure
``` ```
make
``` ```
sudo checkinstall
```

---

### Post by barmaley on 2006-06-18
Hallo, catlett

I installed qemu from the script install_qemu.sh, and I did not use configure, make, make install. The script did everything for me. Though I can see the qemu package in Synaptic, so I can uninstall it there. Would it be correct to uninstall it like this and then try to install the previous version?
Thanks for helping me out.

---

### Post by barmaley on 2006-06-20
Hallo, people
I installed qemu-0.8.1 with kqemu1.3 and it works: sees previously created disk-image and works fine at all.
At home I have managed to run the windows2k in safe mode with internet and have done the backup. What is wrong with the normal mode I don't know and don't understand.
Any ideas?

---

