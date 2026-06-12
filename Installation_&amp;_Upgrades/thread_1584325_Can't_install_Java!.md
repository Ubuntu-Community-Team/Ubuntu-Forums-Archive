---
title: "Can't install Java!"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by Howard Roark on 2010-09-29
Downloaded Java jre-6u21-linux_i586-rpm.bin and the terminal tells me 
could not find package 
I know it's on desktop and in downloads but terminal tells me it can't find file; why?
Thanks! 
Howard

---

### Post by razhov on 2010-09-29
That's because it is NOT a Debian package, but a self-extracting "bin".

If you are not particular in your preference of the minor version, I suggest you install from the Ubuntu repository, not from Sun.

But if you require this EXACT version, then you can "sh" on the bin.  But beware hte JDK will then NOT be managed by the package manager -- use at your own risk, you have been warned.

---

### Post by tommcd on 2010-09-29
To install Java Runtime Environment (JRE) on Ubuntu 10.04 you have to add the Ubuntu Parter repo to your sources. See this:
[http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html)
You can also add the Partner repo by going to: system > administration > software sources, and clicking to add the Partner repo. Then click the reload button when prompted.

---

### Post by tommcd on 2010-10-01
If you have problems with the: "*sudo add-apt-repository*" command, then just go to: system > administration > software_sources. Then click the "*Other Software*" tab and check the Partner repo. Then click the reload button when prompted and you should be able to install java.

---

### Post by Howard Roark on 2010-10-03
When I Go to Sys>Admin>software_sources>other_software I get this

When I click on which ever of the sources I want I get 

Enter the complete APT line of the repository that you want to add as source

When I type the apt line from the repository that I clicked on I don't get the add button highlighted so I must be doing something wrong but I don't know what!!!
Thanks Howard

---

### Post by lykeion on 2010-10-04
Looking at your screenshot I can see that you've already partner repository. Good that's step 1. Now all you have to do is 
[LIST]
[*]Start Ubuntu Software Center (in the Applications menu). 
[*]Search for "sun jre" 
[*]Install "Sun Java(TM) Runtime Environment (JRE) 6" (sun-java6-jre)
[/LIST]

---

### Post by Howard Roark on 2010-10-04
according to the Ubuntu Software Center I already Have the file but when I go to Tools>Ad-ons>Find Updates I get the second of the two attachments

---

### Post by ANew on 2010-10-04
use ** openJRE ** from repositories

---

### Post by lykeion on 2010-10-05
> **ANew said:**
> use ** openJRE ** from repositories
Why should he install "openJRE"?

Regarding Find updates not showing a green thumb for Java plugin. This doesn't mean that Java isn't working. 
You could go to any site using Java to verify that it's working, like this page:
[http://www.w3.org/People/mimasa/test/object/java/jar-nest1](http://www.w3.org/People/mimasa/test/object/java/jar-nest1)

You can check that Java is enabled here
[http://www.javatester.org/enabled.html](http://www.javatester.org/enabled.html)

Or using JavaScript (paste this into address bar):
[HTML]javascript:document.write("Is Java enabled? " + navigator.javaEnabled() )[/HTML]

---

### Post by ANew on 2010-10-05
> **lykeion said:**
> Why should he install "openJRE"?



It's the same as Java? i understand that in 10.04 Java was replaced by openJRE/iced tea.

---

### Post by tommcd on 2010-10-05
> **Howard Roark said:**
> according to the Ubuntu Software Center I already Have the file but when I go to Tools>Ad-ons>Find Updates I get the second of the two attachments

Howard,
Post the output of:
```
aptitude search sun-java
```
An "i" before a package indicates that it is installed. A "p" before a package indicates it is purged (i.e., not installed). A "B" indicates broken dependencies that need to be fixed.

---

