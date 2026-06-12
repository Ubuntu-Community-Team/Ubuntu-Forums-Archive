---
title: "installing x-server 8.04"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by rushinblue on 2008-06-13
How do I install x-server on Ubuntu 8.04 Server?

Thanks

---

### Post by ibutho on 2008-06-13
You can do
```
sudo aptitude update
sudo aptitude install xserver-xorg

```
You can use use the same tool to install a GUI if desired.

---

### Post by rushinblue on 2008-06-13
Hmm, I can't install it. This is the error I get.

```
[COLOR="Red"]Couldn't find any package whose name or description matched "xserver-xorg"
Couldn't find any package whose name or description matched "xserver-xorg"
No packages will be installed, upgraded, or removed.[/COLOR]
```

It looks like this is related to my earlier post...[http://ubuntuforums.org/showthread.php?t=828218]("http://ubuntuforums.org/showthread.php?t=828218")


Thanks

---

### Post by Xyem on 2008-06-13
It should be:

> sudo aptitude install xorg

-----
Edit:

> Preparing for Graphical Environment

The absolute minimum for any graphical environment is X.org
Installing X.org

On Ubuntu Edgy (6.10), Feisty (7.04), and Gutsy (7.10), use the command:

sudo aptitude install xorg 
from [Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems") ( which hasn't been updated for 8.04 yet.. )

---

### Post by ibutho on 2008-06-13
xserver-xorg should work just fine. Its a meta-package that installs various xorg related applications. 

The reason why the install fails does indeed seem to be related to the repo issues mentioned in the other thread.

---

### Post by Xyem on 2008-06-13
> **ibutho said:**
> xserver-xorg should work just fine. Its a meta-package that installs various xorg related applications.

Are these applications not included in the 'xorg' metapackage? If so, are they of any importance?
Whenever I do an minimal/server install, I always install the 'xorg' metapackage..

---

### Post by ibutho on 2008-06-13
I don't really know if the package set they install is different. I am used to xserver-xorg from setting up Debian systems in the past.

---

### Post by Xyem on 2008-06-13
Thanks ibutho and apologies to rushinblue for the thread hijack

---

### Post by rushinblue on 2008-06-14
I ran ```
sudo aptitude install xorg
```

See attached screenshot for the error message:

[COLOR="Red"]"failed to initialize core devices"[/COLOR]

Any ideas?

Thanks,

---

### Post by RESID3NT on 2008-06-14
> **ibutho said:**
> xserver-xorg should work just fine. Its a meta-package that installs various xorg related applications. 

The reason why the install fails does indeed seem to be related to the repo issues mentioned in the other thread.

Agreed. Used this with 8.04 and works.

---

### Post by rushinblue on 2008-06-14
I see, my app does not support 8.04 so I guess I am stuck for now.

---

### Post by ibutho on 2008-06-14
> **rushinblue said:**
> I ran ```
sudo aptitude install xorg
```

See attached screenshot for the error message:

[COLOR="Red"]"failed to initialize core devices"[/COLOR]

Any ideas?

Thanks,

It seems like Ubuntu can't find the vmmouse module which is provided by the xserver-xorg-input-vmmouse package.

---

### Post by rushinblue on 2008-06-16
I noticed that, any ideas on how to correct that? Or to manually check that the "vmmouse" module exists?

Thanks

[COLOR="Blue"]Please note, because the app I want to use does not support 8.04 I reverted back to Ubuntu Server 7.10[/COLOR]

---

