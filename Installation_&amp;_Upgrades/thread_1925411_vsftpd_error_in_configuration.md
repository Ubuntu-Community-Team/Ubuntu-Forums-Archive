---
title: "vsftpd error in configuration"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by rasca7 on 2012-02-14
Hello. I've just installed vsftpd in 10.04LTS.

My goal is to have virtual users that can upload files but not downaload. For this I've read the config, followed some tutorials and examples but I keep gettin: 553 Could not create file.

I can successfully login with "adoora" user but I can't put or send files.

My /etc/vsftpd.conf:

> 
# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
listen_port=21
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Disabled by default)
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# If enabled, vsftpd will display directory listings with the time
# in  your  local  time  zone.  The default is to display GMT. The
# times returned by the MDTM FTP command are also affected by this
# option.
use_localtime=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
chown_uploads=YES
chown_username=www-data
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
#ftpd_banner=Welcome to blah FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=ftp
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/private/vsftpd.pem
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
nopriv_user=ftp

download_enable=NO
pasv_min_port=3000
pasv_max_port=3050

#ssl_enable=YES
#allow_anon_ssl=NO
#force_local_data_ssl=YES
#force_local_logins_ssl=YES
#ssl_tlsv1=YES
#ssl_sslv2=YES
#ssl_sslv3=YES

hide_ids=YES

# Enable (only) guests.
guest_enable=YES
# This is not needed, it's the default. Just here for clarity.
guest_username=ftp
# Where the guests (virtual) usernames are set.
user_config_dir=/etc/vsftpd/vusers


My /etc/vsftpd/vusers/adoora

> write_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
local_root=/srv/ftp
chroot_local_user=YES
dirlist_enable=YES
download_enable=YES
guest_username=ftp



> root@adoora:/var/www/adoora/ftp# ls -al /srv/ftp
total 8
drwxr-xr-x 2 ftp  ftp  4096 2012-02-14 15:13 .
drwxr-xr-x 3 root root 4096 2012-02-14 15:13 ..


Another error I have is that I can't set it to work with /etc/init.d.

If I put `listen=YES` I can `sudo vsftpd` but if I execute it with init.d I get:
> rasca@adoora:~$ sudo /etc/init.d/vsftpd start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service vsftpd start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start vsftpd


And if I change listen=NO I can't start it in standalone mode and for the init.d way same message and no vsftpd.

Can anyone please help me? Thanks!!!
    Iván

---

### Post by rasca7 on 2012-02-15
I managed to upload files but I still cannot start it via service or /etc/init.d

I get: 

> $ sudo /etc/init.d/vsftpd start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service vsftpd start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start vsftpd
vsftpd stop/pre-start, process 3665


> $ start vsftpd
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.5" (uid=1001 pid=3765 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init))

---

### Post by rasca7 on 2012-02-15
Okey solved it. That error was just that I wasn't root and it didn't run because I was running it with listen=NO because /etc/init.d/vsftpd start told me I needed to put listen=NO.

When I changed this to listen=YES and did the service vsftpd start instead of /etc/init.d/vsftpd it started working.

---

