---
title: "VSFTPD virtual users."
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by capi on 2005-05-14
I'm trying to set up a ftp system with virtual users. Right now I'm using vsftpd, but I cna't get  the virtual users part to work. I'm using this guide...

[ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.3/EXAMPLE/VIRTUAL_USERS/README](ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.3/EXAMPLE/VIRTUAL_USERS/README)

and the command db_load doesn't work. Since there is a Pam config file I'm assuming Pam is installed, and so is some sort of Berkley db. Either way I'm not sure whats going wrong, if the packages aren't installed or what. I'm not sure what other packages I would need.

If anyone knows how to get vsftpds virtual user system working in Ubuntu I would be really grateful. I can't seem to find the information anywhere. That or if anyone else knows a good small ftpd server that supports virtual users. It would need to be run in CLI only as well.

 ](*,) 

Thanks

---

### Post by defkewl on 2005-05-14
Open /etc/vsftpd.conf and uncomment local_enable=YES

---

### Post by capi on 2005-05-15
[QUOTE=defkewl]Open /etc/vsftpd.conf and uncomment local_enable=YES[/QUOTE]
 No, I wanted virtual users, meaning to allow users who aren't on the system. I'm using pure-ftpd right now with mysql database. I still can't figure out what why vsftpd won't work with virtual users on ubuntu.

---

### Post by buba on 2005-05-15
I am working on ftp server right now to and had the same problem 5 min ago. You have to install **libdb3-util **
      sudo apt-get install libdb3-util
and then use db3_load to load the databes
     sudo db3_load -T -t hash -f logins.txt /etc/vsftpd_login.db


I'll post full guide if I get it to work.

---

### Post by capi on 2005-05-15
[QUOTE=buba]I am working on ftp server right now to and had the same problem 5 min ago. You have to install **libdb3-util **
      sudo apt-get install libdb3-util
and then use db3_load to load the databes
     sudo db3_load -T -t hash -f logins.txt /etc/vsftpd_login.db


I'll post full guide if I get it to work.[/QUOTE]
 Yeah, a guide would be great. I followed the guide linked above after that and still couldn't get it. I'll keep messing with it, I may have comething configed wrong.

---

### Post by buba on 2005-05-16
I finaly figured out why the instruction don't work. On debian based systems you have to have /etc/pam.d/vsftpd instead of /etc/pam.d/ftp. Or you can put this **pam_service_name=ftp** in /etc/vsftpd.conf. 
Other instructions are OK.

That worked for me.

Hope I have the time to put whole guide together.

---

### Post by capi on 2005-05-16
[IMG]http://www.showtixinc.com/restaurants/restaurant_logos/Bubba_Color.jpg[/IMG] 

I got it  :smile: 

You don't have to write a guide if you don't want to. Setting up a FTP server would be a nice addition to the UbuntuGuide, though.

---

### Post by buba on 2005-05-17
Glad I could help. 

There is a lot of learning in this kind of things. I have been using linux for aprox 2 mounths now and I think my head is twice a size than it has been before.  ;-) We'll see how it goes from here.

See you around.

---

### Post by Lemons. on 2006-03-27
Here are the roadbumps I hit when setting up vsftpd with virtual users:[LIST=1][*]As hinted in the vsftpd [readme]("ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.3/EXAMPLE/VIRTUAL_USERS/README"), you need to use Berkeley db version 3 with pam_userdb. Install package libdb3-util and use db3_load where the readme calls for db_load.


[*]The readme suggests adding a file vsftpd to /etc/pam.d/ containing the pam rules for our new vsftpd virtual user database:```
auth required /lib/security/pam_userdb.so db=/etc/vsftpd_login
account required /lib/security/pam_userdb.so db=/etc/vsftpd_login
```

If you install via the ubuntu vsftpd package, however, /etc/pam.d/vsftpd is created for you with some default values. These values take care of standard ftpd behavior (such as barring anyone in /etc/ftpusers), so it's not a bad idea to append the two virtual userdb lines to the file in the ubuntu package.

*HOWEVER*, other lines in the package-installed file are intended for validating system users (which is fine if you want to give system users access via ftp), but by definition we are validating "virtual" users who are unknown to the system. So, we need to comment out some lines, as shown here:

```
# Standard behaviour for ftpd(8).
auth    required    pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed

# Note: vsftpd handles anonymous logins on its own.  Do not enable
# pam_ftp.so.

# Standard blurb.
#@include common-account
@include common-session
#@include common-auth
#auth    required    pam_shells.so

# Added per the readme to enable virtual users.
auth required /lib/security/pam_userdb.so db=/etc/vsftpd_login
account required /lib/security/pam_userdb.so db=/etc/vsftpd_login
```

The common-account and common-auth lines both deny accounts that aren't present or aren't authorized on the system. The pam_shells.so line denies accounts without a valid login shell. The virtual user we're trying to authenticate fails all three tests (by definition).


[*]The above was enough to get authentication working. If you're having problems with write access for virtual users, remember that by default they are treated like anonymous users in the configuration file, even if you have anonymous access turned off. That is, options like anon_upload_enable affect your virtual users.[/LIST]
marty

---

### Post by arnoldXXX on 2007-03-17
Can't get my server to work :( 
this is what i have done:

1. nano logins.txt
abc
123
def
456

2. db3_load -T -t hash -f ./logins.txt /etc/vsftpd_login.db

3.add virtual_user
#useradd -d /ftpsite virtual
#chmod 700 /ftpsite

4. nano /etc/pam.d/vsftpd
auth required /lib/security/pam_userdb.so db=/etc/vsftpd_login
account required /lib/security/pam_userdb.so db=/etc/vsftpd_login

5.
```
listen=YES
listen_port=1021
pasv_min_port=50000
pasv_max_port=50100
#listen_ipv6=YES
anonymous_enable=NO
local_enable=YES
write_enable=NO
#local_umask=022
anon_upload_enable=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
dirmessage_enable=YES
xferlog_enable=YES
#connect_from_port_20=YES
#chown_uploads=YES
#chown_username=whoever
#xferlog_file=/var/log/vsftpd.log
#xferlog_std_format=YES
#idle_session_timeout=600
#data_connection_timeout=120
#nopriv_user=ftpsecure
#async_abor_enable=YES
#ascii_upload_enable=YES
#ascii_download_enable=YES
ftpd_banner=Pungsvett.
#deny_email_enable=YES
#banned_email_file=/etc/vsftpd.banned_emails
chroot_local_user=YES
guest_enable=YES
guest_username=virtual

#chroot_list_enable=YES
#chroot_list_file=/etc/vsftpd.chroot_list
#ls_recurse_enable=YES
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
#secure_chroot_dir=/var/run/vsftpd
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
```6.
Looking up localhost
Trying localhost:1021
Connected to localhost:1021
USER asd 
331 Please specify the password.
PASS xxxx
530 Login incorrect.
Disconnecting from site localhost


suggestions anyone ?

---

### Post by kosson on 2007-03-25
Worked for me !
Thank you lemons for the hints... helped me very much understand a few things especially 

[COLOR="DarkOrange"]   3. The above was enough to get authentication working. If you're having problems with write access for virtual users, remember that by default they are treated like anonymous users in the configuration file, even if you have anonymous access turned off. That is, options like anon_upload_enable affect your virtual users. [/COLOR]

---

### Post by geraner on 2008-05-11
I had problems with this in Ubuntu Hardy (8.04). The command db3_load did not work for my anymore.

To get this command running there, you have to do:
**sudo apt-get install db4.2-util**

The new command then is:
**sudo db4.2_load -T -t hash -f logins.txt /etc/vsftpd_login.db**

---

