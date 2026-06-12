---
title: "Upgrading from 16.04 to 16.10 (Hash Sum mismatch)"
date: 2016-10-18
forum: Installation &amp; Upgrades
---

### Post by oswald3 on 2016-10-18
:( I am trying to upgar my Ubuntu 16.04 to 16.10 and am getting the following error message

[COLOR=#0000ff]Failed to fetch [/COLOR]
[COLOR=#0000ff]http://au.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice-dictionaries/myspell-en-za_5.2.1-2_all.deb [/COLOR]
[COLOR=#0000ff]Hash Sum mismatch[/COLOR]

I have uninstalled the Libre suite so am thinking it shouldn't be checking for any packages.

How can I get around this error ?

---

### Post by alfas2 on 2016-10-19
Removing all spell checkers that end with "za" seems solve the problem.

---

### Post by oswald3 on 2016-10-19
Can you advise how this is done ?

Sorry but I am a Ubuntu newbie - I know enough to break things  :D

---

### Post by howefield on 2016-10-19
> **oswald3 said:**
> Can you advise how this is done ?...

Try using this command from a terminal..

```
sudo apt purge myspell-en-za
```

to reinstall it would be..

```
sudo apt install myspell-en-za
```

---

