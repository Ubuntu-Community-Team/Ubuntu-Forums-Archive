---
title: "ubuntu auto login"
date: 2015-12-23
forum: Installation &amp; Upgrades
---

### Post by smokeyone2 on 2015-12-23
Hello

Even though I am sure I set the installation to auto login my desktop keeps asking for a password upon start up - search the forum it seems I need to alter the /etc/lightdm/lightdm.conf
file but where do I find this file please - I do hope I have this correct -

SeatDefaults]
autologin-guest=false
autologin-user=password
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=ubuntu
greeter-session=lightdm-gtk-greeter 			 		

Many thanks

---

### Post by deadflowr on 2015-12-23
Do you have a user named password?

---

### Post by smokeyone2 on 2015-12-23
I just did a copy and past - so change password -

SeatDefaults]
autologin-guest=false
autologin-user=smokeyone2
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=ubuntu
greeter-session=lightdm-gtk-greeter                      

Thanks but still do not know where  /etc/lightdm/lightdm.conf is to be found -

---

### Post by deadflowr on 2015-12-23
Is SeatDefaults] wriiten as is, or does it read
[SeatDefaults] <<This is the proper way, btw.
It needs to be encapsulated in brackets.

---

### Post by smokeyone2 on 2015-12-23
Is SeatDefaults] was wriiten as is - so it should all read -

[SeatDefaults] 
autologin-guest=false
autologin-user=smokeyone2
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=ubuntu
greeter-session=lightdm-gtk-greeter

---

### Post by deadflowr on 2015-12-23
> **smokeyone2 said:**
> Is SeatDefaults] was wriiten as is - so it should all read -

[SeatDefaults] 
autologin-guest=false
autologin-user=smokeyone2
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=ubuntu
greeter-session=lightdm-gtk-greeter

Basically yes.
Does it work properly, or is their still more to do?

Though doing a quick look at autologin-session and user-session I don't think both are needed.
As autologin-session's settings override user-session.

---

### Post by smokeyone2 on 2015-12-24
I am still stuck as I do not know where the /etc/lightdm/lightdm.conf
file is kept or how to alter it - if this is the correct file -

---

