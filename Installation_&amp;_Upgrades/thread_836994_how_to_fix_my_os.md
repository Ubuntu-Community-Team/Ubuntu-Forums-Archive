---
title: "how to fix my os"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by sclsch on 2008-06-22
I am a freshman. I have installed ubuntu system using wubi. but I forget my password, now I can not login my system. I notice that it has recovery mode ,but do not know how to fix my os . Who can help me? thanks.

---

### Post by jimv on 2008-06-22
See this post:

[http://ubuntuforums.org/archive/index.php/t-3609.html](http://ubuntuforums.org/archive/index.php/t-3609.html)

---

### Post by sclsch on 2008-06-22
ok . it works well, I changed my password .
but I login os. 
the warning is:
  File should be owned by user and have 644 permissions.User's $HOME directory must beowned by user and not writebly by other users.
 
 so I can not login my system. 
 it seems that some permissions are wrong. How can I do?

---

### Post by housam on 2008-06-22
Try this way :[[COLOR="Red"]_http://www.psychocats.net/ubuntu/resetpassword_[/COLOR]]("http://www.psychocats.net/ubuntu/resetpassword"). it may help.

---

### Post by jimv on 2008-06-22
log back into recovery mode

change the owner of your home folder back to you:

```
sudo chown -R your_username /home/your_username
```

and set the correct permissions:

```
sudo chmod -R 644 /home/your_username
```

---

### Post by sclsch on 2008-06-22
I shut down my windows then reboot to ubuntu recovery mode . I select the secode line : the shell ...(may be it is) 
I type :
sudo chown -R scl /home/scl
 but , shows:
no command  message . 
do I type the charactors wrong ??

the second line command works well.

---

### Post by jimv on 2008-06-22
HMmmm.

Are you still not able to log in?

If not, what's the output of this command:

ls -l /home/scl

---

### Post by dakal on 2008-06-22
> **jimv said:**
> and set the correct permissions:

```
sudo chmod -R 644 /home/your_username
```

Be very, very, **very** careful with this. Mode 0644 works well for documents and similar files but will make directories -- including your home directory itself -- inaccessible. More likely, this would be better (note the upper case X):

```
sudo chmod -R u=rwX,go= /home/your_username
```

As for the error in recovery mode, you probably don't even need to use sudo there. Try leaving out the word "sudo" entirely and see if that works any better. Also, shouldn't it be /target/home/your_username or something similar when working from the recovery console?

---

### Post by jimv on 2008-06-23
> **dakal said:**
> Be very, very, **very** careful with this. Mode 0644 works well for documents and similar files but will make directories -- including your home directory itself -- inaccessible. More likely, this would be better (note the upper case X):

```

File should be owned by user and have 644 permissions.User's $HOME directory must beowned by user and not writebly by other users.
```

So the instructions that Ubuntu spat out at him will break his already broken system?

---

### Post by dakal on 2008-06-23
> **jimv said:**
> So the instructions that Ubuntu spat out at him will break his already broken system?

Setting a home directory to mode 0644 (user read/write, group/world read) would very likely cause login attempts to fail, or at the very least drop the user somewhere else, possibly in an undefined environment. A directory needs "execute" permission in order to be accessible, and the home directory contains a number of configuration files that influence the desktop.

That the system is not working properly is absolutely no reason to risk breaking it any further by setting inappropriate permissions.

> **sclsch said:**
> File should be owned by user and have 644 permissions.User's $HOME directory must beowned by user and not writebly by other users.

I don't think of directories as files, even though at a very low file system level I guess that is how they are implemented. To a regular user, they are different beasts and not interchangeable.

---

### Post by sclsch on 2008-06-24
Thank you above. I have rebuild my system with wubi. I will work hard to study ubuntu.

---

