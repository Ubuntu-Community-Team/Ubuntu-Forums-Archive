---
title: "Interesting localhost problem"
date: 2009-02-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by knytphal on 2009-02-25
First off, I'm currently using the daily builds of Jaunty so I don't know if that's an issue or not - just so you know.

I currently have my Ubuntu box running openssh-server and the NX Nomachine server which I use to connect to from either my XP box or laptop.  I had logged into the NX server one afternoon and applied the daily updates which required a reboot.  So I selected the reboot option from the menu while still in the client (which promptly locked up).  So I believe then that I opened up a PuTTY ssh terminal and then rebooted....but it's been a couple days since then so I don't recall exactly.

Anyhow - afterwards I was no longer able to connect to the NX server from either the desktop or laptop.  Here is the details of the session:
> NX> 203 NXSSH running with pid: 5876
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.100 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.3.0-15 - LFE
NX> 105 Hello NXCLIENT - Version 3.3.0
NX> 134 Accepted protocol: 3.3.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: swrogers
NX> 102 Password: ********
NX> 103 Welcome to: alien user: swrogers
NX> 105 Listsession --user="swrogers" --status="suspended\054running" --geometry="1680x1050x32+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: swrogers
NX> 105 Start session with: --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Alien" --type="unix-gnome" --geometry="1680x1020" --client="winnt" --keyboard="pc102\057en_US" --screeninfo="1680x1020x32+render" 
NXSERVER - Version 3.3.0-15 - LFE
Wed Feb 25 13:13:50 2009 running as user: 'nx' (uid: 113, pid: 8902) on 'alien'
Info: user login is swrogers (NXShell)
Info: user password is '******' (NXShell)
Info: using 'sshd authentication' (NXShell)
Info: selected user 'swrogers' is authenticated (NXNodeExec)
Info: password for selected user is in 'text' mode (NXNodeExec)
Info: preferred auth method is '' (NXNodeExec)
Info: selected NX Node with host name 'localhost', port '22' (NXNodeExec)
Info: selected publickey method to login NX Node (NXNodeExec)
Info: nxssh command line is '/usr/NX/bin/nxssh -nxservermode -l swrogers localhost -p 22 -x -2 -i /usr/NX/etc/keys/node.localhost.id_dsa -o 'PubkeyAuthentication yes' -o 'RSAAuthentication yes' -o 'RhostsAuthentication no' -o 'PasswordAuthentication no' -o 'RhostsRSAAuthentication no' -o 'StrictHostKeyChecking no' /usr/NX/bin/nxnode' (NXNodeExec)
Info: nxssh child pid is: 9023 (NXNodeExec)
Info: NX Node out channel was closed (NXNodeExec)
Info: received data in err channel from NX Node: 'ssh: connect to host localhost port 22: No route to host
' (NXNodeExec)
Info: NX Node err channel was closed (NXNodeExec)
Info: closing nxssh's in, out, err FDs (flagfinished is: 0) (NXNodeExec)
Error: no 'CONNECTED' message from NX Node (NXNodeExec)
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 35F9EBC7. To get detailed information about
NX> 595 ERROR: the error search for the string 35F9EBC7 in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15



Apparently it looks like it can't ssh to the localhost any more.  I had thought that it might just be an NX issue, but now I'm not so sure.

From the Putty terminal I can ssh to the NX box (192.168.1.100 on the LAN).  From within that terminal I can ssh to its own IP address ( 1.100 ).  However, I can't 'ssh localhost'.  I get no route to host.  I've since noticed that I can not traceroute to the localhost either.  Pinging the localhost returns this:

> swrogers@alien:~$ ping localhost
PING localhost (208.69.36.132) 56(84) bytes of data.
64 bytes from hit-nxdomain.opendns.com (208.69.36.132): icmp_seq=1 ttl=54 time=21.2 ms
64 bytes from hit-nxdomain.opendns.com (208.69.36.132): icmp_seq=2 ttl=54 time=21.2 ms
^C
--- localhost ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 21.218/21.246/21.274/0.028 ms


Which is odd - yes I do use opendns servers.  

nslookup localhost gives basically the same info:
> swrogers@alien:~$ nslookup localhost
Server:         208.67.222.222
Address:        208.67.222.222#53

Non-authoritative answer:
Name:   localhost
Address: 208.69.36.132


My /etc/hosts contains:
> 
127.0.0.1       localhost
127.0.1.1       alien

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Although I'm just noticing the differing IP for alien (which is the localhost) so I'm not sure why it's different.

This all started when I ran the update within the NX session.  I've been using opendns servers for awhile now with no other issues.  I'm not sure what's up with the localhost problem.  I'm sure it's something simple that I'm just overlooking....any ideas?

---

### Post by knytphal on 2009-02-26
Evidently it is related to my using OpenDNS....since localhost isn't resolvable by OpenDNS it doesn't return 127.0.0.1 like it should so it returns something else.

If I turn off OpenDNS, then everything works as expected.

Supposedly I can go in and add a VPN exception of 'localhost' to the typo area, but it's not working.  I've also tried disabling typo correction altogether and it doesn't work either...so who knows.

I'd kind of like to continue using OpenDNS, but I also kind of like being able to properly resolve localhost.

---

