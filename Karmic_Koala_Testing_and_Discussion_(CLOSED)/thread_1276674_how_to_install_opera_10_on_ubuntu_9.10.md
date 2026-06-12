---
title: "how to install opera 10 on ubuntu 9.10??"
date: 2009-09-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yoshiki2 on 2009-09-27
Any ideas?? the deb file did not work for me

---

### Post by howefield on 2009-09-27
I have opera 10 running here on Karmic Alpha 6 using this .deb file downloaded from the opera website,
opera_10.00.4585.gcc4.qt4_amd64.deb

I guess it should be possible for you too, with the correct file for your system.

What error(s) did you get ?

---

### Post by sports fan Matt on 2009-09-27
Howe, alot of us are getting on several debs: bad file selectors when trying to install programs.

---

### Post by todak on 2009-09-27
Install using the **sudo dpkg -i <youroperapackagename>.deb** command.

---

### Post by sports fan Matt on 2009-09-27
sudo dpkg -i opera10.deb
[sudo] password for office: 
dpkg: error processing opera10.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 opera10.deb

---

### Post by howefield on 2009-09-27
> **sox fan Matt said:**
> Howe, alot of us are getting on several debs: bad file selectors when trying to install programs.

Sorry, I should have said I had to use the same solution todak mentions to install the .debs I use (handbrake, opera, sopcast, dropbox and virtualbox)

All installed fine, but I see from other threads some are having problems even installing through terminal.

All .debs copied to the desktop, open terminal and cd to the Desktop, run the dpkg command as above.

---

### Post by todak on 2009-09-27
@ Matt

My terminal output:
```
dave@ubuntu:~/Downloads$ sudo dpkg -i opera_10.00.4585.gcc4.qt3_i386.deb
[sudo] password for dave: 
Selecting previously deselected package opera.
(Reading database ... 196179 files and directories currently installed.)
Unpacking opera (from opera_10.00.4585.gcc4.qt3_i386.deb) ...
Setting up opera (10.00.4585.gcc4.qt3) ...
update-alternatives: using /usr/bin/opera to provide /usr/bin/x-www-browser (x-www-browser) in auto mode.

Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
dave@ubuntu:~/Downloads$ 
```

**cannot access archive: No such file or directory**Are you sure you changed directories to where you downloaded Opera before  attempting to install? :-k Notice the **~/Downloads** directory in my terminal output

---

### Post by sports fan Matt on 2009-09-27
So if I were to do a sudo dpkg -i opera10.deb ..it would throw up that error..how could i get around that?

---

### Post by sports fan Matt on 2009-09-27
I havent changed directories..thats why its throwing up the error..but everything is in my tmp directory.

---

### Post by todak on 2009-09-27
> **sox fan Matt said:**
> I havent changed directories..thats why its throwing up the error..but everything is in my tmp directory.

Download the .deb from Opera. Choose a directory to save the file rather than use gdebi to install. Then, in terminal, change to that directory and use my previous command to install. :)

---

