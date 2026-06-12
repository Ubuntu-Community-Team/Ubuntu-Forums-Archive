---
title: "update manager doesn't see 10.10 release"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by jlhughes on 2010-10-10
I have a laptop and a desktop running Ubuntu 10.04 (linux kernal 2.6.32-25-generic, gnome 2.30.2

I ran update manager on both.

The laptop provided the distribution upgrade option.

The desktop did not.

When I manually attempt sudo do-release-upgrade on the desktop I'm told "No new release found"

These machines are attached to the same wired network and both have access to the Internet. (I'm writing this on the desktop machine.)

How do I get the desktop machine to recognize that a new release is available?

TIA

---

### Post by sisco311 on 2010-10-10
System -> Administration -> Software Sources -> Updates tab;  at the bottom set the **Release updates** to *Normal releases*.

---

### Post by sveterv on 2010-10-10
Also type this in a terminal if you still can't get upgrade info to be shown:

update-manager -d

---

### Post by jlhughes on 2010-10-10
> **sisco311 said:**
> System -> Administration -> Software Sources -> Updates tab;  at the bottom set the **Release updates** to *Normal releases*.

Thanks. This did the trick. For some release I had it watching only for long-term releases.

---

### Post by JackNocturne on 2010-10-10
Please Mark Thread as **Solved** :)

---

### Post by imkebe on 2010-10-11
When running ```
update-manager -d
```

```

= Welcome to the Ubuntu 'Maverick Meerkat' development release =

*** 
[COLOR="Red"]This is still a RELEASE-CANDIDATE release.[/COLOR]
Do not install it on production machines.  
***

```

Is it still RC?

---

### Post by DeShark on 2010-10-11
I also see this "Release Candidate" message, despite updating the package list. Is it a release candidate or just an out of date message?

---

### Post by Iray on 2010-10-13
I have the same message... still RC?
Repositories not updated?
Please... anyone has the answer? I'd love to update, but only to the stable version!!

---

### Post by sisco311 on 2010-10-13
Try:```
update-manager -c
```

from **man update-manager**
```
       -c, --check-dist-upgrades
              Check if a **new distribution** release is available

       -d, --devel-release
              Check if upgrading to the latest **devel** release is possible


```

---

### Post by Iray on 2010-10-13
Thank you!!!!
It worked for me!!

I haven't looked into the man page... :-)

Bye & thank you again!

---

### Post by PirateFanAZ on 2010-10-17
Thanks Sisco311, this also worked for me.

---

### Post by marco_ask on 2010-10-25
with *-c* option in *sudo update-manager* I don't see the 10.10
with *-d* I still see the message
[INDENT]*** 
This is still a RELEASE-CANDIDATE release.
Do not install it on production machines.  
***[/INDENT]
Is it normal?

---

