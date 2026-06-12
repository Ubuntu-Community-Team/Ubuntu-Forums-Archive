---
title: "Issues when installing libmagick9-dev"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by gndeux on 2008-05-15
Hi there, 

I am trying to install libmagick9-dev, but it looks like I have some dependencies issues. Here is what it looks like....
```

# apt-get install libmagick9-dev
  libmagick9-dev: Depends: librsvg2-dev but it is not going to be installed

# apt-get install librsvg2-dev
  librsvg2-dev: Depends: libglib2.0-dev (>= 2.12.0) but it is not going to be installed
                Depends: libgtk2.0-dev (>= 2.10.1-1) but it is not going to be installed

# apt-get install libglib2.0-dev
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.16.3-1) but 2.16.3-1ubuntu1 is to be installed

# apt-get install libglib2.0-0
libglib2.0-0 is already the newest version.

# apt-get install libgtk2.0-dev
  libgtk2.0-dev: Depends: libatk1.0-dev (>= 1.6.1-2) but it is not going to be installed
                 Depends: libglib2.0-dev (>= 2.12.0) but it is not going to be installed
                 Depends: libgtk2.0-0 (= 2.12.9-3ubuntu3) but 2.12.9-3ubuntu4 is to be installed
                 Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed

# apt-get install libatk1.0-dev 
  libatk1.0-dev: Depends: libglib2.0-dev (>= 2.4.1-2) but it is not going to be installed

# apt-get install libgtk2.0-0
libgtk2.0-0 is already the newest version.

# apt-get install  libpango1.0-dev
  libpango1.0-dev: Depends: libglib2.0-dev (>= 2.12.0) but it is not going to be installed

```

I don't really understand the problem and therefore how I could solve this. I am running Hardy Heron, by the way, and my system is up to date.

Thanks in advance for your help !

Adrien.

---

### Post by hermes0710 on 2008-05-16
I think the problem is this line:

**Depends: libgtk2.0-0 (= 2.12.9-3ubuntu3) but 2.12.9-3ubuntu4 is to be installed**

Run synaptic package manager and check which version of this package you have and try to downgrade it to what other packages need

---

### Post by gndeux on 2008-05-17
First, thank you very much for your answer !

I have checked the version of my packages, and here is what I found:

I have libgtk2.0-0 version 2.12.9-3ubuntu4 installed. But apt only offers me to install libgtk2.0-dev version 2.12.9-3ubuntu3. 

If I try to downgrade libgtk2.0-0 to version 2.12.9-3ubuntu3, then apt wants to remove some *quite useful* programs such as ubuntu-desktop, libgtk2.0-bin, audacious, gnome-themes, and more.

I don't really know what to do actually...

Thanks in advance for any suggestions,
Adrien.

---

### Post by hermes0710 on 2008-05-17
Are you using Hardy? I tried to install libmagick9-dev and it proceeds normally....

---

### Post by gndeux on 2008-05-17
I do use hardy, installed from the CD (no upgrade).
I am using the main universe multiverse GB repositories.

---

### Post by hermes0710 on 2008-05-17
Go to System>Administration>Software sources and in the third tab tick to enable "Recommended Updates (Hardy updates)". Then close, let it reload the sources and go to System>Administration>Update Manager  and install the latest updates. After that you can proceed normally installing the package you need

---

### Post by gndeux on 2008-05-17
Ah ah ah! I found the problem! I knew that I was already using "Recommended Updates (Hardy updates)", and "Proposed Updates (Hardy proposed)". I have removed the later and refreshed the package manager. After that, I was able to install libmagick9-dev.

I didn't know that the Proposed Updates could cause this kind of issues though. 

Thank you for your help !

---

### Post by hermes0710 on 2008-05-17
Great! :) I didn't know that about the proposed too...

---

