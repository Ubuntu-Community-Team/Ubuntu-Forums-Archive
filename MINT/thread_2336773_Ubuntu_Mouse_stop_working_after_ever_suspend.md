---
title: "Ubuntu Mouse stop working after ever suspend"
date: 2016-09-11
forum: MINT
---

### Post by jaapjaa on 2016-09-11
Hello,

Today I finally decided to switch from Windows to Ubuntu.
I did fully install Ubuntu, but everytime my notebook goes in subspend  and wakes up my mouse will not work anymore. When I do a reboot it works  fine until I let it subspend even if I subspend and wake it up in like 1sec.

So I was like oke no Ubuntu for me so I downloaded Mint and did install  it, even with mint I got the same problem im trying to fix it for the  whole day without any succes. 
I hope you guys can help me!

Notebook:
Asus laptop

On almost all forum post this was the fix:	
sudo apt-get install --reinstall xserver-xorg-input-all

But not for me..

---

### Post by howefield on 2016-09-11
So are you working with a Mint installation, what desktop environment ?

Does this work after waking from suspend ?

Press the Ctrl + Alt + F1 keys to get to a tty then Ctrl + Alt + F7 to get back to the desktop ?

---

### Post by jaapjaa on 2016-09-11
Thanks for the respond. I am currently running Mint wanted to try if it was just ubuntu but no:P

Mint 18 Cinnamon

I tryed what you askt but stil cant move my mouse after that.

Btw: 
When I wake up I cant use my mouse on the login screen also

---

### Post by ajgreeny on 2016-09-11
*Thread moved to **MINT**.* which is more appropriate for the problem.

---

### Post by jaapjaa on 2016-09-11
Could you link the post plz

---

### Post by howefield on 2016-09-11
> **jaapjaa said:**
> Could you link the post plz

You are posting in it, ajgreeny just moved the thread to a different sub forum appropriate to the operating system that you are using.

If you are using intel graphics it could be this bug [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604) which I believe has a fix released recently. Perhaps you could make sure that your system is fully updated ?

---

