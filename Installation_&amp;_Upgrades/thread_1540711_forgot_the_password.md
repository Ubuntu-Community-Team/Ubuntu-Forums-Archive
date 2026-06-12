---
title: "forgot the password"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by mucmicu on 2010-07-28
Hi there

I;m new to ubuntu and I've installed it but i didnlt use it too much. Now I was trying to login into ubuntu but I forgot the root password. 

Can I login into ubuntu or change the root password. I didn't make any other user than the installation were asking me.

If I try to reinstall the ubuntu, the setup will help me to choose the same partition( to overwrite on the previous ubuntu)?

many thx

---

### Post by mhgsys on 2010-07-28
In the grub menu; 

choose recovery mode; 
This will drop you to instant root.

then go to home folder;
 ```
cd /home/
```

type
```
ls -a
```


You'll find your username there.
then

```
passwd username
```

(replace username with your username)

Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully

reboot, log in with your username and passwd.

---

### Post by Nick_Jinn on 2010-07-28
Could somebody hack into your computer that way?

---

### Post by sisco311 on 2010-07-28
> **Nick_Jinn said:**
> Could somebody hack into your computer that way?

Yes, [thread=989517]Physical access is root access[/thread].

@OP. Take a look at [http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)
for detailed instructions & screenshots.

---

