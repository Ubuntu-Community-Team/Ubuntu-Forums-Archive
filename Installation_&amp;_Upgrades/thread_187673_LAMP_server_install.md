---
title: "LAMP server install"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by rgurr on 2006-06-03
I wanted to try installing a default LAMP server install from the Server ISO disk. The claim from ubuntu home page is...

[INDENT]In about 15 minutes, the time it takes to install Ubuntu Server Edition, you can have a LAMP server up and ready to go. This feature, exclusive to Ubuntu Server Edition, is available at the time of installation.[/INDENT]

So, I thought I'd give it a try and downloaded the 6.06 server ISO.

[INDENT]To perform a default server installation, select “Install to the hard disk” and press Enter. The installation process will be started. Simply follow the on-screen instructions, and your Ubuntu system will be installed. 

Alternatively, to install a LAMP server (Linux, Apache, MySQL, PHP/Perl/Python), **select “Install a LAMP server”**, and follow the instructions[/INDENT]

HOWEVER, when starting the install, there are no options available. The ONLY option is to press F1 for help and gives a few boot methods like "expert", "memtest", and "rescue". But, I cannot find LAMP. ](*,) 

How do you install LAMP during the initial installation??

---

### Post by llamakc on 2006-06-03
What about F3? That's always been the default for 'other boot options'.

---

### Post by rgurr on 2006-06-03
F3 is where I found "expert", "memtest", etc. There is no LAMP install there. I even tried typing "lamp" at the boot: prompt. It gave me an error.

---

### Post by llamakc on 2006-06-03
Well that's just weird. Any slight chance that you burned the wrong ISO and not the server one?

---

### Post by rgurr on 2006-06-03
I downloaded ubuntu-6.06-server-i386.iso from the utah.edu mirror and matched the checksum.

---

### Post by llamakc on 2006-06-03
I'm downloading one right now. I'll boot it up and see if I have that option and reply back. About 25% done with the download. Should be about 1/2 an hour before I get back here with an answer.

---

### Post by rgurr on 2006-06-03
Ok, thanks... I'm trying the expert install now and selecting the packages independently. Much more of a pain that way tho.:(

---

### Post by llamakc on 2006-06-03
The Install A LAMP Server option was definitely there on the ISO I downloaded and burned.

I'd try snagging another ISO.

---

### Post by rgurr on 2006-06-03
My install was text based... Is yours?

Will you describe your selection screen where you see the option? Is it the first screen that comes up? How many selections do you have?

Mine just comes to a graphic that says Ubuntu with text below that says press F1 for help and Enter to begin installation.

---

### Post by llamakc on 2006-06-03
Nah, it wasn't text-based. A framebuffered menu with about 6 options was the first thing that popped up.

LAMP Install was 2nd or 3rd option. I chose it and it proceeded to start loading the installer kernel (and I then power-cycled my desktop box).

---

### Post by rgurr on 2006-06-03
Whoa! nvm. My disk is good. I test booted it in my regular computer and got a graphical install screen with "Install LAMP" as a selection.

This appears to be a hardware issue with my test system (HP E-Vectra E-PC C10, 933 MHz, 256MB) and the new graphical installer. The installer is reverting to a text based install, and the selection for LAMP is not there...

So, the original question remains in a changed form, is there a way to install LAMP using the text based install?

---

### Post by tribaal on 2006-06-03
Well you can still install a minimal system and then install LAMP packages "by hand" (i.e. using apt-get). 

But of course, this would take more than 15 minutes :)

- trib'

---

### Post by llamakc on 2006-06-03
Huhm, that is a great question. I'd send an email to somebody on the Ubuntu Server team. Not sure where/who though. Good luck.

---

### Post by llamakc on 2006-06-03
[https://launchpad.net/people/ubuntu-server](https://launchpad.net/people/ubuntu-server)

There's a link.

And from their wiki page: [https://wiki.ubuntu.com/ServerTeam](https://wiki.ubuntu.com/ServerTeam)

Join the [[IMG]https://wiki.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-server") or hop onto IRC (#ubuntu-server on [FreeNode]("https://wiki.ubuntu.com/FreeNode")) and lend a hand with people's questions and problems.

---

### Post by rgurr on 2006-06-03
Trib', that defeats the purpose of the new LAMP server install, doesn't it? There should be a 'workaround'.

llamakc, I'll try to notify the server team and see what they have to say. Thanks for your help.

---

### Post by curuxz on 2006-06-03
I thought the LAMP thing was not implemented yet, im suprised.

---

### Post by rgurr on 2006-06-03
Yes, it is. But apparently only for the new 'graphical' install. The text based LAMP install doesn't seem to implemented. :(

---

### Post by adamkane on 2006-06-07
Easy post-install way:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

``` 
Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

``` 
Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

``` 
Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

