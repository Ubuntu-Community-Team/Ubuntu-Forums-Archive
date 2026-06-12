---
title: "Ubuntu Server 7.10 sudo issue."
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by pks_loss on 2007-12-12
I cannot login to sudo to do ANYTHING on the ubuntu server 7.10 I just installed. Whenever I try to sudo, it just goes to sendmail and tries to sendmail something, but fails. 

 As I said, I just now installed it and I don't know what's wrong.

---

### Post by d0nny2600 on 2007-12-13
Do you have much data on this install or is it fresh?
Are you going to be using sendmail on this server? 
Try reinstalling..Something must have gotten corrupted during the installation.

---

### Post by JangMunho on 2007-12-13
Error link of sudo?
Maybe the soft link was made wrong direction.
Try to relink it using ln -s command.

---

### Post by pks_loss on 2007-12-13
Sorry guys, I figured it out....


 What I needed to do was boot into recovery mode and add pk to the group and sudoers file. 

 It's working right now, I can sudo no problem. 


  The only issues I'm having right now is setting up SAMBA shares, changing the FTP dir, and setting up the webserver.

---

### Post by ddb9587 on 2007-12-14
I'm having the same problem! How do you boot into recovery mode and why would you add pk to the file? I tried to add myself to the sudoers file and I didn't  have sufficient privileges.

---

### Post by pks_loss on 2007-12-14
Sorry, PK is my username. 

 Do you see where I added pk to root and to adm  I think it worked after that

```

 root:x:0:pk
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:pk
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:dovecot
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:pk
fax:x:21:
voice:x:22:
cdrom:x:24:pk,haldaemon
floppy:x:25:pk,haldaemon

```


 also go into /etc/ and nano sudoers make sure it looks like this

```

# Uncomment to allow members of group sudo to not need a password
 %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

```

 Hope that works.


 I know there are other ways of doing it, but this is the way I did it.


 [http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

 Try and read that, that helps a lot.

---

### Post by ddb9587 on 2007-12-15
Thanks, I ended up adding:
username ALL=NOPASSWD:ALL
where username would be your actual username  to the sudoers file and it is now working. Is there any benefit to adding yourself to the other list?

---

### Post by pks_loss on 2007-12-15
I'm not sure how it would benefit you, but I'm sure that doing something in the file results in an outcome of some sort. But remember, I've only been using this OS for less than a week. Previous to that, I never used any linux OS for a server. I don't even have experience in windows 2k3!


  If you're planning on using this server for open use on the internet (regularly, like a forum or something)  be very very careful on how you do things. All it could take is 1 error in your code for someone to  get into your box. 


 Be careful,

  --stay safe.

---

