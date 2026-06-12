---
title: "Several services don't start at boot"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by trx64 on 2010-01-29
I'm having some strange problems in my system (Ubuntu 9.10 32 bits). Several services (Cups, MySQL, VirtualBox kernel driver, etc) aren't starting during boot time. It's possible  start them manually (e.g. /etc/init.d/cups start). The other problem is that my virtual terminals (ctrl + alt + f[1-6]) aren't starting with the system too. Any idea?

---

### Post by blwegrzyn on 2010-01-31
i have exact same problem, it just started, not sure when,
almost all of the services dont start and i must start them manually, is there a way to do some interactive boot to see what is happening?

thx

---

### Post by chronniff on 2010-02-03
I too am having issues with services I installed, notably at the moment nfs-kernel-server and the vmware modules for my vmware workstation, not starting up.  I have all their runlevels set up correctly, or at least what has been correct on linux for about 20 years....although I'm guessing this new upstart service is the cause of all this frustration....I'm running ubuntu 9.10 btw

---

### Post by chronniff on 2010-02-03
Just to let you guys know, I figured out what was going on with my services...don't know if this will help you, but I had forgotten that I changed a setting in /etc/init.d/rc that enabled concurrent booting, which must have messed up the order of my services starting, because after changing the setting back, all my problems were fixed

---

### Post by trx64 on 2010-02-03
That didn't work here. I've started a bug report in [Launchpad]("https://bugs.launchpad.net/ureadahead/+bug/515788").

---

### Post by blwegrzyn on 2010-02-03
same here , 
i tried to modify it to startpar and i run insserv same problem

---

### Post by blwegrzyn on 2010-02-16
this helped:
[https://answers.launchpad.net/upstart/+question/98037](https://answers.launchpad.net/upstart/+question/98037)

---

### Post by trx64 on 2010-02-17
Problem solved. I've edited the file rc-sysinit.conf:

$ sudo gedit /etc/init/rc-sysinit.conf


And changed the line:

```
start on filesystem and net-device-up IFACE=lo

```
to:
```
start on filesystem #and net-device-up IFACE=lo

```

That solved the tty problem and the problems with the services.

---

### Post by sjorsvb on 2010-02-18
This also worked for me, thank you very much!
I am a little curious about the meaning of it though.

---

### Post by trx64 on 2010-02-18
> **sjorsvb said:**
> This also worked for me, thank you very much!
I am a little curious about the meaning of it though.

That line stated that services should only be started after the loopback network device is ready. The problem is that, in Karmic, the network device initializes later and the services that depend on its start can not be initialized correctly.

Commenting the line, the services will no longer wait for the loopback device, then they will start up normally.

---

### Post by alecz20 on 2010-03-22
> **trx64 said:**
> Problem solved. I've edited the file rc-sysinit.conf:

$ sudo gedit /etc/init/rc-sysinit.conf


...

<code>
-bash: cd: /etc/init: No such file or directory
</code>

Apparently there is no directory called init in /etc

Also, in /etc/init.d there is no rc-sysinit.conf file..

So.. what's happening?

---

### Post by RazTaz on 2010-06-23
> **trx64 said:**
> Problem solved. I've edited the file rc-sysinit.conf:

$ sudo gedit /etc/init/rc-sysinit.conf


And changed the line:

```
start on filesystem and net-device-up IFACE=lo

```
to:
```
start on filesystem #and net-device-up IFACE=lo

```

That solved the tty problem and the problems with the services.

I ran into the same problem after upgrading from Karmic to Lucid. Thank you for the solution. It worked for me.

---

