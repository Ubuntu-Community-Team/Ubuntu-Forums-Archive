---
title: "Compiling Problems"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by m0rfin on 2007-09-26
I am trying to compile a program but im having some problems, ill show you the log:
```
xm0rfin@xm0rfin-desktop:/xm0rfin/Ascent$ cd /home/xm0rfin/Ascent/
xm0rfin@xm0rfin-desktop:~/Ascent$ chmod 
chmod: missing operand
Try `chmod --help' for more information.
xm0rfin@xm0rfin-desktop:~/Ascent$ chmod +x reconf && ./reconf && ./configure && make && make install
chmod: cannot access `reconf': No such file or directory
xm0rfin@xm0rfin-desktop:~/Ascent$ sudo autoreconf -f -i
Password:
autoreconf: `configure.ac' or `configure.in' is required

```

---

### Post by LaRoza on 2007-09-26
What are you trying to compile, what language is it in, and how did you try.

The above is not how you compile, if that is what you were trying to do.

---

### Post by m0rfin on 2007-09-26
> **LaRoza said:**
> What are you trying to compile, what language is it in, and how did you try.

The above is not how you compile, if that is what you were trying to do.

trying to compile Ascent,  language is C++ and i try to configure it but it gives me ./configure does not exist (something like that)

---

### Post by LaRoza on 2007-09-26
Are you in the directory?

There should be a read me file, use it.

---

### Post by Pumalite on 2007-09-26
sudo apt-get install build-essential

---

### Post by m0rfin on 2007-09-26
> **LaRoza said:**
> Are you in the directory?

There should be a read me file, use it.

I am, the readme says this:
>    1. Login as Root
   2. apt-get update (to get the newest list from the server bout the available files)
   3. apt-get install subversion libmysql++-dev libssl-dev libtool gcc automake g++
   4. now accept the additional space use and wait for it to be installed
   5. Login as a new user,if there is non yet use
   6. adduser
   7. and write in the information needed
   8. When you are loggedin as new user you should be in your home directory(don't as:why a new user),it's for security,never run programs as root
   9. now type in
  10. svn co (-rXXX) svn://emupedia.com/svn/ascent FOLDER
  11. the -rXXX will force the server to give you revision XXX(attention,no space in between)
  12. the FOLDER defines the folder where ascent will be downloaded in
  13. now use
  14. cd FOLDER
  15. chmod +x reconf && ./reconf && ./configure && make && make install
  16. this will take some time now but it is ok and normal
  17. now you should switch in the "bin" directory using "cd" and put in the maps and the DBC's there
  18. move in the main folder of ascent again and create a new folder called "etc" (mkdir etc)
  19. Now copy the Configs from the "src" folder in the "etc" folder and edit them there so they fir with your mysql config
  20. Now move in the "bin" folder and type in "./logonserver"
  21. In a new session or a screen type in "./ascent" while in the bin folder
  22. If everything was setup correctly we should be fine and it should run smoothly


---

### Post by m0rfin on 2007-09-26
> **Pumalite said:**
> sudo apt-get install build-essential

Still same problems:
```
xm0rfin@xm0rfin-desktop:~/Ascent$ autoreconf -f -i
autoreconf: `configure.ac' or `configure.in' is required
xm0rfin@xm0rfin-desktop:~/Ascent$ ./configure --prefix=/home/xm0rfin/Ascent/
bash: ./configure: No such file or directory
xm0rfin@xm0rfin-desktop:~/Ascent$ 
```

---

### Post by m0rfin on 2007-09-26
bump..

---

### Post by Vadi on 2007-09-27
Where is the programs site? Maybe there is a compiled version already avialable.

---

### Post by JesseEklund on 2007-10-13
Im trying to install the same program and have a identical problem. The build site doesn't offer the best support but they try. Any help from you guys would be nice.

---

