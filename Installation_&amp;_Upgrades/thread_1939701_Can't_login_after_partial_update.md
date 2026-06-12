---
title: "Can't login after partial update"
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by Shadius on 2012-03-12
This morning I updated Ubuntu and then restarted to find out that it won't let me log in. I'm entering the correct password and everything and it's not letting me log in. Help! I want my Ubuntu back!

---

### Post by matt_symes on 2012-03-12
Hi

The first thing i do in these situations is to create a new user and try to login as that user.

That cuts down by half of where to look for the problem: your user settings or system settings.

If you are comfortable with the command line you can boot into the recovery console

Enter the command

```
adduser recovery
```

Enter a password (it will not be echoed to the screen) and answer the rest of the questions.

Then type

```
reboot
```

On the login screen login as user recovery and enter your password. It should recreate your settings for you.

Can you log in ?

Kind regards

---

### Post by Shadius on 2012-03-12
Thank you very much. That worked. I'm currently logged in. I'm curious as to what went wrong in the other account though. It happened after a partial update so I'm suspecting that I have broken packages. Is there a way to check that?

---

### Post by matt_symes on 2012-03-12
Hi

> **Shadius said:**
> Thank you very much. That worked. I'm currently logged in. I'm curious as to what went wrong in the other account though. It happened after a partial update so I'm suspecting that I have broken packages. Is there a way to check that?

Personally i think you have corrupted settings in you old users folder and not corrupted packages although without being at your PC it's hard tell tell.

You have a couple of options now. 

1. You can copy across your old documents and files (not the settings though) and use the new account.
2. You can try to fix the settings of your old account. 

I would look at the settings in all the hidden files  (it may be crashing and that is why you cannot login). Maybe unset all gnomes settings. Look through the log files for clues here.

I would check .ICEauthority and .Xauthority for your old user (you may not have permissions).

The ownership and permission of these files are (where matthew is my user)

```
matthew@matthew-Aspire-7540:~$ ls -l .X* .I*
-rw------- 1 matthew matthew 25462 Mar 12 11:51 .ICEauthority
-rw------- 1 matthew matthew   182 Mar 12 11:51 .Xauthority
matthew@matthew-Aspire-7540:~$ 
```

I would certainy run an

```
sudo apt-get update 
```

and 

```
sudo apt-get upgrade
```

I would delete all the old caches for apt and dpkg just in case.

May may need to boot back into recovery mode and add your new user recovery to some groups.

These are the groups for my user.

```
matthew@matthew-Aspire-7540:~$ groups
matthew adm cdrom sudo dip plugdev lpadmin sambashare
matthew@matthew-Aspire-7540:~$
```

You can add your user to new groups with the command

```
usermod -a -G list,of,groups,seperated,with,commas user
```

So i would be looking at something like

```
usermod -a -G  adm,cdrom,sudo,dip,plugdev,lpadmin,sambashare recovery
```

Kind regards

---

### Post by Shadius on 2012-03-12
Okay, so I did the first 3 codes and upon doing ```
sudo apt-get update
``` I got "recovery is not in the sudoers file. This incident will be reported." Same result with ```
sudo apt-get upgrade
```

---

### Post by matt_symes on 2012-03-12
Hi

Look at the last part of my last post when i talked about add the user (recovery) to new groups from the recovery console. 

Did you do this ?

Open a terminal and type

```
groups
```

Post back the output by copying and pasting from the terminal (highlight text->right click-> select copy) and paste it into your next post between code tags like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```

I will be away from the keyboard for a number of hours. If anybody else want's to help then please feel free.

Kind regards

---

### Post by Shadius on 2012-03-12
```
recovery@shadius-5410US:~$ ls -l .X* .I*
-rw------- 1 recovery recovery 1050 2012-03-12 08:44 .ICEauthority
-rw------- 1 recovery recovery   59 2012-03-12 08:44 .Xauthority
recovery@shadius-5410US:~$ sudo apt-get update
[sudo] password for recovery: 
recovery is not in the sudoers file.  This incident will be reported.
recovery@shadius-5410US:~$ sudo apt-get upgrade
[sudo] password for recovery: 
recovery is not in the sudoers file.  This incident will be reported.
recovery@shadius-5410US:~$ groups
recovery
recovery@shadius-5410US:~$ 

```

---

### Post by Shadius on 2012-03-12
> **matt_symes said:**
> Hi

Look at the last part of my last post when i talked about add the user (recovery) to new groups from the recovery console. 

Did you do this ?

Open a terminal and type

```
groups
```

Post back the output by copying and pasting from the terminal (highlight text->right click-> select copy) and paste it into your next post between code tags like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```

I will be away from the keyboard for a number of hours. If anybody else want's to help then please feel free.

Kind regards


Thank you for trying.

---

### Post by matt_symes on 2012-03-12
Hi

Let's make sure you have done this step.

Reboot into root shell from the grub menu (the same place where you added the user recovery).

Type in this command

```
usermod -a -G  adm,cdrom,sudo,dip,plugdev,lpadmin,sambashare recovery
```

Then type 

```
reboot
```

Boot back into the user recovery. Open a terminal and type

```
groups
```

You should see some text including this

```
adm cdrom sudo dip plugdev lpadmin sambashare
```

Copy and paste the output of that command into your next post if it is different as, if this step fails, then there is a problem elsewhere.

If it is similar, you should then be able to type the sudo apt-get ... commands.

Post back when you have done this as you have made a mistake checking the .X* and .I* files.

Kind regards

---

### Post by Shadius on 2012-03-12
```
recovery@shadius-5410US:~$ groups
recovery
recovery@shadius-5410US:~$ 

```

I've done what you told me to do at least 3 times and I'm still only getting this.

---

### Post by matt_symes on 2012-03-13
Hi

> I've done what you told me to do at least 3 times and I'm still only getting this.

I thought i had better check. That does not bode too well though, if you cannot add a user to supplementary groups using usermod.

Lets have a look at the groups file. When booted into the user recovery.

```
cat /etc/groups
```

Kind regards

---

### Post by Shadius on 2012-03-13
> **matt_symes said:**
> Hi



I thought i had better check. That does not bode too well though, if you cannot add a user to supplementary groups using usermod.

Lets have a look at the groups file. When booted into the user recovery.

```
cat /etc/groups
```

Kind regards

Hey, thank you very much for taking time to try to help me out. After driving myself crazy trying to get it to work, I just decided to do a re-install of Ubuntu. Thanks for your efforts. If it happens again, I will come back to this thread.

---

