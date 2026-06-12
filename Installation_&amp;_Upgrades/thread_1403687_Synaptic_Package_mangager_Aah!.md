---
title: "Synaptic Package mangager Aah!"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by Iokua86 on 2010-02-10
Hi, I've just upgraded to ubuntu 9.10. I want to install some software and I've got to use the synaptic Package manager. However, I keep getting this error

   	 	 	 	 	 	  E: Type 'x' is not known on line 1 in source list /etc/apt/sources.list 
 E: The list of sources could not be read. 
 Go to the repository dialog to correct the problem. 
 E: _cache->open() failed, please report. 



any ideas? I'm fairly new to linux so, use the dumbest terms possible, if that's not too much;)

---

### Post by 73ckn797 on 2010-02-10
Have you enabled the repositories? Go to System/Administration/Software Sources or from within Synaptic open Settings/Repositiries. If you have several unchecked sources, enable those and see what happens. See attached image.

---

### Post by Iokua86 on 2010-02-10
all the buttons are checked expect the "Source Code" button. Should I check that box also?

---

### Post by Iokua86 on 2010-02-10
oh! gotcha. But it still didn't work, i'm getting two errors now. Apparently my update manager is out commission also. the update manager says this:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'x' is not known on line 1 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

---

### Post by oldos2er on 2010-02-10
Open the sources.list with root privileges: ```
gksu gedit /etc/apt/sources.list
```
Edit the first line, or delete it. Each line in this file that is not a comment (#) should begin with either deb or deb-src.

---

### Post by Iokua86 on 2010-02-10
Thanks...it worked perfectly.

---

### Post by snapback77 on 2010-02-11
Thanks, reading this help me solve my problem too.:popcorn::KS:popcorn::popcorn:

---

