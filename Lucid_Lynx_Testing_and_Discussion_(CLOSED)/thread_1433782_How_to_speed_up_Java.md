---
title: "How to speed up Java?"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dxxvi on 2010-03-19
I use Java a lot (to run Idea, which is a java swing application, to run GlassFish/Tomcat), so I think of copying some big Java-related files to a ram disk and making a symbolic link from the original file to the file on the ram disk when the machine starts.

Do you think it will make every java-related thing faster? If yes, then does Ubuntu cache files which are on ram disks already? If yes again, is there any way to tell Ubuntu not to cache certain files?

---

### Post by Stason on 2010-03-19
Write vm.swappiness=1 on your /etc/sysctl.conf file and it won't swap unless totally out of RAM. Works for all data, not selective to java files or any other type of files.

---

### Post by katie-xx on 2010-03-19
Just for avoidance of doubt ..its possible to optimise your code for both the big Frameworks (.Net and Java)
You can also compile both to native code rather than the byte code etc.
You are asking about your own code ?

---

