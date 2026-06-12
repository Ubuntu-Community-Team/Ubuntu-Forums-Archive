---
title: "How do I get apt-get to completely install a package second time?"
date: 2013-03-06
forum: Installation &amp; Upgrades
---

### Post by geiringe on 2013-03-06
How do I get apt-get to completely install a package second time? 

When you use the command apt-get remove <package> it removes that package from
the system but leaves behind config files for that package. 

Here's the case. I used apt-get to remove a package I though I would no
longer use. Some time went by and it look like I was done with it, so
I manually deleted the config files for that package just to clean up
the drive. Some time went by and I needed to use that package again
so I used apt-get to install it again. The 2nd time around the
package does not generate the config files. I'm assuming since it was
installed once it expected them to be there and did not make them
this time. 

Now the package don't to work, it come with many errors and it failed to start

So my question is how do i get apt-get to completely install a package second time?

---

### Post by Mr. Shannon on 2013-03-06
You could try (found from an internet search)
```
sudo dpkg-reconfigure <package name>
```
if that does not work try removing the package with
```
sudo apt-get purge <package name>
```
this will remove the configuration files as well (maybe that will let the system know to install the configuration files next time).  Then install the package again.

NOTE: You should never manually delete system files from your computer unless you know what you are doing.  Instead, use the method above for removing a package with it's configuration files or
```
sudo apt-get autoremove --purge <package name>
```
to remove the package, it's unneeded dependencies, and the configuration files that go with them.

---

### Post by schragge on 2013-03-06
The steps outlined by **Mr. Shannon** should help, but it would be still more helpful if you said, what package are you talking about.


I'll try to explain what happened:
By manually deleting the configuration files, you told dpkg that it shouldn't attempt installing them (that's like saying "Don't mess around with my files, I know better".) The new versions most probably were installed nevertheless, but with funny extensions like *.dpkg-new*

---

