---
title: "root"
date: 2005-07-24
forum: Installation &amp; Upgrades
---

### Post by Lrusso on 2005-07-24
What is the root password after installing?

---

### Post by Juergen on 2005-07-24
It is disabled. 
Read > [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by codejunkie on 2005-07-24
[QUOTE=Lrusso]What is the root password after installing?[/QUOTE]
there is no root password in ubuntu it uses sudo so if it asks for the administrator password it's yours. to gain root access at the terminal type ```
sudo su
```and enter your password if you want to launch and app as root like nautilus it would be ```
gksudo nautilus
``` you can also enable the root account with this ```
sudo passwd root
```if you want hope this helps.

---

### Post by majikstreet on 2005-07-24
I think the whole root-sudo idea is a very good one. It gives people a chance to think: do I really want to be root? do I really want to possibly mess up my computer?

majikstreet

---

### Post by eeried on 2005-07-25
> I think the whole root-sudo idea is a very good one. It gives people a chance to think: do I really want to be root? do I really want to possibly mess up my computer?

Well I'm wondering. I'll read the wiki page on the subject but if your user name and pasword are the same as the root account, the security seems less.

I was used to having a root acount into which I hardly ever logged in, but I typed su within my user account and entered the root password: when I typed exit the access to the system was blocked,a nd I was back in my home dir (no great harm if that was invaded by destructive hackeres or something).

It may be that I don't understand sudo well enough...

---

### Post by majikstreet on 2005-07-25
[QUOTE=eeried]Well I'm wondering. I'll read the wiki page on the subject but if your user name and pasword are the same as the root account, the security seems less.

I was used to having a root acount into which I hardly ever logged in, but I typed su within my user account and entered the root password: when I typed exit the access to the system was blocked,a nd I was back in my home dir (no great harm if that was invaded by destructive hackeres or something).

It may be that I don't understand sudo well enough...[/QUOTE]
 With sudo you can type sudo somecommand and you put in your password, it will do that command from root. Then you will be back to your normal account. 

You can also do sudo su and be transferred into root (like you have done before) then when you are done type exit and you are out.

majikstreet

---

