---
title: "Trying to remotely connect to Ubuntu Server"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by SarAmyKay on 2010-09-20
Hello All,
I am new to Ubuntu and have been trying to make a remote connection to my home server.  I think I almost there.  Here's what I have done:
 
1) Installed Ubuntu Server 10.0 on a Pentium 2 with 256K
2) Installed SSH, MySQL, desktop GUI and enabled remote access
3) Port forwarded my Lynksys to 5900:22 and 80
4) installed Putty and TightVNC Viewer
5) Obtained a DynDDS account
 
My interanl IP Addy = 192.168.x.yyy
My External IP Addy = 76.xxx.y.zzz
 
When I run Putty, the connection times out (which I am guessing that my server may not be setup correclty).
 
Since I am configuring all this at home, I am unable to simulate a true remote access unless I go to an outside location.  Is there a way to test my connection from outside my network rather than waiting to login remotely from a place other than my home?

---

### Post by endotherm on 2010-09-20
well, first things first, you shouldn't forward  5900 like that. have your vnc users tunnel in via ssh and then establish the vnc connection. vnc isn't secure enough to stand on it's own, but ssh can be configured to be pretty robust.

after that, try using canyouseeme.org to test that  22 is correctly forwarded. make sure the forward rule passes the packets to the specific host you want to receive them.

---

### Post by perspectoff on 2010-09-20
I have sections on Remote Access at

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Remote_Access](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Remote_Access)

and

[http://kubuntuguide.org/Lucid#Remote_Access](http://kubuntuguide.org/Lucid#Remote_Access)

They might help.

Also check out:

[https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html)

From your choice of programs (Putty and TightVNC), it appears that you are trying to connect from a Windows machine as the client to an Ubuntu machine as the OpenSSH (and VNC) server.

You do not need to connect from an outside machine to test your system. Just make sure your client machine allows Putty and TightVNC to connect through its firewall (allowing outbound ports 5900 and 22 if your firewall is port-based).

Also, of course, your DynDNS (or other similar DNS provider) URL must be working correctly to have any access through the Internet. That is priority number 1.

Also, as the above post indicates, allowing port 5900 to be open for VPN use is very high risk on the Internet these days (as is an SSH server without the proper security such as very strong passwords or generated keys). Port 22 (the SSH port) is probably the most scanned port in the world (IMO). Other people would love to run your computer for you remotely.

It is best to establish and secure SSH first and then tunnel VNC through SSH.

Putty has a few quirks, so check out Ubuntuguide for details to make it work correctly.

If your remote client is not Windows-based and is another Ubuntu (or other Linux) OS machine, then don't use Putty. Use the SSH client instead.

---

### Post by perspectoff on 2010-09-20
Also, lastly, I have had an unexplainable quirk over the past few months that every time my dynamic IP address changes, I have to restart my networking.

Something came up in one of the new Linux kernels and I can't figure out what has happened.

I periodically need to restart my networking for my new Dynamic IP address to be recognized, or I also get the connection timeout error.

 sudo /etc/init.d/networking restart

---

### Post by SarAmyKay on 2010-09-21
Thanks for the info.  I am not sure if it answered my question or maybe I need to take baby steps.  I have read all the links prior to my installation.
 
So I guess baby step #1 is to access the server remotely in some way.
 
1) I was able to verify that the port is open using a a tool from DynDNS.org
2) I was able to verify that the external IP addy and the one on the host dns account are the same.
3) I am able to run Putty while I am at home.
4) I ran across to a neighbor and typed in my host name and got nothing.
 
This morning, before I left for work, I verified the server was up and running.  When I tried Putty - it returned with a connection time out error message.

---

### Post by endotherm on 2010-09-21
well lets test that your router is forwarding port  correctly. 
go to [http://www.canyouseeme.org/](http://www.canyouseeme.org/) and put in port 22, to make sure you can connect to it.

---

### Post by SarAmyKay on 2010-09-21
I ran the canyouseeme.org with port 22 on the server and received a Success message.

---

### Post by endotherm on 2010-09-21
> **SarAmyKay said:**
> I ran the canyouseeme.org with port 22 on the server and received a Success message.


ok, so the port is open on your router, which narrows down the problem to either the port on your server, or the forward rule in your router. in the router, does it forward to the internal IP address of the router?

you can test that a port is open and has an application listening on it with telnet. do this from a terminal outside your network
```

telnet <server external ip>  22

```
if it does not work, you will recieve a message like this:
```
Lucid:~$ telnet localhost 22
Trying ::1...
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

```whereas if it succeeds, you will see an message like this:
```
Lucid:~$ telnet localhost 139
Trying ::1...
Connected to localhost.
Escape character is '^]'.

```

that will troubleshoot whether the router's nat rule is sending the packets to the wrong host, and whether the servers firewall is blocking the connection, and whether the ssh is listening for connections.

---

### Post by SarAmyKay on 2010-09-21
I went to a neighbors and ran telnet from a windows XP box.  The command was:
 
telnet 204.xxx.yy.zzz 22
 
It started out with the Connecting... message and then it bombed out with
"Could not open connection to the host on port 22"
 
I then decided to try telnet from the command prompt and it required the "o" in front of the IP address:
***o telnet 204.xxx.yy.zzz 22***
 
results - same as above
 
My third try was to use my host name (grasping for straws):
 
***o telnet myDNs.dnsname.com 22***
**** 
Results - protocol mismatch

---

### Post by endotherm on 2010-09-21
well, it seems that though the port is forwarded on the router, packets are not being routed to your ssh server, or that when they get there they are not processed. 
do you have a firewall config tool installed on the server, and if so, have you allowed port 22 for all source addresses? just to confirm, you can ssh within your own network, right?

edit:
this post indicates that the protocol mismatch error may have been a sign of success. have you tried establishing a ssh connection from your neighbors house? [http://lists.freebsd.org/pipermail/freebsd-stable/2005-January/011100.html](http://lists.freebsd.org/pipermail/freebsd-stable/2005-January/011100.html)

---

### Post by SarAmyKay on 2010-09-22
Got it.  For some reason, when I was able to forward Port 80 to the same IP, it worked.  Thanks for your help.  Now I need to see how I can get a USB camera to work on the server. I would imagine that would be a seperate thread.

---

