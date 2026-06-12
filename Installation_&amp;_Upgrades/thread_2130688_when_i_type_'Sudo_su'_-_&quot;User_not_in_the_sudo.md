---
title: "when i type 'Sudo su' - &quot;User not in the sudoers file.This incident will be reported&quot;"
date: 2013-03-30
forum: Installation &amp; Upgrades
---

### Post by vishwanath18 on 2013-03-30
Hi all,

I am very new to the Ubuntu 12.10, I am facing a 2 basic problems,

1.when i type 'sudo su' in the command prompt, i am getting a Error Message as "User not in the sudoers file.This incident will be reported"
2. when i type 'visudo' i am getting "visudo: etc/sududoers:Permission Denied"

I tried lot of things to solve this issue but not succesfull

Could you anyone please help me out in this issue?

Regards,
Vishwa

---

### Post by dabl on 2013-03-30
Understanding that you are new to Ubuntu, what makes you think you need to do either one of those things?  Those commands would not normally be used on a Ubuntu system, even by experienced users.  With "sudo" you have the needed root privilege to do any operation on the system.

The errors are both attributable to a mis-match between the user name and the given password.  When Ubuntu, was installed, the installing user gave a password -- that is the only password on the system that will alow a "sudo" operation, including opening visudo to change passwords.  If you don't know the original password given during installation, then you will not be able to execute any "sudo" privileged command.

---

### Post by matt_symes on 2013-03-30
Hi

You should be able to fix this from a LiveCD.USB or from a root console after remounting it read/write.

But in the first instance, can you open a terminal and post the output of 

```
groups
```

**EDIT:**

Have a good read of dabl's post first just to make sure you understand the basics - i see you are very new to Linux and Ubuntu - as i have assumed you have a problem and that may not necessarily be so.

Kind regards

---

### Post by ManamiVixen on 2013-03-30
By default on Ubuntu, Root "su" is disabled. All you really need is sudo as here is no need to run as root.

---

### Post by matt_symes on 2013-03-30
Hi

> **ManamiVixen said:**
> By default on Ubuntu, Root "su" is disabled. All you really need is sudo as here is no need to run as root.

I think the OP should be able to run *sudo su* though

```
matthew-S206:/usr/share/polkit-1/actions % sudo su 
[sudo] password for matthew: 
root@matthew-S206:/usr/share/polkit-1/actions# 

```

This will get you to a root shell along with
```

matthew-S206:/usr/share/polkit-1/actions % sudo -i
root@matthew-S206:~# exit
logout
matthew-S206:/usr/share/polkit-1/actions %
```

...and some other variants.

But i do agree with you.

```
sudo <command>
```

is the preferred way to do it in Ubuntu.

For the OP:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

**EDIT:**

> Actually, I use "sudo su" or "sudo -i" very frequently

If i have a large number of root commands that i need to type, i will also enter a root shell.

As long as you are careful then there should be no problem. 

BTW: i colour my root shells as red and user shell as green so i know instantly in which shell i am in.

Less typing, so i agree with TheCog here.

Kind regards

---

### Post by The Cog on 2013-03-30
Actually, I use "sudo su" or "sudo -i" very frequently. And if you can't use those commands then there is something wrong with the system.

---

### Post by grahammechanical on 2013-03-30
Here is forum policy regarding this issue

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

Note, that ```
visudo
``` may not be working because it should be

```
sudo visudo
```

Regards.

---

### Post by matt_symes on 2013-03-30
Hi

> Here is forum policy regarding this issue

Just to be 100% clear for the OP, these guidelines are for logging into the root GUI and not entering a root shell.

Kind regards

---

### Post by mharv on 2013-03-30
Both sudo and su are insecure. I usually set root to only be accessible from direct login from a physical terminal and not have any users on the system that can su or sudo. And eliminate setuid permissions.

---

### Post by haqking on 2013-03-30
> **ManamiVixen said:**
> By default on Ubuntu, Root "su" is disabled. All you really need is sudo as here is no need to run as root.

so as to not confuse the OP, "su" and root are not the same thing. Which is how i read your statement.

if you do not specify a username with "su" then it defaults to the root account, however it means "substitute user" and can and is used to switch user account privelege whether root or not.

Peace

---

### Post by sandyd on 2013-03-30
Hi, please keep the thread on topic - the OP is asking about why they can't use sudo/edit the sudoers file

Thanks

---

### Post by The Cog on 2013-03-30
Is the account you are trying to use sudo with the first account that was created during intsall, or is it an account created later?

Can you post the output of the command "id"?

---

### Post by vishwanath18 on 2013-03-31
Hi all.... Thanks for the replies 
stilll i am looking for the answer .. This problem occured when i started to install Java in Ubuntu.
The tried to run the command 'sudo apt-get purge openjdk-\* ',i got the error as "User not in the sudoers file.This incident will be reported"
when i done search on internet ... i got the result as .. if i run "sudo su" then i can run the command mentined above.
Please find the attachment for the snapshot of the error output.

---

### Post by The Cog on 2013-03-31
Please see the questions in my last post.

I don't think you are supposed to be logging in as hadoop. Try logging in as the username you gave during the install. I don't think hadoop should be in sudoers - should not have the right to switch to root.

---

### Post by vishwanath18 on 2013-04-01
yeah ... you are right ... when i try using the first username , I can login ...
but when i login to second username(hadoop) i cant ..

---

### Post by The Cog on 2013-04-01
OK, let's explain a bit more. The first user created during install is automatically given the right to use sudo to raise their privilege. Other users created later are not, and it you want them to be able to use sudo you have to add them to the **adm** group. But you should only put trusted users in the adm group, and should not put applications such as hadoop in there. Applications, especially network-active ones, should not have that ability in case they contain a bug that allows remote exploits.

---

