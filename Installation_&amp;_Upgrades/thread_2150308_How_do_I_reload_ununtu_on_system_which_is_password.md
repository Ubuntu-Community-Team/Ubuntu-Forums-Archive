---
title: "How do I reload ununtu on system which is password protected"
date: 2013-05-31
forum: Installation &amp; Upgrades
---

### Post by Siruke on 2013-05-31
I have a 64 bit Dell computer with a HD (from another Dell exactly the same).
The HD has Ubuntu installed on it (so partition already done) but I do not know the password.
I have tried to reset password without success.
I want to reload Ununtu. What would be my best cause of action.
I can get to the root prompt.
I tried loging on as guest and downloading Ubuntu but it did not work.
How can I remove the current Ubuntu?

---

### Post by grahammechanical on 2013-05-31
This link will give you directions on how to download and install Ubuntu from new. That will overwrite the Ubuntu already on the HD. Especially if you select Erase Disk at the install menu.

[http://www.ubuntu.com/](http://www.ubuntu.com/)

---

### Post by Siruke on 2013-05-31
> **grahammechanical said:**
> This link will give you directions on how to download and install Ubuntu from new. That will overwrite the Ubuntu already on the HD. Especially if you select Erase Disk at the install menu.

[http://www.ubuntu.com/](http://www.ubuntu.com/)

I downloaded Ubuntu before while logged on as guest. What happened was  during the download the computer asked for password and as I did not  know the password I could not do anything except power down.
Just tried again. Same thing happened. I think I will have to download and burn a disc on another computer.

---

### Post by Cheesemill on 2013-05-31
If you just want to reset the password for the admin user...

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by need4lightspeed on 2013-05-31
That should work there. (I know) d:J

---

### Post by Siruke on 2013-06-01
> **Cheesemill said:**
> If you just want to reset the password for the admin user...

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

I did that.
root@PC1: # passwd pc1
enter new UNIX password:(here I typed in a 8 letter password. I also tried a 5 letter password)
retype new UNIX password:(same password here)
passwd: Authentication token manipulation error
passwd: password unchanged
rootpc1: #

I did this first: ls /home
mount -0 rw, remount
and
mount rw -0, remount

still no good

Regards
Glen

---

### Post by Siruke on 2013-06-01
I have a secomd computer which I am using to communicate with.
How can I download ubuntu (on this computer) and make a boot disc to boot (and load ubuntu) the other computer with.
I am a bit hesitant to download ubuntu on this computer as I fear I will load ubuntu before having the option to only burn a ubuntu boot disc.

---

