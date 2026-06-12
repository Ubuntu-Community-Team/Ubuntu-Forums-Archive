---
title: "how can i downgrade my kernel?"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by tp21 on 2007-07-07
hi,
i am working with Thinkpad T40, Ubuntu 7.04 frish installed, kernel 2.6.20. 
i am having wireless troubles with my cisco aironet chip, and i read ([http://thinkwiki.org/wiki/Cisco_Aironet_Wireless_802.11b](http://thinkwiki.org/wiki/Cisco_Aironet_Wireless_802.11b)) that this chip works best with kernel 2.6.11. so my quistion is it possible to install an older kernel, and then choose it from grub and boot with it to test the wireless chip?
thanx

---

### Post by bmorency on 2007-07-07
> **tp21 said:**
> hi,
i am working with Thinkpad T40, Ubuntu 7.04 frish installed, kernel 2.6.20. 
i am having wireless troubles with my cisco aironet chip, and i read ([http://thinkwiki.org/wiki/Cisco_Aironet_Wireless_802.11b](http://thinkwiki.org/wiki/Cisco_Aironet_Wireless_802.11b)) that this chip works best with kernel 2.6.11. so my quistion is it possible to install an older kernel, and then choose it from grub and boot with it to test the wireless chip?
thanx

since it is not in the repos you will have to compile it yourself from source. you can get it  [here]("http://www.kernel.org/pub/linux/kernel/v2.6/") from the official kernel website. but i'm not sure if it might cause other hardware to stop working.

---

### Post by tp21 on 2007-07-08
thanks. 
you are probably right, maybe it is dangerous for other hardware component to use elder kernel. anyway i did my test using dapper live cd, with kernel 2.6.15. i found out that my chip did not work neighter. so i guess it is hardware issue.

---

