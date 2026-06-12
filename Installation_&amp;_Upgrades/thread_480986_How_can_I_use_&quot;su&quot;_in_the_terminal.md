---
title: "How can I use &quot;su&quot; in the terminal?"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by green_earth on 2007-06-22
I'm trying to install the Novell GroupWise Linux client on my ubuntuized laptop such that I might access my work email and contacts. Part of the install instructions tell me to do the following:
>    1. Open a terminal window.
   2. Change to the temp directory where you extracted the GroupWise client code from above.
   3. Enter xhost + localhost.
   4. In the same terminal window, become root by entering su and the root password.
   5. Enter ./install.
   6. To start the Cross-Platform client after installation, click the GroupWise icon on your Linux desktop.


When I entered "su" it told me:
> su: Authentication failure
Sorry.

I'm a total newbie, as new as they come. Any help is appreciated!

---

### Post by onegreenparker on 2007-06-22
Try
```

sudo ./install

```
then enter your password....

---

### Post by jpkotta on 2007-06-22
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Vola on 2007-06-22
if you want root console:

sudo -i 

if you want to set root password

sudo passwd

---

### Post by BobJ on 2007-06-22
Thank you very much

BobJ

---

### Post by dechef on 2007-06-22
op you got the sudo thing right :- 
just to say:- its more of a root authorisation for one to perform administrative tasks. Thats just the wonderful part of Linux my son :)
sudo -i

---

### Post by green_earth on 2007-06-22
Thanks for all your responses... all I've tried so far is "sudo ./install". This got me past the main issue I previously outlined, but I still got an error (illegal action 20 or something like that) that seemed to repeat endlessly in the terminal window (I just had to close it). 

I'm going to try some of the other responses here and get back. Thanks again for your input. I'm amazed at how helpful this ubuntu forum is; as far as a true "help" forum, I've never seen the like!

---

### Post by kerry_s on 2007-06-23
do> sudo su
you will then be root.

---

