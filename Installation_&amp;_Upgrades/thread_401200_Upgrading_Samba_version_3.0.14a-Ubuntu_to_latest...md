---
title: "Upgrading Samba version 3.0.14a-Ubuntu to latest..."
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by iamjakex on 2007-04-04
Hi everyone,
I've got a production ubuntu server (breezy) thats been running last couple months problem free, but 2 macs in the office are causing trouble.  Seems since their last upgrade they are unable to access shares on the server, which is not good.

I'm by no account a linux guru, nor do I pretend to be one.  I've always loved Debian & Ubuntu for the apt-get app.  And I've had little to no issues finalizing setups for software after.

Anyways to the problem, the office macs keep getting:
```

[2007/03/26 17:18:17, 0] lib/util_sock.c:read_socket_data(384)
  read_socket_data: recv failure for 4. Error = No route to host
[2007/04/03 11:25:08, 0] rpc_parse/parse_prs.c:prs_mem_get(537)
  prs_mem_get: reading data of size 2 would overrun buffer.
[2007/04/03 11:25:08, 0] rpc_server/srv_pipe.c:api_pipe_bind_req(919)
  api_pipe_bind_req: unable to unmarshall RPC_HDR_RB struct.
[2007/04/03 17:19:47, 0] lib/util_sock.c:read_socket_data(384)
  read_socket_data: recv failure for 4. Error = No route to host

```

I've research this and found its due to some new update for the MacOS.  But have been unable to get the macs to work. 
Info here: [http://www.debianhelp.org/node/2891]("http://www.debianhelp.org/node/2891")

Anyways HOW do i update my samba while keeping breezy on this server?  This is a production server and I can't afford to bring it down for maintenance (unforeseen dist-upgrade problems). I just have my hand forced into updating samba due to the iMacs not working.

Please help.. I've considered 2 options,
```
apt-get remove samba
```
then
I downloaded the following:
```
 samba_3.0.24-1_i386.deb
```
from samba.org

Option 2:
Find a source for JUST samba that I can update? for some reason breezy is capped at the dreaded Samba version 3.0.14a-Ubuntu

Would it be wise to install the .deb version?  How can I do this? Its for Debian Sarge, I don't know what kind of conflicts to expect, and I can't afford to have this server out of action with all our files hosted on it in the office.  Thanks any and all help appreciated :)

---

### Post by iamjakex on 2007-04-04
Well I did some searching and I went into IRC and I was told by some very helpful people that since Breezy is reaching EOL ( [https://lists.ubuntu.com/archives/ubuntu-announce/2007-March/000099.html](https://lists.ubuntu.com/archives/ubuntu-announce/2007-March/000099.html) )
I should just attempt the dapper update which at least has support for 5+ years.

So I'm gonna do the dapper update as listed here:
[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

I hope this helps someone whos in the same boat as me #-o

---

