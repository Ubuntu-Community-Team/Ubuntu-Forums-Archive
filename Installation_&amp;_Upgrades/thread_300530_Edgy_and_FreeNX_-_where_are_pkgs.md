---
title: "Edgy and FreeNX - where are pkgs?"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by master_b on 2006-11-15
I've just successfully installed Edgy from the Kubuntu LiveCD to my Benq Joybook A32e, and now need to install FreeNX but I have been unable to find packages.

Seveas's does not yet have packages for Edgy, and this is where I obtained packages previously for Dapper.

Does anybody have links/repo listing for Edgy FreeNX packages?

Thanks

Bill

---

### Post by master_b on 2006-11-16
Anyone ?????

---

### Post by detour on 2006-11-16
You may be interested in this post: [http://www.ubuntuforums.org/showpost.php?p=1190037&postcount=2]("http://www.ubuntuforums.org/showpost.php?p=1190037&postcount=2") regarding the topic of NX on Edgy

---

### Post by master_b on 2006-11-17
detour, thanks for the link. Worked fine.
Not sure what NoMachine means by 2 user limit, as I have a 5 pc lan. Guess I'll soon find out:-D 

Probably means only 1 connection at a time - if so, then that's fine

Bill

---

### Post by Jonathan987 on 2006-11-17
I use NX all the time, it basically means that you can only have 2 sessions going at once, thus only...2 suspended sessions....works great for me :D

btw. I don't mean to hijack this thread, but does anyone know how to change the port that NX works on because I want to get SSH off port 22....thanks!!

Jonathan

---

### Post by hscottyh on 2006-12-20
> **Jonathan987 said:**
> I use NX all the time, it basically means that you can only have 2 sessions going at once, thus only...2 suspended sessions....works great for me :D

btw. I don't mean to hijack this thread, but does anyone know how to change the port that NX works on because I want to get SSH off port 22....thanks!!

Jonathan

sudo gedit /etc/ssh/sshd_config

Find

Port 22

and change it to

Port 877

You then need to restart SSHD. Try

sudo /etc/init.d/ssh restart

Edit the file /etc/nxserver/node.conf

sudo gedit /etc/nxserver/node.conf

Find

# The port number where local ’sshd’ is listening.

#SSHD_PORT=22

and change it to

# The port number where local ’sshd’ is listening.

SSHD_PORT=877

That is, change the port number to the one that sshd is listening to, and uncomment the line.

-- Shamelessly copied from: [http://www.debianadmin.com/securely-administring-remote-machines-using-freenx-in-ubuntu.html](http://www.debianadmin.com/securely-administring-remote-machines-using-freenx-in-ubuntu.html)

---

