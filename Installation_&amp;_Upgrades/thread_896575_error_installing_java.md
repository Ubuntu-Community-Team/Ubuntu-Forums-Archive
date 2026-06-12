---
title: "error installing java"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by parapaali on 2008-08-21
I have tried to install sun java in ubuntu 8.04 but get the error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

How do i do that?:P

---

### Post by Vivaldi Gloria on 2008-08-21
> **parapaali said:**
> I have tried to install sun java in ubuntu 8.04 but get the error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

How do i do that?:P

Start "terminal" from apps menu > accessories. Then type

```
sudo dpkg --configure -a
```

and press enter. This should fix it.

---

### Post by meyer99 on 2008-08-21
Just downloalded jre-6u7-linux-i586.bin
I d clik to launch application and system is asking me to choose an application to open link.
What should I choose? from which folder?

Thank you/

---

### Post by Vivaldi Gloria on 2008-08-21
Can't you install using synaptic?

system menu > admin > synaptic

Enable restricted and multiverse repositories from the repository settings to get a more complete list. Then click refresh. 

Now you can search and install whatever you want in synaptic. For example search and install

```
ubuntu-restricted-extras
```

which contains java, codecs, and other goodies.

---

### Post by meyer99 on 2008-08-21
First time with Ubuntu. No clue how to implement your suggestion. Could you post a couple of jpg's so I can see.
Thanks a lot.

---

### Post by tangibleorange on 2008-08-21
> **meyer99 said:**
> First time with Ubuntu. No clue how to implement your suggestion. Could you post a couple of jpg's so I can see.
Thanks a lot.

try typing this at a terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

and see what happens.

---

### Post by meyer99 on 2008-08-21
Tangible and Gloria: thanks
Is downloading a lot of stuff. When it finishes it will be all set?

---

### Post by tangibleorange on 2008-08-21
> **meyer99 said:**
> Tangible and Gloria: thanks
Is downloading a lot of stuff. When it finishes it will be all set?

should be. after its done, just open firefox and try going to a page with java on it. BTW that package also installs flash and MP3 plugins.

also if you want the java development kit (for creating java programs), you need this command:

```
sudo apt-get install sun-java6-jdk
```

---

