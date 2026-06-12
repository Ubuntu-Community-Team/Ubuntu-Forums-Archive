---
title: "Gnome BitTorrent -- what is the secret to sharing?"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by Tomy on 2005-10-13
Hi,
I searched the forums a little but tonight I have little ambition to pursue the answer.

Right now I am downloading the Breezy torrent from Hoary using Gnome BitTorrent and the download is perking along at about half my paid-for bandwidth.

But the tab for** Upload** reports a status of 0.00 KB/s.  How do I fix this so I can share the torrent?

The DSL connection here runs to a Linksys EtherFast Cable/DSL Router (BEFSR41 ?) that supports port forwarding and UPnP forwarding. I assume I need to configure it ?? or what ??

Thanks
Tomy

---

### Post by Storm Rider on 2005-10-14
No expert here  but the Upnp ports you need open are 6881 - 6999

---

### Post by bored2k on 2005-10-14
If you have UPnP support, I'd recommend you use BitTornado or Azureus. Gnome-BT is not really good at all.

[http://www.ubuntuforums.org/showthread.php?t=75272&highlight=azureus](http://www.ubuntuforums.org/showthread.php?t=75272&highlight=azureus)

BitTornado is just a ```
sudo apt-get install bittornado-gui
``` away.

---

### Post by Tomy on 2005-10-14
[quote=Storm Rider]No expert here  but the Upnp ports you need open are 6881 - 6999[/quote] 
Thanks, I added those ports to my "port forwarding" table on the router. At first nothing changed but after my Breezy download completed the "Upload" stats started showing some action. So at this point I don't know if I needed to make the change. Maybe I just needed to wait until the download was completed.

Seems to me that on a different system the torrent download and upload worked at the same time.

I am out of here :) I have my cd burned and it's time to install Breezy.

Tomy

---

### Post by Tomy on 2005-10-14
[quote=bored2k]If you have UPnP support, I'd recommend you use BitTornado or Azureus. Gnome-BT is not really good at all.

[http://www.ubuntuforums.org/showthread.php?t=75272&highlight=azureus]("http://www.ubuntuforums.org/showthread.php?t=75272&highlight=azureus")

BitTornado is just a ```
sudo apt-get install bittornado-gui
``` away.[/quote]  
Thanks, I'll try that. I installed Gnome BitTorrent on Hoary because I saw that it was the standard app on Breezy. It is defintely "straight forward and simple" :-| and perhaps "not really good at all" :). I am willing to try something else - I was expecting it to be much faster.

Later
tomy

---

