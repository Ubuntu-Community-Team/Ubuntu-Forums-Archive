---
title: "Samba connecting to Windows 7 (failed)"
date: 2015-02-14
forum: Installation &amp; Upgrades
---

### Post by CrAzY12 on 2015-02-14
I have scoured google and there is alot of information on samba configuration and it helped greatly but the problem I am having I can not seem to find a solution through google. 

 I am setting up my first samba share(on ubuntu server 14.X)  and I am trying to connect it to my windows 7. I have successfully added the server to my windows 7 "as a network computer" and now I am trying to log into the server from my win-7 to start sharing a folder, but when the I try to connect to the samba server it request me to enter my password. My password is "password" for both and I try to login in with my hostname from my win-7 & server side, (failed) 

So I thought the problem was in my samba.conf file under Networking section.
I have:
[I]#interfaces = 127.0.0.0/8,eth0,eth1 
#bind interfaces only =yes

; I also tried with #bind interfaces only commented out and added:
host allow = 127.0.0.1, 192.168.1.0/24, 10.10.20.0/24
host deny = 0.0.0.0/0 
[/I]
[FONT=times new roman]I have a hunch that one of these is causing me problems.  But I could be wrong. Any help would be greatly appreciated [/FONT]

---

### Post by SeijiSensei on 2015-02-14
Did you create a Samba user and password with the smbpasswd utility?
```
sudo smbpasswd -a username
```

---

### Post by CrAzY12 on 2015-02-15
This was done before hand but replied it just in case. When I am logging into a samba share from windows, I am getting a "Access denied" once I have implemented the following net use command in windows.(I am running as administrator)
[I]C:\> net use s: \\UBUNUTU\test /user:splunk password

[/I][FONT=times new roman]I think I have changed my smb.conf file wrong to disallow my "10.10.20.12" windows 7 to connect to the server. Here is what I have for the Networking section of the smb.conf : See Attachment[/FONT]

[FONT=times new roman]I also have uncommented the "host allow" and "host deny" and when I ran the command [/FONT]*testpharm *[FONT=times new roman]&#8203;it failed to recognize and said "unknown parameter encountered" [/FONT]

---

