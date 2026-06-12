---
title: "FreeNX Install Help"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by derpishi on 2012-05-04
I used [http://notepad2.blogspot.com.au/2012/04/install-freenx-server-on-ubuntu-1110.html]("http://notepad2.blogspot.com.au/2012/04/install-freenx-server-on-ubuntu-1110.html") to install FreeNX on 12.04 LTS. It says it's installed. 

Can anyone who has successfully used NX Server help me verify it is installed and lead me down a path to get it working with windows nomachine client? right now it says SSH connection timed out. 

I do see a directory for /usr/NX

I also can not connect to SSH via PuTTY.

Thanks for the help ya'll

---

### Post by wwlliiuu2009 on 2012-05-07
You need to make sure that your ssh server has been installed:
```
sudo apt-get install ssh
/etc/init.d/freenx restart

```

To check if the NX server is running:
```
sudo /usr/NX/bin/nxserver --status
```

---

### Post by derpishi on 2012-05-07
> **wwlliiuu2009 said:**
> You need to make sure that your ssh server has been installed:
```
sudo apt-get install ssh
/etc/init.d/freenx restart

```

To check if the NX server is running:
```
sudo /usr/NX/bin/nxserver --status
```

here's what it returned:
```
mvyvoda@Vyvoda-Laptock:~$ /etc/init.d/freenx restart
WARNING: Service was already stopped, trying to start
NXSERVER - Version 3.2.0-73 OS (GPL, using backend: 3.5.0)
Usage: nxserver <option>
--passwd: Change password
mvyvoda@Vyvoda-Laptock:~$ sudo /usr/NX/bin/nxserver --status
NX> 100 NXSERVER - Version 3.2.0-73 OS (GPL, using backend: 3.5.0)
NX> 110 NX Server is running
NX> 999 Bye
mvyvoda@Vyvoda-Laptock:~$ 

```

looks like its running. but, when i try to connect from windows client or putty, it says timed out.

---

### Post by blackice8r on 2012-05-08
freenx uses ssh so if that doesn't work...

I've tried that script too, I hope it hasn't turned my micro server on to zombie.. :D
It doesn't work for me either but I'll try to tinker with it over the next couple of days

in the mean time , I have a few suggestions for you:

forward port 22 on your home router - I have done that and I can connect to my server using a putty

if you still can't connect to your ubuntu machine via ssh, make sure it's installed 
see here how to install it:[http://www.ubuntugeek.com/how-to-setup-freenx-server-and-client-in-ubuntu-810-intrepid.html](http://www.ubuntugeek.com/how-to-setup-freenx-server-and-client-in-ubuntu-810-intrepid.html)

I think, you also need to add your user to freenx?

I did a:  sudo /usr/NX/bin/nxserver --userlist and it complained that a password component wasn't enabled , so I enabled that in  /user/NX/etc/node.conf

and added my user to freenx: sudo /usr/NX/bin/nxserver --useradd username

I have to get the key  from /home/username/.ssh/authorised_keys2  and paste it on to the client I installed on windows..I think

I'm half guessing here, but I'm sure about port forwarding and about you making sure ssh is working.
 
I need to get this working too so if anyone can help it would be greatly appreciate.
Currently I'm getting this when trying to connect to ubuntu via freenx:
NX> 203 NXSSH running with pid: 3752
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: (my IP) on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.


"Using auth method: publickey "     I think I have to change that, no?

---

### Post by derpishi on 2012-05-08
> **blackice8r said:**
> freenx uses ssh so if that doesn't work...

I've tried that script too, I hope it hasn't turned my micro server on to zombie.. :D
It doesn't work for me either but I'll try to tinker with it over the next couple of days

in the mean time , I have a few suggestions for you:

forward port 22 on your home router - I have done that and I can connect to my server using a putty

if you still can't connect to your ubuntu machine via ssh, make sure it's installed 
see here how to install it:[http://www.ubuntugeek.com/how-to-setup-freenx-server-and-client-in-ubuntu-810-intrepid.html](http://www.ubuntugeek.com/how-to-setup-freenx-server-and-client-in-ubuntu-810-intrepid.html)

I think, you also need to add your user to freenx?

I did a:  sudo /usr/NX/bin/nxserver --userlist and it complained that a password component wasn't enabled , so I enabled that in  /user/NX/etc/node.conf

and added my user to freenx: sudo /usr/NX/bin/nxserver --useradd username

I have to get the key  from /home/username/.ssh/authorised_keys2  and paste it on to the client I installed on windows..I think

I'm half guessing here, but I'm sure about port forwarding and about you making sure ssh is working.
 
I need to get this working too so if anyone can help it would be greatly appreciate.
Currently I'm getting this when trying to connect to ubuntu via freenx:
NX> 203 NXSSH running with pid: 3752
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: (my IP) on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.


"Using auth method: publickey "     I think I have to change that, no?

when i try to add a user, this is what it returns.

```
[/mvyvoda@Vyvoda-Laptock:~$ sudo /usr/NX/bin/nxserver --useradd mvyvoda
NX> 100 NXSERVER - Version 3.2.0-73 OS (GPL, using backend: 3.5.0)
NX> 500 Error: The passdb function is not activated in node.conf.

Most probably your FreeNX setup will work out of the box without this
functionality and you've been misleaded by an old tutorial or old
documentation to do this step.

If however you really need this functionality, just set
ENABLE_PASSDB_AUTHENTICATION="1" in node.conf.

NX> 999 Bye
mvyvoda@Vyvoda-Laptock:~$ 

```

i enabled passbd authentication to 1, then saved it. i restarted the freenx server. what else do i need to do?

i think i am out of my league with this software. just wanted to securely remote desktop is all....

---

### Post by blackice8r on 2012-05-09
add the user to freenx: sudo /usr/NX/bin/nxserver --useradd username

but, did you get ssh to work?

---

### Post by derpishi on 2012-05-09
> **blackice8r said:**
> add the user to freenx: sudo /usr/NX/bin/nxserver --useradd username

but, did you get ssh to work?

here's what adduser returns:

```
mvyvoda@Vyvoda-Laptock:~$ sudo /usr/NX/bin/nxserver --useradd mvyvoda
[sudo] password for mvyvoda: 
NX> 100 NXSERVER - Version 3.2.0-73 OS (GPL, using backend: 3.5.0)
NX> 500 Error: The passdb function is not activated in node.conf.

Most probably your FreeNX setup will work out of the box without this
functionality and you've been misleaded by an old tutorial or old
documentation to do this step.

If however you really need this functionality, just set
ENABLE_PASSDB_AUTHENTICATION="1" in node.conf.

NX> 999 Bye
```

I can not connect via SSH on a client machine.

---

### Post by derpishi on 2012-05-09
> **derpishi said:**
> here's what adduser returns:

```
mvyvoda@Vyvoda-Laptock:~$ sudo /usr/NX/bin/nxserver --useradd mvyvoda
[sudo] password for mvyvoda: 
NX> 100 NXSERVER - Version 3.2.0-73 OS (GPL, using backend: 3.5.0)
NX> 500 Error: The passdb function is not activated in node.conf.

Most probably your FreeNX setup will work out of the box without this
functionality and you've been misleaded by an old tutorial or old
documentation to do this step.

If however you really need this functionality, just set
ENABLE_PASSDB_AUTHENTICATION="1" in node.conf.

NX> 999 Bye
```

I can not connect via SSH on a client machine.

UPDATE: I added the ssh port to my firewall on Ubuntu and SSH works now. 
there are a series of mistakes I made until now. I followed: [http://ubuntuforums.org/showthread.php?t=1490038]("http://ubuntuforums.org/showthread.php?t=1490038") and changed settings in sshd_config. 

if you want to login to an existing session, use Shadow instead of UNIX. Need to change some files too: [https://bbs.archlinux.org/viewtopic.php?id=104488]("https://bbs.archlinux.org/viewtopic.php?id=104488")

---

### Post by blackice8r on 2012-05-10
> **derpishi said:**
> UPDATE: I added the ssh port to my firewall on Ubuntu and SSH works now. 
there are a series of mistakes I made until now. I followed: [http://ubuntuforums.org/showthread.php?t=1490038]("http://ubuntuforums.org/showthread.php?t=1490038") and changed settings in sshd_config. 

if you want to login to an existing session, use Shadow instead of UNIX. Need to change some files too: [https://bbs.archlinux.org/viewtopic.php?id=104488]("https://bbs.archlinux.org/viewtopic.php?id=104488")

to enable it, edit the node.conf file in : /user/NX/etc/node.conf

change ENABLE_PASSDB_AUTHENTICATION="0" to ENABLE_PASSDB_AUTHENTICATION="1" and delete the "#" in front of the line

you can do this using vi I think: vi /user/NX/etc/node.conf
or in terminal open nautilus as root (sudo nautilus) and browse to the file to edit it

this will allow you to enable the function and add your user , but after that? I really don't know...
I didn't have time to try new things...

any of the Ubuntu pros around for some advice?

---

### Post by derpishi on 2012-05-11
> **blackice8r said:**
> to enable it, edit the node.conf file in : /user/NX/etc/node.conf

change ENABLE_PASSDB_AUTHENTICATION="0" to ENABLE_PASSDB_AUTHENTICATION="1" and delete the "#" in front of the line

you can do this using vi I think: vi /user/NX/etc/node.conf
or in terminal open nautilus as root (sudo nautilus) and browse to the file to edit it

this will allow you to enable the function and add your user , but after that? I really don't know...
I didn't have time to try new things...

any of the Ubuntu pros around for some advice?

good tip about the # in front!!! i am able to login to NX Server from Windows into a new session of Ubuntu. However, I am unable to use a shadow session. This is what I am continuing to explore. 

Also, not sure if I did the RSA key correctly. hmmm...

---

### Post by blackice8r on 2012-05-18
> **derpishi said:**
> good tip about the # in front!!! i am able to login to NX Server from Windows into a new session of Ubuntu. However, I am unable to use a shadow session. This is what I am continuing to explore. 

Also, not sure if I did the RSA key correctly. hmmm...

good to hear it's working at least to some extent...
I also fallowed  [http://notepad2.blogspot.com.au/2012/04/install-freenx-server-on-ubuntu-1110.html](http://notepad2.blogspot.com.au/2012/04/install-freenx-server-on-ubuntu-1110.html)

but I didn't get it to work, could be a different problem as X crashes from time to time...

I'm going back to the snapshot before the Ubuntu upgrade, when everything was working
I was thinking to install ubuntu directly on the server and ditch vmware...but I can really see the benefits now..
My ubuntu it's running as as virtual machine in esxi5 so I can go back to the old status...

You used to be able to get a lot of support really fast on these forums but now..nothing..

If I find the time I'll start studying ubuntu from a book or something as it seems tricky to fix something when it's not working.

---

