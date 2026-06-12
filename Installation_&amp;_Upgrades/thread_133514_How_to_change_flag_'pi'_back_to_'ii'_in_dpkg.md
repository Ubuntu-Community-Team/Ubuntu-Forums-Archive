---
title: "How to change flag 'pi' back to 'ii' in dpkg"
date: 2006-02-20
forum: Installation &amp; Upgrades
---

### Post by metaosp on 2006-02-20
Hi,

I accidently tried to remove libgtk2.0-0 package using dpkg -P, the operation was failed 'cause lots of packages depend on it.  But the problem is, the package prefix shown by dpkg -l becomes 'pi' instead of the normal 'ii':

[COLOR="Blue"][FONT="Courier New"]$ dpkg -l libgtk2.0-0
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name              Version           Description
+++-=================-=================-==================================================
[COLOR="Red"]pi[/COLOR]  libgtk2.0-0       2.8.6-0ubuntu2.1  The GTK+ graphical user interface library[/FONT][/COLOR]

How can I change the 'pi' back to 'ii' ?  It seems to prevent me from installing any other package depends on libgtk2.0-0  :( 


Thanks,
Metaosp

---

