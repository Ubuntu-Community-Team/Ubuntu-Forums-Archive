---
title: "FLah drive iNSTALL"
date: 2022-11-25
forum: Installation &amp; Upgrades
---

### Post by John_Carver on 2022-11-25
I have successfully installed the 22.0 version of Ubuntu on a flash drive.
My only issue is there was not a login/password required.
My scanner program did not connect to my scanner device (but did connect to the printer)
I wanted to login into Cups to see if it could be corrected but Cups requires a login credentials 
This is somewhat of a strange issue but can probably be resolved with someone smarter than I

---

### Post by ubfan1 on 2022-11-25
Could it be you just set up an install media -- username ubuntu, no pw.  An install will ask your for a username and allow you to login without a password, but the default is to require a pw. What do you see when you boot grub?  If it's "try", install, ...  and the desktop comes with an install icon, then definitely an install media

---

### Post by ajgreeny on 2022-11-25
Open up a terminal and tell us what the prompt that you see is; I think it will probably be **ubuntu@ubuntu:~$** in which case you simply have a live system, not an installation of Ubuntu

---

### Post by John_Carver on 2022-12-06
I thought I had what I would call an installation and have [B]ubuntu@ubuntu:~$
The install went really well and all else seems normal but not having the scanner work is all that isn't working
You would think that having a working printer would help.  
This ain't the end of the world and will live with what I have
[/B]

---

### Post by yancek on 2022-12-07
As indicated above, you have a 'live' usb which means that no changes are saved on reboot so even if you found a method to enable using the scanner, you would need to repeat the process on each boot.  Using it without the scanner capability is your only option.

---

### Post by grahammechanical on 2022-12-07
> This ain't the end of the world and will live with what I have

If "the end of the world" comes sooner than expected you could try installing Ubuntu with persistence. Then any changes to the OS will remain after shutdwon.

[https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

Regards

---

### Post by C.S.Cameron on 2022-12-09
In a Persistent install you can add yourself as a new user using Settings/User.

---

