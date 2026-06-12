---
title: "unable to use sudo command in ubuntu 9.10"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by ubunbuntu on 2010-02-24
i am using ubuntu 9.10 .i recently installed vmware server in ubuntu. since during installation of vmware i gave default values the default username for vmware server is root. inorder to access vmware server i changed the root password in terminal. i gave the following command in terminal
sudo password root
it prompted for new password and i entered the password. after that i accessed the vmware server using the username as root and password. it worked fine,i created a virtual machine and it worked fine.now the problem is when i restarted the system and login to vmware server i was unable to access virtual machines created previously. also now i am not able to use sudo command .the following message shows up. sudo: must be setuid root. may be this prob is due to the command i gave sudo password root. can someone help me resolve this prob and go back to my previous state.before when i used to give a sudo command it asked for my account password.

---

### Post by 1/0 on 2010-02-24
Can you login as root by:

```
login root
```

or by exiting to gdm and logging in from there

---

### Post by sisco311 on 2010-02-24
Did you change the file permissions in /usr/bin?

What's the output of:
```
history | grep chmod
```
&
```
find {/usr,}/{s,}bin -perm -4000 -exec ls -al '{}' +;
```
?

---

### Post by ubunbuntu on 2010-02-24
i tried login root and i got the following message
login : cannot possibly work without effective root

---

### Post by ubunbuntu on 2010-02-24
i tried to change file permissions in /usr/bin but i got a message saying operation not permitted

---

### Post by sisco311 on 2010-02-24
The setuid bit of the sudo command is not set. 

Switch to virtual console (Ctrl+Alt+F1), login as root & restore the file's permissions:
```
chmod 4111 /usr/bin/sudo
``` 

You may have altered the permissions of other setuid commands. Please post the output of the *find* command from my first reply, so we can tell you if you have to restore the permissions of other commands.

---

### Post by ubunbuntu on 2010-02-24
please find the output of find command in the attachment

---

### Post by ubunbuntu on 2010-02-24
i gave the command  chmod 4111 /usr/bin/sudo in virtual console and its working.thank you so much . can u tell me if i need to change anything by checking the attchment

---

### Post by sisco311 on 2010-02-24
Did you copy and paste the command exactly:
```
find {/usr,}/{s,}bin -perm -4000 -exec ls -al '{}' +;
```
?

You can paste the output here. Enclose it beetween code tags:
[noparse]```
output
```[/noparse]

---

### Post by ubunbuntu on 2010-02-24
i gave the exact command which you gave. i copied the output into a word file.were u able to read that?

---

### Post by sisco311 on 2010-02-24
> **ubunbuntu said:**
> i gave the exact command which you gave. i copied the output into a word file.were u able to read that?

Yes, but is something wrong with the syntax of the command, it doesn't seem to work for you like it works for me. 

Anyway, try this one:
```
find /bin /sbin /usr/bin /usr/sbin -perm -4000 -exec ls -al '{}' +;
```

---

