---
title: "Wireshark issues"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by Grafixx01 on 2010-10-01
Ok, I've installed Wireshark and even followed the directions on this forum for dumpcap. Wireshark still doesn't recognize my Atheros wireless card. 
 
I also tried the following:
 
groupadd -g packetcapture
chmod 750 /usr/bin/dumpcap
chgrp packetcapture /usr/bin/dumpcap
setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap
setcap cap_net_raw,cap_net_admin+eip /usr/bin/tshark
 
 
Nothing works. I get an error for not finding 'packetcapture' but it is installed and so is tshark.
 
Any ideas?

---

### Post by Rubi1200 on 2010-10-01
Try these commands and see it it helps:

```
sudo apt-get install libcap2-bin wireshark
sudo chgrp admin /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap
```

---

