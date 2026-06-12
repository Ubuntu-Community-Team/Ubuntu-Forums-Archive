---
title: "WINE help required:: How to install custom applicatoins???"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by true_friend on 2006-08-22
HI
 i have just installed wine hq in my ubuntu system. all installation is over through wine tools now wondering how to install an application of my own choice. there is not help in offical documentation at winehq.com.
plz some wine user help me in this regard. where is the folder of wine c:\ and how to install a custom windows application in it.
Regards
True_Friend

---

### Post by croak77 on 2006-08-22
I just open a terminal and enter;

```
wine /path/to/program.exe
```

---

### Post by true_friend on 2006-08-22
but my q was how to install it.
should i run setup file.exe through this command??????

---

### Post by true_friend on 2006-08-22
i got a solution
winefiles in terminal and then in explorer i will run setup file.
trying .......

---

### Post by croak77 on 2006-08-22
If there is an Install.exe or Setup.exe run that with wine /path/to/setup.exe. It will automagically install in your fake C: drive. Mine is in ~/.wine but if you used winetools, I think it creates a different folder in your /home directory. To run the installed program, I run through terminal, it's wine ~/.wine/drive_c/Program Files/Folder/program.exe. Sometimes I have had to 'cd' to the folder which contains the .exe or else it wouldn't run.

---

### Post by true_friend on 2006-08-22
tried to run a setup file but cannot. is it the problem of wine tools??
there is not option to install a software. one is for tested softwares only. :(

---

