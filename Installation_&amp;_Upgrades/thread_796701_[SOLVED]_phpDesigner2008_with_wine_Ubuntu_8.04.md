---
title: "[SOLVED] phpDesigner2008 with wine? Ubuntu 8.04"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by ThePHPguy on 2008-05-16
Hello, I just switched over to Ubuntu last night and I really like using Ubuntu. My only problem is I can't get my favorite PHP editor to work ([phpDesigner2008](http://mpsoftware.dk/phpdesigner.php)).

I installed the latest version of WINE and installed phpDesigner successfully but when I try to run it I get this error.

```

Exception EAccessViolation in module phpDesigner2008.exe at 800030001
Acess violation at adress 8000400. Read of address 80004001.

```

Thanks in advance.

---

### Post by yogo on 2008-05-16
Personally I like Rapid PHP much better but last time I had the same type of issues when trying to run it in Wine, I may try it again to see what happens.


ETA, just downloaded a trial of Rapid PHP and it installed without any error, looks like it will work good, the gui is much different than before, I like the improvements.

---

### Post by ThePHPguy on 2008-05-16
Well... I've been googling but I have yet to find a solution :( So is there another way to install XP programs on Ubuntu 8.04?

---

### Post by ThePHPguy on 2008-05-16
Oops I just saw your edit.

Thanks For The Help

---

### Post by yogo on 2008-05-16
> **ThePHPguy said:**
> Oops I just saw your edit.

Thanks For The Help


I think you will love the way Rapid php implements FTP transfers. It has the best ability of ftp transfers of any editor. I know php designer had many problems with bugs in the ftp but this was back in 2005.

Anyways, it works great for editing on the fly and with php, that is the only way to go IMO.

---

### Post by 3StrikesDesign on 2008-10-15
To get phpDesigner 2008 working correctly with Wine you need to run the following command as the user which you are logged in as.

wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks) && sh winetricks msxml3

---

