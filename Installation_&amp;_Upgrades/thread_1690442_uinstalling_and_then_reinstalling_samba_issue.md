---
title: "uinstalling and then reinstalling samba issue"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by cormu7 on 2011-02-18
Hello,

I'm having an issue with samba and trying to reinstall it.

I uninstalled samba with this command

>     }sudo apt-get remove samba   or

 >   sudo apt-get purge samba  After either one of these steps, i noticed that the /etc/samba/ directory still existed, which was odd since I thought i uinstalled samba. So, I proceeded to remove all of the fiels within the /etc/samba/ directory and removed the samba directory as well.

After this, I tried to reinstall samba with this command

>   sudo apt-get install samba  After this installation step, the /etc/samba directory does not exist and  neither does the smb.conf file and other files within he /etc/samba directory exist after installation.



when i type 

>  testparm -s i get the following message

>  Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:OpenConfFile() - Unable to open configuration file "/etc/samba/smb.conf":
    No such file or directory
Error loading services. I'm not sure what is going on here. I'm trying to get my samba up and running again.

Any thoughts?

---

### Post by mikewhatever on 2011-02-18
Removing /etc/samba was a mistake, recreate it, then you can grab an smb.conf from /usr/share/samba/smb.conf.

---

### Post by cormu7 on 2011-02-21
mike,

thanks for the tip. 

i'm still not there yet though.

the testparm -s command now spits out the info in my smb.conf file. here it is below:

> [global]
    workgroup = WORKIGROUP
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[data]
    comment = Ubuntu File Server Shar
    path = /data/
    valid users = user1,user2,user3
    read only = No
    create mask = 0755


i'm now able to type the commands

> sudo restart smbd

and

> sudo restart nmbd[/QUOTE

without any errros.

however i'm still not able to access the server via samba on a windows machine. i see the workgroup name on our LAN, but when trying to access I get the "you do not have permission to use this network resource...".

when i type the command

[QUOTE]ps -ef | grep mbd

i get this result


>   root      9484     1  0 08:34 ?        00:00:00 smbd -F
root      9487  9484  0 08:34 ?        00:00:00 smbd -F
root      9493     1  0 08:34 ?        00:00:00 nmbd -D
username       9495  9361  0 08:34 pts/1    00:00:00 grep mbd   

So, i think the issue is the "-F" you see on the first 2 lines of the output above, but i'm not sure how to fix this?

Any ideas?

Thanks,

cor

---

### Post by cormu7 on 2011-02-21
i tried something based on the thread below:

[http://ubuntuforums.org/showthread.php?t=1599818](http://ubuntuforums.org/showthread.php?t=1599818)

i changed the command:

**[COLOR=Blue]exec smbd -F to [/COLOR]**[B][COLOR=Blue]exec smbd -D

[/COLOR][/B][COLOR=Black]in the [/COLOR]/etc/init/smbd.conf file.

i then rebooted my server.

now when I type

> ps -ef | grep mbd i get this output

> root      1358     1  0 12:45 ?        00:00:00 smbd -D
root      1503  1358  0 12:45 ?        00:00:00 smbd -D
root      1912     1  0 12:45 ?        00:00:00 nmbd -D
username       2849  2769  0 13:41 pts/0    00:00:00 grep mbd
that seem to do the trick. i don't know why, but samba seems to work now and i can access the server from a windows machine.

cor

---

