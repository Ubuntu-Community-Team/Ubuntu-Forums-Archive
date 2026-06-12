---
title: "How to restore gdm?"
date: 2009-08-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by keypox on 2009-08-05
I installed kubuntu-desktop, then tried to uninstall. Now I get no *dm.  Want gdm back. Can I do this?

---

### Post by wayne_cat on 2009-08-05
> **keypox said:**
> I installed kubuntu-desktop, then tried to uninstall. Now I get no *dm.  Want gdm back. Can I do this?

```
sudo gedit /etc/X11/default-display-manager
```enter just one line in the file

```
/usr/sbin/gdm
```
this is what it should look like

```
root@macbook:~# cat /etc/X11/default-display-manager
/usr/sbin/gdm
root@macbook:~# 

```

---

### Post by keypox on 2009-08-06
thanks man i will try this in a bit. Got a plane to catch.

---

### Post by Leighman on 2009-08-06
I'm also having this problem and the suggested solution doesn't work
Whenever I try and install/reenable gdm once I have used kdm it quits with the error
invoke-rc.d: initscript gdm, action "reload" failed
This occurs even when I have removed kdm
Would appreciate some help :D

---

### Post by Zorael on 2009-08-06
```
$ sudo dpkg-reconfigure gdm
```
Alternatively;
```
$ sudo aptitude reinstall gdm
```

---

### Post by Leighman on 2009-08-06
Both those return the same error as above.
This happened once before when I managed to solve it by randomly reinstalling and removing but that doesn't seem to be working this time :P

---

### Post by keypox on 2009-08-06
yeah i am getting the same error
gedit doesnt work either cause not in gui i  think

---

### Post by taavikko on 2009-08-06
> **keypox said:**
> 
gedit doesnt work either cause not in gui i  think

Yes, gedit is GUI editor, if in virtual-console, then one will use "nano" or "vi" or "pico"
for editors.

---

### Post by philinux on 2009-08-06
Use nano instead of gedit.

---

### Post by Leighman on 2009-08-06
I tried with vi, appears to have no effect

---

### Post by Leighman on 2009-08-06
Guess I'm just going to be stuck with kdm for a while :P

---

### Post by wayne_cat on 2009-08-06
> **Leighman said:**
> Guess I'm just going to be stuck with kdm for a while :P

please run these two commands and post the result:

```
cat /etc/X11/default-display-manager
``````
which gdm
```

---

### Post by Leighman on 2009-08-06
The first gives /usr/bin/kdm
I've tried changing that as suggested but that either does nothing or dumps me to command-line
The second gives /usr/sbin/gdm
Cheers

---

### Post by wayne_cat on 2009-08-06
> **Leighman said:**
> The first gives /usr/bin/kdm
I've tried changing that as suggested but that either does nothing or dumps me to command-line
The second gives /usr/sbin/gdm
Cheers

It is quite simple ... change this line in /etc/X11/default-display-manager

```
/usr/bin/kdm
```to

```
/usr/sbin/gdm
```that's all ... now GDM appears after the next reboot

---

### Post by wayne_cat on 2009-08-06
the "error message":

```
invoke-rc.d: initscript gdm, action "reload" failed
```is not a real error ... a script wants to a restart a running GDM ... but GDM is not running. Nothing bad ... just a warning :)

---

### Post by Leighman on 2009-08-06
I suspected that's what you had to do after which gdm :D
As you can see I'm a noob, but why couldn't it manage that itself?
Cheers!

---

### Post by keypox on 2009-08-06
> **wayne_cat said:**
> It is quite simple ... change this line in /etc/X11/default-display-manager

```
/usr/bin/kdm
```to

```
/usr/sbin/gdm
```that's all ... now GDM appears after the next reboot


thank you for working thrpugh this with us

---

