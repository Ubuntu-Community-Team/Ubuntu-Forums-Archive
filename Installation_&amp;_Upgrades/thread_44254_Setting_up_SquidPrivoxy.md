---
title: "Setting up Squid/Privoxy"
date: 2005-06-25
forum: Installation &amp; Upgrades
---

### Post by SWo2005 on 2005-06-25
Hi

[New to all this linux stuff - hey it's great!!]

I had squid/privoxy running on windows fine, but I want to put it onto my ubuntu box. I've installed both - (repositories - brilliant!) but I'm struggling getting it going.

1) I can't look at my squid log. I think it's in /var/log/squid but when I 'cd' to it I get permission denied - 'sudo cd' doesn't work. 

2) I am getting a message from squid from my browser but I'm not getting out onto the web so I think my config file's not right. There's a line in it which I'd be grateful if some would correct

I've got several machines running at home with router assigned ip 192.168.0.1-192.168.0.100
acl home_network src 192.168.0.1-192.168.0.100

I'm not sure what the mask should be 255.255.255.0 or what?

3) I'm a bit unsure about the best way to test whether each bit is functioning. Any suggestions

Thanks

Simon

---

### Post by OwlManAtt on 2005-06-25
[QUOTE=SWo2005]1) I can't look at my squid log. I think it's in /var/log/squid but when I 'cd' to it I get permission denied - 'sudo cd' doesn't work.[/QUOTE]You can't view the contents of a file with cd, you need something to open it and handle it. sudo cat /var/log/squid would show you the contents of the file, if that's the name of the log. 

(You can find the proper name of the log by doing cd /var/log and listing the contents of the directory with ls.)
[QUOTE=SWo2005]2) I am getting a message from squid from my browser but I'm not getting out onto the web so I think my config file's not right. There's a line in it which I'd be grateful if some would correct[/QUOTE]If you open the file up and go through it yourself, you'll be able to get it running. If memory serves, the file is extremely well commented, so each line should be explained in there.

[QUOTE=SWo2005]I've got several machines running at home with router assigned ip 192.168.0.1-192.168.0.100
acl home_network src 192.168.0.1-192.168.0.100

I'm not sure what the mask should be 255.255.255.0 or what?[/QUOTE]The netmask would be 255.255.0.0, wouldn't it be? According to my router's switch range page, it is. Don't quote me there though.

---

