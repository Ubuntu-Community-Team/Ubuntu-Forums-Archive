---
title: "[SOLVED] stuck"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by dpwilson on 2008-04-16
I have two problems that I cannot get around.  The first is that while trying to upgrade 7.04, I could not get past this "setting up mono-gac.  It would go to the installing 1 assembly and then hang.  The only way I knew to get around it was if I hit CTRL+C it would skip and move on to the next line in which I would have to do the same thing  and so on until it finished.  Everytime I try to install/update something it tries to install it again and I have to continually go through the same process.  

The second problem is that I was trying to install ntfs-config and of course it goes through that process first and once I get it past that, it gets stuck at the last line show here, "creating fuse group".  I left it over night and it was at the same place when I got up in the morning.  When I try to reinstall it, I get this message "*E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."*.  I run that command it goes back to the output below.  Its like I am stuck in a loop.  Any advice?

```
wilson@main:~$ sudo dpkg --configure -a
Password:
Setting up mono-gac (1.2.3.1-1ubuntu1.1) ...
* Installing 1 assembly from libgmime2.2-cil into Mono
* Installing 1 assembly from libndesk-dbus1.0-cil into Mono
* Installing 1 assembly from libndesk-dbus-glib1.0-cil into Mono
dpkg: error processing mono-gac (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Setting up fuse-utils (2.6.3-1ubuntu2) ...
creating fuse device node...
udev active, devices will be created in /dev/.static/dev/
creating fuse group...


```

---

### Post by kellemes on 2008-04-16
Try the following to fix dependancy problems..
```
sudo apt-get -f install
```

Reconfigure mono-gac..
```
sudo dpkg-reconfigure mono-gac 
```

Hope it helps.

---

### Post by dpwilson on 2008-04-16
Thanks.  Will give it a try this afternoon when I get home from work.

---

### Post by dpwilson on 2008-04-16
Still can't get past that.  Output is below.  It keeps throwing me into that loop to run the "dpkg", then when I do it goes back to  installing that ntsf program and hangs there.

```
dpwilson@main:~$ sudo apt-get -f install
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
dpwilson@main:~$ sudo dpkg --configure -a
Setting up mono-gac (1.2.3.1-1ubuntu1.1) ...
* Installing 1 assembly from libgmime2.2-cil into Mono
* Installing 1 assembly from libndesk-dbus1.0-cil into Mono
* Installing 1 assembly from libndesk-dbus-glib1.0-cil into Mono
dpkg: error processing mono-gac (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Setting up fuse-utils (2.6.3-1ubuntu2) ...
creating fuse device node...
udev active, devices will be created in /dev/.static/dev/
creating fuse group...

```

---

### Post by dpwilson on 2008-04-16
If I try to do the latter first, I get this message..
```
dpwilson@main:~$ sudo dpkg-reconfigure mono-gac
Password:
/usr/sbin/dpkg-reconfigure: mono-gac is broken or not fully installed
dpwilson@main:~$ 
```

---

### Post by dpwilson on 2008-04-17
Is there a way to stop the ntsf from trying to re-install after I get through the dpkg --configure -a?

---

### Post by kellemes on 2008-04-17
> **dpwilson said:**
> Is there a way to stop the ntsf from trying to re-install after I get through the dpkg --configure -a?

Have you tried removing (and purging) all mono-related stuff?
And after this reinstall?

---

### Post by dpwilson on 2008-04-17
> **kellemes said:**
> Have you tried removing (and purging) all mono-related stuff?
And after this reinstall?
I have an idea of what you are saying, but I am not 100% sure as to how and go about doing this.  I cant do anything in synaptic as it tells me to run the dpkg first and then of course, I cant get through that.

---

### Post by kellemes on 2008-04-17
*Maybe* I've found the "bug"-fix.
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=458443#28]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=458443#28")

If you need guidance let me know.

---

### Post by dpwilson on 2008-04-17
OK, If I am going about this right, I would attempt to run the first command listed in the bugfix which is..
apt-get install libmono-addins0.2-cil libmono-addins-gui0.2-cil
Once I do that, the dreaded message comes up  as listed below
```
wilson@main:~$ sudo apt-get install libmono-addins0.2-cil libmono-addins-gui0.2-cil
Password:
[COLOR="Navy"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.[/COLOR] 
wilson@main:~$ sudo dpkg --configure -a
Setting up mono-gac (1.2.3.1-1ubuntu1.1) ...
* Installing 1 assembly from libgmime2.2-cil into Mono

```

Thats as far as I go unless I CTRL+C, then I get another line
```
* Installing 1 assembly from libndesk-dbus1.0-cil into Mono
```
again, hangs at this line, so I CTRL+C and get the next line
```
* Installing 1 assembly from libndesk-dbus-glib1.0-cil into Mono

```which once again hangs up.  If I CTRL+C once again, then I get 
```
dpkg: error processing mono-gac (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Setting up fuse-utils (2.6.3-1ubuntu2) ...
creating fuse device node...
udev active, devices will be created in /dev/.static/dev/
creating fuse group...
```
which is basically as far as I can go.  It hangs up there and nothing can get me any further. I close terminal and try again, but  it just starts all over again.  

I am not sure how  to get around this.

---

