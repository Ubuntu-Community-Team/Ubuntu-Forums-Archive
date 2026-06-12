---
title: "update manager locks up"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by tundra2006 on 2008-05-06
i just got the hardy heron and my update manager locks up after u hit install updates and after that starting administrative window pops up; same goes for my package manager ;  can anyone help;  on the road so i'll post my email tundra06@ zoominternet.net   help please ; cause i need these things to fix a couple other problems i'm having

---

### Post by amohanty on 2008-05-06
Just to be sure I understand what is happening:

1. You click on the update icon in the notification area.
2. You click on 'Install Updates'
3. The password entry window pops up.
4. You enter the password (???)
then what?

AM

---

### Post by alffis on 2008-05-07
I think Tundra has the same problem I'm having, the packet manager never reaches the phase where password is asked.

The system informs me that there are new updates to install and when I click "install selected updates" the system fails to ask the password and Update Manager locks up.

Now I can't change any setting in my system, where administrative password is needed. Although I could install updates by typing "sudo synaptic", then the Packet Manager started.

---

### Post by amohanty on 2008-05-09
To see what might be going in try:

sudo update-manager

Also see if reinstalling gksu helps:

sudo apt-get --reinstall install gksu

hth
AM

---

### Post by selberherr on 2008-05-09
> **amohanty said:**
> To see what might be going in try:

sudo update-manager

Also see if reinstalling gksu helps:

sudo apt-get -reinstall install gksu

hth
AM


The direct way of access via "sudo update-manager" worked for me.

The option -reinstall does not exist under my 8.04 installation?

The problem appears to have something to do with the proper
configuration of the /etc/hosts file, in particular with the localhost entry 127.0.0.1 localhost mymachine.mydomain

Remarks and solutions are welcome

---

### Post by GrumpyOldMan on 2008-05-09
I too have a problem with the update manager locking up. Also whenever I try to execute any sudo command, after a short pause I get the response

sudo: unable to resolve host <hostname>

This seems to be source of the update-manager locking up problem but I don't know what the solution is (yet).

---

### Post by p_quarles on 2008-05-09
> **GrumpyOldMan said:**
> I too have a problem with the update manager locking up. Also whenever I try to execute any sudo command, after a short pause I get the response

sudo: unable to resolve host <hostname>

This seems to be source of the update-manager locking up problem but I don't know what the solution is (yet).
This problem (and most likely the same is true for the other posters in this thread) is a known bug in Hardy. To fix, you'll need to boot into recovery mode and do a couple things. First, run:
```
hostname
```
and make a note of the output. That's the correct name of your computer.

Now, edit /etc/hosts to correct it:
```
nano /etc/hosts
```
The second line should read:
```
127.0.1.1              *hostname*
```
Replace the word "hostname" with the actual hostname from the earlier command.

Now, reboot, and you should be all set:
```
reboot
```

---

### Post by alffis on 2008-05-09
when I start update manager from the command line, the following occurs:
-----
[sudo] password for 'user': 
current dist not found in meta-release file
----------

Then the update manager starts and installs some of the updates, but cannot install all packages - I get this error:

----------
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/transmission/transmission-common_1.06-0ubuntu5_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/transmission/transmission-common_1.06-0ubuntu5_all.deb)
  404 Not Found [IP: 91.189.88.46 80]
---------------

Apparently there is some kind of error in my packet manager settings but I don't have a clue where to start, where are those configuration files?
If I once change the "sources" file manually, is there a chance that Ubuntu has further problems with my manually set sources?

So, is there some kind of easy solution, or do I have to change some sources-file manually?

8)

---

### Post by amohanty on 2008-05-10
> **selberherr said:**
> The direct way of access via "sudo update-manager" worked for me.

The option -reinstall does not exist under my 8.04 installation?

The problem appears to have something to do with the proper
configuration of the /etc/hosts file, in particular with the localhost entry 127.0.0.1 localhost mymachine.mydomain

Remarks and solutions are welcome

I think it is **--**reinstall not **-**reinstall :)

---

### Post by amohanty on 2008-05-10
Take a look at this:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Also in there you can replace us.archive.ubuntu.com with any of the mirrors from here:
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

HTH
AM

---

### Post by alffis on 2008-05-10
Thank you p_quarles,
I changed the "hosts" file and now update manager seems to be working.

---

### Post by GrumpyOldMan on 2008-05-10
Thanks for your response, P_quarles. I actually solved the problem before I managed to read your post by going into System>Administration>Network and adding my hostname as an alias to the 127.0.0.1 IP address (under the hosts tab). Everything seems OK now.

Thanks.

---

### Post by tundra2006 on 2008-05-14
Sorry I didn't get back right away on the road without internet.  HAHA
I did the hostname change and it fixed the problem with not getting to password screen.

---

### Post by der Konner on 2008-07-24
Thanks!  Very helpful info.  Solved my problems immediately.

---

### Post by nikhilxi on 2008-08-03
hi i am new to ubuntu
i also have the update manager.
i tried what p_quariles told but after typing hostname there is no otput. i again get the rompt.
the file /etc/hosts only contains "# The following lines are desirable for IPv6 capable hosts " 
plz help me with this

---

### Post by nikhilxi on 2008-08-03
there s another problem i can't open my web brouser or terminal and many such applications after connecting to net
i can't onen applications from system->administration

---

