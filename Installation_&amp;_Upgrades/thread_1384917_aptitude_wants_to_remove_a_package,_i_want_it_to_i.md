---
title: "aptitude wants to remove a package, i want it to ignore it"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by kylegio on 2010-01-19
i installed a package with dpkg --install  and told it to ignore an unmet dependency because the package it depended on could not be installed with apt-get (it was a perl module) and i have manually installed the perl module, it works... however every time i do "apt-get upgrade" or anything like that it wants to remove the package i forced to install because it still thinks there are unmet dependencies, is there a way to either tell it to ignore that the package has unmet dependencies (i mean ignore that always, not something i will have to add every time i use aptitude) or is there a way to convince it that the package it thinks is missing (the unmet dependency) is actually met. 


thanks kyle

---

### Post by tommcd on 2010-01-19
You can try running:
```
sudo aptitude hold package_name
```
Where package_name is the name of the package you want to keep.
If you ever want to reverse this, simply run:
```
sudo aptitude unhold package_name
```
If this does not work, then since you installed the package with dpkg, you could try:
> 
To put a package to hold:
echo "package_name hold"|dpkg --set-selections

to 'unhold' it:
echo "package_name install"|dpkg --set-selecions

To see what your packages on hold are, do an:

dpkg --get-selections | grep hold

Be sure to use sudo before those dpkg commands since Ubuntu uses sudo.
references:
[http://www.howtoforge.com/forums/archive/index.php/t-9618.html](http://www.howtoforge.com/forums/archive/index.php/t-9618.html)
[http://forums.debian.net/viewtopic.php?f=10&t=240&start=0](http://forums.debian.net/viewtopic.php?f=10&t=240&start=0)
I don't know if the "hold" option works for apt-get. I don't see a hold option when reading "man apt-get". I only find hold mentioned in "man aptitude".
Hope this helps.

---

### Post by audiomick on 2010-01-19
There is a function in synaptic package manager that does that, I think.
Open it
system> administration> synaptic
search the package and select it, then go to the "package" menu and check the box. It is probably called something like "lock package" (Paket sperren on my German version)

---

### Post by kylegio on 2010-01-19
thanks for your replies, firstly i have access to terminal only (there is no GUI, so anything i do has to be from terminal.

sudo aptitude hold package_name

 does not work. it simply says "the following packages are BROKEN" then lists the package that it doesnt think the dependencies are met for and asks me how to resolve it "Resolve these dependencies by hand? [N/+/-/_/:/?] "  i can tell it to hold from there with = or mark as manually installed with &m but it doesnt work it just goes into a loop asking the same thing again and again. 

the command "echo "package_name hold"|dpkg --set-selections" doesnt return any errors, but it doesnt solve the problem and "dpkg --get-selections | grep hold" immediately after is still blank

its just getting annoying, it will not let me perform any upgrade or anything because it believes that the dependencies for 1 package are not met, when they clearly are met

---

