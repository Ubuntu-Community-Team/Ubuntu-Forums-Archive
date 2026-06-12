---
title: "ubuntu 7.10 server root troubles"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by esdee303 on 2007-10-25
Hello, I've recently installed Ubuntu 7.10 server.
During installatiion, no root password was asked, only a username (f;ex. Tralala) and password (f.ex. Troeloeloe

When I'm in the console screen, and I want to execute some superuser commands (f.ex. sudo apt-get update), i get:
*[sudo] password for Tralala:*
I enter the password Troeloeloe
After that i get:[I]
Tralala is not in the sudoers file.  This incident will be reported
Tralala@server1:~$ sendmail: open /etc/postfix/main.cf: No such file or directory[/I]

When i typ su, i am also asked for a password, i enter Troeloeloe, but i get an authentication failure.

So i can't change anything, so how can i correct this and why do i get this problem anyway ?

---

### Post by 505 on 2007-10-25
Why this happend, no idea, it should.
How to fix it, boot in recovery mode. In grub, you should have a recovery option. If you don't get the grub menu, there is a brief instance during boot where you can press a key to get the menu. See if the option is there, if not, edit an option and add 'single' after the boot options.
When you get the root console, add Tralala to the admin group ('addgroup Tralala admin')

---

### Post by esdee303 on 2007-10-25
Is there another way, without having to reboot ? because the server is located elsewhere (i'm connected through SHH)
i also can't boot properly with a shutdown command (also requires sudo), so i'm going to try just a manual shutdown (push the button), and hope to get in the recovery mode...
I hope to get to the server tomorrow, I'll keep you posted

Thx

---

### Post by taurus on 2007-10-25
Are you the first user, the one that you created during the installing process?  What's the output of this command from a terminal?

```
id
```

---

### Post by esdee303 on 2007-10-25
Yes, i am the first user, created during setup

Tralala@server1:~$: id
uid=1000(Tralala) gid=1000(Tralala) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),109(lpadmin),1000(Tralala)

thx

---

### Post by taurus on 2007-10-25
Did you by any chance playing around (editing it) with the file /etc/sudoers?

---

### Post by esdee303 on 2007-10-25
no :-) i can't even get in the sudoers file, let alone change anything.
He keeps asking me gor a password when i do a **sudo vi /etc/sudoers**
But I only configured one password (during installation, and this password works to log in the console

---

### Post by taurus on 2007-10-25
First of all, that is NOT how you would edit /etc/sudoers.  You should run

```
sudo visudo
```

Now, boot into recovery mode from GRUB menu and post the content of your /etc/sudoers here.

```
cat /etc/sudoers
```

---

### Post by esdee303 on 2007-10-25
I'll do this tomorrow, server is miles away from here, and i can't reboot in save mode from remote
I'll keep you posted.

Thx

---

### Post by 505 on 2007-10-26
Could you post the output of the command 'groups Tralala'?

If admin is in there, you know you need to change sudoers, if no, the user does not belong to the group admin, and you just have to add it.

---

### Post by esdee303 on 2007-10-26
Tralala : Tralala adm dialout cdrom floppy audio dip video plugdev scanner lpadmin

---

### Post by 505 on 2007-10-26
Oke, so no need to change the sudoers file, just boot to recovery mode and type 
```
addgroup Tralala admin
```

---

### Post by esdee303 on 2007-10-26
I can reboot with a Ctrl-Alt-Del, but when restarting, i don't see an option to boot in recovery.  Is there a special key-combination to make it boot in recovery ?

Thx

---

### Post by esdee303 on 2007-10-26
i've rebooted in recovery mode (pressed escape during GRUB loading...)
when i try

addgroup Tralala admin

I get the message that the group 'admin' does not exist.

Also here is my sudoers file (only the lines that are uncommented:

Defaults    !lecture,tty_tickets,!fqdn

root   ALL=(ALL) ALL

thx

---

### Post by taurus on 2007-10-26
Can you post the output of this command here?

```
cat /etc/group
```

---

### Post by esdee303 on 2007-10-26
ok,  I'm there ( I think).
In recovery mode:
i've added the group admin
```
addgroup admin
```
after that, I've added Tralala to the admin group
```
addgroup Tralala admin
```
en then changed my sudoers file so that the admin group sudo rights(with visudo)
I added this line:
```
%admin ALL=(ALL) ALL
```

Is this ok, or did i forget anything ?

---

### Post by NoodleSmythe on 2007-10-26
For what it's worth, I too am having the same problem described above.

When installing the mail server components, I can't "sudo". If I do an install just without the mail components, sudo works a treat. I've tried the various combination and proved this to be true.

It's not a great show-stopper for me, but worth being aware of all the same.

Cheers,

Neil.

---

### Post by rolex42 on 2007-11-08
Hi,

Same problem for me.
Downloaded the Ubuntu 7.10 server and installed it.

The user and password  created during installation works OK to login with,
but when executing sudo I get
 [sudo] password for <user>
I enter my own password (created together with <user> at installation) and then I get:
 <user> is not in sudoers file. ...

When fixing this as described above (boot recovery etc) I suppose I could either just add the "adm" group in /etc/sudoers or first add the admin group and then add admin to sudoers.
What is the purpose of "adm"?
Is it supposed to be an "admin" group?

/Roland

---

### Post by rolex42 on 2007-11-08
OK,
I tried the following:

1/ boot install CD in recovery mode

2/ In the root session I added the group "adm" in sudoers file:
# echo "%adm ALL=(ALL) ALL" >> /etc/sudoers

3/ Check the sudoers file
# cat /etc/sudoers
root  ALL=(ALL) ALL
%adm ALL=(ALL) ALL

4/ Restarted the system (without install CD)

5/ Login on console with my own user (created at installation) and exected
$ sudo -i
And it worked!

Now, I son't know if this is the correct way to solve this.
Does anyone know if it is supposed to be a group "admin" or is "adm" fine?

/Roland

---

### Post by cjwatson on 2007-11-20
It's supposed to be admin, not adm. adm is for reading logs; admin is for sudo access. (Yes, the names are confusing for historical reasons.)

---

### Post by cjwatson on 2007-11-20
If you encountered this bug during installation and haven't trashed the machine since then, could you please mail /var/log/installer/syslog to [email]cjwatson@ubuntu.com[/email]? I would greatly appreciate it, as we're having trouble tracking this bug down. (Note that you'll need to become root to read that file.)

---

### Post by cjwatson on 2007-11-20
David Linton was kind enough to respond to this privately, and we've now isolated the issue; it only happens when you select "No configuration" in answer to the "General type of mail configuration:" question. The fix is straightforward, and will be forthcoming at least in Hardy shortly, along with an addition to the 7.10 release notes. In the meantime, you can work around this by selecting something else in response to that question.

---

### Post by kkuula on 2007-11-26
Hi. I had this same problem in  same situation.   I selected "No configuration" in answer to the "General type of mail configuration:" question and got this bug. solved it via reinstall and selectin something else.

---

