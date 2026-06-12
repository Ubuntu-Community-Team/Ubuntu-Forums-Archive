---
title: "ubuntu root password"
date: 2005-04-01
forum: Installation &amp; Upgrades
---

### Post by Gandalf on 2005-04-01
Hello,
i installed the hoary 5.04 today, it's my first view of ubunto i'm a 1 year debian woody/sarge user. and i wanna say, you guys really growing up so fast and the distro is also better than any other distro i've ever seen, nice install procedure etc...

i have one question though, i remember well that the setup didn't ask me about any root password to setup so i tried su with all the passwords that i may enter just in case i enter it and i forgot but none worked, so what is the initial root password???
thank you

---

### Post by bored2k on 2005-04-01
[QUOTE=Gandalf]Hello,
i installed the hoary 5.04 today, it's my first view of ubunto i'm a 1 year debian woody/sarge user. and i wanna say, you guys really growing up so fast and the distro is also better than any other distro i've ever seen, nice install procedure etc...

i have one question though, i remember well that the setup didn't ask me about any root password to setup so i tried su with all the passwords that i may enter just in case i enter it and i forgot but none worked, so what is the initial root password???
thank you[/QUOTE]
 there is no root passwd

we use sudo
anythng asking for passwd, its ur user password.

any terminal stuff
sudo then command

if you still want su , sudo passwd


Welcome btw .

---

### Post by Gandalf on 2005-04-01
hmmmmmmmmm... it's new for me this!!!!
i have a question though if you don't mind, if sudo stands for su and it asks user password, that means that all regular users can run root privilidge things? or the user that i've created(during setup) is in fact a root but need sudo command to run root passwords?
and thx for the welcome  :grin:

---

### Post by bored2k on 2005-04-01
[QUOTE=Gandalf]hmmmmmmmmm... it's new for me this!!!!
i have a question though if you don't mind, if sudo stands for su and it asks user password, that means that all regular users can run root privilidge things? or the user that i've created(during setup) is in fact a root but need sudo command to run root passwords?
and thx for the welcome  :grin:[/QUOTE]
 Only one able to sudo is the user you created first. To enable on others, read
man sudo ; man sudoers
Then modify your /etc/sudoers

---

### Post by Gandalf on 2005-04-01
ok thanks man for the info and for the fast replies

---

### Post by bored2k on 2005-04-01
[QUOTE=Gandalf]ok thanks man for the info and for the fast replies[/QUOTE]
 Before you go off-topic with another question : don't do it :-P. Your welcome to do so, but on a thread with the right topic ;) .

---

### Post by Gandalf on 2005-04-01
[QUOTE=bored2k]Before you go off-topic with another question : don't do it :-P. Your welcome to do so, but on a thread with the right topic ;) .[/QUOTE] lol \\:D/  ok i won't (i have a forum and i know how it disturb to go a lot off-topic so i won't :D Bye... (till another question came up on a new thread maybe....)

---

### Post by armar on 2005-04-01
Also, if you want to work under the context of root:

sudo -H -s

It helps if you're doing things that require root permission, but don't want preface every command with sudo.

---

### Post by Gandalf on 2005-04-01
[QUOTE=armar]Also, if you want to work under the context of root:

sudo -H -s

It helps if you're doing things that require root permission, but don't want preface every command with sudo.[/QUOTE]
 that will give you the root shell, i already did it by sudo passwd, change the passworg and go in the old fashion way :lol:

---

### Post by bored2k on 2005-04-02
All the applications on the menus use sudo, so you might as well stick to it. You want su? just sudo su and that' it.

I did the same you did when I started Ubuntu, I thought I'd never like sudo, but here I am, using sudoers ;).

---

### Post by Gandalf on 2005-04-02
[QUOTE=bored2k]All the applications on the menus use sudo, so you might as well stick to it. You want su? just sudo su and that' it.

I did the same you did when I started Ubuntu, I thought I'd never like sudo, but here I am, using sudoers ;).[/QUOTE]
 yea maybe you're right just a matter of time

---

### Post by kristi on 2005-04-03
Thanks profusely for having this conversation (found with search) 2 days before I needed it.  Great timing! :mrgreen:  
Kristi

---

### Post by gvang on 2006-10-24
Hey, what if i wanted to log in as root. What is the password for root? Thanks. BTW: I know about sudo, but I just want to log in as root. Thanks again.

---

### Post by tkdolphin on 2006-10-24
Although it isn't recommended that you not use root in Ubuntu, there are a couple ways of doing it. You can type, sudo su and then your password. This way you dont have to type sudo all the time.

Or you can go to this webpage, [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I was able to enable the root account. I have since disabled the root account and use sudo su.

---

