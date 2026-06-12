---
title: "Java help for 11.04 as well as Terminal commands..."
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by Camashu on 2011-07-27
Hey'a! I'm... Slightly... new to linux. I started off in linux mint but went to Ubuntu after a while. 
Anyway, i'm having problems with installing java. I've read the site and i can't really do it through there... I've gone through the fourms allready and looked for anything that could help; a lot of what i did find helped.

But it didn't solve my problem... I tried using java's chat support but it was honestly crappy...

So that didn't help.


I've tried using the software manager and i don't really know how to use it... so it doesn't help too much either if i don't how to use it!... well!...


And i'm also having a problem with the terminal... = =


> azmond@azmond-PC136A-ABA-SR1150NX-NA430:~$ su azmond
Password: 
su: Authentication failure
azmond@azmond-PC136A-ABA-SR1150NX-NA430:~$ 
I've tried simply su as well and try to type in my password. Nothing shows up!...  and when i try it with my password AFTER the su command it gives me unknow id: *password*



So, basically... I need help alltogether with ubuntu- i'm a newbie to be honest... tech savy! but still a noob... -what the heck is going on with the su command, and how the heck i can install java on ubuntu 11.04 Because i think it's diffrent for 10.04... ...

HELP~!

---

### Post by luckyu on 2011-07-27
okay to install Java jdk (Java Development Kit) type in the following command.
```

sudo apt-get install openjdk-6-jdk 

```
if you forgot your password you can reset it by using the passwd command.
[HTML]
passwd
[/HTML]
Also the su command won't work because Ubuntu on default doesn't allow the user to be the root user. You have to stick with your user and use the sudo command.

---

