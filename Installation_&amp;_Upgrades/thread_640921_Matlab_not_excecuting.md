---
title: "Matlab not excecuting"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by Dambrosio on 2007-12-14
I recently installed matlab on my computer and got the borders and menu bars to work with compiz. I just have two questions. 

1. I try to run matlab by typing matlab in the command prompt and it says "command not found", I looked in my bin directory and its not there. Now the only way i can execute matlab is to go into the location where i installed it /opt/matlab/bin/matlab and execute using the sudo sh command. Is there a way i can make a link so that I can execute from the command line? Do I need to change file permissions?

2. How can I add a link to my menu so I can also throw that launcher onto my AWN dock?

Thanks so much for the help!
Dan

---

### Post by taurus on 2007-12-14
Why don't you add that to your path in ~/.bashrc so you can execute everything in there anywhere you want.

Edit ~/.bashrc with

```
gedit ~/.bashrc
```
and add these two lines to the end of it.

```
PATH=$PATH:/opt/matlab/bin
export PATH
```
Save the change.  Now, source it and see if you can run it from a terminal with just a command.

```
source ~/.bashrc
matlab
```

---

