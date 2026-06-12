---
title: "Samba and Swat"
date: 2005-08-20
forum: Installation &amp; Upgrades
---

### Post by svetlo56 on 2005-08-20
I installed both Samba and Swat. Samba appears to be working, but I can't launch Swat. When I try [http://127.0.0.1:901/](http://127.0.0.1:901/) I get "the connection was refused when attempting to contact 127.0.0.1". Now I do not know how to launch Swat. Anyone?

---

### Post by dberetta on 2005-08-20
We dont know what you have done and what you have not. 
Have you tried this ?

sudo update-inetd --enable 'swat'

---

### Post by hamil on 2005-10-16
Hello!

I think I will reopen this thread...
Earlier today, I installed swat via Synaptic, togheter with the samba packages.
I am triyng to set up a small network to share files between the computers at our WLAN at home.

When trying to access [http://localhost:901](http://localhost:901), or [http://127.0.0.1:901](http://127.0.0.1:901) I get an "Connection refused" message...

I have no clue whatsoever, about my next step...
I have tried some googling, but most of the replies I could find, asked me to do some editing in files I do not have on my computer.

Any ideas?

Brdgs
Lasse

---

### Post by rider343 on 2005-10-16
I have the same problem here :(

---

### Post by triplep on 2005-10-16
inetd doesn't work initally in breezy, you need to get 'netkit-inetd' with either snaptic or apt-get, whichever you prefer


i doubt that this applies to the 5.04 Hoary rls, i was just replying to the asked question.

---

### Post by hamil on 2005-10-17
Jupps, that did miracles! :)

Triplep, thanx for the solution!

---

### Post by Thymen on 2005-11-21
perhaps you can help me out then....:D 

I installed Xinet package, swat etc, but swat does not run. When I try to re-install using apt-get, it says that both are already installed. But a ps -e | grep -e 'swat' shows swat service is not running.

So, nor via 'sudo swat', not via firefox ([http://localhost:901](http://localhost:901)) I can get swat to run. Firefox gives the message too: "conection refused".

Manually configuring the samba config file and adding samba users was OK, I can share folders / files over my windows/Ubuntu network, but I would like swat as a graphical interface available to me.

So... any suggestions? Like how to start up swat manually?

Thymen

edit: I edited the /etc/inetd.conf file, removing the #<off># comment before the swat commands..... then reboot....now swat fires up  with Firefox!

Thymen

edit: what a bummer... I expected a full swat package, as in RedHat, allowing me to change every setting through swat.... but this swat does not allow me to do anything except for changing a password....:(

---

### Post by fabioleitao on 2006-05-03
Oddly enough, I think SWAT was never in the planes for Ubuntu.

I have no problem in setting things up manually, and scrubbing a few conf files till perfection... but I've realized it's a commom problem for most people.

Of course I've been through the usual steps, such as **sudo apt-get samba samba-common smbfs smbclient swat**

But for you to get **swat** to work, you will need to install a dependency beforehand **apt-get install xinetd **.

Then, **sudo vi /etc/inetd.conf** and uncomment the line:
#<off># swat             stream  tcp     nowait.400      root    /usr/sbin/tcpd  \ /usr/sbin/swat

Then make an entry for Swat under xinetd with **sudo vi /etc/xinetd.d/swat**

And it should look like this:
[INDENT][FONT="Courier New"]# description: SAMBA SWAT
service swat
{
  disable  = no
  socket_type  = stream
  protocol  = tcp
  #should use a more limited user here
  user  = root
  wait  = no
  server  = /usr/sbin/swat
}[/FONT][/INDENT]

Then, **sudo dpkg-reconfigure xinetd** to restart with the new configuration.

Now the **netstat -lt** should echo something similar to this:
[INDENT][FONT="Courier New"]Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 *:5666                  *:*                     LISTEN
tcp        0      0 localhost:1026          *:*                     LISTEN
tcp        0      0 localhost:1027          *:*                     LISTEN
**tcp        0      0 *:swat                  *:*                     LISTEN**
tcp        0      0 localhost:mysql         *:*                     LISTEN
tcp        0      0 *:netbios-ssn           *:*                     LISTEN
tcp        0      0 *:10000                 *:*                     LISTEN
tcp        0      0 *:1040                  *:*                     LISTEN
tcp        0      0 *:munin                 *:*                     LISTEN
tcp        0      0 localhost:ipp           *:*                     LISTEN
tcp        0      0 *:smtp                  *:*                     LISTEN
tcp        0      0 *:microsoft-ds          *:*                     LISTEN
tcp6       0      0 *:2080                  *:*                     LISTEN
tcp6       0      0 *:www                   *:*                     LISTEN
tcp6       0      0 *:ssh                   *:*                     LISTEN[/FONT][/INDENT]

Which indicates the swat service is running and listening to the correct 901 tcp port.

Remember to open the TCP port for the firewall if you are using any.

My **iptables -L -v** looks like that:
[FONT="Courier New"][INDENT]Chain INPUT (policy ACCEPT 1607 packets, 168K bytes)
 pkts bytes target     prot opt in     out     source               destination
18688 3148K ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED
    0     0 ACCEPT     tcp  --  eth0   any     anywhere             anywhere            tcp dpt:ssh
    0     0 ACCEPT     tcp  --  eth0   any     anywhere             anywhere            tcp dpt:www
    0     0 ACCEPT     tcp  --  eth0   any     anywhere             anywhere            tcp dpt:microsoft-ds
   18  3450 ACCEPT       udp  --  eth0   any     anywhere             anywhere            udp dpts:netbios-ns:netbios-ssn
**   11   528 ACCEPT     tcp  --  eth0   any     localnet/24          anywhere            tcp dpt:swat**
    0     0 ACCEPT     tcp  --  eth0   any     anywhere             anywhere            tcp dpt: x11
  291 39656 ACCEPT     udp  --  eth0   any     localnet/24          anywhere
    0     0 ACCEPT     icmp --  eth0   any     localnet/24          anywhere
   94  6728 ACCEPT     all  --  lo     any     anywhere             anywhere
    0     0 DROP       all  --  any    any     anywhere             anywhere

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 2317K packets, 2125M bytes)
 pkts bytes target     prot opt in     out     source               destination[/INDENT][/FONT]

You might be able to access **http://<yourserver>:901/**

---

### Post by cwhamsun on 2006-05-15
I am using Dapper right now. Following advice (fabio) given here, I installed the packages needed and edited the files also. netstat -lt shows swat is listening, and checked iptables to make sure it allows the connection, and it does. Browser still will not connect to 901. I also used firestarter and turned the firewall to STOP temporarily and still no luck. Samba is running when I check services. I have previously set up samba on as a file server using redhat enterprise linux 3 on a small mixed network (about 30 pcs, one NT server, one novell netware server and mix of win 98/2000/xp) and it was fairly easy, I don't recall having these kind of problems. If anyone has any ideas it would be much appreciated. I tried both as my default user, and then manually added a root account and tried that also, and no luck at all.](*,)

---

### Post by nischg on 2006-07-04
thank you fabioleitao, that worked for me!

---

### Post by encho on 2006-07-10
Thanks! Finally worked.=D>

---

### Post by Gen. Hospital on 2006-07-10
When logged in as a regular user, all I get is Home, Status, View, and Password. On my Fedora box, I can log in as root to access the useful part of SWAT, but that does not work on my Ubuntu powered laptop. Any ideas?

Thanks

---

### Post by jhull99 on 2006-08-05
I had to give the root account a password (with passwd, not smbpasswd) to get SWAT to let me log in as root.  If there is another way to do it, please someone post it.

---

### Post by bensexson on 2006-08-10
Does anyone have any ideas about how to get full control of samba without enabling the root accout? I forgot to mention control through swat.

---

### Post by ner0tic on 2006-11-12
it worked for me accept i dont' have a working l/p to get me into it? did i miss a step?

---

### Post by rumour88 on 2006-11-21
Another tanks to fabioleitao I can now stop banging my head of a wall ](*,)  > :-D

---

### Post by davidbacsik on 2006-11-27
Ugh!

I've followed all advice here to a T, and I still get nothing when I run netstat -lt

Here's my /etc/xinetd.d/swat
```

# description: SAMBA SWAT
service swat {
 disable = no
 socket_type = stream
 protocol = tcp
 user = root
 wait = no
 server = /usr/sbin/swat
}

```

And my /etc/inetd.conf
```

<off>  netbios-ssn      stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/smbd
<off>  swat      stream tcp nowait.400 root /usr/sbin/tcpd \ /usr/sbin/swat

```

I've also tried 

apt-get install samba swat netkit-inetd
sudo update-inetd --enable 'swat'

and this made no change too.

I'm at a loss.  Am I doing something wrong?

---

### Post by Corolla92 on 2006-11-27
> **davidbacsik said:**
> Ugh!

I've followed all advice here to a T, and I still get nothing when I run netstat -lt

Here's my /etc/xinetd.d/swat
```

# description: SAMBA SWAT
service swat {
 disable = no
 socket_type = stream
 protocol = tcp
 user = root
 wait = no
 server = /usr/sbin/swat
}

```

And my /etc/inetd.conf
```

<off>  netbios-ssn      stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/smbd
<off>  swat      stream tcp nowait.400 root /usr/sbin/tcpd \ /usr/sbin/swat

```

I've also tried 

apt-get install samba swat netkit-inetd
sudo update-inetd --enable 'swat'

and this made no change too.

I'm at a loss.  Am I doing something wrong?

Same thing here :confused:

---

### Post by smazero on 2006-12-20
I'm far from being any kind of expert, and I haven't tested this; but when you edited your inetd.conf file, aren't you supposed to remove the whole #<off># block from the line, rather than just the # characters.

So your inetd.conf file would look like this:

```

netbios-ssn      stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/smbd
swat                   stream tcp nowait.400 root /usr/sbin/tcpd \ /usr/sbin/swat

```

---

### Post by dvdhldn on 2006-12-27
ditto, thanks fabio.

---

### Post by bvucinic on 2007-01-31
Thanks fabioleitao :D

---

### Post by punkybouy on 2007-01-31
Isn't SWAT a secure app?  So wouldn't you have to type "https" and not "http"?

---

### Post by ddoctor on 2007-02-20
It would probably be good if swat was running over ssl, but that'd take more work. 

I could be completely full of ****, but here's my understanding:

I don't think inetd or xinetd are web servers - their descriptions indicate that they merely act as a superserver - accepting requests on a large number of ports, and palming the requests off to different subservers. In this way, you have a single point of configuration for all of your services - something known to be reliable as the front-man for hosted services... acting like a kind of proxy.

Contrast to Apache, a true web server. It lets you configure websites, running as collections of static files, plugins or cgi scripts (php et al). HTTPS is quite configurable through apache.

swat seems to be like a compiled app with its own simple webserver built-in. 

To configure it to run over HTTPS, you'd need, like, a swat plugin for Apache, or a swat version that ran as, eg, PHP scripts. For all I know, swat's built-in webserver may be apache, so it could well be capable of https :)


I'd just lock swat down at with a firewall and password. In a small network, there's no real reason why it needs to be accessed by anything other than localhost.

---

### Post by hardin0341 on 2007-03-19
Two days almost non-stop and still no SWAT! I have tried it all, but my **netstat** does not indicate any swat listening posts. 
This is what it looks like:
[B]
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost.localdo:mysql *:*                     LISTEN
tcp        0      0 *:netbios-ssn           *:*                     LISTEN
tcp        0      0 *:microsoft-ds          *:*                     LISTEN
tcp6       0      0 *:www                   *:*                     LISTEN
tcp6       0      0 *:ssh                   *:*                     LISTEN
tcp6       0    132 rsjzMedia.ryan.com:ssh  ::ffff:192.168.1.2:1430 ESTABLISHED
udp        0      0 rsjzMedia.ry:netbios-ns *:*
udp        0      0 *:netbios-ns            *:*
udp        0      0 rsjzMedia.r:netbios-dgm *:*
udp        0      0 *:netbios-dgm           *:*
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ]         DGRAM                    4933     @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     8568     /var/run/mysqld/mysqld.sock
unix  7      [ ]         DGRAM                    8411     /dev/log
unix  2      [ ]         DGRAM                    10662
unix  2      [ ]         DGRAM                    10383
unix  3      [ ]         STREAM     CONNECTED     10380
unix  3      [ ]         STREAM     CONNECTED     10379
unix  2      [ ]         DGRAM                    8820
unix  2      [ ]         DGRAM                    8565
unix  2      [ ]         DGRAM                    8468
[/B]

I am going cross-eyed quick. Running Ubuntu 6.10 Server as a LAMP. I've reconfigured and reconfigured and I'm not getting anywhere. 
Please help.

Thanks in advance for ANYTHING! (it's even okay to tell me to give up and go home).

---

### Post by danbopes on 2007-03-28
I'm getting this same issue too.  I set up all of the files correctly, but it still doesn't come up in the netstat -lt menu.

---

### Post by fermo111 on 2007-04-24
I had the same problem. I solved it inserting the SWAT port number in the xinetd.conf file

```
port = 901
```


```
# description: SAMBA SWAT
service swat 
{
	disable = no
	socket_type = stream
	protocol = tcp
	user = root
	wait = no
	server = /usr/sbin/swat
	port = 901
}
```

Luca

---

### Post by chang47 on 2007-05-20
It seems like a long standing issue.  I was trying to get swat working on Xubuntu 7.04 with the same problem mentioned here.  installing  inetd solved the problem.  Thank you.:D

One would think that by installing swat, it would also install inetd or xinetd as a dependency.  Anyhow, after making swat working, I wondered if it was worth the effort for a desktop user.  It didn't give me more info or any friendlier than working with command lines.  I guess you need to run swat in root privilege in order to have swat displayed more info.

---

### Post by IcarusR on 2007-06-18
If you do not get enough options using SWAT try installing Webmin.
with Webmin you get full control of SAMBA & other servers, as well as other stuff.

---

### Post by maphew on 2007-06-20
Thank you fabioleitao!

I added part of your help to [https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat)

---

### Post by jeiworth on 2007-07-08
Hi,

first post on this board i believe :)

Since I was struggling with the same problems getting Swat to run I'd thought I follow up in this thread. And thanks to fabioleitao for the great HowTo and maphew for keeping the community docs up to date :)

Only one thing remains, and that is, as bensexson also posted, how can I manage Samba through Swat without having to use/activate the root account?

Is it advisable to run Samba and/or Swat with e dedicated swat-user? What user rights would this user/group need?

As I understand it Sambas own user management is not active in (K)Ubuntu (it did have one, didn't it?)...

Thanks!

---

### Post by danielelias on 2007-07-13
Thank you, Fabio. Your accurate instructions were very helpful.

---

### Post by jet2230 on 2007-07-28
> **hardin0341 said:**
> Two days almost non-stop and still no SWAT! I have tried it all, but my **netstat** does not indicate any swat listening posts. ....

having the same problem, any fixes to this yet?  my netstat -lt

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:nfs                   *:*                     LISTEN     
tcp        0      0 *:44869                 *:*                     LISTEN     
tcp        0      0 *:mysql                 *:*                     LISTEN     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 *:779                   *:*                     LISTEN     
tcp        0      0 *:x11-1                 *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 *:49720                 *:*                     LISTEN     
tcp        0      0 *:smtp                  *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
tcp6       0      0 *:imap2                 *:*                     LISTEN     
tcp6       0      0 *:x11-1                 *:*                     LISTEN     
tcp6       0      0 *:smtp                  *:*                     LISTEN 

also tried 'port = 901' with no effect. would be grateful if someone could help. thanks.

---

### Post by jet2230 on 2007-07-28
> **maphew said:**
> Thank you fabioleitao!

I added part of your help to [https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat)

sorry im blind :), this guide did the job for me thanks.

---

### Post by Heliix on 2007-08-28
> **triplep said:**
> inetd doesn't work initally in breezy, you need to get 'netkit-inetd' with either snaptic or apt-get, whichever you prefer


i doubt that this applies to the 5.04 Hoary rls, i was just replying to the asked question.
thanks, worked for me (ubuntu edgy) :-)

---

### Post by cjraven on 2007-12-31
A long time after this was originally posted, but I just found it after doing some searching trying to find out how to better admin Samba.

Bravo and thanks! This worked precisely as described - out of the box. Same issue with Gutsy, same solution.

Thanks for this, even if it is somewhat "after the fact" the info is still good, and much appreciated.

---

### Post by cartes on 2008-01-05
If like me you've read all the forums and tried many of the suggestions to get SWAT going, take a pause and fully restart your pc - worked for me. All the ways of trying to restart the service and the old fashioned way done the trick!

---

### Post by Jnetty99 on 2008-03-19
I been trying to check out SWAT but haven’t been able to get it working. 
I installed Ubuntu Server and I’m trying this through VMware. I got Webmin working but can't get SWAT so I started with a clean installation again. I want to see which one is better. 

Basically once swat is installed I got to:
[http://localhost:901](http://localhost:901)
[http://192.168.1.x:901](http://192.168.1.x:901),
[http://servername:901](http://servername:901)
[http://127.0.0.1:901](http://127.0.0.1:901)
Nothing gets me connected to SWAP. I just get the “can’t connect” or “the connection was reset” using Firefox. I read several ways people installed but still nothing. Here are the steps that I try to get it installed, maybe someone could point out if I missed something. 

I used this website as a reference [https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat)

sudo apt-get install xinetd (because I don't have it, I think, its 7.10 server)
sudo update-inetd --enable 'swat'
sudo apt-get install swat
sudo nano /etc/xinetd.d/swat to edit

I add the following to swat file
```
# default: off 
# description: SWAT is the Samba Web Admin Tool. Use swat \
#              to configure your Samba server. To use SWAT, \
#              connect to port 901 with your favorite web browser.
service swat
{
        port    = 901
        socket_type     = stream
        wait    = no
        only_from = localhost
        user    = root
        server  = /usr/sbin/swat
        log_on_failure  += USERID
        disable = no
}
```
Exit and save 

sudo dpkg-reconfigure xinetd

After that I try to access it and nothing works.

I restart the server also and still not working. I also check the /etc/inetd.conf file and #<off># has been removed. 
I also run netstat –lt and get the following

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 *:swat                  *:*                     LISTEN
tcp        0      0 *:netbios-ssn           *:*                     LISTEN
tcp        0      0 *:microsoft-ds          *:*                     LISTEN
tcp6       0      0 *:ssh                   *:*                     LISTEN

any tips?

---

### Post by Scott1960 on 2008-03-30
Thanks fabio

---

### Post by elventear on 2008-04-04
Everyone having problems to access SWAT, please check the only_from directive in the configuration file.

---

