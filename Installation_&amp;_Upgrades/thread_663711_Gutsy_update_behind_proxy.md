---
title: "Gutsy update behind proxy"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by tonjaggart on 2008-01-10
I am a noob andI recently upgraded to Gutsy 7.10 and I am behind a firewall at my office. I installed ntlmaps and I can get to websites just fine. When I run sudo apt-get update I get a  407 Proxy Authorization Required. Any help with this issue is greatly appreciated.

---

### Post by Partyboi2 on 2008-01-11
Maybe you need to configure apt-get to work with a proxy? System>Admin>Synaptic Package Manager
Click on "settings" then "preferences" click on "Network" tab then add the required info.

---

### Post by tonjaggart on 2008-01-11
I did that and still getting the same errors. Currently I am configuring the apt.conf file and setting the Network Proxy in System> Preference> Network Proxy to direct internet connection.

---

