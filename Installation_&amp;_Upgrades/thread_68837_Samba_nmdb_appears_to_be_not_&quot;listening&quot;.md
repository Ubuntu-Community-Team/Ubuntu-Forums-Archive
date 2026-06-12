---
title: "Samba nmdb appears to be not &quot;listening&quot;"
date: 2005-09-24
forum: Installation &amp; Upgrades
---

### Post by wacole on 2005-09-24
Have been having trouble seeing Windows machines from my Samba server and vice versa.  To be specific: I can see the Samba server from one Windows PC but not the other, but I can't access shares at all.  I cannot see any Windows machines from the Samba server.

Ran some tests and I think I've found that nmdb which is supposed to be listening on UDP port 137, isn't.  [BTW the reference to nmdb using port 137 UDP comes from The Official Samba-3 Howto and Reference Guide, page 455.  Maybe Ubuntu handles it differently?] PenguinBeach is the Samba server.  Here's the evidence:

First I ran smblookup:
[COLOR=Blue]root@PenguinBeach:/home/wcole # nmblookup -B PENGUINBEACH
Usage: [-?|--help] [--usage] [-B|--broadcast BROADCAST-ADDRESS] [-f|--flags]
        [-U|--unicast STRING] [-M|--master-browser] [-R|--recursion]
        [-S|--status] [-T|--translate] [-r|--root-port] [-A|--lookup-by-ip]
        [-d|--debuglevel DEBUGLEVEL] [-s|--configfile CONFIGFILE]
        [-l|--log-basename LOGFILEBASE] [-V|--version]
        [-O|--socket-options SOCKETOPTIONS] [-n|--netbiosname NETBIOSNAME]
        [-W|--workgroup WORKGROUP] [-i|--scope SCOPE] <NODE> ...[/COLOR]

I did this for several variations on capitalization (just in case) for the Samba server, all with the same result.  Seems to indicate that nothings there?  So next check port activity with nmap:
 
[COLOR=Blue]root@PenguinBeach:/home/wcole # nmap -sT -O localhost

Starting nmap 3.75 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-09-24 11:33 EDT
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1657 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
25/tcp   open  smtp
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
901/tcp  open  samba-swat
5432/tcp open  postgres
Device type: general purpose
Running: Linux 2.4.X
OS details: Linux 2.4.7 (x86)

Nmap run completed -- 1 IP address (1 host up) scanned in 2.777 seconds[/COLOR]

Notice that there is no port 137 in the listing.

In addition I ran netstat:
[COLOR=Blue]
root@PenguinBeach:/home/wcole # netstat -ap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:swat                  *:*                     LISTEN     6513/inetd
[COLOR=Red]tcp        0      0 *:netbios-ssn           *:*                     LISTEN     6881/smbd[/COLOR]
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     7478/cupsd
tcp        0      0 *:postgresql            *:*                     LISTEN     6712/postmaster
tcp        0      0 localhost.localdom:smtp *:*                     LISTEN     6644/master
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     6881/smbd
tcp        0      0 localhost.localdoma:ipp localhost.localdo:32847 ESTABLISHED7478/cupsd
tcp        1      0 localhost.localdo:33069 localhost.localdoma:ipp CLOSE_WAIT 9925/soffice.bin
tcp        0      0 localhost.localdo:32847 localhost.localdoma:ipp ESTABLISHED7168/gnome-cups-ico
tcp6       0      0 *:postgresql            *:*                     LISTEN     6712/postmaster
tcp6       0      0 localhost:smtp          *:*                     LISTEN     6644/master
udp        0      0 localhost.localdo:32768 localhost.localdo:32768 ESTABLISHED6712/postmaster
[COLOR=Red]udp        0      0 192.168.1.10:netbios-ns *:*                                6879/nmbd
udp        0      0 *:netbios-ns            *:*                                6879/nmbd
udp        0      0 192.168.1.1:netbios-dgm *:*                                6879/nmbd
udp        0      0 *:netbios-dgm           *:*                                6879/nmbd[/COLOR]
udp        0      0 *:ipp                   *:*                                7478/cupsd[/COLOR]

which shows nmdb active, but I can't tell if it is listening.  So I ran lsof and see that all of the TCP sessions are marked listen, but none of the UDP sessions are similarly marked which leads me to believe that I may be interpreting the output incorrectly; assuming that any port which is listening is marked with (LISTEN) when that may be true for TCP but not for UDP.  I'm now in over my head.

[COLOR=Blue]root@PenguinBeach:/home/wcole # lsof -i
COMMAND    PID     USER   FD   TYPE DEVICE SIZE NODE NAME
inetd     6513     root    4u  IPv4   9930       TCP *:swat (LISTEN)
master    6644     root   12u  IPv4  10159       TCP localhost.localdomain:smtp (LISTEN)
master    6644     root   13u  IPv6  10160       TCP localhost:smtp (LISTEN)
postmaste 6712 postgres    3u  IPv6  10333       TCP *:postgresql (LISTEN)
postmaste 6712 postgres    4u  IPv4  10334       TCP *:postgresql (LISTEN)
postmaste 6712 postgres    6u  IPv4  10339       UDP localhost.localdomain:32768->localhost.localdomain:32768
postmaste 6716 postgres    6u  IPv4  10339       UDP localhost.localdomain:32768->localhost.localdomain:32768
[COLOR=Red]nmbd      6879     root    6u  IPv4  10607       UDP *:netbios-ns
nmbd      6879     root    7u  IPv4  10608       UDP *:netbios-dgm
nmbd      6879     root    8u  IPv4  10610       UDP 192.168.1.109:netbios-ns
nmbd      6879     root    9u  IPv4  10611       UDP 192.168.1.109:netbios-dgm
smbd      6881     root   20u  IPv4  10636       TCP *:microsoft-ds (LISTEN)
smbd      6881     root   21u  IPv4  10637       TCP *:netbios-ssn (LISTEN)[/COLOR][/COLOR]

I'm stumped.  (BTW SWAT says both smdb and nmdb are running.)

Thank you very much for putting up with this long post.

---

