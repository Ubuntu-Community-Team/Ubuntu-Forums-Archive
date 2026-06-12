---
title: "Need help, synaptic password."
date: 2011-08-08
forum: Installation &amp; Upgrades
---

### Post by canine10 on 2011-08-08
So ok, i bought this neo notebook.
and i'm trying to install adobe flash player. but when i tried to install the program.
a pop-up appeard 'SYNAPTIC PASSWORD' i don't know what the password is. so i surf alittle to find out what's the problem & nothing.
so here is what i tried
i open the terminal then. the neo@neo-M1110M:~$
i inputed sudo thingy
then this appeared [sudo] password for neo:
things like that, i don't know what to do. i want to enjoy youtube & stuff.
PLEASE HELP ME!

- canine10

---

### Post by haqking on 2011-08-08
> **canine10 said:**
> So ok, i bought this neo notebook.
and i'm trying to install adobe flash player. but when i tried to install the program.
a pop-up appeard 'SYNAPTIC PASSWORD' i don't know what the password is. so i surf alittle to find out what's the problem & nothing.
so here is what i tried
i open the terminal then. the neo@neo-M1110M:~$
i inputed sudo thingy
then this appeared [sudo] password for neo:
things like that, i don't know what to do. i want to enjoy youtube & stuff.
PLEASE HELP ME!

- canine10

type in your login password, as long as it is your system then you should be in the sudo group which allows you to provide credentials for temporary elevation of priveleges.

see here [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by canine10 on 2011-08-08
btw, i don't know the **password** of my notebook.
and i'm trying to figure out what's the password.
its kinda brand new & the retailer didn't tell me the password.
is there anything i can do, to know what the password is?
This is kinda awkward but the link you gave me, i don't understand a thing.
SORRY :b 
fyi : everytime i'm installing programs 'that always appears'

Thanks
canine10

---

### Post by fidelandche on 2011-08-08
> **canine10 said:**
> btw, i don't know the **password** of my notebook.
and i'm trying to figure out what's the password.
its kinda brand new & the retailer didn't tell me the password.
is there anything i can do, to know what the password is?
This is kinda awkward but the link you gave me, i don't understand a thing.
SORRY :b 
fyi : everytime i'm installing programs 'that always appears'

Thanks
canine10

When you boot up the notebook do you get to a login page? If you do, then at this point you enter a password. Then this is the password you use for sudo etc etc

---

### Post by oldos2er on 2011-08-08
Either contact the retailer for the password, or better yet, reset it. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by canine10 on 2011-08-08
> **fidelandche said:**
> When you boot up the notebook do you get to a login page? If you do, then at this point you enter a password. Then this is the password you use for sudo etc etc
My notebook don't have login page. it automatically sends me to by desktop.
i'm just having a problem on installing stuffs. I really need the adobe flash player to play the youtube. -_-

---

### Post by raja.genupula on 2011-08-08
was your system have automatic login with out asking any password for login. if so try some default one like 
ubuntu or root in terminal after sudo 

if dont work ,  i dont know about your notebook , but if you're having recovery mode in grub  then i can tell you how to reset a password .......

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by coffeecat on 2011-08-08
> **canine10 said:**
> btw, i don't know the **password** of my notebook.
and i'm trying to figure out what's the password.
its kinda brand new & the retailer didn't tell me the password.

Have I got this straight? You bought a notebook with Ubuntu pre-installed and a user account already set up and the supplier didn't give you the log in password? I'm at a loss for words! :(

> **canine10 said:**
> is there anything i can do, to know what the password is?

There's certainly a way of resetting the password, but let's clarify a few things first.

Is the notebook running Ubuntu or another version of Linux? Was this pre-installed before you purchased the machine? Do you get a login screen and, if so, how do you login without a password? Or does the boot process take you straight to the desktop GUI?

Open a terminal (ctrl-alt-T if you can't find it in the menus) and post the output of these two commands:

```
cat /etc/lsb-release
cat /etc/debian_version
```

---

### Post by raja.genupula on 2011-08-08
> **oldos2er said:**
> Either contact the retailer for the password, or better yet, reset it. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)


both are posted at a time , same link man,  dont think like bad  man ......

---

### Post by canine10 on 2011-08-08
problem solve :>
thank you guys ;)

---

### Post by raja.genupula on 2011-08-08
we are glad to hear that . please dont forget to  mark your thread as solved after you got the solution for the issue . for doing like that goto thread tools . there you can find out a option for marking as solved

---

