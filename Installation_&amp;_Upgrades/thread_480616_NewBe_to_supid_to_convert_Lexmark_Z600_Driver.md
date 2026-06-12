---
title: "NewBe to supid to convert Lexmark Z600 Driver"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by FAS786 on 2007-06-21
Hiya
I got a Z600 Driver but its made for ReHat9.0 
Im using ubuntu and i have to convert the rpm files to dubs but i cant 

i just dont get it
Does any one have or give me or tell me 
where i can get a ready made driver from 
Thank You

I been trying for a week i just dont get the instruction that follow

   1. download CJLZ600LE-CUPS-1.0-1.TAR.gz from Lexmark.com - it is the CUPS driver for RedHat 9.0 DONE
   2. Untar and unzip this file using
      $ tar -zxvf CJLZ600LE-CUPS-1.0-1.TAR.gz DONE
   3. You will end up with a file called
      z600cups-1.0-1.gz.sh DONE
   4. Extract the .rpm part of this file using
      sh z600cups-1.0-1.gz.sh -target temp_lex
      this will create a sub-directory called "temp_lex" under the current directory, and put a whole lot of files in it. Ignore any errors you might get - if the two .rpm files are in temp_lex you are fine. 
??????? I GET ERRORS SAY THE THING DONT EXIST AND THE REST IS HISTORY :(

   5. In the newly created directory temp_lex you will find, amongst others, the files:
      z600cups-1.0-1.i386.rpm, and
      z600llpddk-2.0-1.i386.rpm
   6. To install to a debian system (or Ubuntu or Knoppix) you need to convert these two files to the .deb equivalent. The program to use is called "alien" and you run it as follows:
      $ alien z600cups-1.0-1.i386.rpm

      $ alien z600llpddk-2.0-1.i386.rpm
   7. You will now find the dpkg packages:
      z600cups-1.0-1.i386.deb
      z600llpddk-2.0-1.i386.deb
   8. Now install the driver with:
      dpkg -i z600cups-1.0-1.i386.deb
      dpkg -i z600llpddk-2.0-1.i386.deb
   9. Now use CUPS or the Printer configuration tool in Ubuntu to add the printer

---

### Post by Thelasko on 2008-01-09
My guess is that you are using 64-bit Ubuntu in which case you can't convert the RPM files to DEB files.  You have to follow the directions [here]("http://ubuntuforums.org/showthread.php?t=616097").
you may have to delete some files you created before because I don't think some programs will write over them.  Especially if they were created as root.

Let me know if that works for you.

---

### Post by Thelasko on 2008-01-09
Let me reiterate, don't try to convert the RPMs to DEBs you need to use ```
alien -t
``` to convert the files to a .tgz package and install that.  The -t is very important.

---

### Post by oldsoundguy on 2008-01-09
have you tried to go to system> administration> printing> and selecting "install printer"?
Darn good chance there is a cups driver for your printer in the selections.
Just follow the yellow brick road.
I have 6 printers .. 4 tied to a WinDOZE box (a laser, a 4 in one, a pro photo printer and a label printer), two tied to Gutsy boxes.  I can print to all but one of them (the  label printer with no cups driver) from any machine on my network. 
ALL were installed via that utility.  (you do need the device URI on the networked remote printers.)

---

### Post by Thelasko on 2008-01-09
The z600 driver isn't included with Ubuntu.  There is a[ bug report]("https://bugs.launchpad.net/ubuntu/+source/cupsddk/+bug/133121") to correct that.

---

