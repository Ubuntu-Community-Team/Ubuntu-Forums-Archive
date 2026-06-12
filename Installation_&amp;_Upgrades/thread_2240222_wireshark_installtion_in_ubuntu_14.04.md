---
title: "wireshark installtion in ubuntu 14.04"
date: 2014-08-18
forum: Installation &amp; Upgrades
---

### Post by -@23%^yu* on 2014-08-18
I have followed the following steps to install and run wireshark in my desktop
```
sudo apt-get install wireshark
sudo groupadd wireshark
sudo usermod -a -G wireshark YOUR_USER_NAME
sudo chgrp wireshark /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin=eip /usr/bin/dumpcap
sudo getcap /usr/bin/dumpcap


```
found that this does not work. how to make wireshark detect my interfaces? And is there any possible vulnarability created by following the above steps. If so how to remove them?(I'm concerned by the command ```
sudo chmod 750 /usr/bin/dumpcap
```)

---

### Post by Harley_Bailey on 2015-01-28
I ran the following commands
sudo apt-get install wireshark
sudo groupadd wireshark
sudo usermod -a -G wireshark YOUR_USER_NAME
sudo chgrp wireshark /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin=eip /usr/bin/dumpcap
sudo getcap /usr/bin/dumpcap

when I started wireshark, it gave me a dumpcap error, so I ran 
sudo chmod 777 /usr/bin/dumpcap and now wireshark works. 
Please be advised setting the 777 file permission isn't strongly advised due to security reasons.
And yes I'm still pretty new to the linux CLI.

I hope someone finds this useful. :)

---

