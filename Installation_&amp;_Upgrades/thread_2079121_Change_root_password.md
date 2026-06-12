---
title: "Change root password"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by bencouve on 2012-11-01
My first install of Ubuntu was on an old pce 500mb ram and only just runs. However, I still like to use it from time to time.

I discovered today that the root password was not what I expected it to be, i.e. I have appeared to forgotten it. 

Is there a way to change the root password?

Thanks in advance for your help.

---

### Post by darkod on 2012-11-01
Ubuntu doesn't use the root account. The first user created during install has the permissions to run system commands when the word 'sudo' is used before the command in terminal, or 'gksu' before GUI commands.

For example:
sudo fdisk -l (small L)

It will ask you to enter your password again and it will execute the command.

Users that were created later don't have this permission by default but can be given the permission.

---

### Post by bencouve on 2012-11-01
Ok, but if I wanted to change the root password how do I do that?

---

### Post by darkod on 2012-11-01
There is no root password, the root user is disabled. You confirm system commands with the first user. And you run system commands as the first user.

---

### Post by arpanaut on 2012-11-01
This should help:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by bencouve on 2012-11-01
Ok, I have not read the link yet but I will. 

So if I type

su    
I get
Password:
If I now type the password that it should be then I get
su: Authentication failure

How do I change the password for this user. 

Will read the link now, it may answer what I am asking.

It is just on my laptop, it I enter 'su' I type in the password
Then I get 
root@mylaptop:/home#

This is what I want the password for ??????

---

### Post by darkod on 2012-11-01
You don't use 'su' on ubuntu. How many times I have to say it, forget about the root user. Try with:
sudo -i

---

### Post by jerome1232 on 2012-11-01
As Darkod has been saying, Ubuntu locks the root account, what is it exactly that you think you need root for?

---

