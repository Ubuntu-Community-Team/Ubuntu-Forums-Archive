---
title: "administrator password"
date: 2013-12-01
forum: Installation &amp; Upgrades
---

### Post by HR70s on 2013-12-01
Guys I hope I'm in the right forum.
   Anyway I have 12.04 LTE. I went to install updates and comes autyentication failed. I know my password as I use it all the time. I have used ever method offered
online with no luck to find out what happened to my password. No one else has access to this computer but me. I feel I'm going to have to scrap my harddrive as without
admin. prevledrges I can't do anything. Any ideas would be great..

---

### Post by heir4c on 2013-12-01
Open a terminal and type:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Bucky Ball on 2013-12-01
> **heir4c said:**
> Open a terminal and type:
```
sudo apt-get update && sudo apt-get upgrade
```

That is exactly what they *can't* do. Password has stopped working and can't do updates is the problem. :-k

> **HR70s said:**
>  I went to install updates and comes autyentication failed.

---

### Post by HR70s on 2013-12-01
I tried that and it comes up [sudo] password for ray. I enter my password and it says sorry try again

---

### Post by Bucky Ball on 2013-12-01
This is on the same machine you are typing on now? Thought you might have had the caps lock on and if you're in a terminal typing the password, you wouldn't see it.

Does it work in any other circumstance, like when you open Gparted?

---

### Post by aysiu on 2013-12-01
You have to figure out which of the two is going on:

1. Somehow you've forgotten your password or it's changed... or you have CAPS LOCK on without knowing it... or some other weird thing with your password.

or

2. Somehow your password is fine, but your user is no longer able to perform administrative tasks.

---

### Post by heir4c on 2013-12-01
> **Bucky Ball said:**
> That is exactly what they *can't* do. Password has stopped working and can't do updates is the problem. :-k

I now that but maybe via terminal it will go right OR there are error message and more info via the terminal.

---

### Post by heir4c on 2013-12-01
Change your password (on the left side):
[https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Forgotten-password:-what-to-do](https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Forgotten-password:-what-to-do)

---

### Post by HR70s on 2013-12-02
Caps lock is not on. Yes this is the same computer. I don't know what Gparted is. Anything that requires admin. prevledges I can't do. As I stated before I have used this password
many times. So forgetting my password can't happen. This has really got me dumbfounded.

---

### Post by aysiu on 2013-12-02
The point isn't that you forgot it. Forgetting it or having caps lock or having some other password issue (maybe one not mentioned) is *fundamentally different* from not having administrator rights.

In other words, one of two scenarios is occurring:

1. Ubuntu, for whatever reason, isn't acknowledging your username/password combination as correct

2. Ubuntu recognizes your username/password combination as correct but denies you the ability to authenticate as an admin user

My point wasn't that you forgot your password. My point was that you have to figure out if this is a password-related issue or an admin rights issue. Can you enter your password still for other things okay? For example, if you log out and log back in, your password works for that?

---

### Post by HR70s on 2013-12-02
Update: I found out My root log in password is fine. [This is same password I use for admin. purposes also] So I am at the conclusion that it's something to do with the admin
authentication password only as it does recoginize me as the administrator. At the bottom of the authentication failure dialogue box it has details: org.freedesktop.accounts.user-administration. which I looked up but the site didn't offer any insight that I could see

---

### Post by HR70s on 2013-12-05
This has been resolved: I finally remembered my admin user password. But for future reference. When I did: ls  /home to see all users on my computer only the root
user name shows up. I don't know why the admin user name doesn't show up, I'm not that knowledgable on this sort of thing.
    But thanks for all the support.

---

### Post by aysiu on 2013-12-06
If this is a standard Ubuntu installation (sounds as if it's not), there shouldn't be an active root login. Not saying you can't change the defaults, but that information is important if you want to ask others for tech support.

---

