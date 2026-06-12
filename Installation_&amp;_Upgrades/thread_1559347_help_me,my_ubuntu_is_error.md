---
title: "help me,my ubuntu is error"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by Abdika on 2010-08-23
hi,
i have a problem with my ubuntu lucid,i can't entrance to desktop because if i login to ubuntu,there are only terminal.nothing else.
i think, it's problem before that i change login screen and splash screen. now my ubuntu only show terminal,and i can;t use it very well.can u help me to solve this problem? i want my ubuntu back.
thx

---

### Post by martin_legion on 2010-08-23
> **Abdika said:**
> hi,
i have a problem with my ubuntu lucid,i can't entrance to desktop because if i login to ubuntu,there are only terminal.nothing else.
i think, it's problem before that i change login screen and splash screen. now my ubuntu only show terminal,and i can;t use it very well.can u help me to solve this problem? i want my ubuntu back.
thx

Probably you removed some package related with the graphical login. You can try this command to try to reinstall all the default packages that come with the normal install:

```
sudo apt-cache depends ubuntu-desktop | awk -F ":" '{print $2}' | sed '/^$/d' | xargs sudo apt-get install --reinstall --install-recommends --yes
```

Note that this is just one command in a single line.

---

### Post by drpjkurian on 2010-08-23
Hi Use the command
```
startx
```you may go to Display manager

---

### Post by Abdika on 2010-08-25
thanks martin, but i still confuse,when i should do this instruction? when log in or after that. when i login i can close terminal with "exit" instruction. but after that terminal is come back. can explain again?

@dpjkurian : thanks, but this instruction can't use. there is a problem.any another solution?

---

### Post by martin_legion on 2010-08-27
You should run that after you log in. That is, you enter your username, then your password, and then you can type commands.
So you type the command EXACTLY as I put it, and it should re-install all the default applications that come by default, including the desktop.
Pay special attention to the symbols like " , ' and ^ and also to the blank spaces.
I know it's a complicated command, but I can't figure out another way.

---

### Post by Abdika on 2010-08-27
but if i try again, then show "
comand line option --install is not understood, maybe there is a problem or wrong instruction from me?
thanks b4

---

### Post by martin_legion on 2010-10-21
It's not "--install", it's "install"

---

