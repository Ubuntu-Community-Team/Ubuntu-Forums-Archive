---
title: "vsftpd anon access"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-11-15
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)


alot of help came from this web page....

[http://www.g-loaded.eu/2008/12/02/set-up-an-anonymous-ftp-server-with-vsftpd-in-less-than-a-minute/](http://www.g-loaded.eu/2008/12/02/set-up-an-anonymous-ftp-server-with-vsftpd-in-less-than-a-minute/)

much credit to them....

im going to my friends place in a few days and have some movies to share.  im bringing my laptop to distribute the movies though i do not have apache (gasp) on the linux machine.  apache is a bit of a heavy handed solution to share 3 files, so i will instead setup an anon access vsftpd server instead.  vsftpd is good enough for kernel.org, its good enough for 3 files.

ok

alt + f2

gnome-terminal

run

go god mode

```

sudo su

```

(if you dont have vsftpd already then drop this code)
```

apt-get install vsftpd

```

drop this block of code....

```

mv /etc/vsftpd.conf /etc/vsftpd.conf.default
mkdir /home/ftp
cat > /etc/vsftpd.conf.anon << EOF
listen=YES
local_enable=NO
anonymous_enable=YES
write_enable=NO
anon_root=/home/ftp
EOF
ln -s /etc/vsftpd.conf.anon /etc/vsftpd.conf
/etc/init.d/vsftpd restart
exit

```

drop a test file in /home/ftp...

```

sudo touch /home/ftp/test

```

point your browser @ [ftp://127.0.0.1/](ftp://127.0.0.1/)

to verify that the test has gone successfully.

then remove the test file and mount bind to link files to the FTP root, vsftp does not like symlinks.

for me, im sharing videos found in $HOME/Videos

```

sudo mount --bind $HOME/Videos /home/ftp

```

the previous command will populate files directly to the FTP anon root.  the next command will give the videos their own subdirectory in the ftp root for if i want to populate other files directly to the root of the ftp like a welcome message.

```

sudo mkdir /home/ftp/videos
sudo mount --bind $HOME/Videos /home/ftp/videos

```

to make this permanent upon reboot sudo gedit /etc/fstab and add (change the USER to the holder of videos)

```

/home/USER/Videos    /home/ftp/videos     none    bind  0  0

```

---

