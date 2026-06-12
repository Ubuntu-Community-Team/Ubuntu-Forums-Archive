---
title: "Error message installing Cisco VPN Client"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by bstreet85 on 2007-01-21
I'm trying to install the Cisco VPN Client v 4.8 and when I try to run the install script on the command line (as root) it gives me the following error:
bash: ./vpn_install : Permission denied

Any suggestions?
Thanks in advance,
bstreet85

---

### Post by meng on 2007-01-21
You could try
sudo ./vpn_install

but frankly, I think you're better off forgetting about Cisco VPN client and installing vpnc from the repositories instead. It's compatible with Cisco concentrators.

---

### Post by bstreet85 on 2007-01-21
Tried it, but that doesn't work either. I would be interested in using another VPN client, but the problem is that this is what my workplace specified, so I'm kind of stuck with it.

---

### Post by meng on 2007-01-21
Sorry it didn't work for you. My workplace also supplies the Cisco VPN client, but I use vpnc instead. Guess I'm lucky.

---

### Post by zivagolee on 2007-01-24
chmod +x vpn_install
then, ./vpn_install

---

