---
title: "low graphics mode  error on every boot"
date: 2012-11-29
forum: Installation &amp; Upgrades
---

### Post by avidesh on 2012-11-29
I have Ubuntu 12.10

I get an error that says
```
 The system is running in low-graphics mode
```
I get this error on every boot.
I after I click ok, I get an option to run in low graphics mode for this one session.

When I click ok everything works fine.

But I keep getting this annoying message every time.

How do I fix it?

---

### Post by dino99 on 2012-11-29
some driver like nvidia actually do weird things, so better to use nouveau.

what you can try:

sudo rm /etc/X11/xorg.conf
then reboot

and/or purge then reinstall the graphic driver, then reboot

---

### Post by avidesh on 2012-11-30
No that did not work.

I read on the forums somewhere that this may be a greeter issue. The post suggested readers to change the greeter from lightdm-gtk-greeter to unity-greeter in lightdm.conf file

I changed it. Now the error does not appear & I get a login prompt (despite of autologin being on)

but despite of entering the password, it does not sign me in. instead the same login screen appears.

I tried the guest login, that works but it wont accept my login.

now I am stuck.

---

### Post by 2F4U on 2012-11-30
> I tried the guest login, that works but it wont accept my login.

If you are able to login with another user, there seems to be a problem with the configuration of your main user. Try if you can get to a console by pressing Ctrl-Alt-F1 and login. Your home folder should contain a file .xsession-errors, which probably contains more information about what fails.

---

