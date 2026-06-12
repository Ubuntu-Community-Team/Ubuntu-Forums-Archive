---
title: "Problem with firefox installation"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by KlMASDO444 on 2010-10-01
Hi Guys,
i trying to install firefox with the terminal but i Having Problem with the installation

wget 'http://kyoto-mz-dl.sinet.ad.jp/pub/mozilla.org/firefox/releases/3.6.10/linux-i686/en-US/firefox-3.6.10.tar.bz2'
tar -xjf firefox-3.6.10.tar.bz2
cd firefox
./firefox

problem:
libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory 


Help Please!:guitar:

---

### Post by wojox on 2010-10-01
Did you extract it?

```
tar xjf firefox-*.tar.bz2
```

---

### Post by KlMASDO444 on 2010-10-01
> **wojox said:**
> Did you extract it?

```
tar xjf firefox-*.tar.bz2
```

yes man

---

### Post by snowpine on 2010-10-01
Firefox is in the Ubuntu repositories, so you can easily install it using the Software Center or the terminal command:

```
sudo apt-get install firefox
```

In fact, Firefox should be installed already (unless you did a custom/minimal install). :)

---

### Post by KlMASDO444 on 2010-10-01
> **snowpine said:**
> Firefox is in the Ubuntu repositories, so you can easily install it using the Software Center or the terminal command:

```
sudo apt-get install firefox
```

In fact, Firefox should be installed already (unless you did a custom/minimal install). :)

[B]I Know  to do apt-get but i dont want it

Show Me Who Can I to install firefox with wget . . .. . . . . .Please[/B]

---

### Post by wojox on 2010-10-01
What does this tell us:

```
uname -a
```

---

### Post by KlMASDO444 on 2010-10-01
> **wojox said:**
> What does this tell us:

```
uname -a
```


Linux ubuntu 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:58:24 UTC 2010 x86_64 GNU/Linux

---

### Post by wojox on 2010-10-01
Try installing the 32 bit libraries:

```
sudo apt-get update; sudo apt-get install ia32-libs-libnss3 ia32-libs-gtk
```

---

### Post by KlMASDO444 on 2010-10-01
> **wojox said:**
> Try installing the 32 bit libraries:

```
sudo apt-get update; sudo apt-get install ia32-libs-libnss3 ia32-libs-gtk
```

yair@ubuntu:~$ sudo apt-get install ia32-libs-libnss3 ia32-libs-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs-libnss3
yair@ubuntu:~$

---

### Post by wojox on 2010-10-01
I think I'm in Fedora land. Try

```
sudo apt-get update; sudo apt-get install ia32-libs
```

Or download a 64 bit version [http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/)

---

### Post by KlMASDO444 on 2010-10-01
> **wojox said:**
> I think I'm in Fedora land. Try

```
sudo apt-get update; sudo apt-get install ia32-libs
```

Or download a 64 bit version [http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/)

**thanks but i hava know erors in the terminal but firefox is uploading**

eror:


** (firefox-bin:3807): WARNING **: Can not stat /tmp/orbit-yair

GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

---

### Post by KlMASDO444 on 2010-10-02
help Please!

---

### Post by KlMASDO444 on 2010-10-02
Hi,
Last Errors in run firefox :

./firefox
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

---

