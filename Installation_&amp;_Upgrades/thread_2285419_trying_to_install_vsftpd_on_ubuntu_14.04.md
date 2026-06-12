---
title: "trying to install vsftpd on ubuntu 14.04"
date: 2015-07-05
forum: Installation &amp; Upgrades
---

### Post by niklas_u_f on 2015-07-05
hello

I´m new in this, i only have my server on a hotell, but now i´m using amazon.
like the title say so i´m trying to install vsftpd on ubuntu.
But it´s doesent work for me.

I install it: 

[COLOR=#000000][FONT=monospace]sudo apt-get install vsftpd
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]
sudo nano /etc/vsftpd.conf
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]- [/FONT][/COLOR][COLOR=#000000][FONT=monospace]anonymous_enable=NO
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]- [/FONT][/COLOR][COLOR=#000000][FONT=monospace]local_enable=YES
- [/FONT][/COLOR][COLOR=#000000][FONT=monospace]write_enable=YES
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]- [/FONT][/COLOR][COLOR=#000000][FONT=monospace]chroot_local_user=YES

[/FONT][/COLOR][COLOR=#000000][FONT=monospace]I create a new folder with

[/FONT][/COLOR][COLOR=#000000][FONT=monospace]mkdir /home/[/FONT][/COLOR]*username*[COLOR=#000000][FONT=monospace]/files

[/FONT][/COLOR][COLOR=#000000][FONT=monospace]chown root:root /home/[/FONT][/COLOR][I]username

[/I][COLOR=#000000][FONT=monospace]sudo service vsftpd restart[/FONT][/COLOR][COLOR=#000000][FONT=monospace]
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]And then i try to access the ftp.
I can´t get in.

And i dont now what is wrong.

I hope someone can help me.
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]
[/FONT][/COLOR]

---

### Post by niklas_u_f on 2015-07-07
Bump

---

### Post by sinep2 on 2015-07-07
Try removing VSFTPD with,
**[COLOR=#696969]sudo apt-get --purge remove vsftpd[/COLOR]**
Then reinstall it with,
[COLOR=#696969][B]sudo apt-get install vsftpd
[/B][/COLOR]Then configure it again at /etc/vsftpd.conf
Now, when you login to your FTP client login with your account you created at first(Ubuntu Installation Account)
When I installed VSFTPD I never changed any file permissions for VSTPD.
[COLOR=#696969][B][COLOR=#000000][FONT=monospace]
[/FONT][/COLOR][/B][/COLOR]

---

