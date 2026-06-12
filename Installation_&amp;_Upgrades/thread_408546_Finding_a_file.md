---
title: "Finding a file"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by Neko_D on 2007-04-13
So I am trying to install Tomcat using [This Guide]("http://ubuntuforums.org/showthread.php?t=44006").

I previously had installed Java SDK 6 on my Machine so I skipped the first step.  On step 4, however I cannot seem to find the place where my .bashrc file is stored.  I am currently looking in /usr/lib/jvm/java-6-sun or /usr/lib/jvm/java-6-sun-1.6.0.00 and as far as I can tell the file is not in either place.

Can someone PLEASE tell me where I can find this file?

---

### Post by aysiu on 2007-04-13
As the guide says, just paste this command into the terminal: ```
gedit ~/.bashrc
``` ~/ is just another way of saying /home/nekod

So ~/.bashrc is /home/nekod/.bashrc

And any file that has a . in front of its name is a hidden file. Just press Control-H in your file browser, and you'll see all the hidden files.

---

### Post by Neko_D on 2007-04-13
> **aysiu said:**
> As the guide says, just paste this command into the terminal: ```
gedit ~/.bashrc
``` ~/ is just another way of saying /home/nekod

So ~/.bashrc is /home/nekod/.bashrc

And any file that has a . in front of its name is a hidden file. Just press Control-H in your file browser, and you'll see all the hidden files.But in my home directory the file is empty.  Does it not exist before hand?

---

### Post by aysiu on 2007-04-13
> **Neko_D said:**
> But in my home directory the file is empty.  Does it not exist before hand?
I don't know.

---

### Post by Neko_D on 2007-04-13
> **aysiu said:**
> I don't know.
Ok thanks for your help.

---

