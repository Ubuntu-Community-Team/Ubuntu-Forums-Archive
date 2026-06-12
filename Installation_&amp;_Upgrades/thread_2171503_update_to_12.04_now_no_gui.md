---
title: "update to 12.04 now no gui"
date: 2013-08-31
forum: Installation &amp; Upgrades
---

### Post by Twiggypottox on 2013-08-31
After updating in 12.04 I get a terminal screen After giving username and p/w I then get a terminal prompt. How do I get back to the GUI? And then complete the update.

---

### Post by grahammechanical on 2013-08-31
Why do you say?

> And then complete the update.

Was the update prevented from finishing? That may make a difference to the advice given. 

1) At the Grub menu select Recovery Mode. That will bring you to the Recovery Menu.
2) Select Network. That will read the connection information in Network Manager and establish an Internet connection, and then take you back to the Recovery Menu.
3) Select Root. That will give you a root prompt. Now run

```
apt-get update
```
```
apt-get upgrade
```

You do not need sudo in this case. That will complete the update. Now run

```
exit
```

That will bring you back to the Recovery Menu. Select Resume. That may get you to a desktop but it will be without using a proprietary video driver. If the update brought in an update to the Linux kernel you may need to activate a proprietary video driver. You can do that from Additional Drivers utility. The real test of course is when you shutdown and reboot. What happens then?

Regards.

---

### Post by Twiggypottox on 2013-08-31
Thands Grahmmechanical, 

I said and then complete the update because before the promplt it said : 

6 packages can be updated
0 updates are security


 I ran update & upgrade exit and re-boot per your instructions,

 the update took, I am now back at the prompt.

inplace of the 6 packages.... there is now Welcome to ubuntu 12.04.3 LTS (3.2.0.52 i686)
 it is also a dual boot setup 
It may be worth noting that my original install of 12.04.3 was over kubuntu, (I still get the blue boot screen)   it is also a dual boot setup with win7 On one HDD

How do I start the GUI?

thanks in advance.

---

### Post by ibjsb4 on 2013-08-31
Press Ctrl + Alt + F1 at the same time.  Will this get you to terminal?  If so, try:

```
startx
```

The way I am reading your post, this was a version upgrade to 12.04.  Am I right?

---

### Post by Twiggypottox on 2013-08-31
ibjsb4,

thanks for responding, to answer you questions;

It was supposed to be a simple _update_ of the type regularly done and prompted by the system.  I had previously _upgraded_ to 12.04.3 sucessfully. 

The update had some 50 files and when it finished i was at a terminal prompt saying there were 6 files to install. somehow it lost the ability to get to a gui / or x.



Now running startx gives a no screens found error , fatal error module nvidia173 not found   etc.

---

### Post by ibjsb4 on 2013-08-31
Sounds like you did a [partial upgrade]("http://ubuntuforums.org/showthread.php?t=1859240") and your nvidia driver did not get installed.

---

### Post by Twiggypottox on 2013-08-31
My intent was to update. stay with the lts version.   Something somehow apparently felt differently.  where do I find a guide to install the nvidia driver or otherwise get this problem child back on track.  I am not a wiz at at the command line but can follow instructions.

---

### Post by ibjsb4 on 2013-08-31
Try this in terminal

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by Twiggypottox on 2013-08-31
Thanks again,  ibjsb4,  

Ran the update and upgrade as suggested. no new files added or installed. I'm still in the same place as before, no x no desktop gui.  my username and password take and I get the command line.  x wont start, errors per above: (  a no screens found error , fatal error module nvidia173 not found   etc.)  

this install has been repeatedly upgraded and updated since  at least 11.4  is it time to just start over with a clean new install?

---

### Post by ibjsb4 on 2013-08-31
> this install has been repeatedly upgraded and updated since  at least  11.4  is it time to just start over with a clean new install? 						

That would be a very good idea :)

---

### Post by Twiggypottox on 2013-09-02
And most likely a time saver. Thanks for your efforts.

---

