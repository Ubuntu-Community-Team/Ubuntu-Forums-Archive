---
title: "Running a shell on ltsp client"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by sgbotsford on 2007-08-07
How do I run a shell on an LTSP client?


If I play with lts.conf and run Screen_12=shell
I get a bash shell login to the server.

This is NOT what I want.
I want to do the reverse:  From the server, I want to open a shell on the client.

My first attempt at this was to copy a working /etc/ssh directory from another linux box into 

/opt/ltsp/i386/etc/ssh

copy /etc/init.d/ssh to /opt/ltsp/i386/etc/ssh

make appropriate links in /opt/ltsp/i386/etc/rc*.d

This does not work.  I'm missing something here.

(Why do I want to do this? you ask.

1.  Be able to run diagnostics on the local machine e.g. ps, netstat,
2.  Be able to use ltsp + ntfs-3g as an installer for MS winsnooze
3.  Be able to force reboot of a particular client.)

---

### Post by sgbotsford on 2007-08-08
Answer:
On server edit /opt/ltsp/i386/etc/lts.conf
Put an entry for a shell screen.
If it's the only Screen_xx  entry, it will default to that.

Chroot to /opt/ltsp/i386.
Run passwd to set a root password in the local /etc/passwd shadow.

Reboot the client.  You will get a command shell login instead of X windows login.

THIS much I figure out before the previous post.

The deceiver is that the client thinks that its hostname is the same as the server name.
This is becuase the ltsp-setup just copies /etc/hostname from the server to the client directory.  IMNOHO this is incorrect behaviour.  Hostnames for the client should be determined by dhclient.  

The next step is to get ssh working on the client.
This requires several steps:
1.  Copy /usr/sbin/sshd to /opt/ltsp/i386/usr/sbin.  
2. Copy /etc/init.d/ssh to /opt/ltsp/i386/etc/init.d
3.  Duplicate the symlink structure  in /etc/rc*.d to the corresponding directories in the lstp tree so that ssh will start on boot.
4.  Edit passwd and shadow in /opt/ltsp/i386/etc and add the entries for sshd from
the files of the same name in /etc/
5.  Create an appropriate set of host keys.  (I cheated here:  These machines are to boot
both windows and linux, and I want them all to have the same host keys.)
6.  Create an appropriate sshd_config
7.  Test at your console login that you can ssh to yourself.

This requies a lot of running back and forth.  When loggen in on the client you don't have write access to the file system, so you have to make changes on the server.

So NOW I can run a shell on the client.

---

### Post by bazz on 2007-09-23
> **sgbotsford said:**
> Answer:
On server edit /opt/ltsp/i386/etc/lts.conf
Put an entry for a shell screen.
If it's the only Screen_xx  entry, it will default to that.

Chroot to /opt/ltsp/i386.
Run passwd to set a root password in the local /etc/passwd shadow.

Reboot the client.  You will get a command shell login instead of X windows login.

THIS much I figure out before the previous post.

The deceiver is that the client thinks that its hostname is the same as the server name.
This is becuase the ltsp-setup just copies /etc/hostname from the server to the client directory.  IMNOHO this is incorrect behaviour.  Hostnames for the client should be determined by dhclient.  

The next step is to get ssh working on the client.
This requires several steps:
1.  Copy /usr/sbin/sshd to /opt/ltsp/i386/usr/sbin.  
2. Copy /etc/init.d/ssh to /opt/ltsp/i386/etc/init.d
3.  Duplicate the symlink structure  in /etc/rc*.d to the corresponding directories in the lstp tree so that ssh will start on boot.
4.  Edit passwd and shadow in /opt/ltsp/i386/etc and add the entries for sshd from
the files of the same name in /etc/
5.  Create an appropriate set of host keys.  (I cheated here:  These machines are to boot
both windows and linux, and I want them all to have the same host keys.)
6.  Create an appropriate sshd_config
7.  Test at your console login that you can ssh to yourself.

This requies a lot of running back and forth.  When loggen in on the client you don't have write access to the file system, so you have to make changes on the server.

So NOW I can run a shell on the client.

dont think you could help me out with that could ya?
I understand everything up until step 5
How did you cheat? I'm looking to do the same thing.
Please let me know 
Thanks

---

### Post by bazz on 2007-09-28
So Is there anyone out there that can help me do this? Or any ideas how to go about it?

---

### Post by bazz on 2007-09-28
Never mind again... This seems to work well!

[https://help.ubuntu.com/community/HowToSetupLTSPDevelEnvironment](https://help.ubuntu.com/community/HowToSetupLTSPDevelEnvironment)

First, install SSH in the chroot.

# SSH needs /dev/random and proc interface, so mount them
mount --bind /dev /opt/ltsp/i386/dev
mount -t proc none /opt/ltsp/i386/proc
# Make sure that resolv will work iin chroot
cp /etc/resolv.conf /opt/ltsp/i386/etc/
chroot /opt/ltsp/i386
# Install ssh server
apt-get install ssh
# Enable root user by setting a password
passwd root

It's also possible to install your public key in $CHROOT/root/.ssh/authorized_keys to connect to the terminal without using the root password.

---

