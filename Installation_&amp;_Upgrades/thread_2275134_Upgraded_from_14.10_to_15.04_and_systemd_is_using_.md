---
title: "Upgraded from 14.10 to 15.04 and systemd is using /etc/init.d script...?"
date: 2015-04-24
forum: Installation &amp; Upgrades
---

### Post by r0d3nt on 2015-04-24
Hi All,

I had found a way to setup a vncserver as a service in Ubuntu. This was on Ubuntu Server 14.10 with the init script in /etc/init.d. I replicated this setup in a VM and did a test upgrade to 15.04, and I am a bit bewildered that systemd in 15.04 is referencing this startup script in /etc/init.d?

Here's the startup script for the service:
```
uquevedo@ubuntu-test:~$ ls -la /etc/init.d/vncserver-rwxr-xr-x 1 root root 1303 Mar 27 14:42 /etc/init.d/vncserver
```
Here's the output when running systemctl checking the status of the service:
```
uquevedo@ubuntu-test:~$ systemctl -l status vncserver&#9679; vncserver.service - (null)
   Loaded: loaded (/etc/init.d/vncserver)
   Active: active (exited) since Thu 2015-04-23 11:15:45 PDT; 17min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 1102 ExecStart=/etc/init.d/vncserver start (code=exited, status=0/SUCCESS)


Apr 23 11:15:41 ubuntu-test systemd[1]: Starting (null)...
Apr 23 11:15:41 ubuntu-test su[1107]: Successful su for uquevedo by root
Apr 23 11:15:41 ubuntu-test su[1107]: + ??? root:uquevedo
Apr 23 11:15:41 ubuntu-test su[1107]: pam_unix(su:session): session opened for user uquevedo by (uid=0)
Apr 23 11:15:45 ubuntu-test vncserver[1102]: Starting VNC server: 1:uquevedo
Apr 23 11:15:45 ubuntu-test vncserver[1102]: New 'ubuntu-test:1 (uquevedo)' desktop is ubuntu-test:1
Apr 23 11:15:45 ubuntu-test vncserver[1102]: Starting applications specified in /home/uquevedo/.vnc/xstartup
Apr 23 11:15:45 ubuntu-test vncserver[1102]: Log file is /home/uquevedo/.vnc/ubuntu-test:1.log
Apr 23 11:15:45 ubuntu-test systemd[1]: Started (null).
```
There is no vnc related startup script in /lib/systemd/system/:
```
uquevedo@ubuntu-test:~$ ls -la /lib/systemd/system/vncserver*ls: cannot access /lib/systemd/system/vncserver*: No such file or directory
```

What's really confusing me too is that there is a startup script for ssh from before the 15.04 upgrade [/etc/init.d/ssh], but after the upgrade systemd is looking elsewhere for the startup script:
```
uquevedo@ubuntu-test:~$ ls -la /etc/init.d/ssh
-rwxr-xr-x 1 root root 4077 Jun 29  2014 /etc/init.d/ssh

uquevedo@ubuntu-test:~$ systemctl status ssh
&#9679; ssh.service - OpenBSD Secure Shell server
   Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2015-04-24 05:51:52 PDT; 2min 47s ago
 Main PID: 948 (sshd)
   CGroup: /system.slice/ssh.service
           &#9492;&#9472;948 /usr/sbin/sshd -D


Apr 24 05:51:52 ubuntu-test systemd[1]: Started OpenBSD Secure Shell server.
Apr 24 05:51:52 ubuntu-test systemd[1]: Starting OpenBSD Secure Shell server...
Apr 24 05:51:53 ubuntu-test sshd[948]: Server listening on 0.0.0.0 port 22.
Apr 24 05:51:53 ubuntu-test sshd[948]: Server listening on :: port 22.
```

My main question is, why did systemd use /etc/init.d to start and manage my vnc server service?  How did it know to do that?  Why didn't systemd look at the startup script for ssh in /etc/init.d like it did for my vnc server service script?  Is it because the 15.04 update put a new service script in /lib/systemd/system?  How does systemd know where to look for these scripts?

I took a peek in /etc/systemd, and I didn't see anything too helpful except for a whole bunch of what looked like control files with commented out lines?

I'd ultimately like to change my vnc server script to be systemd aware so that it'll still work whenever upstart/init style scripts are fully obsoleted.

If someone can help clarify for me why this is working, I'd really appreciate it.

-Ubence

---

### Post by ian-weisser on 2015-04-24
> **r0d3nt said:**
> My main question is, why did systemd use /etc/init.d to start and manage my vnc server service?
Systemd includes *limited* sysvinit compatibility, just like Upstart.

> **r0d3nt said:**
> Why didn't systemd look at the startup script for ssh in /etc/init.d like it did for my vnc server service script?
Systemd did look in /etc/init.d/ . Maybe the ssh script ran. Maybe it broke. Insufficient data.

---

### Post by r0d3nt on 2015-04-24
Thanks for the response.
> Systemd includes limited sysvinit compatibility, just like Upstart.
But how? What controls this behavior? A control file? Programmatically?

Regarding the ssh service, I should have put more emphasis on the output from the systemctl status ssh command that it was looking at the /lib/systemd/system/ssh.service file to initiate this service [at least that's what I'm gathering from my limited understanding of systemd]:
```
Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
```

This is why I was confused about why my vnc server script was working by being referenced in /etc/init.d and the ssh server script which looks to be referenced in /etc/init.d but is actually being referenced in /lib/systemd/system/.

---

### Post by r0d3nt on 2015-04-25
I went ahead and updated my main server to 15.04 and with some guidance from this article I found [[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-remote-access-for-the-gnome-desktop-on-centos-7](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-remote-access-for-the-gnome-desktop-on-centos-7)] I was able to create a working systemd service file for Ubuntu systemd and remove the upstart startup script file to start my vncserver through systemd and not upstart at boot.

There are still some scripts in /etc/init.d that are being referenced for now [VMware Player 7.1 which I got to work with kernel 3.19 from this link: [https://wiki.archlinux.org/index.php/VMware#3.19_kernels](https://wiki.archlinux.org/index.php/VMware#3.19_kernels)], but I imagine in a future update that systemd support startup for ubuntu will come.

I'd still like to know how it is that systemd references upstart init scripts. Is it just by the fact that an /etc/init.d script exists and was configured through upstart that systemd will utilize it? Are there configuration files that control this? Or is it programmatically built in? I'd just like a better handle on how systemd handles /etc/init.d scripts in case I run into this again.

---

### Post by ian-weisser on 2015-04-25
> **r0d3nt said:**
> I'd still like to know how it is that systemd references upstart init scripts. Is it just by the fact that an /etc/init.d script exists [....]

Pretty much, though systemd understands most sysvinit scripts (/etc/init.d/), not Upstart configuration files (/etc/init/).
systemd (and Upstart before it) scans /etc/init.d for scripts (since that's where sysvinit expects them to be), and tries to apply them. That's what 'sysvinit compatibility' means.

---

