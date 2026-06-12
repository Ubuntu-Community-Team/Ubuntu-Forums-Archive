---
title: "Python - should I upgrade packages?"
date: 2021-01-27
forum: Installation &amp; Upgrades
---

### Post by Norman_Price on 2021-01-27
Using this command:
python3 -m pip list --outdated

I get a massive list of outdated Python packages.
Should I upgrade this lot, or might that break something, or maybe it doesn't matter so leave it alone?
Also - does the normal Ubuntu update process include Python packages?
Thanks
(Apologies if this is the wrong forum for the question)

---

### Post by TheFu on 2021-01-27
Don't mess with the system python or system python libraries ever.  Those are maintained by APT.

If you need a different version or different libraries/modules, then you should setup a separate environment (that just means a sudirectory) where you can put 1, 5, 20 different versions of python (2, 3, 4, 5, 6, whatever) and the modiles/libraries needed by each of those python versions.  There are python management tools just for this, just like there are tools for perl, ruby, and other languages to keep them separate from the "system" versions.

The system versions of any of these tools are meant to support what the OS and scripts created by Canonical and other developers need. If you change thought outside what APT provides, expect a broken system. Sometimes this can create a system that won't boot at all.

pyenv is popular for managing python environments. [https://realpython.com/python-virtual-environments-a-primer/](https://realpython.com/python-virtual-environments-a-primer/) tries to explain.  Looks like the python people have decided to call these "virtual environments."   That can be confusing for there are many other sorts of virtual environments that have nothing whatever to do with python.

---

### Post by Norman_Price on 2021-01-28
Thanks very much TheFu - I'll certainly follow your advice!
The only reason I was messing with python modules/packages at all is that I had to install some as prerequisites for a bit of Open-source software (Gramps - excellent by the way).
I would guess that it must be harmless for the system if I find that a given package is not installed then install it. I think right now I'll save a list of the current Python 3 packages & their versions as I have a working system right now.

---

### Post by TheFu on 2021-01-28
If you need a module/library for python for a specific tool, then the Canonical packager may packaged up a system version of that module.  That's how it works with Perl. It is unclear to me whether pip or pip3 should be used on a system to add modules. With Perl modules, the system versions get updates just like any other program if/when a security failure is found.  

But the versions of the Perl modules used in Ubuntu are often 2+ yrs old.  I find that I use the perl-environment tool, perlbrew, to maintain multiple versions of perl, and multiple versions of perl modules for my custom perl code. I've done paid perl development in my career, but have never been paid to do python. That explains my lack of python direct knowledge. Programming is a team sport almost always. That's good, because it forces us to do things in a team way which is better for the code.

I'd hoped that someone with more paid python skillz would reply.

---

### Post by Norman_Price on 2021-01-28
One reason I installed the extra Python packages using 'python3 -m pip package-name' rather than relying on Python packages wrapped up as Ubuntu packages is the one you give - I have noticed that the Ubuntu repository may be lagging behind on versions (eg for Gimp or LibreOffice). I also thought that an installer like this would only install stable versions and that all new versions would be backward-compatible. However I won't take the risk anyway of updating Python packages that I didn't myself install.

---

### Post by TheFu on 2021-01-28
New is the enemy stable.
New means unknown bugs.ntheory, ld ans he bug are known, but that isn't always true. OTOH, old bugs usually don't impact working software.

Every project has a versioning nomenclature for when changes break any existing API.  IME, that happens when the 2nd level changes in the release number.
1.2.3  --> 1.2.5 doesn't change any interfaces.
1.2.3  --> 1.3.0 does have an API change.

---

