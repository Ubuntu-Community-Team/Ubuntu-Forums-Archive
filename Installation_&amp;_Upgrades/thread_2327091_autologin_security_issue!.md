---
title: "autologin security issue!"
date: 2016-06-07
forum: Installation &amp; Upgrades
---

### Post by cmcanulty on 2016-06-07
One of the computers I upgraded from xubuntu 14.04 to 16.04 keeps doing autologin to the wrong user. This is a library and I don't want the admin account to be set to autologin. I have set it to the other user in "users and groups" and have it set correctly in /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf but it still always reboots to the admin account. I really need this fixed before some patron gets into our system files

---

### Post by kansasnoob on 2016-06-07
Have a look in "/etc/lightdm/lightdm.conf". Just as an example here's mine with root user set to auto-login:

```
lance@lance-amd-desktop:~$ cat /etc/lightdm/lightdm.conf
[Seat:*]
autologin-guest=false
autologin-user=lance
autologin-user-timeout=0

```

Of course if I wanted the guest user account to auto-login I'd set 'autologin-user' to false instead of lance, and I'd set 'autologin-guest' to true.

I don't use Xubuntu so don't know why it's not working from GUI, or even how to do it with that DE :(

---

### Post by cmcanulty on 2016-06-08
my file sequence is diffent see the screenshots


[ATTACH=CONFIG]269469[/ATTACH][ATTACH=CONFIG]269470[/ATTACH][ATTACH=CONFIG]269471[/ATTACH]

---

### Post by kansasnoob on 2016-06-08
Please read:

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

> LightDM configuration is provided by the following files:

/usr/share/lightdm/lightdm.conf.d/*.conf
/etc/lightdm/lightdm.conf.d/*.conf
/etc/lightdm/lightdm.conf

System provided configuration is stored in /usr/share/lightdm/lightdm.conf.d/*.conf and is not user editable. System administrators can override this configuration in /etc/lightdm/lightdm.conf.d/*.conf and /etc/lightdm/lightdm.conf. Files are read in the above order and combined together to make the LightDM configuration. 

---

