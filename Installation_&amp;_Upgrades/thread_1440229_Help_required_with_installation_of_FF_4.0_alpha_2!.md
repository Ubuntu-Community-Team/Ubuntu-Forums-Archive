---
title: "Help required with installation of FF 4.0 alpha 2!"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by Saurabhdua on 2010-03-27
Hi Guys!:popcorn:

I have got this 'Weird' format of downloaded file viz.>> .tar.bz2 ?!
'Right Click' offers me 2 options; either to open it with Archive Manager or Mount it?

First option takes me to Firefox folder that further contains sub-folders & other file types OTHER than the installer?

Now, what on Earth can make me install this FF 4.0 alpha 2?

---

### Post by Helkaluin on 2010-03-27
May I ask where exactly have you obtained this '4.0' version of FF? So far the newest preview release seems to be 3.7 alpha 3, released 17th March. I thought there're only mockups currently for the 4.0 version.

Regardless, if you want to crash headlong into this dubious '4.0' version, try: [http://www.linuxforums.org/forum/suse-linux-help/50107-how-install-tar-gz-files.html](http://www.linuxforums.org/forum/suse-linux-help/50107-how-install-tar-gz-files.html)

Google is your friend.

---

### Post by Chris_cur on 2010-03-27
1) Open up a terminal
2) type in ```
tar -zxvf nameoftheffalphafile.tar.gz

```3) ```
  ./configure
sudo make
sudo make install

```You will have to enter your password of course, so do that when prompted.

Tars were confusing as heck for me as well when I first started out.

---

### Post by gjoellee on 2010-03-27
> **Helkaluin said:**
> 
Regardless, if you want to crash headlong into this dubious '4.0' version, try: [http://www.linuxforums.org/forum/suse-linux-help/50107-how-install-tar-gz-files.html](http://www.linuxforums.org/forum/suse-linux-help/50107-how-install-tar-gz-files.html)

Google is your friend.

> 1) Open up a terminal
2) type in      Code:
     tar -zxvf nameoftheffalphafile.tar.gz 
3)      Code:
       ./configure
sudo make
sudo make install 
You will have to enter your password of course, so do that when  prompted.

Tars were confusing as heck for me as well when I first started out.**You don't install Firefox tarballs that way!!!!!**

Actually you don't install Firefox with tarballs. What you have to do is to extract the downloaded tarball, and enter the extracted folder. Find the file named "firefox", right click on it and search for the "Allow program to be executable" in the opened window. When you have allowed it to be executed, you simply double click on the "firefox" file to run it. If you kind of want to install it in some way try this:

[http://www.cyberciti.biz/faq/install-firefox3tarbz2-linux/](http://www.cyberciti.biz/faq/install-firefox3tarbz2-linux/)

---

### Post by Chris_cur on 2010-03-27
> **gjoellee said:**
> **You don't install Firefox tarballs that way!!!!!**

Actually you don't install Firefox with tarballs. What you have to do is to extract the downloaded tarball, and enter the extracted folder. 

Sorry. I assumed FF would be the same as other tarballs. I didn't mean to give bad advice.

---

