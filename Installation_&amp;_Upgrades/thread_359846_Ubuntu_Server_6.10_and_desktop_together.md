---
title: "Ubuntu Server 6.10 and desktop together?"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by jayp927 on 2007-02-12
I installed Ubuntu server 6.10 with the lamp option, then I installed the gui desktop. now that the desktop is up and working, it seems as if LAMP has disappeared. Might it have been renamed? where would it have gone? I have no clue.

---

### Post by go2dell on 2007-02-14
The server install is for a command-line only install.  Since you did the LAMP install, the Apache, MySQL, and PHP packages were also installed.

If you installed the gui desktop by doing something like
```

sudo apt-get install ubuntu-desktop

```

then all the server bits are still there.  If you put the CD back in and did a new installation, then it may or may not be there, depending on the options you chose.

You can check for MySQL by opening a terminal and typing
```

sudo /etc/init.d/mysql status

```

and you should get a whole bunch of fun facts about your installation.  If not, instructions for reinstalling the rest of the LAMP stack without reinstalling your whole system are here:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP).

You should probably also read (at a minimum) the documentation here:

[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/index.html)

and specifically the sections on HTTPD (Apache), PHP5, and Databases:
[list]
[*][https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html)
[*][https://help.ubuntu.com/6.10/ubuntu/serverguide/C/php5.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/php5.html)
[*][https://help.ubuntu.com/6.10/ubuntu/serverguide/C/databases.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/databases.html)
[/list]

Good luck!

---

