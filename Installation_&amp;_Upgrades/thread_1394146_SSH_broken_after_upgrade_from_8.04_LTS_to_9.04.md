---
title: "SSH broken after upgrade from 8.04 LTS to 9.04"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by theluse on 2010-01-30
On my Ubuntu Hardy 8.04 LTS web server I ran the command: do-release-upgrade

Everything worked fine except after reboot I wasn't able to log into my machine via ssh.

I built SSH from source could this be my problem and what can I do? 

I don't have physical access to the machine. The only way I can access it is via another partition that acts like a Debian Live CD. From there I can mount the Ubuntu file system and modify things.

I tried this and made sure iptables wasn't blocking port 22 and the port I normally use to login via SSH (42000).  Also, I made sure the file /etc/init.d/ssh was correct. 

Then I rebooted the machine.

Still can't login via ssh.

I get the error:

ssh: connect to host 12.345.67.890 port 42000: Connection refused

If i try  ssh user@12.345.67.890 I get the same error.

---

