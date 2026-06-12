---
title: "gufw won't cooperate and allow subnet access to port 22"
date: 2017-11-10
forum: MINT
---

### Post by TechnoJunky on 2017-11-10
I'm setting up a web server on a VM, running Mint 18.2, patches updated.  I had the firewall setup to allow all for ports 80, 22 and 115.  I was able to SSH to it, SFTP, and I was able to see my webpage from the net.  For security, I only forwarded port 80 traffic to the server from the router.  I decided that I should lock it down a bit tighter though and restrict 22 and 115 to only allow from my subnet.  However, I just can't seem to get gufw to cooperate.  I have the rule in place "sudo ufw allow 192.168.1.0/24 port 22".  But now I'm locked out of SSH from my remote computer.  This isn't a big deal, the other computer is in the next room.  But why won't this allow me to access the webserver using SSH?

---

