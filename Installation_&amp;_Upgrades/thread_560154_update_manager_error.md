---
title: "update manager error"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by 9170 on 2007-09-26
Hello everyone.

I believe that I'm in serious trouble! I have tried to download the newest Swiftfox and that doesn't work. As an result of it get I some problems with my ”update manager” that not works and shows me that I have to reinstall the Swiftfox. I have tried all that I can imagine .... apt-get remove; automatix; new download and reinstall with Gdebi.................. and nothing helps! 
I get all the time only one message, please reinstall Swiftfox :confused:


Christian

---

### Post by zvacet on 2007-09-26
```
 sudo apt-get remove --purge package name
```

When you remove Swiftfox 

```
sudo aptitude update
```


and after that try to install again.

---

### Post by 9170 on 2007-09-26
Thanks but, I'm sorry to say this, it doesn't help. 
I have tried it but I get the same error message again, I have to reinstall the Swiftfox.

---

### Post by 9170 on 2007-09-26
It replies me also all the time that it have no “archives” to write it in.

---

