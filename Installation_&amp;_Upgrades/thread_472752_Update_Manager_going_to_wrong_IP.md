---
title: "Update Manager going to wrong IP"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by dsieg on 2007-06-13
Hello, My first post. I have been using Ubuntu Fiesty on several computers for several months and 
like it a lot. So, I am new to Ubuntu but not to *NIX.
  I have run into an issue with the Update Manager. I had installed Ubuntu 7.04 on a machine in the lab,
and it worked fine. Update Manager and all. I then re-configured the network settings so that it was
sitting behind a firewall/router (CentOS5) machine on a private IP address (192.168.0.2). I have since
recofigured the Ubuntu machine back to the original network settings on the public net (172.25.xxx.xxx)
and everything works fine, even Mozilla. However, when I use the Update Manager and select any
update to download, I get error messages about the link with 192.168.0.1 timming out. This was the
previous configuration's gateway address. As I said, I have changed all the network settings including
gateway address via the Administration -> Network and Preferences -> Network Proxy. I cannot
find anything in the Update Manager preferences that references this address or how it determines
which address to use. 
  Any suggestions would be appreciated
dsieg

---

### Post by dannyboy79 on 2007-06-13
have you ensured that the /etc/network/interfaces file doesn't have a reference to the old gateway within that. It shouldn't if you used the gui and the settings were saved but I noticed that sometimes, rarely, stuff get's left behind. also, this may have to do with resolve.conf package?

---

### Post by dsieg on 2007-06-13
Thanks Dan, all that looked OK. Actually, I kind of stumbled acrossed it by trying to find the "beam"
package using the "Synaptic Package Manager". While in that dialog, I noticed a "Preferences" button,
which took me to a window that had a "Network" tab. Viola! It still had the "Proxy" settings to the
192 private address. I must have set them to this at some point, but can't remember when. Anyway,
I set it back to "Direct Connect", and it now works.

---

### Post by dannyboy79 on 2007-06-13
great.

---

