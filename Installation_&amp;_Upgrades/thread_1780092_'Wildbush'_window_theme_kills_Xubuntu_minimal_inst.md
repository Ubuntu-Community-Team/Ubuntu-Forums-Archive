---
title: "'Wildbush' window theme kills Xubuntu minimal install ..."
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2011-06-11
Hi all,

I have just done a minimal install of Ubuntu 10.04 LTS alongside Windows 7 and 10.10. I am using Xfce.

All went great and I am happy with the speedy, slick environment. Problem is: Customising and tweaking, I was trying out some window themes and when I chose 'Wildbush' it killed everything and took me to the log-in screen. When I log in I get a blank screen for a nano-second then I'm back at the log-in screen again! Potential for an endless loop.

Obviously, my install doesn't like something about the 'Wildbush' window theme.

Question is: How do I change this window theme when I can't get into the install???

Possible solution: I can boot into 10.10 and access the partitions of the 10.04 install and change it that way. But where would I start? Where is the setting 'Wildbush' for the window theme likely to be stored and what might I replace it with???

Thanks in advance for any ideas and I'll start digging. ;)

---

### Post by Bucky Ball on 2011-06-11
Okay, after some digging I figured what to change and can access the 10.04 install from 10.10 but can't seem to get to where I want to go there. Where I want to go is here:

> ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml

And find this line:
 <property name="theme" type="string" value="Simian"/>According to this page:

[http://ubuntuforums.org/archive/index.php/t-1452435.html](http://ubuntuforums.org/archive/index.php/t-1452435.html)

I'm guessing the 10.04 minimal install file would replace "Simian" with "Wildbush". My 10.10 install is a bit of a hybrid which has Xfce4 on it and that file exists there and that line also exists but looks like this:

```
<property name="theme" type="string" value="Quiet-purple"/>

```Can anyone help me get to that same file in the inoperable 10.04 install from the operating 10.10? Love to get back to customising my new minimalist  install. ;)

* EDIT: Duh, I have the xterm option under sessions at the login screen in the new install. I just remembered! I will give that a go.

---

### Post by Bucky Ball on 2011-06-11
Yep, that fixed it! Problem solved. I did this:

* Logged into 10.04 using 'xterm' as my 'Session'. 
* Opened the appropriate file with this:
```
sudo nano ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml
```* Changed the line:
```
<property name="theme" type="string" value="Wildbush"/>
```...to:
```
<property name="theme" type="string" value="Xfce-basic"/>
```Done. Now when I break it again (hopefully not) I'll know how to fix it. Couldn't have done it without the help of the folks in the link in my post #2. Cheers, whoever you are. ;)

---

