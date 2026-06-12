---
title: "A bit late, I know, but Karmic Samba &quot;fail&quot; issues...."
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-20
Recently I posted my difficulties in getting 3 PC's networked (still haven't succeeded) on this thread in "Networking and Wireless" and wonder if there is any additional info that maybe I am missing regarding Karmic and Samba?

[http://ubuntuforums.org/showthread.php?p=8114815#post8114815](http://ubuntuforums.org/showthread.php?p=8114815#post8114815)

It's not "mission critical" but highly frustrating.  As I have more experience with Ubuntu than most novice users, this may indicate something that needs substantial attention for Lucid.  I don't expect a Windows Wizard, with an "out of the box" instant connection, but there is still way too much CLI as well as educated guessing in what should be a straightforward process.

Thanks!

---

### Post by rtalcott on 2009-10-20
Samba was working fine for me with KK until I did clean installs with the Daily Build from a few days ago...now I see the workgroup but it won't let me log on when I attempt to (using the password of course).  I suppose I should look at samba.conf
rt

---

### Post by Mr. Picklesworth on 2009-10-20
> **rtalcott said:**
> Samba was working fine for me with KK until I did clean installs with the Daily Build from a few days ago...now I see the workgroup but it won't let me log on when I attempt to (using the password of course).  I suppose I should look at samba.conf
rt

I have exactly the same issue here, although I can't actually recall Karmic's Samba working for me at any point. (Jaunty's did,  and I may have just missed a brief period where Karmic's did).

Fresh samba.conf. Mainly Windows Vista and Windows 7 on the network. Worse, it takes about 5 minutes in between failures. (And does so with absolute, impeccable consistency). I don't have time myself, but if someone finds a bug report on this issue, please let us know here. I'll be happy to provide information on my setup where necessary :)

---

### Post by emarkay on 2009-10-20
Hey waitaminute - this is **serious! **

---

### Post by AlanR8 on 2009-10-20
This is odd.

I have a home network with 6 machines. Three including my "server" running Linux, and the rest running XP. All talk and play nicely together.

When I do an install I always do the following:

> sudo apt-get install samba winbind smbfs

My experience has been that samba doesn't fully install by default.

Then I edit my smb.cong file:

> sudo gedit /etc/samba.smb.conf

and scroll down to the line:

> Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = XXXXXXXXX 

and change the name of the workgroup

After a reboot and a couple of minutes, the machine will appear in the workgroup, PROVIDING you have created a shared folder on the machine.

---

### Post by rtalcott on 2009-10-20
My machines appear and are all members of my workgroup...but I enter my user name + psswd and can't get on  (currently my head is pounding from a sinus infection so I am not thinking clearly).  EVERYTHING worked fine a few days ago...pre clean install from the latest Daily Build...I know,...I should have left it alone...

rt

---

### Post by emarkay on 2009-10-20
> **AlanR8 said:**
> This is odd.
I have a home network with 6 machines. Three including my "server" running Linux, and the rest running XP. All talk and play nicely together.
 When I do an install I always do the following:
 My experience has been that samba doesn't fully install by default.
 Then I edit my smb.cong file:
 and scroll down to the line:
 and change the name of the workgroup
 After a reboot and a couple of minutes, the machine will appear in the workgroup, PROVIDING you have created a shared folder on the machine.

Yup all that and more:

```
Configuring SAMBA - October 18, 2009
BACKUP ORIGINAL FILE:  sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup
1. sudo ufw disable

2. gksu gedit /etc/default/ufw
Find and change to this: IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc nf_conntrack_netbios_ns"

3. sudo ifconfig | grep Bcast
Look for "inet addr: and replace last segment  of this IP address with  "0/24".  In my case it's: 192.xxx.x.0/24. Now do:
sudo ufw allow proto udp to any port 137 from 192.xxx.x.0/24
sudo ufw allow proto udp to any port 138 from 192.xxx.x.0/24
sudo ufw allow proto udp to any port 139 from 192.xxx.x.0/24
sudo ufw allow proto udp to any port 445 from 192.xxx.x.0/24

4. Enable and confirm: sudo ufw enable | sudo ufw status

5. Add a user to the Database or change an existing user's password (as root) with smbpasswd:
sudo smbpasswd -a <username>
New SMB password: ######
Retype new SMB password: ######

6. Confirm with: sudo pdbedit -L

7. Paste this stanza into smb.conf:
[global] 
workgroup = WORKGROUP_NAME
netbios name = NETBIOS_NAME
server string =
name resolve order = bcast host lmhosts wins
preferred master = no

printing = cups
printcap name = cups
printcap cache time = 750
cups options = raw
load printers = yes
use client driver = yes
[printers]
comment = All Printers
path = /var/spool/samba
printable = Yes
create mask = 0700
browseable = No
guest ok = Yes
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
browseable = yes
read only = yes
guest ok = no

8. Each share is defined in a separate stanza in smb.conf. - In my case it's:  path = /home/<username>/XXXX_Shared-"X" 
[ShareName]
path = /path_to/shared_directory
read only = no

9. Then: sudo chmod 1777 /path_to/shared_directory

10. Restart Samba: sudo /etc/init.d/samba restart
```

And nuthin', nada, zip.
Filed a bug, maybe it will be addressed for Lucid:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/456808](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/456808)

---

### Post by Mr. Picklesworth on 2009-10-25
Thanks for the link. I really don't think this a "wait until Lucid" kind of issue. Samba has worked without trouble in Ubuntu for about three releases. (Albeit a bit slow). This breaking would be a horrible thing for *a lot* of people.

---

### Post by screaminj3sus on 2009-10-25
> **Mr. Picklesworth said:**
> Thanks for the link. I really don't think this a "wait until Lucid" kind of issue. Samba has worked without trouble in Ubuntu for about three releases. (Albeit a bit slow). This breaking would be a horrible thing for *a lot* of people.

Yeah this is absolutely ridiculous and should be a showstopping bug. It worked perfectly in previous released. No suggestions I have seen have fixed this. I have workgroups correct, firewall makes no difference.

---

### Post by emarkay on 2009-10-26
I cleared 2 machines for just this issue recently, and as you can see on the bug reaport, there's been no effort in progressing further.  I can do no more but hope someone with more authority or skills can chime in and we can get this addressed.

Also, AlanR8, you will see on that bug report that "windbind" is not necessary, or so one person says (while others elsewhere disagree); I had hoped for both a a legit bugfix and some form of "official" tutorial to clarify and specify the "recommended" procedure to get this working for all.

---

### Post by rtalcott on 2009-10-26
I have rechecked all my file permissions, samba.conf and everything else I can think of but no cigar...Samba was working fine until a week or so ago...HELP!

rt

---

