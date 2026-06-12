---
title: "automatix2"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by fficsori on 2007-05-01
Hi all, 

I am totally new to Ubuntu, just installed feisty and tried to find out the following steps. I found a guide which led me through steps and got to the point of installing automatix2. I did everything as it is described overhere:

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Everything worked fine but at the end, something went wrong, since I got an error message. Now I get the same error message when trying to open Synaptic Package Manager, or even Add or Remove...

The error message goes like this:

An error occured
The following details are provided

E: Type 'wget' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

And this is what I get, and both Add/Remove... and Synaptic Package Manager close down afterwards. What to do now?

Thanks

---

### Post by kelvin spratt on 2007-05-01
if its any help i downloaded automatix for fiesty straight from there site as a deb file installed a dream and the site is back up

---

### Post by taurus on 2007-05-01
You need to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the first line that has the wget in there.  Save the chance and run

```
sudo aptitude update
sudo aptitude upgrade
```
And if you have problems or questions about Automatix, should ask them in their forum since they can help you better over there.

---

### Post by fficsori on 2007-05-01
what is dream?

---

### Post by taurus on 2007-05-01
> **fficsori said:**
> what is dream?

:confused:  :confused:  :confused:

---

