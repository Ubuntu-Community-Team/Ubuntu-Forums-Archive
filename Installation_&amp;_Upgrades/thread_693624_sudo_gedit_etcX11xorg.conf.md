---
title: "sudo gedit /etc/X11/xorg.conf"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by mistypotato on 2008-02-11
**sudo gedit /etc/X11/xorg.conf**



I've installed Server 7.04 and this command does NOT work nor does gedit exist.

What is the equivalent in SERVER 7.04 and how do I edit the video configuration in SERVER 7.04?



Thanks!

---

### Post by Seisen on 2008-02-11
Try ```
sudo vim /etc/X11/xorg.conf 
``` or ```
sudo nano /etc/X11/xorg.conf
```

---

### Post by jrib on 2008-02-11
sudo nano /etc/X11/xorg.conf

---

### Post by mistypotato on 2008-02-11
Thank you fellas

---

### Post by mistypotato on 2008-02-11
sudo nano /etc/X11/xorg.conf




The response is.......


Error opening terminal: bterm

---

### Post by mistypotato on 2008-02-11
**find xorg**


the response is......

[COLOR="Red"]No such file or directory[/COLOR]



**find X11**

the response is......

[COLOR="Red"]No such file or directory[/COLOR]

---

### Post by PmDematagoda on 2008-02-11
First of all did you install the X-Server packages before trying the commands out?

---

### Post by mistypotato on 2008-02-11
I inserted the CD (Ubuntu Server 7.04) and let it run.

I never saw such a choice or option.


I cannot get past 

**STARTING UP........**

It reboots

---

### Post by hyper_ch on 2008-02-11
well, the server does not have X installed ;)

If you want a desktop:

```

sudo apt-get install ubuntu-desktop

```
or
```

sudo apt-get install kubuntu-desktop

```
or
```

sudo apt-get install xubuntu-desktop

```

---

### Post by mistypotato on 2008-02-11
Thank you for trying.

But the response for ALL of these is.......



**Couldn't find package (name of package)**

---

### Post by mistypotato on 2008-02-11
Does anyone know if it would be better to first install 6.06 (NON server edition), get that working THEN install the server edition over that?

---

### Post by zvacet on 2008-02-11
```
sudo nano /etc/apt/sources.list
```

add this line 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse

crtl+o ctrl+x

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Ayuthia on 2008-02-11
> **zvacet said:**
> ```
sudo nano /etc/apt/sources.list
```

add this line 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse

crtl+o ctrl+x

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install ubuntu-desktop
```
If you cannot use nano, you can add the repository by using this:
```
echo 'deb http://archive.ubuntu.com/ubuntu dapper universe multiverse'|sudo tee -a /etc/apt/sources.list
```

---

### Post by mistypotato on 2008-02-11
Thanks Ayuthia (and others who tried to help),

I WILL try your suggestions:KS

I really like Ubuntu and it's running great on one desktop that we use.  But DARN that 7.04 server edition!
Could not get it working so for now, I've put a WindowsXP server back in it's place and will go back to trying again another time.

Best Wishes !

---

