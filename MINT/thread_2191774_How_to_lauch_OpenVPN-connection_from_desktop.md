---
title: "How to lauch OpenVPN-connection from desktop"
date: 2013-12-04
forum: MINT
---

### Post by suncatcher_13 on 2013-12-04
Could you tell me how to launch OpenVPN connection via launcher (shortcut)?


I've installed OpenVPN, set up connection (crt, conf-files). All is correct and working.
Created bash-script **/bin/conn.sh** which launch connection:
```
cd /etc/openvpn
openvpn client.conf
```

I have **auth-user-pass** mode of authentification, therefore in order to exclude credentials input I've created **login.conf** and wrote out it in **client.conf**
```
auth-user-pass login.conf
```


All is working good. It's when I execute it in console under root

> **xxx-host#** /bin/conn.sh


How can I execute this script by clicking on shortcut?


Ive tried to create different types of launcher (application and application in terminal) but no luck.
specially I want it to be executed with showing output in console. I want to be informed about errors.


I run LMDE 15 x32 with MATE 1.6.0 as a guest under VirtualBox 4.3.4

---

### Post by jimmyh1972 on 2013-12-05
create a bash script with running permissions on your desktop begin with
#!/bin/bash
write_your_commands_here

config your Dconf manager to run scripts (if your distro is 12.10 and above)

---

### Post by suncatcher_13 on 2013-12-06
> **jimmyh1972 said:**
> create a bash script with running permissions on your desktop begin with
#!/bin/bash
write_your_commands_here

config your Dconf manager to run scripts (if your distro is 12.10 and above)

But I'm running Linux Mint Debian Edition under MATE 1.6.0 DE. What should be my steps in that case?

---

