---
title: "chown -R root:root /usr HELP"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by aolias on 2007-04-24
Do not ask why but I did

sudo chown -R root:root /usr  and I made a disaster of my system. Is there any way to restore to the right "user" "group" every single file?

I do not want to reinstall the SO because I have other files (lots) in /usr I do not want to lose.

Thanks

---

### Post by kidders on 2007-04-25
Hi there and welcome,

Before I say what I'm about to say, I should quickly mention two things...

[LIST=1]
[*]I know this *reallllly* isn't what you want to hear.
[*]I would almost never recommend that a user do this.
[/LIST]

**My best suggestion, unfortunately, is to _reinstall Ubuntu_.** :-( Sorry.

The main reason is that /usr houses most of the underlying OS, and is not really intended to be meddled with. Even a slight error in the restoration of the correct permissions could, at the very least, create a serious security problem, and at the very worst, cause performance instability.

If you are an experienced Linux user, then you will already know this, and might as well attempt to undo your little accident. If not, I just wouldn't recommend it. Also, it's very important to _remember to think twice ... and then think again ... before ever using sudo_. It is not a command that should be used regularly.

---

### Post by wiscados on 2008-05-17
if it's just "chown -R root:root /usr" and not "chown -R root:root /usr/*"
then it's just the /usr directory itself, and not the files and sub-directories in /usr, right? If that's the case it's reparable.

---

### Post by kidders on 2008-05-17
Actually, **chown -R root:root /usr** does recursively rewrite ownership of /usr. The distinction is that **chown -R root:root /usr/*** leaves the /usr directory itself unchanged, but recursively modifies its contents.

---

