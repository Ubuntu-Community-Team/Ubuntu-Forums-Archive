---
title: "LAMP Server installs fine, but won't boot 1st time"
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by degminsec on 2006-07-30
Hi. I am trying to install server version on a Dell Latitude D505 with 512mb ram.  I had Ubuntu setup partition the hard drive automatically, and then the install proceeded without any problems.  (There is a 10GB partition that has windows XP on it, which it left alone and works just fine).  When it then tells me that installation is complete and I should restart, I get the GRUB menu.  When I select the Ubuntu server, it gets to the point where it says, "Uncompressing Llinux... Ok, booting the kernel." and then it just sits there with a blinking cursor on the next line... forever.  Did the install over again, after deleting the partitions and making new ones, and I still have the same problem.  I even tried the normal server install, not the LAMP install, and have the same problem. BTW, when I boot off the desktop live disk, everything works fine... I'm a noob, so please bear with me.  Until this point, I've been using apache/php/mysql on my mac, but I thought it would be a good educational experience to set it up and use it on a Linux server, and ubuntu seemed great.  Hope someone won't mind helping me out.  (P.s. I saw some threads about turing acpi off, which I tried to do by editing the commands before booting within the GRUB, but that didn't seem to help).  

Best,
DAN

---

### Post by degminsec on 2006-07-31
I heard so many good things about this community being helpful - no one can give me some advice?:-(

---

### Post by adamkane on 2006-07-31
See below for the best way to install LAMP on Ubuntu. Bag the Ubuntu Server LAMP install. 

Uf.org is the best forum you're ever going to find. Not too many know much about LAMP I'm afraid. I wish it was different as well.

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
Reboot (or start apache and mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

### Post by az on 2006-07-31
> **degminsec said:**
> Hi. I am trying to install server version on a Dell Latitude D505 with 512mb ram.  I had Ubuntu setup partition the hard drive automatically, and then the install proceeded without any problems.  (There is a 10GB partition that has windows XP on it, which it left alone and works just fine).  When it then tells me that installation is complete and I should restart, I get the GRUB menu.  When I select the Ubuntu server, it gets to the point where it says, "Uncompressing Llinux... Ok, booting the kernel." and then it just sits there with a blinking cursor on the next line... forever.  Did the install over again, after deleting the partitions and making new ones, and I still have the same problem.  


Did you check the cd integrity?  Maybe it's a bug in the linux-server kernel.  Can you boot from the instaler, chroot into the server installation and install linux-386?  Maybe that will help?  You will be useing the desktop kernel (the same one the installer uses, which seems to be working for you)

If that's too complicated, try downloading the alternate cd and installing using the server mode.  It will install a base system with the linux-386 kernel by default.  Then install LAMP

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server
(Exactly the same packages that the LAMP installer installs for you)

---

### Post by igb on 2006-08-01
This happened to me. In my case I discovered the problem was the installer uses the i386kernel, but it's actually the i686 kernel that it installed. If for some reason your hardware doesn't support this kernel, you get exactly the symptoms you describe when you reboot.

My solution was to download the textmode installer and select the server option. This installs an i386 kernel.

Ian.

---

### Post by degminsec on 2006-08-01
thanks for the input, everyone.  Hey Ian, is the textmode installer the same thing as the "alternate" install?

---

### Post by igb on 2006-08-02
If you download the alternative CD and boot it, you will end up at a text mode installer. One of the options is to install a "server".

Ian.

---

### Post by az on 2006-08-02
> **degminsec said:**
> Hi. I am trying to install server version on a Dell Latitude D505 with 512mb ram. 
I just checked and that runs a Celeron M.  Post back if the 386 kernel from the alternate cd works.  It would make sense that the server kernel is not made to run on a mobile processor....

---

