---
title: "install ubuntu on labtop with windows 7"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by abdo5 on 2011-04-08
Hi all;
I installed 
ubuntu-11.04-beta1-desktop-i386
ubuntu-10.10-netbook-i386

from windows 7 i select to install on same windows7 partition
after installation i select ubuntu and it start up to complete the installation put i get a message:
"**_No root file system please correct this from the partitiong_**"
 

i reinstall again on a vartual machine with windows 7 it worked ok;

i installed it with other pc with windows xp it worked ok

i installed on another labtop the same problem occured.

can any one help me.

thanks

---

### Post by Dutch70 on 2011-04-08
When you get to the screen in the pic below, click the drop down box in front of 'mountpoint" and select "/" aka "root" just as the pic shows.

---

### Post by abdo5 on 2011-04-08
thanks for replay
put actually i did't get like this picture; i install from windows only this dialog appears;

---

### Post by Dutch70 on 2011-04-08
Sorry, I didn't know you were installing inside of windows. I don't know much about that.

---

### Post by reborn7778 on 2011-04-08
> **abdo5 said:**
> thanks for replay
put actually i did't get like this picture; i install from windows only this dialog appears;

wubi installer for try use ubuntu with windows 7, but if u want to boot, then just start up and click ESC, here you go.

---

### Post by madjr on 2011-04-08
w.ub.i (windows ubuntu install) is just for quick try, is not meant for real or permanent use.

you should try other means of install, like live-cd.

check here
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by oldsoundguy on 2011-04-08
What is a "labtop"?

---

### Post by abdo5 on 2011-04-08
msi cr 420
intel core i3-370 M
3G DDR3

---

### Post by abdo5 on 2011-04-08
i can startup and it display complete installing and the error message appear

---

### Post by bcbc on 2011-04-08
> **abdo5 said:**
> Hi all;
I installed 
ubuntu-11.04-beta1-desktop-i386
ubuntu-10.10-netbook-i386

from windows 7 i select to install on same windows7 partition
after installation i select ubuntu and it start up to complete the installation put i get a message:
"**_No root file system please correct this from the partitiong_**"
 

i reinstall again on a vartual machine with windows 7 it worked ok;

i installed it with other pc with windows xp it worked ok

i installed on another labtop the same problem occured.

can any one help me.

thanks
The beta-1 isn't working for Wubi. Beta-2 (when it comes out) or the current daily images for 11.04 will work. Beta's aren't a good idea if you're new to Ubuntu though.

The problem you're having is an issue with Ubiquity - I've seen other cases where there is fakeraid metadata present that confuses ubiquity or a mix of gpt and mbr partition table information.

Boot from the Ubuntu CD, select "Try it" and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results back here.

---

