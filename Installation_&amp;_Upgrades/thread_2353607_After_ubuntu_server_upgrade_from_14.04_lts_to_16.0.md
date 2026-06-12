---
title: "After ubuntu server upgrade from 14.04 lts to 16.04lts I encounter samba errors"
date: 2017-02-23
forum: Installation &amp; Upgrades
---

### Post by wild.lucifero on 2017-02-23
Hello to everybody,
       I just upgrade the ubuntu server to 16.04lts (apt-get update apt-get upgrade do-release-upgrade). I made many times this operation into other servers without any problems, but this time I found one BIG problem. Googling doesn't helps me to find a solution. The problem is: SAMBA doesn't work (because it doesn't start...) I tried to uninstall it with "*--purge autoremove*" and install it again but I see some errors:
[COLOR=#ff0000][B]Initctl: unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
insserv: waring: script 'screen-cleanup' missing LSB tags and overrides[/B][/COLOR]
etc
I see the same errors when I uninstall SAMBA, also when I try to show the status of the service.
systemctl shows errors on smbd.service nmbd.service and winbind.service
For example "*systemctl status smbd.service*" shows: (I'm manually typing it....)
[B][COLOR=#ff0000]smbd.service - LSB: start Samba SMB/CIFS daemon (smbd)
Loaded: loaded (/etc/init.d/smbd; bad; vendor preset: enabled)
Active: failed (Result: exit-code) since ...
Process: xxxx ExecStart=/etc/init.d/smbd start (code=exited, status=1/FAILURE)
Starting LSB: start Samba SMB/CIFS daemon (smbd)....
* Starting SMB/CIFS daemon smbd
....fail
smbd.service: Control process exited, code=exited, status=1
Failed to Start LSB: start Samba SMB/CIFS daemon (smbd)[/COLOR][/B]
journalctl -xe shows also:
[COLOR=#ff0000][B]smbd.service: Unit entered failed state
smbd.service: Failed with result 'exit-code'
[/B][/COLOR]
Are there somebody that can helps me please to find a solution? 
Thanks, really many thanks in advance.
Ciao!

---

### Post by TheFu on 2017-02-23
Some others are seeing this issue.  I googled  *16.04 samba won't start*.
Found: [https://askubuntu.com/questions/762705/samba-does-not-launch-after-upgrading-to-16-04](https://askubuntu.com/questions/762705/samba-does-not-launch-after-upgrading-to-16-04)
That said removing the **security = share** fixed it.  Just restart the smbd and nmbd services.

---

### Post by wild.lucifero on 2017-02-24
> **TheFu said:**
> Some others are seeing this issue.  I googled  *16.04 samba won't start*.
Found: [https://askubuntu.com/questions/762705/samba-does-not-launch-after-upgrading-to-16-04](https://askubuntu.com/questions/762705/samba-does-not-launch-after-upgrading-to-16-04)
That said removing the **security = share** fixed it.  Just restart the smbd and nmbd services.
Really many thanks for your reply.
I already read that post and it is not my case.
For your reference, I got the standard smb.conf from /usr/share/samba directory to be sure there are not any mistakes.
And now I just checked the statement "security = share" isn't present too
 I repeat that now I have the problems to install SAMBA.
When I install SAMBA (apt-get install samba) I read some errors after the rows:
Configuration of python-dnspython (1.12.0-1)...
Configuration of samba (2:4.3.11+dfsg-0ubuntu0.16.04.3)...
[COLOR=#ff0000][B]initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
[/B][/COLOR]etc...
I read something about the difference way to start the services in 16.04 but I don't understand how to fix my problem because remove (apt-get --purge autoremove samba) & install (apt-get install samba) don't solve it

Thanks
Ciao!

---

### Post by wild.lucifero on 2017-02-24
> **wild.lucifero said:**
> 
...
When I install SAMBA (apt-get install samba) I read some errors after the rows:
Configuration of python-dnspython (1.12.0-1)...
Configuration of samba (2:4.3.11+dfsg-0ubuntu0.16.04.3)...
[COLOR=#ff0000][B]initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
[/B][/COLOR]etc...
I read something about the difference way to start the services in 16.04 but I don't understand how to fix my problem because remove (apt-get --purge autoremove samba) & install (apt-get install samba) don't solve it

There is some confusion because the new version... 
upstart is no longer available...
The samba.service is no longer available (it is inked with /dev/null)...
Now I must check SAMBA by smbd

The real problem, also in my case, was the wrong smb.conf (that I fixed using the standard version but the samba install errors misled me)
I would like to solve the upstart errors removing it, but I wouldn't make any problems to other parts of ubuntu (now samba works and it is better to don't touch anything).

Thanks to all.
Ciao!

---

