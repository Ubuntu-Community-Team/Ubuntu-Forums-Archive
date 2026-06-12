---
title: "Instaling Java Version 7 Update 67"
date: 2014-08-13
forum: Installation &amp; Upgrades
---

### Post by Supersonicx10 on 2014-08-13
I'm trying to intall Version 7 Update 67 into Ubuntu, howerver i'm having problems with the install I've already look at the other foums dealing with this problem, but they are no help. Can any one help me? 

jre-7u67-linux-i586.tar.gz

---

### Post by QIII on 2014-08-13
Hello!

Make this easy on yourself.  Take a look at the Java link in my signature and find "Using webupd8.org's strikingly simple method."

It's in both the Oracle Java 7 and Oracle Java 8 sections.

---

### Post by Supersonicx10 on 2014-08-18
> **QIII said:**
> Hello!

Make this easy on yourself.  Take a look at the Java link in my signature and find "Using webupd8.org's strikingly simple method."

It's in both the Oracle Java 7 and Oracle Java 8 sections.

Ok what do I do next?

---

### Post by QIII on 2014-08-18
Did you follow the instructions in one or the other of the webupd8.org links I pointed out in the wiki?

---

### Post by Supersonicx10 on 2014-08-21
Yes but it's a little hard to understand?

---

### Post by QIII on 2014-08-21
Shouldn't be too hard to understand.

If you want Oracle Java 7, all you need to do is issue the following commands in the terminal, in order, one at a time:

```
sudo add-apt-repository ppa:webupd8team/java
```
to add the Personal Package Archive

```
sudo apt-get update
```
to update your database

```
sudo apt-get install oracle-java7-installer
```
to install.  You have to agree to the terms in this step.

Then, to check your version, do
```
java -version
```

If you have done the first three, could you do the last and post the results back here?

---

### Post by Supersonicx10 on 2014-08-22
Well I tried the  sudo apt-get update and it worked I was able to update Java thanks thanks for your help.

---

