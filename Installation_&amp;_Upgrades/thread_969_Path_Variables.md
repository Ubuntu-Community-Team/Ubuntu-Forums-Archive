---
title: "Path Variables"
date: 2004-10-17
forum: Installation &amp; Upgrades
---

### Post by cDAwoody on 2004-10-17
First of all I am a NB pretty much to linux and am not to savvy on techinal terms and how to configure and edit my system. But... I was wondering if anyone could help me with this one occuring problem I recieve when trying to install applications. I have recieved several notices either when trying to install a binary file or when trying to compile some applications that it cannot find a certain file/lib in my path variable...even if the certain file/lib is installed. Is there a way to configure my path variable that is simple? I would appreciate any suggestions or help.

---

### Post by HungSquirrel on 2004-10-17
The global $PATH is defined in /etc/profile .  Put colons between entries, e.g. PATH="/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin:/usr/bin/X11:/usr/games", etc. etc.  You can also add things to your $PATH in your user's bash startup scripts ~/.bashrc and ~/.bash_profile, but I prefer to do it globally in /etc/profile.

---

### Post by cDAwoody on 2004-10-17
I need a little more help. not sure exactly what i need to put in /etc/profile
I am trying to link it to my java vm which is installed in /usr/java. I am installing LimeWire which requires java vm.

---

### Post by HungSquirrel on 2004-10-17
Add /usr/java/bin to the variable described above.

---

### Post by pan69 on 2006-12-05
Does anyone happen to know a convient way to set the environment variables (like PATH) after changing them (instead of reboot)?

thnx

---

### Post by speedman on 2006-12-05
> **pan69 said:**
> Does anyone happen to know a convient way to set the environment variables (like PATH) after changing them (instead of reboot)?

Source the file where you made changes like one of the following examples:

. .bashrc

. .bash_profile

. /etc/profile


Regards,

SM

---

### Post by pan69 on 2006-12-06
Hi speedman. I know where to change the variables but just changing them doesn't make them active. In other words, if I change my path variable and then do an "echo $PATH" I still see the old path. So, my question was: what is a convient way to make the changes to variables active without doing a reboot? (I do not use any gui system, btw)

thnx

---

### Post by speedman on 2006-12-07
Read my post again.  You can source the files (make them active) after making a change to them by using the syntax I posted above.

<dot> <space> .bashrc

... which I noted above as:

. .bashrc

... which you obviously didn't read, will resource the your bashrc file and make it take effect immediately.  The same applies to any other bash rc and profile configs.


SM

---

### Post by sniece on 2007-02-02
OK, I'm pretty new to both Linux and Ubuntu.  I'm trying to get the Acrobat Reader plugin working, and it keeps telling me I have to set it in my Path.  I've made the changes to the PATH in the file listed above, but it won't let me save it for some reason.  Any thoughts, suggestions?  Something I'm doing completely wrong?

Thanks,
Stephen

---

### Post by Roma_emu on 2007-02-05
If you are editting /etc/profile, you have to do it as root (or use sudo or gksudo).

---

