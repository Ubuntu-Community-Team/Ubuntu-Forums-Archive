---
title: "Problem Launching Java Applications"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by Fat Controller on 2008-05-25
I have manually installed a java application (editix) and located it at: /usr/local/bin/editix-free-2008-sp3
the file path to the executable file is
/usr/local/bin/editix-free-2008-sp3/bin/run.sh

If I browse to the file using Nautilus and double click on run.sh, it prompts me if I want to run it, display it or display in terminal. I select run and the application starts - no problem.

If I use a terminal with the path set to the file location, again it starts fine. 

If I try and start the application by supplying the full or partial path e.g. from say one directory up [sh ./bin/run.sh] I get the message [Exception in thread "main" java.lang.NoClassDefFoundError: com/japisoft/editix/Main]

This problem is preventing me from creating an application launcher!

I am new to linux and I am sure that there is a simple solution for this can anybody spell it out to me in simple terms

Thanks

---

### Post by jamesstansell on 2008-05-25
I haven't heard of editix before (if an alternative would be of interest one of my favorites is jEdit) but it sounds like an issue with run.sh.

It may be doing something like "java -cp editix.jar:some-other.jar" which would be fine when the jars are in your current directory, but cause problems otherwise.

For the launcher you're creating would it be reasonable to switch into the editix-free-2008-sp3/bin directory before you call run.sh?

---

### Post by Fat Controller on 2008-05-25
That's cracked it, I wrote another shell that changed to the application directory and then called that from the launcher.

---

