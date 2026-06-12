---
title: "Transition from 9.04 to 9.10- questions to ease the pain"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by smilingfrog on 2010-03-19
Hi,
I have been dual booting between 9.04 and 9.10 for the last 4 or five months. I have had difficult transitions in the past, and I don't like to totally give up what is familiar right away, so I generally do a clean install on a separate partition, and I don't upgrade using the update manager.

My big question is regarding transitioning is is there a way to see what is installed on one system in a simple to print/download format that would make reinstallation through apt-get easier? A *list* command, or equivalent?

With 10.04 coming out, I'd like to transition again, but I would like to do it with fewer (if possible) growing pains. 
Thanks

---

### Post by Ozymandias_117 on 2010-03-20
> **smilingfrog said:**
> 
My big question is regarding transitioning is is there a way to see what is installed on one system in a simple to print/download format that would make reinstallation through apt-get easier? A *list* command, or equivalent?

```
dpkg -l > ~/Desktop/installed_programs.txt
```
Will put all installed packages into a text file on your desktop called "installed_programs.txt"

---

### Post by oldfred on 2010-03-20
You can also export the list and reimport it in your new system. The only problem I found was it will import some older programs that are updated to newer versions. like I reinstalled python 2.5 when now 2.6 is the standard. 

[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

Almost all you settings are in /home so you can copy it  or as many recommend create a separate /home partition so your settings will be reused. Not recommended if going back and forth with old and new versions as old version may not like newer versions settings.

---

### Post by smilingfrog on 2010-03-21
Wonderful. Worked great. Thanks for the tips.

---

