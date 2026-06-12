---
title: "Installing a modem driver Intel chipset"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by Ethelbert2 on 2007-03-01
[COLOR="DarkOliveGreen"][SIZE="3"][FONT="Georgia"]Excuse me if this is the wrong section of the forum - it is about installing a modem.  This is for a 536ep V9x DF for which I eventually found Intel has drivers for Linux. But these are compiled for Red Hat etc. You can download a general source file which you make yourself as I understand it. The *read me* says in part:[/FONT][/SIZE][/COLOR]

[COLOR="Sienna"][SIZE="1"][FONT="Tahoma"]3.  INSTALLATION

Prerequisites:
   1. root access
   2. bash shell to run install scripts
   3. an Intel536ep modem
   4. KERNEL SOURCE HEADERS FOR THE KERNEL YOU ARE RUNNING.
      (found on your distribution's CD)

6 steps to install
   1. login as ROOT 
   2. extract the archive into a directory with "tar -zxvf <archivename>.tgz"
   3. cd into the directory it created.
   4. Type: make clean
   5. Type: make 536
   6. Type: make install
This will create a /dev/modem device file. This file is used as an interface to 
modem by all applications: minicom, kpppd, efax, etc. Please configure the applications
to use /dev/modem if neccessary.

The installation script has been designed for the following distributions 
release versions

   Mandrake-release
   SuSE-release
   Redhat-release
   Fedora Core 2 -release
   Unknown distributions install modules and utilities but
   will not install boot scripts!.

Please examine the 536ep-inst and 536ep-boot scripts if you have a different distribution.

The driver registers itself as character device 
   major number 240, minor number 1.[/FONT][/SIZE][/COLOR]

[COLOR="Green"][SIZE="3"][FONT="Georgia"]among other stuff.  This means very little to me (a relative newby person).
I have downloaded this stuff but don't understand the *read-me* fully, especially the bit about inspecting 536ep-inst etc.

Can anyone explain in simply terms what I need to do (or point me at past explanations)- or does the above include enough for Debian? ie if I follow the six steps will I be there or is there special extra stuff to do?

(Also I have no internet connection so explanations that tell me to get additional stuff loaded by finding things through the Internet simply will not help me do it.)


Is there a way to use the already compiled bin files for the other distributions?   I have vaguely heard of [FONT="Fixedsys"]alien[/FONT]. There are posted versions for Suse and Red Hat and Fedora. I hope this is enough information for a sensible answer - thank you.

I am using an old P3 450Mx 190RAM Xubuntu 6.10.

[/FONT][/SIZE][/COLOR]

---

### Post by Ethelbert2 on 2007-03-01
[FONT="Georgia"][SIZE="3"][COLOR="DarkOliveGreen"]I may have found my own answer for this at[/FONT]

[https://help.ubuntu.com/community/DialupModemHowto/Intel536EP](https://help.ubuntu.com/community/DialupModemHowto/Intel536EP)

[FONT="Georgia"]which seems to talk you through it comprehensively
Apologies for wasting time.[/COLOR][/SIZE][/FONT]

---

