---
title: "how to enter grub"
date: 2012-03-07
forum: Installation &amp; Upgrades
---

### Post by Ericyue on 2012-03-07
[SIZE=3]Hi all, i just install the ubuntu 10.04LTS version on my  pc and it was the only OS on my pc. i want to install some software but  1st i have to log in as root just can install. i forget the root  password already and when startup, it don't appear grub menu screen. i  have try to press the "Shift" button and also "Esc" button but it still  don't appear. 

Anyone got idea how to work about this problem ? Thanks in advance [/SIZE]

---

### Post by winh8r on 2012-03-07
In order to install software you can go to the Ubuntu Software Centre, or on 10.04LTS you can use the Synaptic Package Manager which is installed by default.

You need to enter your login password in order to do this. If you are using the terminal to install software you do not need to log in as root, all you have to do is use the sudo command like this:

```
sudo apt-get install <name-of-the-software>
```

The root account is disabled by default in Ubuntu for security and operational safety reasons.Any time you require higher privilieges you just use the "sudo" command.

Please see this page for further details:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")


If i have misunderstood your question and you have in fact forgotten your login password then in order to enter the grub menu and recovery mode you need to hold the shift key down as you switch the machine on, before it starts to boot. You can find details of how to reset your login password here:

[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")
 Hope this helps you

---

