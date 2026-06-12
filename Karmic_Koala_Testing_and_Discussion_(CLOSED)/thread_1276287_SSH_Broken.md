---
title: "SSH Broken?"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2009-09-26
When I try to access my machine through ssh, I get "connection refused". This used to work before my latest reinstall, and it's not a firewall issue as far as I know. In fact, I get "connection refused" even when trying to SSH to myself. 

When I restart the daemon, this is what I get:

> jeremy@jeremy-desktop:~$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server sshd
Warning: Fake start-stop-daemon called, doing nothing.

Warning: Fake start-stop-daemon called, doing nothing.


Is anyone else having this problem or know how to fix it?

---

### Post by psyke83 on 2009-09-26
> **jlacroix said:**
> When I try to access my machine through ssh, I get "connection refused". This used to work before my latest reinstall, and it's not a firewall issue as far as I know. In fact, I get "connection refused" even when trying to SSH to myself. 

When I restart the daemon, this is what I get:



Is anyone else having this problem or know how to fix it?

I'm not getting those messages, and ssh works fine here. Are you definitely updated? Try to purge all the ssh packages and re-install.

---

### Post by jlacroix on 2009-09-26
> **psyke83 said:**
> I'm not getting those messages, and ssh works fine here. Are you definitely updated? Try to purge all the ssh packages and re-install.

Thank you. I tried to purge the packages and reinstall, but I am having the same problem. :(

I do have all updates, and I just checked my laptop and it's working there...

---

### Post by inportb on 2009-09-26
what about...

sudo restart ssh

?

---

### Post by jlacroix on 2009-09-26
> **inportb said:**
> what about...

sudo restart ssh

?

```
jeremy@jeremy-desktop:~$ sudo restart ssh
restart: Unknown job: ssh

```

I tried restarting my computer too.

---

### Post by psyke83 on 2009-09-26
> **jlacroix said:**
> ```
jeremy@jeremy-desktop:~$ sudo restart ssh
restart: Unknown job: ssh

```

I tried restarting my computer too.

Here's mine:

```
conn@inspiron:~/Download$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server sshd                           [ OK ] 
```

```
conn@inspiron:~/Download$ dpkg -l | grep ssh
ii  openssh-client                        1:5.1p1-6ubuntu1                                               secure shell client, an rlogin/rsh/rcp repla
ii  openssh-server                        1:5.1p1-6ubuntu1                                               secure shell server, an rshd replacement
ii  python-paramiko                       1.7.4-0.1                                                      Make ssh v2 connections with python
ii  ssh                                   1:5.1p1-6ubuntu1                                               secure shell client and server (metapackage)
ii  ssh-askpass-gnome                     1:5.1p1-6ubuntu1                                               interactive X program to prompt users for a 

```

---

### Post by kklimonda on 2009-09-26
You have somehow broken your installation of dpkg, your /sbin/start-stop-daemon is probably just a shell script that prints this message.
To fix it run ```
sudo apt-get install --reinstall dpkg
``` but it may not be the only problem you will run into.

---

### Post by jlacroix on 2009-09-26
> **kklimonda said:**
> You have somehow broken your installation of dpkg, your /sbin/start-stop-daemon is probably just a shell script that prints this message.
To fix it run ```
sudo apt-get install --reinstall dpkg
``` but it may not be the only problem you will run into.

That got rid of the error messages when restarting the SSH service, but my laptop still gets "connection refused" when trying to connect to my desktop. This is strange because it worked until I reinstalled yesterday...

---

### Post by Stereotypical Rage on 2009-09-26
> **jlacroix said:**
> That got rid of the error messages when restarting the SSH service, but my laptop still gets "connection refused" when trying to connect to my desktop. This is strange because it worked until I reinstalled yesterday...

Firewall? AppArmor?

---

### Post by jlacroix on 2009-09-26
> **Stereotypical Rage said:**
> Firewall? AppArmor?

No firewall. I'm not sure about AppArmor, both my laptop and desktop run Karmic so both should work although only my laptop works...

---

### Post by Stereotypical Rage on 2009-09-26
> **jlacroix said:**
> No firewall. I'm not sure about AppArmor, both my laptop and desktop run Karmic so both should work although only my laptop works...
nmap yourself. :-P

---

### Post by jlacroix on 2009-09-26
> **Stereotypical Rage said:**
> nmap yourself. :-P

```
Starting Nmap 5.00 ( http://nmap.org ) at 2009-09-26 23:43 EDT
Interesting ports on 172.16.254.107:
Not shown: 997 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 0.12 seconds

```

---

### Post by cariboo on 2009-09-26
Could you post the output of:

```
ssh -v <user@server>
```

Substitute your user and server names for the above example.

---

### Post by jlacroix on 2009-09-27
> **cariboo907 said:**
> Could you post the output of:

```
ssh -v <user@server>
```

Substitute your user and server names for the above example.

This is from my laptop:

```
jeremy@jeremy-laptop:~$ ssh -v jeremy@jeremy-laptop
OpenSSH_5.1p1 Debian-6ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config   
debug1: Applying options for *                           
debug1: Connecting to jeremy-laptop [127.0.1.1] port 22. 
debug1: Connection established.                          
debug1: identity file /home/jeremy/.ssh/identity type -1 
debug1: identity file /home/jeremy/.ssh/id_rsa type -1   
debug1: identity file /home/jeremy/.ssh/id_dsa type -1   
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu1                                                                      
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu1 pat OpenSSH*                       
debug1: Enabling compatibility mode for protocol 2.0                            
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu1              
debug1: SSH2_MSG_KEXINIT sent                                                   
debug1: SSH2_MSG_KEXINIT received                                               
debug1: kex: server->client aes128-cbc hmac-md5 none                            
debug1: kex: client->server aes128-cbc hmac-md5 none                            
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent                        
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP                                     
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent                                           
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY                                     
The authenticity of host 'jeremy-laptop (127.0.1.1)' can't be established.      
RSA key fingerprint is 2f:ce:b2:37:ca:16:0c:64:a9:55:52:10:dc:9b:f4:64.         
Are you sure you want to continue connecting (yes/no)? yes                      
Warning: Permanently added 'jeremy-laptop' (RSA) to the list of known hosts.    
debug1: ssh_rsa_verify: signature correct                                       
debug1: SSH2_MSG_NEWKEYS sent                                                   
debug1: expecting SSH2_MSG_NEWKEYS                                              
debug1: SSH2_MSG_NEWKEYS received                                               
debug1: SSH2_MSG_SERVICE_REQUEST sent                                           
debug1: SSH2_MSG_SERVICE_ACCEPT received                                        
debug1: Authentications that can continue: publickey,password                   
debug1: Next authentication method: publickey                                   
debug1: Trying private key: /home/jeremy/.ssh/identity                          
debug1: Trying private key: /home/jeremy/.ssh/id_rsa                            
debug1: Trying private key: /home/jeremy/.ssh/id_dsa                            
debug1: Next authentication method: password                                    
jeremy@jeremy-laptop's password:                                                
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
jeremy@jeremy-laptop's password:
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Linux jeremy-laptop 2.6.31-11-generic #36-Ubuntu SMP Fri Sep 25 06:37:23 UTC 2009 x86_64

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

Last login: Sat Sep 26 21:34:46 2009

```

---

### Post by jlacroix on 2009-09-27
From my desktop:

```
                                                       
jeremy@jeremy-desktop:~$ ssh -v jeremy@jeremy-desktop
OpenSSH_5.1p1 Debian-6ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config   
debug1: Applying options for *                           
debug1: Connecting to jeremy-desktop [127.0.1.1] port 22.
debug1: Connection established.                          
debug1: identity file /home/jeremy/.ssh/identity type -1 
debug1: identity file /home/jeremy/.ssh/id_rsa type -1   
debug1: identity file /home/jeremy/.ssh/id_dsa type -1   
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu1                                        
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu1 pat OpenSSH*        
debug1: Enabling compatibility mode for protocol 2.0             
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu1                                                                
debug1: SSH2_MSG_KEXINIT sent                                    
debug1: SSH2_MSG_KEXINIT received                                
debug1: kex: server->client aes128-cbc hmac-md5 none             
debug1: kex: client->server aes128-cbc hmac-md5 none             
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent         
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP                      
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent                            
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY                      
The authenticity of host 'jeremy-desktop (127.0.1.1)' can't be established.                                                       
RSA key fingerprint is f4:df:67:5a:08:6b:e8:a6:c7:e6:22:f1:87:6f:83:26.                                                           
Are you sure you want to continue connecting (yes/no)? yes       
Warning: Permanently added 'jeremy-desktop' (RSA) to the list of known hosts.                                                     
debug1: ssh_rsa_verify: signature correct                        
debug1: SSH2_MSG_NEWKEYS sent                                    
debug1: expecting SSH2_MSG_NEWKEYS                               
debug1: SSH2_MSG_NEWKEYS received                                
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/jeremy/.ssh/identity
debug1: Trying private key: /home/jeremy/.ssh/id_rsa
debug1: Trying private key: /home/jeremy/.ssh/id_dsa
debug1: Next authentication method: password
jeremy@jeremy-desktop's password:
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Linux jeremy-desktop 2.6.31-11-generic #36-Ubuntu SMP Fri Sep 25 06:37:23 UTC 2009 x86_64

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

Last login: Sat Sep 26 21:31:58 2009
jeremy@jeremy-desktop:~$

```

---

### Post by jlacroix on 2009-09-27
It started working just now. Weird. Thanks all!

---

