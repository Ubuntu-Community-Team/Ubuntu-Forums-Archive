---
title: "Nautilus cannot handle &quot;network&quot; locations..."
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by spotdog14 on 2010-04-01
I am having a problem with my machine where I cannot browse any network location either via the network icon or by manually typing in the smb address. I get the error "cound not display "network:///" nautilus cannot handle "network" locations." 

Anyone have any ideas? I have the most recent updates as of 4/1/10. I had originally upgraded from 9.04. 

Thanks!

---

### Post by dr88dr88 on 2010-04-01
I also have this issue

---

### Post by spotdog14 on 2010-04-01
Bump, anyone else?

---

### Post by doas777 on 2010-04-01
well, if it says "network:///"
then your workgroup may not be set right. what happens when you replace it with:
```
network://WORKGROUPNAME
```?

also remember networ:// only works for the workgroup/domain itself, so if you want to look at a machine by hostname/IP, use smb:// instead
```
smb://HostnameorIP
```

---

### Post by dazvansgillio on 2010-04-01
I don't know if this has any relevence but if I run Nautilus as root "gksu nautilus" I get this same error message. I don't think you can view Network connections when running as root.
Just a thought but how are you starting Nautilus.

---

### Post by Killigrew on 2010-04-02
Hi

I have similar problems, if i start nautilus as root i also get the "cound not display "network:///" nautilus cannot handle "network"  locations." error message.
Moreover if use nautilus as standart user, i can the computers in network places, but
nautilus crashes completely the moment i click on them.

greetings

---

### Post by tica vun on 2010-04-02
I had the same problem, I fixed it by reinstalling nautilus:

```
#apt-get remove --purge nautilus
#apt-get install nautilus
```

---

### Post by Killigrew on 2010-04-02
For me the Problem is related to Nautilus-Actions
if i remove it, everything is working fine.

greetings

---

### Post by dcstar on 2010-04-03
> **dazvansgillio said:**
> I don't know if this has any relevence but if I run Nautilus as root "gksu nautilus" I get this same error message. I don't think you can view Network connections when running as root.


Either try this launcher command:

```
gksudo "dbus-launch nautilus --no-desktop --browser"
```

Or install the **nautilus-gksu** package.

---

### Post by djchandler on 2010-04-03
> **doas777 said:**
> well, if it says "network:///"
then your workgroup may not be set right. what happens when you replace it with:
```
network://WORKGROUPNAME
```?

also remember network:// only works for the workgroup/domain itself, so if you want to look at a machine by hostname/IP, use smb:// instead
```
smb://HostnameorIP
```

Ditto.

And make sure the permissions and firewall on the servers and/or peers are set properly.

Are you trying to connect to a *workgroup* or *homegroup* network with computers running Windows 7 (this may also apply to Vista SP2)? Make sure encryption is not set to 128-bits on Windows 7.

> Control Panel - Administrative Tools - Local Security  Policy

Local Policies - Security Options

Network security: LAN Manager authentication level
Send LM & NTLM responses

Minimum session security for NTLM SSP
Disable Require 128-bit encryption It seems more straightforward to me if Windows 7 computers are set for an office environment, not home when mixing with Linux. Perhaps it's easier now for Linux to connect to a homegroup since the Win7 RTM was released, but the Win7 Beta and RC both were temperamental about allowing connections from almost any other computer not running Windows and especially discovering servers running Linux. We still find connecting to Linux servers even with Windows 7's network discovery enabled sometimes requires fully specifying the path and mounting as a network share. Once we had if configured with the RC, we stuck to what we were doing when the RTM was released to MS Technet subscribers and OEMs in August.

What happens if you reduce connection permissions to the absolute minimum in a workgroup (as an experiment of course and making sure no remote NetBIOS connections are allowed)?

Right now there are 4 computers in this workgroup. Two are running Windows 7 Ultimate, one with MySQL and Apache server running on Ubuntu 9.10, and my laptop dual boots 10.04 beta and Windows 7. I'm having no problems since I decided to not fool with the foolproofed (read: obfuscated to me) MS homegroup solution and did things the way I already knew. I have not encountered a problem where it was suspected that Nautilus was causing trouble in 10.04.

---

### Post by spotdog14 on 2010-04-06
> **tica vun said:**
> I had the same problem, I fixed it by reinstalling nautilus:

```
#apt-get remove --purge nautilus
#apt-get install nautilus
```
this worked for me, thank you!

---

### Post by dentaku65 on 2010-04-09
> **spotdog14 said:**
> I am having a problem with my machine where I cannot browse any network location either via the network icon or by manually typing in the smb address. I get the error "cound not display "network:///" nautilus cannot handle "network" locations." 

Anyone have any ideas? I have the most recent updates as of 4/1/10. I had originally upgraded from 9.04. 

Thanks!

You can try this:
Edit your smb.conf
```
sudo gedit /etc/samba/smb.conf
```
Insert this line under "name resolver" option
```
name resolve order = lmhosts bcast wins host
```
Save the file and reboot your box.

Now the network locations should be fine :-)

---

