---
title: "*help* can't turn off hotspot on Linux mint so I can't connect to wifi!"
date: 2015-09-18
forum: MINT
---

### Post by denny5 on 2015-09-18
I turned on the hotspot by accident and it looks like I turn it off and it exits me out of network manager and when I go back in its on again. Please help I am new with this. All I know is this is Linux Mint and don't know the version but I don't have the Sudo password or whatever so I can't do hardly anything with the terminal. I don't have it cuz it's my dads laptop and he passed away now I have it but I don't know the password! Can anyone help? I tried looking for the network directories in .gconf but couldn't find it following the directions. I need help. Any suggestions?

---

### Post by QIII on 2015-09-18
*Moved to **Mint***

---

### Post by coffeecat on 2015-09-18
I can't help you with the hotspot, but you really need a password for the admin account - not just for the terminal. This link tells you how to reset a password in Ubuntu, but it should work in Mint if you can get into recovery mode in the same way:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by denny5 on 2015-09-18
Ok thanks sir and I'm Sorry wrong section

---

### Post by denny5 on 2015-09-19
Ok guys I changed my password but I can't get hotspot or airplane mode switched off please help? Suggestions? I've tried sudo rfkill unblock all and block all also. It didn't affect anything. I can't get wifi on my computer anymore.

---

### Post by denny5 on 2015-09-20
Bump? Need help. Thanks

---

### Post by jeremy31 on 2015-09-21
```
ls /etc/NetworkManager/sytem-connections
```
Post the result

---

