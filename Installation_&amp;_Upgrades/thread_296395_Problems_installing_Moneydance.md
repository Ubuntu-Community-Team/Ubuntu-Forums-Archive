---
title: "Problems installing Moneydance"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by SnTholiday on 2006-11-09
Hello,

I would really like to try Moneydance but am having trouble with the installation. When the installer starts it will ask which directory you want to install Moneydance, from there it tells me I do not have permission. How do I get around this, and what would be the proper directory for installation? 

Thanks for any help.

---

### Post by Sef on 2006-11-10
So are you using the default directory?  And if so, then you get the message that you can't install to that directory?

---

### Post by SnTholiday on 2006-11-10
Any directory I try to use tells me I don't have permission. I am going to try it again tonight, Any help would be appreciated.

---

### Post by SnTholiday on 2006-11-10
I can get the installation process to start by making the file executable,
and java downloads, but any directory I try to use for install tells me I do
not have permission. 

Thanks again for any help.

---

### Post by SnTholiday on 2006-11-15
Does anyone have any suggestions as to what I am doing wrong? I don't want to have to go back to using Windows XP just for Quicken, but it looks like I may have to. Tried Gnucash and Grisbi but they do not have online banking.

---

### Post by dcstar on 2006-11-15
> **SnTholiday said:**
> Does anyone have any suggestions as to what I am doing wrong? I don't want to have to go back to using Windows XP just for Quicken, but it looks like I may have to. Tried Gnucash and Grisbi but they do not have online banking.

One assumes you are using **sudo** for the installation?

---

### Post by SnTholiday on 2006-11-16
Yes, I used sudo for the install. The installer still tells me I have no permission.

---

### Post by wilberfan on 2006-12-16
I ran into this problem, too...   The solution was to right-click on the install script, change all the permissions to read/write, and check the little box that says something about allowing it to be executed as a program (or something)...

Then back to the command line, sudo ./moneydance(etc), and voila!  (make sure you're in the directory that the install script is in)

---

