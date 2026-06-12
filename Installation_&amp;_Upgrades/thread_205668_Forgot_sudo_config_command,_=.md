---
title: "Forgot sudo config command, =\"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by Cheese_Police on 2006-06-28
After installing Xubuntu 6.06 before rebooting, it tells you a command you have to enter in order to set it up to your desire.

Being me, I forgot the command :-\" 

Could anyone tell me this command so I can get on with my Linux life? ;)

---

### Post by TigerWolf on 2006-06-28
im not sure exactly what you mean but it could be
enter your username and it will prompt you for password
or su to login

---

### Post by Cheese_Police on 2006-06-28
[QUOTE=TigerWolf]im not sure exactly what you mean but it could be
enter your username and it will prompt you for password
or su to login[/QUOTE]

I am able to login fine, but as far as I remember there was some sort of config command the installer told me to do at the end. Also, there is no GUI, just a shell.

---

### Post by taurus on 2006-06-28
Maybe
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by Albi on 2006-07-04
Hey,
The command was 
sudo oem-config-prepare

Can I ask how you managed to log in?

---

### Post by dantastik on 2006-07-16
hope you read this despite the age of this post:

i think you need run:

sudo oem-config-prepare

when you log on again it prompts you to create a new user

i havent quite figured out what happens to the root user tho... the password that is good for sudo commands, thats the one i chose for the oem user, doesnt work for the root user.

i installed linux yesterday for the first time tho, so im quite confident im gonna find out at some point :)

dx

---

