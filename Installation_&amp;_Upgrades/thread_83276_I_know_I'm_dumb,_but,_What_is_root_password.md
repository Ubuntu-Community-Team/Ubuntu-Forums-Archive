---
title: "I know I'm dumb, but, What is root password?"
date: 2005-10-28
forum: Installation &amp; Upgrades
---

### Post by ntony on 2005-10-28
I've searched post and troubleshoot and starter guide. I'm sorry to ask a silly question here. Yes, I'm new and noob.

root password was not asked to input during installation. I've tried the user password that the installation asked for, but no luck.

Any kind ladies or gentlemen would help a noob? Thanks!

---

### Post by stuporglue on 2005-10-28
The root account isn't enabled on Ubuntu, by default. 

Instead of changing to root, you can use sudo to run commands *as* root, but from your normal user by running sudo. To use sudo, prefix the command you want to run with the command sudo. Sudo checks a list of allowed users, then prompts you for your password. If the list and password check out, it'll run the command as root. 

examples:

$ sudo vi /etc/X11/xorg.conf
password:

(opens file in vim)

Doing it with sudo is more secure since you can't accidentally run commands as root.

---

### Post by ntony on 2005-10-28
[QUOTE=stuporglue]The root account isn't enabled on Ubuntu, by default. 

Instead of changing to root, you can use sudo to run commands *as* root, but from your normal user by running sudo. To use sudo, prefix the command you want to run with the command sudo. Sudo checks a list of allowed users, then prompts you for your password. If the list and password check out, it'll run the command as root. 

examples:

$ sudo vi /etc/X11/xorg.conf
password:

(opens file in vim)

Doing it with sudo is more secure since you can't accidentally run commands as root.[/QUOTE]



Thanks a lot, stuporglue! I think I got what you mean. But the password that was prompted to enter, is that the password I entered for the first user?

---

### Post by stuporglue on 2005-10-28
> Thanks a lot, stuporglue! I think I got what you mean. But the password that was prompted to enter, is that the password I entered for the first user?

Yes. It is your users password. If you had two admin accounts on your computer, each user would use their own password.

Note that this way when one user left (a company, a dorm room, a whatever, demotion, lack of trust) you could just change their account to a non-admin account and they suddenly don't have root access. There's no need to change the root password whenever someone's status changes.

---

### Post by ntony on 2005-10-28
Thanks a lot, stuporglue!

---

### Post by CrunchyDoodle on 2005-10-28
When I want to do more than one command as root, I enter:

$ sudo -s
password:

Now I am root until I exit.

Bye.    :cool:

---

