---
title: "help me pleas ... !"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by matt the best on 2008-08-04
Hi people .

I've installed ubuntu 2 months ago , and yesterday my cousin (screw him) shut the power off .

And my system goes down .

And ,

I've installed lots of programs , so I've no intention in reinstall it .

does any body know how to fix it or boot it from the CD ?

I need your help :(

and by the way , my system is 7.10

---

### Post by snowpine on 2008-08-04
Hi Matt, welcome to the forums... what happens if you just turn the power back on?

---

### Post by K2712 on 2008-08-04
And some common admin procedures via the LiveCD can be found here:

[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

---

### Post by matt the best on 2008-08-04
> **snowpine said:**
> Hi Matt, welcome to the forums... what happens if you just turn the power back on?

:)

when I turn it back and open my PC it makes some kind of checking the system , then it tells that some commands is unknown and it terns to the terminal .

---

### Post by ARhere on 2008-08-04
We would love to help but you need to give us more detail.

Please type here what the PC says, "*then it tells that some commands is unknown *"

Something you can try immediately, when the PC is first turned on, you will see a comment to hit the ESC key to enter the GRUB menu.
***EDIT: I removed the image link for fear of having it changed, will post image in next post!***
Select the option (recovery mode) and there are some options to auto-recover.

Again, we need more detail!

-AR

---

### Post by overdrank on 2008-08-04
> **matt the best said:**
> :)

when I turn it back and open my PC it makes some kind of checking the system , then it tells that some commands is unknown and it terns to the terminal .

Ok can you be more specific with the error message. When you reach the command prompt (terminal) what happens if you use the command startx ?
You may try and boot into recovery mode and use the xfix option also.

---

### Post by Vorian Grey on 2008-08-04
It would be helpful to know exactly what the messages say.

---

### Post by ARhere on 2008-08-04
Imgage of GRUB option...

---

### Post by matt the best on 2008-08-04
hi guys .

umm , I can't remember exactly what the it says but kinda :

*** :
command not found .

then :

root@matt:~#

I should try the recovery mode .

---

### Post by overdrank on 2008-08-04
> **matt the best said:**
> hi guys .

umm , I can't remember exactly what the it says but kinda :

*** :
command not found .

then :

root@matt:~#

I should try the recovery mode .

Hi and if it show root@matt then you are in recovery I believe. Use the command startx.

---

### Post by matt the best on 2008-08-04
> **overdrank said:**
> Hi and if it show root@matt then you are in recovery I believe. Use the command startx.

no actually I was in the normal mode , and I tried the recovery mode as well but the same thing appeared .

and I tried startx but that what it tells :

> [SIZE="4"]root@matt-desktop:~# startx
command 'startx' is available in '/usr/bin/startx' 
the command could not be located because '/usr/bin/' is not included in the environment variable .
dash: startx: command not found .[/SIZE]

---

### Post by matt the best on 2008-08-06
any one can help ... !!

don't be so shy , come on and help me . :)

---

### Post by Pumalite on 2008-08-06
See what happens if you do a:
sudo apt-get update
sudo apt-get dist-upgrade
from the command line

---

