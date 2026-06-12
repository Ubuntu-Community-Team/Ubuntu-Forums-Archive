---
title: "Installation/Configuration Debugging Hints (telnetd)"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by cmnorton on 2007-06-30
Setting aside for the moment the argument that sshd is more secure than telnetd, I am looking at Ubuntu server as one of several possible replacements for a Red Hat 9 server which hosts a municipal tax collection package. 

The package's data store is implemented as Informix SE, and the primary interface is Informix forms, which requires clients to log in via telnet. All client connections take place inside a very secure firewall, and there is no access to the current server from outside the firewall.

I have tried installing telnetd a couple of different ways, but cannot get it running. I want to debug what is wrong, have looked in /var/log/messages, and found nothing conclusive. The installation says it completed just fine.

I am having trouble finding the location of the actual telnetd daemon and then finding out why it won't start. So, debugging hints on what to look for after the telnetd installation, that is what should be there, configuration, telnetd's path, and how to hand-start it, and so on would be very appreciatied.

The ubuntu installer package lists a few different ways to download telnetd. If someone suggests a group of preferred packages, I can easily remove what's there, and try again.

Many thanks.
cmn

---

### Post by cmnorton on 2007-07-17
I got the telnetd running by installing netkit-inetd, telnetd, and modifing inetd.conf, so the telnetd line looks like this

telnet		stream	tcp	nowait	telnetd.telnetd	/usr/sbin/tcpd	/usr/sbin/in.telnetd

Originally it looked like this after the installation:

telnet		stream	tcp	nowait	telnetd.telnetd	/usr/sbin/tcpd	/usr/sbin/telnetd

---

### Post by Hunza on 2007-07-17
I recently installed ubuntu on my pc Adm64 mechine, running window xp,by creating 50mg boot drive on harddisk0. second hard drive  was formatted for unix in which ubuntu evetually got installed by bootloader which came with downloaded ubentu  adm64 distro.
 Iam still a newbie, hate to give up my windowxp yet,as  I still have problems with ubentu such as sound card not working. currently i have limited  time,evetually i will learn with time to correct this problem.
 My issue now is if i donot do any thing after i start my pc, in few second ubuntu gets loaded. Can i able to Chose  to get windows xp come up in loadind stack.:confused::confused:
If this possible let me know step by step instructions,Remmber I am total newbe.
thanks

---

