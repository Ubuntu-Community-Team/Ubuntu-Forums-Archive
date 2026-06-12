---
title: "sudo doesn't work!?! wtf?"
date: 2005-03-02
forum: Installation &amp; Upgrades
---

### Post by plesk on 2005-03-02
OK fristly ubuntu! Great distro! a debian based distro that works for me! but doing sudo <whatever> asks for a password? wtf? the only way I could get root was via booting from the live cd and mounting /dev/hda1 and chrooting to it and doing passwd. I am not looking support, I am just wondering why it dosen't work... Anybody offer any ideas?? BTW its not a bad download because I have 50 ubuntu disks! (Only got 3 left! hehe!) Thanks in advance! 

Plesk

---

### Post by lao_V on 2005-03-02
You need to enter your **user password** when you try to do something in sudo!!!!

---

### Post by plesk on 2005-03-02
[QUOTE=lao_V]You need to enter your **user password** when you try to do something in sudo!!!![/QUOTE]
 Ok thats crazy but it works! Thanks for the quick reply!

---

### Post by lao_V on 2005-03-02
Its not crazy. Its a security feature which allows to log all the activity done with superuser privilage

---

### Post by az on 2005-03-02
It is called priviledge escallation.

---

### Post by lao_V on 2005-03-02
A good site for ALL your sudo information.

[http://www.gratisoft.us/sudo/](http://www.gratisoft.us/sudo/)

---

### Post by plesk on 2005-03-02
Why i said its crazy is because I have to enter my own password to do something as root... its mad!

---

### Post by Marauder1 on 2005-03-02
No it's not, you have to remember only one password !!!
You installed it so you would know both passwords anyway !!! :wink:

---

### Post by lao_V on 2005-03-02
There is an advantage of having to only remember one password. 

However, in an unwished situation of an intruder gaining control over my pc (and my user password) he can also gain access as root!!! I'm not sure how having sudo in that situation helps???

---

### Post by Marauder1 on 2005-03-02
Still better then Windblows and their "Everyboby ia an Administrator" policy.
And if you dont like it, just make a password for root !!!

Bye. \\:D/

---

