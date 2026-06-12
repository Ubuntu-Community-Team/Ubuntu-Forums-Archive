---
title: "Since GDEBI wont install packages..."
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-10-02
What is the other way to install packages? 

There is a way in terminal, I remember but cant remember the command.  

Edit: trying to run Opera 10.

---

### Post by sisco311 on 2009-10-02
```
sudo gdebi path/to/file.deb
```
or```
sudo dpkg -i path/to/file.deb
```

---

### Post by sports fan Matt on 2009-10-02
I tried a sudo gdebi opera.deb
gdebi error, file not found: opera.deb
Surely they didn't take the opera debs away?

---

### Post by FuturePilot on 2009-10-02
> **sox fan Matt said:**
> I tried a sudo gdebi opera.deb
gdebi error, file not found: opera.deb
Surely they didn't take the opera debs away?

You need to specify where the deb package is and the full name of the file.

---

### Post by sisco311 on 2009-10-02
> **FuturePilot said:**
> You need to specify where the deb package is and the full name of the file.

+1

Type:
```
sudo gdebi
```
type a space and drag the .deb file in the terminal window, then press Enter.

---

### Post by sports fan Matt on 2009-10-02
Apparently the bad file descriptors are still present...sudo gdebi '/home/office/Desktop/opera_10.10.4644.gcc4.qt4_i386.deb' 

dpkg: unable to read filedescriptor flags for <package status and progress file descriptor: bad file descriptor

---

### Post by sisco311 on 2009-10-02
> **sox fan Matt said:**
> Apparently the bad file descriptors are still present...sudo gdebi '/home/office/Desktop/opera_10.10.4644.gcc4.qt4_i386.deb' 

dpkg: unable to read filedescriptor flags for <package status and progress file descriptor: bad file descriptor

Is your system up-to-date?

dpkg works for me (dpkg-gtk still throws an error).

anyway, did you try?
```
sudo dpkg -i '/home/office/Desktop/opera_10.10.4644.gcc4.qt4_i386.deb'
```

---

### Post by kansasnoob on 2009-10-02
I do things a bit different and it just works for me. Lets say I've saved the download to my Desktop, I'd run the command:

```
cd Desktop
```

So terminal looks like this afterwards:

> lance@lance-desktop ~ $ cd Desktop
lance@lance-desktop ~/Desktop $ 


Then I type:

```
sudo dpkg -i 
```

Then whatever download I want to install I right click and then click on Properties:

[ATTACH]130529[/ATTACH]

I then copy and paste that file name (you can see I've highlighted it in the example) to the terminal (example):

```
sudo dpkg -i ubuntuzilla-4.6.1-0ubuntu1-i386.deb
```

Then I just hit enter and let the magic happen!

---

### Post by dalonso on 2009-10-02
Fresh install of Karmic Alpha 6, updated to beta here.

No problems with gdebi at all, I simply double-click at the deb and it autoopens gdebi.

---

### Post by sisco311 on 2009-10-02
> **dalonso said:**
> Fresh install of Karmic Alpha 6, updated to beta here.

No problems with gdebi at all, I simply double-click at the deb and it autoopens gdebi.

Did you actually install a package with gdebi-gtk?
It opens just fine, but when i try to install the package it says:
 [img]http://www.upload3r.com/serve/021009/1254522763.png[/img]

---

### Post by theo2881 on 2009-10-02
i cant even update, let alone install a deb package, update gives me error of "dpkg: error processing debconf (--configure):"

---

### Post by dalonso on 2009-10-02
> **sisco311 said:**
> Did you actually install a package with gdebi-gtk?
It opens just fine, but when i try to install the package it says:
 [img]http://www.upload3r.com/serve/021009/1254522763.png[/img]
Ooops, it's true, it is not working now. Sorry. I promise I installed yesterday the skype beta using gdebi and it worked, but it's not working now.

---

### Post by theo2881 on 2009-10-02
Im just looking for any help, I did a fresh install of the beta but now I cant update anything. or run any deb package.

---

### Post by kansasnoob on 2009-10-02
> **theo2881 said:**
> i cant even update, let alone install a deb package, update gives me error of "dpkg: error processing debconf (--configure):"

My best guess is that an upgrade was interrupted. The Ubuntu servers are flooded right now.

Be patient! BTW that had nothing to do with what the OP was asking!

---

### Post by justldd on 2009-10-02
I got a similar problem.
To solve it I did the following
1.
```
 sudo apt-get install debconf 
```2. (optional)
```
 sudo apt-get update 
```try installing it now.. it should *theoretically work*

Nevertheless, I did this because I couldn't even do 'sudo apt-get ...' after installing the beta. 
(I am not an experienced user, so I would be unable to tell you why debconf solved my problem...)

**edit:** if it doesnt work, try uninstalling debconf first (Though I am not sure if it is ok to uninstall it so it's better to wait until someone can confirm that my solution works)

---

### Post by sports fan Matt on 2009-10-03
When I get home tomorrow, I shall try the suggestion :)

---

### Post by sports fan Matt on 2009-10-03
Just tried to run that above command and got: dpkg: error processing /home/office/Desktop/opera_10.10.4644.gcc4.qt4_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/office/Desktop/opera_10.10.4644.gcc4.qt4_i386.deb

---

### Post by kansasnoob on 2009-10-03
Updates this morning appear to have fixed Gdebi, otherwise read my post #8.

---

### Post by sports fan Matt on 2009-10-03
Everything has been fixed :)

---

### Post by cariboo on 2009-10-03
+1, I used it to install virtualbox puel last night.

---

