---
title: "sudo aptitude safe-upgrade ... following packages have been kept back"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by boondocks on 2008-05-23
I am doing a:

  sudo   aptitude   safe-upgrade
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
[COLOR="Red"]The following packages have been kept back:
  openssh-client openssh-server ssl-cert
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.[/COLOR]
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
```How do I upgrade these 3 ssh packages?
I only have remote ssh access to this Ubuntu 8.04 system.

---

### Post by iaculallad on 2008-05-23
> **boondocks said:**
> I am doing a:

  sudo   aptitude   safe-upgrade
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
[COLOR="Red"]The following packages have been kept back:
  openssh-client openssh-server ssl-cert
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.[/COLOR]
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
```How do I upgrade these 3 ssh packages?
I only have remote ssh access to this Ubuntu 8.04 system.


I think this could not be possible for it will kill the current SSH session on the remote system. Upgrading SSH could only do this on the remote system itself. Ideas?

---

### Post by zvacet on 2008-05-23
```
sudo aptitude install  openssh-client openssh-server ssl-cert
```

---

### Post by boondocks on 2008-05-23
> **zvacet said:**
> ```
sudo aptitude install  openssh-client openssh-server ssl-cert
```

zvacet,
How will this impact my remote ssh login?
If I get kicked out of the ssh, can I log back in later?
To get to this **remote** system, I would need to take a 12-hour flight!
So I need to be sure.

---

### Post by oys on 2008-05-23
> **boondocks said:**
> zvacet,
How will this impact my remote ssh login?
If I get kicked out of the ssh, can I log back in later?
To get to this **remote** system, I would need to take a 12-hour flight!
So I need to be sure.

Maybe install and test something like phpshell, telnet (gasp) or other alternative way of accessing the system in case something goes wrong.

Another tip if you're playing around with something that may cut you off (e.g. firewall rules) is to run sleep 3600 && reboot & in a screen window. If things work out the way you expect, kill the reboot process. If not, your system will reboot in an hour and hopefully you'll be able to reconnect.

A last piece of advice for future situations is to have an old laptop low-power mini-itx pc with a serial port so that you can get console access going via this.

---

### Post by frankos44 on 2008-05-29
> **zvacet said:**
> ```
sudo aptitude install  openssh-client openssh-server ssl-cert
```

Thanks, 1 down 2 to go. It now reports 2 not upgraded?

---

### Post by frankos44 on 2008-05-29
> **frankos44 said:**
> Thanks, 1 down 2 to go. It now reports 2 not upgraded?

Sorted. In my case:

sudo aptitude install openssh-client openssh-server ssl-cert
sudo aptitude install linux-image-server linux-server

---

### Post by frankos44 on 2008-05-29
> **boondocks said:**
> zvacet,
How will this impact my remote ssh login?
If I get kicked out of the ssh, can I log back in later?
To get to this **remote** system, I would need to take a 12-hour flight!
So I need to be sure.

No issue, I was able to upgrade my server without affecting the ssh session in use at the time.

I do recommend you type rm ~/.ssh/* on your local PC afterwards so to recreate the keys. 

It will also be wise to re-create the certificate CSR if you are using SSL. Its a pain I know.

---

### Post by boondocks on 2008-05-29
Thanks zvacet for the original suggestion.
Thanks frankos44 for doing the remote ssh "sudo aptitude install ..."

I followed these steps and it is working for me.

I am doing the dance of joy! :)

---

