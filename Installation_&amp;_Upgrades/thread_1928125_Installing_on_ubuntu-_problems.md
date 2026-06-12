---
title: "Installing on ubuntu- problems"
date: 2012-02-19
forum: Installation &amp; Upgrades
---

### Post by anaemica on 2012-02-19
hi. I'm new to Ubuntu and I'm having problems installing Minecraft. i have downloaded the minecraft.jar. installed the "OpenJDK java 6 runtime" and still i cannot open the program. it only says 

"The file '/home/markus/Nedlastinger/minecraft.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

thanks on advance for the help

---

### Post by divague on 2012-02-19
Hi, to make a file executable you have to open a terminal and run:

```
chmod +x /home/markus/Nedlastinger/minecraft.jar
```

Hope it helps.

---

### Post by anaemica on 2012-02-19
> **divague said:**
> Hi, to make a file executable you have to open a terminal and run:

```
chmod +x /home/markus/Nedlastinger/minecraft.jar
```Hope it helps.



I tried to run that code, and got 

" chmod: cannot access '/home/markus/nedlastinger/minecraft.jar' : No such file or directory "

---

### Post by divague on 2012-02-19
> chmod: cannot access '/home/markus/nedlastinger/minecraft.jar' : No such file or directory

Don't forget that Linux is case sensitive. Did you write the directory Nedlastinger with a capital N?

---

### Post by anaemica on 2012-02-19
wrote " chmod +x /home/markus/Nedlastinger/minecraft.jar" and pressed enter, nothing happened. just jumped a line down in the terminal.

---

### Post by divague on 2012-02-19
chmod +x /home/markus/Nedlastinger/minecraft.jar

should't have an output, did you try running minecraft again?

---

### Post by anaemica on 2012-02-19
Thank you very much for being patient with a newbie! 
it worked now. one more question ; is that code the same for every ".jar" file ?

---

### Post by divague on 2012-02-19
It should work with any file that needs to be executable. The command chmod changes the permissions of files. If you want to learn more, open a terminal and type:

```
man chmod
```

---

