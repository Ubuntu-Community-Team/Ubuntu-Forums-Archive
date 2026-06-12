---
title: "help in installing Samba - password ?"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by Gordonisnz on 2010-03-27
Hello, I'm reading :- [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)  and it seems to be working fine - However I'm stuck.


I'm reading the first post by '[Stormbringer]("http://ubuntuforums.org/member.php?u=56737")'  - 

Query, is there an updated version of this tutorial ?


My problem - i'm up to this point in the tutorial (before 3. Security considerations.)

> 
Upon reboot you may now map the network drive within Windows.

With WINS enabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\DAPPER\MyFiles
*NOTE: Adjust this to the hostname and sharename you chose above!*
- Click "Finish"
my drive name is LINUXBOX (as I entered in  netbios name = DAPPER

I have netbios name = LINUXBOX  ( sudo gedit /etc/samba/smb.conf )


problem :- After I map the drive letter 0 it brings up a "connecting" message, asking for my username / password 

i enter the username/password of my linux box (same as I loaded for Samba too), however it doesn't work...


I either get one of these replies

a) it doesn't accept my password & re-displays the login prompt again, asking for username/password

or

b) a message comes up

> 
The network path \\LINUXMACHINE\home\samba\ could not be found.
- this is where i manually type in the folder name in the mapping process

ALSO -  (another problem)


In the mapping process, in windows XP, I see a "browse" option.

I can see the pathname :-

My Network Places \ Entire Network \ Microsoft Windows Network \ Mshome \ Linuxmachine\

(note linuxmachine is Linuxmachine, not LINUXMACHINE )

I've restarted samba now - renaming it to "linuxmachine" - same as Windows - but still no go.



anyway, After I select "linuxmachine" I see no further sub-foders, & the "OK" button is not active (so I can't press it & the exact pathname should automatically appear. )


QUERY..

have I got the folder name wrong? 


what process do I follow in my linux box, & windows to check/re-check the exact paths for each to use.

thanks.



EDIT :-

in my Windows Explorer, in "network places', I do NOT see my linux Box. (But i do see it in the mapping process)
 
Does that matter ?

---

### Post by new_tolinux on 2010-03-27
A few things:
You have to setup a samba-share
You have to use \\localmachine.localdomain\share to connect
LINUXBOX is something different as linuxbox (mind the capitals ;))
You have to assign a username + password to your samba-account (which can be different from your linux-credentials).
If the machine doesn't get an IP from a DHCP-server, you might need to connect to \\ip.ad.dr.ess\sharename (will also work if the machine does obtain an IP from a DHCP-server)

And ofcourse if there's a firewall installed it need to be configured to accept incoming connections.

---

### Post by Morbius1 on 2010-03-27
> problem :- After I map the drive letter 0 it brings up a "connecting" message, asking for my username / password 

i enter the username/password of my linux box (same as I loaded for Samba too), however it doesn't work...


I either get one of these replies

a) it doesn't accept my password & re-displays the login prompt again, asking for username/passwordYour post is very confusing but if you're trying to access the linux share from Windows using the linux username and password then you have to create one first. Samba doesn't use the linux login password it uses a samba password. To create one:

Open **Terminal**
Type **sudo smbpasswd -a morbius**
[COLOR=Blue]*Change morbius to your local linux login user name.*[/COLOR]

This will add **AND** enable a "morbius" samba user and ask for a samba password. That's the password you would use from Windows to access the share.

As for the rest of your post, why not post the output of the following commands so we can all follow along:

Open **Terminal**
Type **smbtree**
Type **testparm -s**

---

### Post by Gordonisnz on 2010-03-27
what does smbtree do ??  

here is what i did :-
> 
gordon@gordon-desktop:~$ sudo smbpasswd -a gordon
[sudo] password for gordon: 
New SMB password:
Retype new SMB password:
gordon@gordon-desktop:~$ smbtree
Enter gordon's password: 
gordon@gordon-desktop:~$ testparm -s
The program 'testparm' can be found in the following packages:
 * samba-common-bin
 * samba4-common-bin
Try: sudo apt-get install <selected package>
testparm: command not found
gordon@gordon-desktop:~$ sudo smbtree
Enter root's password: 
gordon@gordon-desktop:~$ 



:- i created new user (I thought I did already, But it didn't say any user exists)
:- added password etc..

did smbtree (nothing happened) 

and the testparm command....

Does the above tell you anything useful ??

---

### Post by Morbius1 on 2010-03-27
Yes it tells me that your install of samba is either incomplete or corrupted. Why Ubuntu doesn't install samba by default is beyond me.

Try at least to install the missing piece first:

**sudo apt-get install samba-common-bin**

Then try the commands again:

**smbtree**
**testparm -s**

---

### Post by Gordonisnz on 2010-03-27
ah - more data :) 

> 
gordon@gordon-desktop:~$ smbtree
Enter gordon's password: 
gordon@gordon-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[print$]"
Processing section "[printers]"
Processing section "[MyFiles]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = MSHOME
    netbios name = LINUXMACHINE
    server string = 
    null passwords = Yes
    username map = /etc/samba/smbusers
    syslog only = Yes
    announce version = 5.0
    name resolve order = hosts wins bcast
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = CUPS
    wins support = Yes

[print$]
    path = /var/lib/samba/printers
    write list = root
    create mask = 0664
    directory mask = 0775
    guest ok = Yes

[printers]
    path = /tmp
    guest ok = Yes
    printable = Yes
    browseable = No
    browsable = No

[MyFiles]
    path = /home/samba/
    force user = gordon
    force group = gordon
    read only = No
    create mask = 0644
gordon@gordon-desktop:~$ 




This shows the words in CAPITALS (the "linuxmachine" i entered) - i guess capitals don't matter ? 

- the actual file doesn't have capitals

---

### Post by Gordonisnz on 2010-03-27
All Fixed...


THOUGH, If I did the "normal' Way - I couldn't map it to my windows box..


I went to "my network places" in WINXP - & it wasn't there (my linux machine) 

but i did a search for "linuxmachine" in the network places, & it found it.. 

I went into a sub-fdirectory & mapped it to Z drive 

Now its showing in my Win XP machine & I can edit / pass files


Thank you

---

