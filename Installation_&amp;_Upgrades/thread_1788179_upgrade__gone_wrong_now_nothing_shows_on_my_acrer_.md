---
title: "upgrade  gone wrong now nothing shows on my acrer net book please help"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by debbie1973 on 2011-06-22
please help!!! i have a acer net book which runs ubuntu it said i could upgrade so it was checking for upgrades  installed them them i had to restart the netbook so i do,  when  it came back on it said  my talk talk network was establisshed  but then the screen just stays blank  nothing come s up just the arrow for the mouse is visable on the screen please help mwe fix this as it's my daughters net book which she uses for for school work please any help what i can do thanks:confused:

---

### Post by garvinrick4 on 2011-06-22
What version are you running and was it a dist-upgrade or just a normal upgrade in same version?
When you get to that screen see if:
ctrl/alt/F1 will get you to a terminal so you can log in:
```
lsb_release -a
```above will tell you version:

---

### Post by debbie1973 on 2011-06-22
hi it's ubuntu 11.04 acer-AOA150 tty1  i put the code in but now it's asking for acer AOA150 LOGIN AND I TRIED MY DAUGHTERS PSSWORD AND IT'S NOT ACCEPTING IT ? THANKS

---

### Post by debbie1973 on 2011-06-22
hi it's a ubuntu 11.04 acer-AOA150 ttyl
i put the code in but now it's asking for 
acer-AOA150 login and i don't know it i tried the normal loging password but it's saying it's wrong? thanks for you your help

---

### Post by dino99 on 2011-06-22
password are case sensitive, so be sure to do it exactly (specialy if it has numeric and/or special characters)

---

### Post by mswift on 2011-06-22
Debbie, when you type ctrl+alt+F1, you get to a virtual console, 
where you can log into your computer.
When you see
```
acer-AOA150 login:
```

your computer asks for your** USERNAME**
first, and then for your password!

---

### Post by debbie1973 on 2011-06-22
> **mswift said:**
> Debbie, when you type ctrl+alt+F1, you get to a virtual console, 
where you can log into your computer.
When you see
```
acer-AOA150 login:
```
 
your computer asks for your** USERNAME**
first, and then for your password!
 hi yes i'm a dumby i don't know it please help me

---

### Post by mswift on 2011-06-22
OK. 
When you see login: 
type your daughters username (usually her first name) and press enter.

then type in her password.

---

### Post by dino99 on 2011-06-22
while installation was made, the installer have asked you to enter a username and an associated password, so on every boot you need to enter back these info

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

