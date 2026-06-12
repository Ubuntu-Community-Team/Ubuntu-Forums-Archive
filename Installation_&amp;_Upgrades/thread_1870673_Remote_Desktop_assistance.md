---
title: "Remote Desktop assistance"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by thoman999 on 2011-10-27
Hello All,
 
I've been tasked with setting up a Ubuntu 10.04 server and am having many challenges with the remote access portion. If anyone has some guidance, I'd greatly appreciate it.
 
I need to have remote access without have someone already logged in.
 
The basic Vino Remote Desktop works fine as long as a user is logged into the server. 
 
I've downloaded the vnc4server and followed the various guides found at:
 
[1] [http://theseekersquill.wordpress.com/2010/03/16/vnc-server-ubuntu-windows/](http://theseekersquill.wordpress.com/2010/03/16/vnc-server-ubuntu-windows/) 
[2] [http://zatansuibi.blogspot.com/2011/06/vnc-set-up-in-ubuntu.html](http://zatansuibi.blogspot.com/2011/06/vnc-set-up-in-ubuntu.html)
 
As well as all 5 references of item [2]
 
It appears that Vino is overshadowing vnc4server for control and I have no idea how to work around this.
 
Help please!
 
Regards,
 
Tom

---

### Post by collisionystm on 2011-10-27
> **thoman999 said:**
> Hello All,
 
I've been tasked with setting up a Ubuntu 10.04 server and am having many challenges with the remote access portion. If anyone has some guidance, I'd greatly appreciate it.
 
I need to have remote access without have someone already logged in.
 
The basic Vino Remote Desktop works fine as long as a user is logged into the server. 
 
I've downloaded the vnc4server and followed the various guides found at:
 
[1] [http://theseekersquill.wordpress.com/2010/03/16/vnc-server-ubuntu-windows/](http://theseekersquill.wordpress.com/2010/03/16/vnc-server-ubuntu-windows/) 
[2] [http://zatansuibi.blogspot.com/2011/06/vnc-set-up-in-ubuntu.html](http://zatansuibi.blogspot.com/2011/06/vnc-set-up-in-ubuntu.html)
 
As well as all 5 references of item [2]
 
It appears that Vino is overshadowing vnc4server for control and I have no idea how to work around this.
 
Help please!
 
Regards,
 
Tom

I believe there is an option in the remote desktop settings to run before logon. Atleast in CentOS there is.

What are you using your server for? Check out Zentyal. It has a web interface and is Pretty much Ubuntu 10.04 with a million better features.

---

### Post by thoman999 on 2011-11-01
Sorry, no option to run at startup prior to logon.
 
Server will be used as a sftp gateway betwen 2 servers. It will pull from one and push to another on a schedule.
 
Tom

---

