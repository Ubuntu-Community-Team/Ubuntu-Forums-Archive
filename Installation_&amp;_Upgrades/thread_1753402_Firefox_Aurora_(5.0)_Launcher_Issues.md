---
title: "Firefox Aurora (5.0) Launcher Issues"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by mihalybaci on 2011-05-08
I recently downloaded Firefox 5.0 Aurora (alpha). I just extracted the tarball in my home directory and the program itself seems to work okay. However, when I add the shortcut to the launcher it does nothing more than blink when clicked. The only way I've found to get the Firefox to open without running from terminal was to add a symbolic link to the desktop, which is fine I suppose. I was just curious if there is a way to edit the launcher icon itself to make it work, or a more sophisticated install procedure that I need to use. Thanks in advance for any feedback on this isssue.

---

### Post by cjb900 on 2011-05-14
I have the Firefox 5.0 Aurora package downloaded on my computer but I can not seem to figure out how to install it. If you could pleas show me how you installed it thanks.

---

### Post by mihalybaci on 2011-05-15
Step by step:
1. download the file to your home directory, /home/(username)/
2. unzip the file using - gunzip (firefoxfilename).tar.gz
3. untar the the file - tar -xvvf (firefoxfilename).tar
4. go to the directory - cd /home/(username)/firefox/
5. make sure it runs -  ./firefox
6. if it runs add an alias to your .bashrc or .cshrc in your home directory. if you only run aurora then you could do - 
alias firefox '/home/(username)/firefox/firefox'
if you want to keep a the stable version of firefox 4.0.1 as well it would be best to use a different alias, like
alias aurora '/home/(username)/firefox/firefox'

Hope that helps.

Also, in response to my first post, they have since fixed the launcher problem, and i haven't had any other problems with aurora in 11.04.

---

