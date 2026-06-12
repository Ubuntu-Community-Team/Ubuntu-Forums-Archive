---
title: "Remote X applications don't work after upgrade to Lucid (Ubuntu 10.04)"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by aajax on 2010-10-02
I upgraded my Ubuntu 8.04 (Hardy) system to 10.04 (Lucid) and my remote X applications no longer work.  The problem seems to pertain to Xauthority.  When the remote X client attempts to access the X server on Lucid it receives an error indicating that there is no matching MIT Magic Cookie (hereafter cookie) for the display.  It turns out that this is true.  I'm of the belief that the subject cookie should be generated for my display when the X session is started on Lucid.  I thought this was being done by GDM when I logged on.  However, $HOME/.Xauthority contains only 1 cookie which is for the display identified as "Pluto/Unix:0" (Pluto is the name of the host).  I'm expecting a cookie for a display identified as "Pluto.my.test:0" where "my.test" is the domain name for my network.  This is the display name that is used on a remote host.

Other strange findings include the following:
- There is no /etc/gdm/gdm.conf only /etc/gdm/dgm.conf.dpkg-bak
- There is a file /etc/gdm/custom.conf which contains a statement "DisallowTCP=false".  I suspect the upgrade was able to figure out that I was permitting remote X sessions and therefore created this statement.  Possibly this also explains why I have this file.
- Unlike the predecessor system "sudo gdmsetup" doesn't allow me to do anything that looks like it will help configure my system for remote X sessions.  Possibly the absence of gdm.conf is affecting the behavior of gdmsetup.
- The gdm man page discusses the purpose of various config files but doesn't mention custom.conf
- When I ping to pluto.my.test I receive replies from 127.0.1.1.  What is that?  My localhost is 127.0.0.1.  Why don't I receive replies from the network interface, which is what happens on other Ubuntu systems I'm running.
- If I run "nslookup pluto.my.test" I receive the proper network address for my host.

---

### Post by gypaete09 on 2010-10-02
I have a similar problem: Using a IP remote HTTP access feature in a control box for thermal (heating / solar) systems from Technische Alternative in Austria.
I find that neither of my Ubuntu Lucid machines can get beyond the HTTP login screen of the control box, after that, I get a new login request and am told another user is already in a session.
Trying Firefox and Internet Explorer (under virtualbox and XP) does not change anything.

I don't have different Ubuntu versions here, but an old native XP machine (yuck!) with the same Internet Explorer 6.0 works, which makes me believe that I lose the session cookie, but weird enough, this seems to happen in Ubuntu Linux 10.04 LTS, not in the browser.

I have seen other similar cases reported in various places on the net, so I hope this will be recognized as a bug and subsequently solved. 

:(

---

### Post by aajax on 2010-10-02
I've now done a little more investigation.  It seems that Lucid is not using $HOME./.Xauthority file.  Rather it has moved it to a subdirectory in /var/run/gdm/ that seems to have been created for the applicable user.  The environment variable XAUTHORITY is set to reference this file.  However, /var/run/gdm/ is protected such that the user cannot access it for updating.  This means that xauth cannot be used to create magic cookies which seems to violate the fundamental design objective for xauth.  Could someone please explain why Lucid wants to prevent proper use of xauth?  This seems like bad design to me.  Possibly someone can explain what I fail to understand.

---

### Post by efflandt on 2010-10-02
How exactly are you enabling remote X apps, using **xhost** command, or using **ForwardX11 yes** in ~/.ssh/config to forward X display back through ssh?  Or are you trying to see an entire remote X server?

If I run **xclock** in ssh to an old SuSE Linux 8.2 (i586) box, it runs xclock on the remote and displays  on my local PC (in gnome).  The prompt in ssh does not return unless I  either fork it into the background instead using **xclock &**, or if I close the xclock displayed locally.

But I notice that if I run **mozilla** in ssh to same old SuSE box, instead of running Netscape on the old server and displaying on my local server, the shell prompt in ssh immediately returns, and it actually ends up launching Firefox 3.6.10 on my local PC.  Not sure why the difference.

Since you upgraded instead of fresh install, maybe some existing files are no are longer relevant or updated (X server version changed).

Also check your /etc/hosts file to see what IP(s) that points to for certain hostnames.  That might mess up an **xhost** setting if it thinks a remote host is local (loopback).  If you are using **xauth**, that might be the wrong tool.  I have not used either because ssh usually does what I need it to do (tunneling ports, IP's, and X apps).

---

### Post by aajax on 2010-10-02
I don't use xhost but rather MIT MAGIC COOKIE.  In this case you create a cookie on the X server machine for the display that is going to be used by the X client (i.e., remote host).  Then you run -

xauth extract - $HOSTNAME.my.test:0 | ssh remhost xauth merge -

which transfers the cookie to the remote host.  Then when you execute the X client application using the same display the cookies match and the session is permitted.  Of course I have some scripts that automate this to the point that the signon script I use on the X server does everything to make the remote host ready to use the local display.  However, now that the Xauthority file is inaccessible I basically cannot use the xauth command which is intended to be a user command.  This is why I think the new design has a major flaw.

I intend to hack around and see what I can do to put the Xauthority file back where it belongs but I fear that this may break the new GDM.  I'll post my findings when I have some more knowledge.

---

### Post by pirx67 on 2011-02-04
> **aajax said:**
> I've now done a little more investigation.  It seems that Lucid is not using $HOME./.Xauthority file.  Rather it has moved it to a subdirectory in /var/run/gdm/ that seems to have been created for the applicable user.  The environment variable XAUTHORITY is set to reference this file.  However, /var/run/gdm/ is protected such that the user cannot access it for updating.  This means that xauth cannot be used to create magic cookies which seems to violate the fundamental design objective for xauth.

xauth still works as expected. If you view the rights of the file then you see that it is owned by the currently logged in user. But the rights of the /var/run/gdm and its subdirectories are set in a way that an unpriviledged user can't list the directory contents and therefore can't guess where the Xauthority file of "pirx67" has been generated by gdm. I think this was done for security reasons and the directory name of the database file contains some random data.

As root you can do:

```

root@hal2006:~# ls -ld /var /var/run /var/run/gdm /var/run/gdm/auth-for-pirx67-OyGdRL/ /var/run/gdm/auth-for-pirx67-OyGdRL/database
drwxr-xr-x 17 root   root   4096 2011-01-12 23:24 /var
drwxr-xr-x 22 root   root    800 2011-02-04 09:50 /var/run
drwx--x--x  4 root   gdm     100 2011-02-04 08:59 /var/run/gdm
drwx--x--x  2 pirx67 pirx67   60 2011-02-04 08:59 /var/run/gdm/auth-for-pirx67-OyGdRL/
-rw-------  1 pirx67 pirx67   52 2011-02-04 08:59 /var/run/gdm/auth-for-pirx67-OyGdRL/database

```

---

### Post by pirx67 on 2011-02-06
I have had nearly the same problems that you had. I also investigated how to get around these issues.

First I want to try to explain the effects you have seen quoting your findings. At last I'll give a
kind of small howto to configure a plain Lucid the way we need.

> **aajax said:**
> 
- There is no /etc/gdm/gdm.conf only /etc/gdm/dgm.conf.dpkg-bak
- There is a file /etc/gdm/custom.conf which contains a statement "DisallowTCP=false". I suspect the upgrade was able to figure out that I was permitting remote X sessions and therefore created this statement. Possibly this also explains why I have this file.


I think you guess right with the upgrade. I had to setup my Lucid from scratch. Therefore I even didn't get the /etc/gdm/gdm.conf file.

> **aajax said:**
> 
- Unlike the predecessor system "sudo gdmsetup" doesn't allow me to do anything that looks like it will help configure my system for remote X sessions. Possibly the absence of gdm.conf is affecting the behavior of gdmsetup.


Between Hardy (gdm < 2.20?) and Lucid (gdm = 2.30.2*) the GNOME guys decided to completely rewrite gdm. Therefore this what we have now is
called gdm2 (since around version 2.20?) and it doesn't support some things that gdm1 supported before. Also the "new" gdmsetup can't 
configure gdm to let you have X remote logins because gdm2 doesn't fully support it.

> **aajax said:**
> 
- The gdm man page discusses the purpose of various config files but doesn't mention custom.conf


You can start the GNOME help browser with "LANG=C;yelp" to get the standard English documentation. There is a section about the custom.conf 
file:

> 
5.4.&#8195;Daemon Configuration

        The GDM daemon is configured using the <etc>/gdm/custom.conf file.  Default
        values are stored in GConf in the gdm.schemas file.  It is recommended that 
        end-users modify the <etc>/gdm/custom.conf file because the
        schemas file may be overwritten when the user updates their system to
        have a newer version of GDM.

        Note that older versions of GDM supported additional configuration
        options which are no longer supported in the latest versions of GDM.      




> **aajax said:**
> 
- When I ping to pluto.my.test I receive replies from 127.0.1.1. What is that? My localhost is 127.0.0.1. Why don't I receive replies from the network interface, which is what happens on other Ubuntu systems I'm running.


A short explanation for this behaviour can be read here: 
[http://www.leonardoborda.com/blog/127-0-1-1-ubuntu-debian/]("http://www.leonardoborda.com/blog/127-0-1-1-ubuntu-debian/")

Some more explanation on name lookup and the FQDN of the local host can be read here:
[http://lists.debian.org/debian-user/2007/09/msg00003.html]("http://lists.debian.org/debian-user/2007/09/msg00003.html")


> **aajax said:**
> 
- If I run "nslookup pluto.my.test" I receive the proper network address for my host.


It boils down to the fact that 127.0.1.1 comes from the /etc/hosts file because it is setup by Debian/Ubuntu to provide
127.0.1.1 as "fallback" for pluto when no other IP interface is up than lo: the loopback interface. The resolver is
configured via /etc/nsswitch.conf for hostnames first look in /etc/hosts and then ask any servers. Therefore 127.0.1.1
from the /etc/hosts file takes precedence over the DNS server.

If you instead query your DNS server directly it delivers the proper network address to you.

To correct this put the proper network address (i.e. the same that the DNS server will deliver) into
the /etc/hosts file for "pluto".

---

### Post by pirx67 on 2011-02-06
The easiest way to provide access for a remote application to the local X server is to use a login in the remote machine with

```

$ ssh -X remoteHost

```

This way the sshd on the remote machine sets the DISPLAY variable to something like "localhost:10.0" to tell the remote application to connect to port #6000+10 on the remote host. There already listens the
sshd to transport any connections to the ssh client which in turns accesses the X server on the local machine using the credentials loaded from the Xauthority file of the user that executes the ssh
client. This is a secure way to get it running.

Unfortunately I needed to connect to a machine where no sshd is present nor could be installed easily. Same problem as you have.
Also I connect only via a trusted network to this machine. With Ubuntu Hardy it worked fine, but Lucid kicked me ...

So I will provide here the steps to get it running again with the MIT-MAGIC-COOKIE transported to the remote host.

First enable the direct connection to the X server via IP networks again by configuring /etc/gdm/custom.conf as needed. If you don't have any in place get the skeleton from the docs:

```

root@thisHost:/etc/gdm# cp -p /usr/share/doc/gdm/examples/custom.conf /etc/gdm

```

Edit the section security to contain the following:

```

[security]
DisallowTCP=false

```

This inhibits gdm to issue "-nolisten tcp" on the command line to the X server when it starts the server.

To check that is working restart gdm and inspect if the X server is listening:
```

root@thisHost:~# service gdm restart
gdm start/running, process 8527
root@thisHost:~# netstat --inet -nap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      848/portmap
tcp        0      0 0.0.0.0:6000            0.0.0.0:*               LISTEN      8531/X
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      1427/vsftpd
:
udp        0      0 0.0.0.0:111             0.0.0.0:*                           848/portmap

```

You can see above the X server listening on port 6000.

Make shure that /etc/hosts fits your configuration:
```

stefan@thisHost:~$ cat /etc/hosts
127.0.0.1	localhost
# 127.0.1.1	thisHost	# dummy only from Debian

192.168.0.3	thisHost

# more lines  follow
#

```

Now we have to add another MIT-MAGIC-COOKIE on demand to the Xauthority file because GDM still only initialises one for the local host to connect via unix sockets. You can check this with "xauth" without parameters from the current user's command line:

```

pirx67@thisHost:~$ xauth
Using authority file /var/run/gdm/auth-for-pirx67-T8W2hy/database
xauth> list
thisHost/unix:0  MIT-MAGIC-COOKIE-1  da92d023e6d5f76bd62b9aad1ebb52ea
xauth> quit
pirx67@thisHost:~$ 

```

The following code snippet from my bash login script will do the trick:
```

# Add a MIT-MAGIC-COOKIE-1 for IP sockets ...
if test -z "`xauth list | grep -v unix | grep $HOSTNAME`"; then
    # No cookie for IP connections present till now.
    # Extract the random pattern of the cookie for our host on unix sockets.
    set `xauth list | grep $HOSTNAME`;
    # Add this also for the IP sockets
    xauth add ${HOSTNAME}${DISPLAY} . $3
fi;

```

This code first checks if no COOKIEs are setup for our HOSTNAME not using unix sockets. Only
then it adds another one for the IP connections and reuses the random pattern that GDM provided
for the COOKIE for the unix sockets. After that something like the following

```

$XAUTH extract - ${HOSTNAME}${MYDISP} | rsh -l $REMUSR $REMSRV $REMPATH/$XAUTH merge -

```

should do the trick to add the MIT-MAGIC-COOKIE on the remote server. Keep an eye on the "REMPATH"
of the xauth program on the remote machine. Its location varies from system to system.

The attached script works for me. But keep in mind to use these things (rsh, telnet and so on) only in trusted networks.

Also you have to have .rhosts setup correctly on the remote host to get the piping of the cookie going as you can't enter any password if rsh / xauth reads the COOKIE from stdin.

Hope that helps somebody,
    pirx67

---

