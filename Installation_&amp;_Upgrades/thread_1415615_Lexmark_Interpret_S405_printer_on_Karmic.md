---
title: "Lexmark Interpret S405 printer on Karmic"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by slonepaul on 2010-02-25
I recently bought a Lexmark Interpret S405 printer, and the box says that it's compatible with ubuntu. I downloaded the **lexmark-inkjet-09-driver-1.0-1.i386.rpm.sh**, which begins installation but gives the error message **The installer package is not supported by your native packaging system. The installer will exit.** I also downloaded the **Linux_S305_E.sh**, which doesn't even begin installation. PLEASE HELP, I have two brand new Lexmark printers, (the other being an X5630) and they both refuse to install :(:(:(:(:(:confused: or i just have no idea how to install them.

---

### Post by slonepaul on 2010-02-25
Ubuntu 9.10 running on my Acer Travelmate 6492 laptop. I also tried it on my desktop computer, which is running Ubuntu 9.04 Ultimate Edition, to no avail

---

### Post by nathan726 on 2010-03-01
The file you downloaded is a "rpm" version, but Ubuntu requires the "deb" (debian/ubuntu) version.
Unfortunately Lexmark haven't created a debian/ubuntu version yet.
You could convert the rpm package to deb using [Alien]("https://help.ubuntu.com/community/RPM/AlienHowto"), but I can't guarantee that it'll work...

Open the terminal (Applications > Accessories > Terminal)

Change directory to location of the Lexmark driver you downloaded, eg:
```
cd /home/user/
```

Dump the contents of the .sh file:
```
./lexmark-inkjet-09-driver-1.0-1.i386.rpm.sh --noexec --target lexmark_install
```

Change directory to lexmark_install folder:
```
cd lexmark_install
```

Extract the "instarchive_all" file (it may have a different name):
```
tar -xvvf instarchive_all --lzma
```

Inside instarchive_all folder you should find the .rpm file.

Now you need to install alien:
```
sudo apt-get install alien dpkg-dev debhelper build-essential
```

Convert the rpm to deb
```
sudo alien lexmark-inkjet-09-driver-1.0-1.i386.rpm
```

Install the deb
```
sudo dpkg -i lexmark-inkjet-09-driver-1.0-1.i386.deb
```

Plug in your printer and see if it works!

---

### Post by xkahn on 2010-03-08
> **nathan726 said:**
> The file you downloaded is a "rpm" version, but Ubuntu requires the "deb" (debian/ubuntu) version.
Unfortunately Lexmark haven't created a debian/ubuntu version yet.
You could convert the rpm package to deb using [Alien]("https://help.ubuntu.com/community/RPM/AlienHowto"), but I can't guarantee that it'll work...

...snip...

```
sudo alien lexmark-inkjet-09-driver-1.0-1.i386.rpm
```Install the deb

```
sudo dpkg -i lexmark-inkjet-09-driver-1.0-1.i386.deb
```Plug in your printer and see if it works!

Err..  No, it won't work.  The alien command above isn't complete enough.  Here are the steps:


[LIST=1]
[*]Download the driver [lexmark-inkjet-09-driver-1.0-1.i386.rpm.sh]("http://www.downloaddelivery.com/downloads/cpd/lexmark_inkjet_09_driver_1.0_1.i386.rpm.sh.tar.gz")
[*]Uncompress it: ```
tar xfz lexmark_inkjet_09_driver_1.0_1.i386.rpm.sh.tar.gz
```
[*]Run the script: ```
./lexmark-inkjet-09-driver-1.0-1.i386.rpm.sh --noexec --target lexmark_install
```
[*]Change to the new directory: ```
cd lexmark_install
```
[*]Install lzma and other needed packages: ```
sudo apt-get install lzma alien dpkg-dev debhelper build-essential
```
[*]Rename the archive to something sane: ```
mv instarchive_all instarchive_all.tar.lzma
```
[*]Uncompress: ```
lzma -df instarchive_all.tar.lzma
```
[*]Unarchive: ```
mkdir instarchive_all; cd instarchive_all; tar xf ../instarchive_all.tar
```
[*]Convert to debs (with scripts!) ```
sudo alien --scripts lexmark-inkjet-09-driver-1.0-1.i386.rpm
```
[*]Install: ```
sudo dpkg -i lexmark-inkjet-09-driver_1.0-2_i386.deb
```
[*]Now we install the built in JRE: ```
cd /usr/lexinkjet; sudo ~/lexmark_install/instarchive_all/jre-6u12-linux-i586.bin
```
[*]And, rename the directory: ```
sudo mv jre1.6.0_12 jre
```
[*]And restart udev: ```
sudo /etc/init.d/udev restart
```
[*]And cups, just in case: ```
sudo /etc/init.d/cupsys restart
```
[/LIST]
There!  That ought to do it.  The printer control panel is in System -> Administration -> Lexmark Printer Toolbox.  Both local and network printing should work.  Local computer initiated scanning should work too.  Enjoy!

---

### Post by lefty_lou on 2010-03-20
Or go here and get the .Deb ones

[http://support.lexmark.com/index?page=content&id=DR4255&actp=search&viewlocale=en_US&userlocale=EN_US&segment=DOWNLOAD&productCode=LEXMARK_INTERPRET_S405&searchid=1269116506704]("http://support.lexmark.com/index?page=content&id=DR4255&actp=search&viewlocale=en_US&userlocale=EN_US&segment=DOWNLOAD&productCode=LEXMARK_INTERPRET_S405&searchid=1269116506704")

Easier ;)

Enjoy 

Is the same ones by the way but already in deb files you just have to put ubuntu on the search on the middle right hand side on lexmark page after you put in the model to get them.

For some odd reason they don't show under linux go figure :-k

---

### Post by j4ck455 on 2010-04-03
That .deb barfs on AMD64, seems only i386 is supported by Lexmark.

---

### Post by davidmohammed on 2010-04-03
the following is copied from [phoronix.com]("http://www.phoronix.com/scan.php?page=article&item=lexmark_linux&num=4")

```
Prerequisite packages: ia32-libs, openjdk-6-jre

1. Get the latest driver
2. Untar driver
3. run in terminal "./lexmark-inkjet-09-driver-1.5.i386.deb.sh --noexec --target lexmark"
4. a "lexmark" (from --target) directory was created, "cd lexmark"
5. run in terminal "tar xvf instarchive_all --lzma"
6. run in terminal "dpkg -i --force-all lexmark-inkjet-09-driver-1.5-1.i386.deb"

```

suggest have a read of the phoronix article to see if it helps you.

---

### Post by drasticbrisk on 2010-04-20
I downloaded the driver update for ubuntu from the Lexmark website and when going through the setup it asks for an administrator password. I put in the password that I log in with but it doesn't work. What am I doing wrong?

---

### Post by kwanseum on 2010-05-08
> **drasticbrisk said:**
> I downloaded the driver update for ubuntu from the Lexmark website and when going through the setup it asks for an administrator password. I put in the password that I log in with but it doesn't work. What am I doing wrong?

It is because you have not set a root password but you can do that easily.  Type in the following  in the shell:

 > sudo passwd


 After that you are asked to type in the new root password twice.  Finally, your root user has its own password and you will need this to install the software.


I hope this helps, Kwanseum

---

### Post by Trinity1976 on 2010-07-25
I bought this printer today and followed the steps described by xkhan. Seems to print fine but when I try to open XSane to scan I get the following:

> Failed to open device 'Lexmark_1_0_0:libusb/001/002': Device busyAny ideas, anyone?

Never mind. Have rebooted machine and it works now!

---

### Post by danflash on 2010-11-24
Steps worked perfectly for me.

Thank you.

---

### Post by jasonfriedman80238 on 2011-04-04
I found this page helpful:
[http://support.lexmark.com/index?page=productSelection&userlocale=EN_US&locale=EN](http://support.lexmark.com/index?page=productSelection&userlocale=EN_US&locale=EN)
I selected my printer and was directed to a page of downloads, including .deb.

---

### Post by xwang on 2011-09-17
Hi to all,
I would like to buy this printer, but I want to know if it works perfectly (both printing and scanning with and without the ADF) when connected only via the wifi connection.
Alternatively adding 30€ I can buy a Brother MCF J430W printer.
Which is the best?
Thank you,
Xwang

---

