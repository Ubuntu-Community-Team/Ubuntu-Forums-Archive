---
title: "No login with upgrade to 12.04"
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by joelgsf on 2012-09-06
I have upgraded my desktop system online from 10.04 to 12.04, after having so upgraded my notebook with success. It seemded to have gone all well but, after restarting the system, I could not have access to it anymore. I am the only registered user and it is not accepting my password, though it does not say so, simply returning to the login box after blanking the screen a while.
At first I thougt that it could have been some "glitch" which had altered my password. I've got access to a "root terminal" restoring my old password, but it was useless. I still can't have access to the system.
Any hints? I'm really desperate to get access to the system, as this is my "workhorse".
Thank you for any help.

Joel Guilherme

---

### Post by dino99 on 2012-09-06
As i can remember:
- 10.04 is using gdm, but 12.04 use lightdm
- 12.04 lightdm use by default unity-greeter

so the questions are :
- is gdm been purged ?
- are you login with lightdm ?

To get around:
- boot in recovery mode and select root session, then check the above packages.

If you then still get troubles, erase the hidden files: .gconf, .local, .gnome2, .config ; they will be cleanly recreated on next boot (but without your custom settings)

---

### Post by joelgsf on 2012-09-06
Thank you, dino99, but I've tried all your sugestions without success. What didi worked was to force gdm to be the default display manager with
```

sudo apt-get install gdm
sudo dpkg-reconfigure gdm
sudo shutdown -r now
```
as I found in [http://askubuntu.com/questions/130387/stuck-at-login-screen]("http://askubuntu.com/questions/130387/stuck-at-login-screen"), in a post by Shah.
This way I get the "old style" login page, but it works. I still don't know why lightdm doesn't work, but that's another problem.
Thanks anyway.

---

