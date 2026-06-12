---
title: "how do I tell if sshd is running?"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by wwuster on 2005-10-26
I'm not sure whether I have sshd installed or not. I don't see sshd in ps. How do I tell? If I don't have it installed how do I install it and get it to run?

apt-cache pkgnames says that I have openssh-client, openssh-server, and openssl installed (if that's the way you tell if they are installed).

thanks,
William

---

### Post by cydizen on 2005-10-26
Hi there, 

 Here is how you can tell if it's running:

```
bruce@3510La:~$ ps -ef |grep ssh
```
root      6822     1  0 Oct20 ?        00:00:00 /usr/sbin/sshd
bruce   10371 10333  0 Oct25 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
bruce   13441 13429  0 10:14 pts/1    00:00:00 grep ssh


do you get similar results?

Regards,
Bruce

---

### Post by angkor on 2005-10-26
```
ps aux | grep ssh
root      7841  0.0  0.1   3544  1540 ?        Ss   Oct25   0:00 /usr/sbin/sshd
angkor    8017  0.0  0.0   3120  1016 ?        Ss   Oct25   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
angkor   13362  0.0  0.0   2932   748 pts/0    R+   19:16   0:00 grep ssh

```

It should show up if you've got it running.

---

### Post by wwuster on 2005-10-26
ps does NOT show anything like ssh or sshd. So it's not running. How do I tell if it's installed and if it's not installed how do I install it. If it is installed how do I start it whenever I boot?

thanks,
William

---

### Post by cydizen on 2005-10-26
Okay, we will get you going.... 

If you like the command line do this:

```
sudo apt-get install ssh
```

or if you like synaptic just search for 'ssh'  you may yield a number of results, however you want the one that is plain 'ole ssh.  

Now, when installing either way, not only will it start the sshd daemon, but it will add it to your default startup scripts. Here are a couple ways to check...

if you like command line.  do this:

```
ls -l /etc/rc5.d
```

and you should see an entry that look something like s55sshd

Otherwise go to System -> Administration -> Services

...it should be on the bottom of the list already checked to start @ boot. 

Hope this helps,
Bruce

---

### Post by wwuster on 2005-10-26
it wasn't running because it wasn't installed.

But I thought that "apt-cache pkgnames" gave you a list of what is installed. openssh-server was listed there, but I was able to insall it with apt-get and then it worked.

So my question is:

does apt-cache pkgnames tell you what really is installed. It seems like it doesn't.

William

---

### Post by cydizen on 2005-10-26
Not sure to be honest. I use dpkg --list to see what is installed.

---

### Post by rockrhino27 on 2005-11-20
Good thread guys.  

     I did get confused one day when i tried to ssh to my Ubuntu desktop machine and the connection was refused.  I just assumed that the server was installed and running because prior I had no problems using ssh to connect to other servers from my desktop machine.  From reading this thread I realized that the service was not installed, and I learned the graphical way to activate and deactivate services on startup.  

Thanks Ubuntu Forums!!

rich

---

