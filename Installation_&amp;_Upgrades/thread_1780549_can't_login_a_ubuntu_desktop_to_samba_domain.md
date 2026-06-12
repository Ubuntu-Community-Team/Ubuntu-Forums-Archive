---
title: "can't login a ubuntu desktop to samba domain"
date: 2011-06-12
forum: Installation &amp; Upgrades
---

### Post by kombinerka on 2011-06-12
Hallo I'm not sure if I write this in the right section of teh forum so if not im sorry for that >.<

well back to the topic :P
Hello everyone as stated in the title I cant login into my samba domain/workgroup on a ubuntu 11,04 machine
(all my users are configured by samba) 
im not good in writing a good explantation so ill point it out... ](*,)
* my servers runs on a ubunut 11,04 desktop version 
* I got 2 Windows xp clients to join the domain and they joined just fine with shares working
* I cant get my ubuntu 11.04 cleint machines to log into the domain trid several options:
       - net join DOMAINNAME  -- got a reply > "Cannot join as a standalone machine"
       - changed the smb.conf file with sudo nano /etc/samba/smb.conf   >> workgroup = domainname
       - and also tried logging in  as one of the domain users ofcourse it didnt work >.<
 Im fairly new to linux OS and dont know much about the commands or utilities in linux/ubuntu


my configuration on server looks like this:
```
# Samba config file created using SWAT
# from UNKNOWN (127.0.0.1)
# Date: 2011/06/12 13:11:48

 [global]
 workgroup = JCS.LOCAL
 server string = %h server (Samba, Ubuntu)
 map to guest = Bad User
 obey pam restrictions = Yes
 pam password change = Yes
 passwd program = /usr/bin/passwd %u
 passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
 unix password sync = Yes
 syslog = 0
 log file = /var/log/samba/log.%m
 max log size = 1000
 add machine script = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
 logon drive = H:
 domain logons = Yes
 os level = 64
 preferred master = Yes
 domain master = Yes
 dns proxy = No
 usershare allow guests = Yes
 panic action = /usr/share/samba/panic-action %d

 [homes]
 comment = Home Directories
 read only = No
 browseable = No

 [aleen-vrijwilligers]
 path = /home/vrijwilligers
 valid users = @vrijwilligers
 read only = No

 [daklozen]
 path = /home/daklozen
 valid users = @daklozen

 [vrijwilligers toegang tot daklozen]
 path = /home/daklozen
 valid users = @vrijwilligers
 read only = No

 [netlogon]
 comment = Network Logon Service
 path = /home/samba/netlogon
 guest ok = Yes
 share modes = No

 [profiles]
 comment = Users profiles
 path = /home/samba/profiles
 create mask = 0600
 directory mask = 0700
 browseable = No

 [printers]
 comment = All Printers
 path = /var/spool/samba
 create mask = 0700
 printable = Yes
 browseable = No

 [print$]
 comment = Printer Drivers
 path = /var/lib/samba/printers 

```

any help would be appreciated :)
thanks and greetings,
kombinerka

---

### Post by kombinerka on 2011-06-12
allright I got a little bit further (I think)by following these steps:
thrashbox:~ # net rpc join -S DOMAIN -U Administrator cannot join as standalone machine 

IF get this error - then check these : 


thrashbox:~ # net rpc getsid Storing SID S-- for Domain DOMAIN in secrets.tdb 

Relevant bits from /etc/nsswitch.conf: 

passwd: files winbind shadow: files group: files winbind 

On smb.conf security = domain 

thrashbox:~ # net rpc getsid Storing SID S-- for Domain DOMAIN in secrets.tdb 

thrashbox:/var/log/samba # smbpasswd -w w1shin2 Setting stored password for "cn=Manager,dc=domainname,dc=com" in secrets.tdb 


 thrashbox:/var/log/samba # net rpc join -U Administrator Password: Joined domain DOMAINNAME.


however I still cant login on my client machine with a user made on the server with smbpasswd -a user

---

