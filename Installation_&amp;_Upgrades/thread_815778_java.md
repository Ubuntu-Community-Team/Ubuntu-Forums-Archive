---
title: "java"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by irshan on 2008-06-02
Dear Friends,

i download java application but that also not working and giving this is msg "Could not open the file /home/irshan/Desktop/jre-6u6-linux-i586-rpm.bin." and "gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again." so give me reason what is goin on my linux.

---

### Post by PmDematagoda on 2008-06-02
You are installing Java the wrong way, and there are simpler ways of doing it, you can install Sun Java with:-
```
sudo apt-get install sun-java6-jre
```

---

### Post by irshan on 2008-06-02
i typed as u given but again it gives following msg "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." so what is mean it.and i want work java with eclipse so help me.

---

### Post by PmDematagoda on 2008-06-02
> **irshan said:**
> i typed as u given but again it gives following msg "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." so what is mean it.and i want work java with eclipse so help me.

Execute:-
```
sudo dpkg --configure -a
```
as mentioned in the error message.

Then try installing Java again.

---

