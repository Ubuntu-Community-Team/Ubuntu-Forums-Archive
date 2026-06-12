---
title: "Brother scanner problems with Ubuntu 11.10"
date: 2011-11-02
forum: Installation &amp; Upgrades
---

### Post by smi402 on 2011-11-02
I have a Brother MFC-8460N printer/scanner/copier/fax on my network which worked flawlessly with Ubuntu 11.04 and previous releases. However, after recently upgrading to 11.10 with the Final Release *alternate-amd64* disk the scanner function ceased to work - neither xsane, Gimp nor Simple Scan could find the scanner device. Brother has issued a fix for this problem that applied to the Beta 2 version of 11.10. It is among the FAQs [**_listed here_**]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html").

The problem arises because of paths to the **sane** libraries the Brother software uses. I have solved this problem in my installed Final Release 64bit 11.10 by setting up symbolic links to the appropriate libraries as in the code below. You firstly need to get the **brscan-skey** and **brscan** packages that apply to your scanner from the [**_Brother site_**]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html").

My scanner uses the **brscan2** package so I then set up the following links (**NOTE:** Make sure you use the library names that are appropriate to the version of **brscan** that you installed): 

```
frank@server:~$ cd /usr/lib
frank@server:/usr/lib$ 
frank@server:/usr/lib$ sudo ln -s /usr/lib64/libbrcolm2.so libbrcolm2.so
frank@server:/usr/lib$ sudo ln -s /usr/lib64/libbrcolm2.so.1 libbrcolm2.so.1 
frank@server:/usr/lib$ sudo ln -s /usr/lib64/libbrcolm2.so.1.0.1 libbrcolm2.so.1.0.1 
frank@server:/usr/lib$ sudo ln -s /usr/lib64/libbrscandec2.so libbrscandec2.so 
frank@server:/usr/lib$ sudo ln -s /usr/lib64/libbrscandec2.so.1 libbrscandec2.so.1 
frank@server:/usr/lib$ sudo ln -s /usr/lib64/libbrscandec2.so.1.0.0 libbrscandec2.so.1.0.0 
frank@server:/usr/lib$ cd sane
frank@server:/usr/lib/sane$ sudo ln -s /usr/lib64/sane/libsane-brother2.so libsane-brother2.so 
frank@server:/usr/lib/sane$ sudo ln -s /usr/lib64/sane/libsane-brother2.so.1 libsane-brother2.so.1 
frank@server:/usr/lib/sane$ sudo ln -s /usr/lib64/sane/libsane-brother2.so.1.0.7 libsane-brother2.so.1.0.7
```

Reboot, turn the scanner on, open a terminal and run ***xsane***. It should then find the scanner device and enable scanning :D:D I trust this may help some of those trying to run Brother scanners using 11.10.

Frank

---

### Post by ct302 on 2011-11-10
I've been searching for this fix for hours! My Brother MFC-440CN works perfectly now! THANK YOU!!!!

---

### Post by smi402 on 2011-11-10
Glad this fix has worked well for you ct302.

---

### Post by Hugin17 on 2011-11-13
This fix works with my Brother DCP-J715W. Thanks a lot smi402.

---

### Post by cometdog on 2012-02-20
The corresponding entry in the FAQ worked for me with a Brother MFC-7840W. Thanks for the tip!

---

### Post by momashi on 2012-05-01
I have the exact same printer (8460N) and 11.10 but that solution just did not work for me. Are you connected to the printer via a network or via USB?

---

### Post by lgharriman on 2012-07-20
Thanks for the help.  It worked for my Brother MFC-5890CN using Pinguy 11.04
:popcorn:

---

### Post by Halfling Rogue on 2012-09-23
Worked for Brother MFC-J835DW on 11.10, with a wireless network setup and a 32 bit machine (meaning only 3 links had to made in /usr/lib from /usr/lib/sane).

Momashi, are you setting up your printer on a wireless network? If so you'll need to config your version of brscan with your printer's IP address as well. eg.:

```
brsaneconfig4 -a name=Brother model=MFC-J835DW ip=192.168.1.103
```

---

