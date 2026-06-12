---
title: "Upgrade to 13.04"
date: 2013-09-23
forum: Installation &amp; Upgrades
---

### Post by matkobrcko on 2013-09-23
Hello, I have recently upgraded to 13.04 version, but during the boot there are three lines of ''error files'' or something like that and then press to continue, after that it boots to OS but its not very stable, it freezes and so on. Could anyone help please what it means and how to fix it???

---

### Post by ibjsb4 on 2013-09-23
Can you post the errors?

---

### Post by matkobrcko on 2013-09-23
error: file not found.
error: file not found.
error: file not found.

Press any key to continue....

I forgot to mention that its multiboot with Windows 7, previous versions of Ubuntu worked fine installed on the same partition.

---

### Post by ibjsb4 on 2013-09-23
Thats not a lot to go on.

Try this in terminal.

```
sudo apt-get update && sudo dpkg --configure -a && sudo apt-get -f install
```

If you get any errors, please post them.

---

### Post by matkobrcko on 2013-09-23
I tried to run those commands in terminal but I still get those error messages.

---

### Post by ibjsb4 on 2013-09-23
Sorry, but I do not understand and need clarification.

You tried to run those commands?  They did not run?  No errors were produced?

---

### Post by matkobrcko on 2013-09-24
No errors were produced

---

### Post by ibjsb4 on 2013-09-24
Seems to be several possible causes for this and a few possible fixes.  If it was me, I think I would just do a fresh install, but thats just me.  Maybe someone else will have a better idea.

[https://www.google.com/search?client=ubuntu&channel=fs&q=boot+error%3A+file+not+found+ubuntu&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=boot+error%3A+file+not+found+ubuntu&ie=utf-8&oe=utf-8)

---

### Post by matkobrcko on 2013-09-24
Ok thank you for your help

---

