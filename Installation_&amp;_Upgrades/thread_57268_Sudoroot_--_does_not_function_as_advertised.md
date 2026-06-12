---
title: "Sudo/root -- does not function as advertised"
date: 2005-08-15
forum: Installation &amp; Upgrades
---

### Post by j.hill on 2005-08-15
I've always heard that Ubuntu's distinguishing feature is that the root account is disabled by default and administration is done through sudo.  However, I have now installed Hoary twice, and both times the installer has created a root account.  Moreover, when I try to sudo, I am warned that I am not on the sudoers list and "this incident will be reported."  (To whom, I wonder, since I am the only user on this system and thus I am root?)

From a practical perspective this is not a big deal.  I added myself to the sudoers list, and all is good.  But I'm curious about why this happens.  My theories at the moment are:

1.  I have a defective installation CD
2.  I misunderstood this whole disabled-root-account deal, and actually it means something different

Anyone care to enlighten me?

---

### Post by GreyFox503 on 2005-08-15
I don't know why yours is different, but I installed the plain Ubuntu 5.04 without anything special worth noting, and my root account did not have a password, and therefore I could not log into it until I set one myself.  I don't ever remember the installer asking about the root account, either.

And I was also automatically put on the sudoers list.

So Ubuntu did this correctly on my comp. but I wonder why it would be any different for you?

---

### Post by heimo on 2005-08-15
[QUOTE=j.hill]
Anyone care to enlighten me?[/QUOTE]

Did you use server or expert install?

---

### Post by j.hill on 2005-08-16
> Did you use server or expert install?

Expert.

---

### Post by heimo on 2005-08-16
[QUOTE=j.hill]Expert.[/QUOTE]

I think expert install (possibly server too) behaves differently and sets the root password. That's the reason.

---

### Post by nocturn on 2005-08-16
Your installation is correct.  The root account must exist (to run init).
By disabled, Ubuntu means that you cannot log in as root (no password).

---

### Post by j.hill on 2005-08-16
[QUOTE=heimo]I think expert install (possibly server too) behaves differently and sets the root password. That's the reason.[/QUOTE]

Since you're more likely to be a sysadmin if you're using the expert install...that makes sense.

---

### Post by bin on 2005-08-16
[QUOTE=j.hill]Moreover, when I try to sudo, I am warned that I am not on the sudoers list and "this incident will be reported."  (To whom, I wonder, since I am the only user on this system and thus I am root?)

From a practical perspective this is not a big deal.  I added myself to the sudoers list, and all is good.  But I'm curious about why this happens.  My theories at the moment are:

1.  I have a defective installation CD
2.  I misunderstood this whole disabled-root-account deal, and actually it means something different

Anyone care to enlighten me?[/QUOTE]

Don't use sudo, use su

e.g. su apt-get install blah

NOT sudo apt-get install blah

you'll be prompted for a password which is the one you create on installation

in light

bin

---

### Post by j.hill on 2005-08-16
[QUOTE=bin]Don't use sudo, use su

e.g. su apt-get install blah

NOT sudo apt-get install blah

you'll be prompted for a password which is the one you create on installation

in light

bin[/QUOTE]

Why?  I use sudo all the time -- how is su different?  It sounds just like sudo.  When I use sudo, the computer asks for my password, and it's all good.

---

### Post by bin on 2005-08-16
Sorry, I'm talking absolute rubbish..... I'm working in Mepis at the moment and got my wires crossed.

---

