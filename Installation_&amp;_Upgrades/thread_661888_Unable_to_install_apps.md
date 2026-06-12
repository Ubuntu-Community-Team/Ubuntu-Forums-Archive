---
title: "Unable to install apps"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by fmsagas on 2008-01-08
I've tried installing applications in several ways:

emacs and putty:  tried using the add/remove interface.  I search for the app and get some choices.  I check the box.  I get a "list of applications is not available" dialog. I click the reload button.  It always tries to download 6 files, and never gets an error.  I'm back at the check the box step, no changes.  This happens with both applications.

mysql:  See below for the terminal interaction:

:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mysql-server

Any advice on what I can do to resolve these problems?

Thanks in advance.

---

### Post by forestpixie on 2008-01-08
if you're soources have been commented out - you need to uncomment them
run this in terminal

```
cat /etc/apt/sources.list
```

if you each line has # at the beginning open for edit

```
gksudo gedit /etc/apt/sources.list
```

remove # from lines starting with deb

except first line - deb cdrom - put a # a the start of that line, save and close

```
sudo apt-get update
```

then try again

if howevr that isn't the problem post your sources.list here

---

### Post by fmsagas on 2008-01-08
Perfect!  That solved my issue.  New question, each line was prefaced by:

# Line commented out by installer because it failed to verify:

Why did that happen?

---

### Post by zvacet on 2008-01-08
system>administration>software source>tick all boxes under Ubuntu software tab and also under updates tab.Close and your repositories will be refresh.Now you are able to install any program from Ubuntu repositories.

---

### Post by TheWizzard on 2008-01-08
> **fmsagas said:**
> Perfect!  That solved my issue.  New question, each line was prefaced by:

# Line commented out by installer because it failed to verify:

Why did that happen?

this happens if your pc is not on-line when you install ubuntu.

---

### Post by .nedberg on 2008-01-08
> **TheWizzard said:**
> this happens if your pc is not on-line when you install ubuntu.

It happened to me once also. I did not configure the wireless before I installed on my laptop. When I booted the box it had no sources! This is not the way it should be. What is wrong with having repositories you can not reach? Is there a good reason for this to happen? It is easily fixed though...

---

