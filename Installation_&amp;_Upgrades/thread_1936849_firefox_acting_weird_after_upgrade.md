---
title: "firefox acting weird after upgrade"
date: 2012-03-06
forum: Installation &amp; Upgrades
---

### Post by impromptu-impression on 2012-03-06
Well my good old 10.04 LTS was working fine until the hardware caught up with it, so I finally got myself seated and went through the process to get everything up to the current stable release with a fresh install of the 11.10 , but now the firefox acted weird. Everytime I am launching it, it return the error message 

nglayout.initialpaint.delay is invalid

but will load after I just excuse the dialog. Its Firefox 10 Daily build I am using and it was perfectly fine on first try but act weird after I load the Update after the initial install ..

Ok I would appreciate some input from you guys as to what might be under the hood for this.

Mech

---

### Post by ajgreeny on 2012-03-06
In addressbar type **about:config** then in the filter box type **nglayout**.

Right click on the line mentioned in your error and modify the entry to 0. That should sort it for you.  What was the setting showing when the error occurred?

Why are you not using FF 10 from the repos?

---

### Post by lovinglinux on 2012-03-08
> **ajgreeny said:**
> In addressbar type **about:config** then in the filter box type **nglayout**.

Right click on the line mentioned in your error and modify the entry to 0. That should sort it for you.  What was the setting showing when the error occurred?

Why are you not using FF 10 from the repos?

If that doesn't work, try right-clicking that preference, selecting the "Reset" option and then restarting Firefox.

---

### Post by impromptu-impression on 2012-03-11
OK , will try , well the repo somehow always crash this way when I try the apt-get update, that I will have to sort it out

---

