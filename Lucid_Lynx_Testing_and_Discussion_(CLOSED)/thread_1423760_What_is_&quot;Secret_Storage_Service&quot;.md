---
title: "What is &quot;Secret Storage Service&quot;???"
date: 2010-03-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by KrazyPenguin on 2010-03-07
Just wondering what is the "Secret Storage Service" in Startup Applications??

I didn't notice it in Karmic and was wondering if it can be disabled.

thanks

---

### Post by KrazyPenguin on 2010-03-07
Any ideas???

I'm now thinking this stores my password to my wireless internet connection.

---

### Post by KrazyPenguin on 2010-03-07
Here is a screenshot and I have it disabled.

---

### Post by exploder on 2010-03-07
It's a secret... :D

Kind of like my system freezing problem, if you get what I am saying.

---

### Post by KrazyPenguin on 2010-03-07
> **exploder said:**
> It's a secret... :D

Kind of like my system freezing problem, if you get what I am saying.

Aren't you the guy with the frozen laptop?? ;-)
If so , editing the stanzas in grub might solve your problem.
( nolapic noapic no acpi etc)

---

### Post by 23meg on 2010-03-07
It's a daemon that's used by GNOME Keyring that stores your passwords and other secrets, based on the freedesktop.org secret storage spec.

---

### Post by buzzmandt on 2010-03-07
is that similar to kwallet?

---

### Post by 23meg on 2010-03-07
> **buzzmandt said:**
> is that similar to kwallet?

It's *used by* it.

---

### Post by Reiger on 2010-03-07
The spec, that is -- not the daemon mentioned by the OP, which apparently is a GNOME program to handle the details of that.

---

### Post by MacUntu on 2010-03-07
> **23meg said:**
> It's a daemon that's used by GNOME Keyring that stores your passwords and other secrets, based on the freedesktop.org secret storage spec.

And because such useful descriptions are too long we make it:

```
**Certificate and Key Storage**
GNOME Keyring: PKCS#11 Component

**Secret Storage Service**
GNOME Keyring: Secret Service

**SSH Key Agent**
GNOME Keyring: SSH Agent
```

Seriously, what? :roll:

---

### Post by Mr. Picklesworth on 2010-03-07
The GNOME keyring thing is just a cover. It really is the secret service! That's why Lucid is so good at [connecting to wireless networks]("http://xkcd.com/416/") :b

---

### Post by emarkay on 2010-03-07
So how do us security-aware disable this "Windows" approach; this  digital "write your password on a Post-It note and stick it to the keyboard", so there's no possibility of an inadvertent "autologin" or worse.

---

### Post by benjo316 on 2010-04-19
"Network Connections" in System -> Preferences menu, open your network (wired, wireless, etc.) settings, and un-check the "Connect Automatically" option, I think?

That only fixes it for you network connection, though... I'm not sure where you'd be able to set it up to ask permission when an application asks for a password. Maybe open seahorse and set permissions on each password? Should be a better way.

Edit: You can lock a keyring in seahorse; not sure if that prevents applications from accessing it or not, though.

---

### Post by Mr. Picklesworth on 2010-04-19
Any keyring with a password needs a password to be unlocked. The contents are encrypted with a one-way function, so your password is the *only* way to get them out. (That's also why the login keyring is how it is). Just be happy that your passwords are nice and safe instead of being stored in plain text somewhere :)

If you want, you can create an unencrypted keyring. Open Seahorse (Passwords and Encryption Keys), go to File›New, and choose Password Keyring. (I don't know what it has to do with files either).
Give it a name, and at the password screen don't enter a password; just hit Okay.

I don't know how to do this in a fine-grained fashion, but you can set that unencrypted keyring as your default by right clicking it and choosing "Set as default". Keep in mind that this means your passwords are easily compromised if someone knowledgeable has access to your computer.

---

### Post by VMC on 2010-04-19
> **Mr. Picklesworth said:**
> ...Keep in mind that this means your passwords are easily compromised if someone knowledgeable has access to your computer.

No truer words have been spoken. If someone has access to my computer, I've already been compromised.
Same thing if someone has access to my wallet :)

---

### Post by Peter09 on 2010-04-19
> **VMC said:**
> No truer words have been spoken. If someone has access to my computer, I've already been compromised.
Same thing if someone has access to my wallet :)


Ahhh ... so you keep all your pin numbers for your credit cards written down on a piece of paper in your wallet   ........ interesting .......

---

### Post by EMCGFX on 2010-04-23
All I know is that after upgrade to 10.04 RC, I got my iptables rules falshed and applied with different ones. So "Secret Service" ROFL Might not be a joke. What I want to know if I can disable this services from running on my box.

Certificate and Key Storage
PolicyKit Authentication Agent
Secret Storage Service (GNOME Keyring: Secret Service) -- WTF?
SSH Key Agent (GNOME Keyring: SSH Agent) -- Is this remote ssh ?

Can I disable those and be ok ?

Thanks.

---

### Post by Longinus00 on 2010-04-23
You realize the other posters were being facetious right?

---

### Post by EMCGFX on 2010-04-24
> **Longinus00 said:**
> You realize the other posters were being facetious right?

Yeah well, fake or not. Still does not explain all of this issues I'm having with my iptables rules. Every time I reboot It gets flashed.

EDITED: I fixed the problem, it was APF script that I've installed and forgot about it LOL

---

