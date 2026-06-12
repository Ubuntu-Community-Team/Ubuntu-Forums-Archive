---
title: "New version won't install"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by MCBaker on 2010-05-14
I have been using Ubuntu for the past four months offline, and just got connected.  I have 8.04  Hardy Heron, and have updated it.  I tried to install 10.4, but got an error message,  I copied the message but it would not paste.  Something about open office.  Can anyone help with this?  

I am impressed with the security advanatges of Ubuntu over Windows, but my tech advisor says I need an up-to date version to take complete advantage of this.

---

### Post by infamous-online on 2010-05-14
> **MCBaker said:**
> I have been using Ubuntu for the past four months offline, and just got connected.  I have 8.04  Hardy Heron, and have updated it.  I tried to install 10.4, but got an error message,  I copied the message but it would not paste.  Something about open office.  Can anyone help with this?  

I am impressed with the security advanatges of Ubuntu over Windows, but my tech advisor says I need an up-to date version to take complete advantage of this.

you need to tell us what messages you're getting, we can't begin to help you if you don't tell us something. Write down a few lines of the code so we can get an idea as to what the issue may be k.

---

### Post by MCBaker on 2010-05-14
I thought you would say that!!   :P

OK I got it.  "Couldn't configure pre-depend jre for open office.org- writer2latex probably a dependency cycle"

So do I have to install the whole thing package by package, except the problem one?  I'm just an amateur at this.

---

### Post by _0R10N on 2010-05-15
How did you tried to upgrade your system? Here is my three steps to do it.

```

# First, update packages info
aptitude update
# Second, update the actual version
aptitude upgrade
# Third, upgrade the ditro
aptitude dist-upgrade 

```

If you skip steps, the system may try to install packages, that rely on newer versions of the already installed ones.

---

### Post by MCBaker on 2010-05-15
Oh, yeah, I updated Heron before I tried to switch to newest version. I am using a dell laptop, if that will help

---

### Post by MCBaker on 2010-05-15
Done.  A setting wanted me to jump all the way to the latest version.  I changed that, and worked my way through all of them.  Lengthly process, but well worth it.  No problems so far.

---

### Post by Catharsis on 2010-05-16
Glad to hear you got it working. Do you mind marking this thread as solved under "Thread Tools" at the top? Thanks.

---

