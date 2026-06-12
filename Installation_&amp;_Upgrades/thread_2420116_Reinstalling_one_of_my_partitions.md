---
title: "Reinstalling one of my partitions"
date: 2019-05-30
forum: Installation &amp; Upgrades
---

### Post by RegUB on 2019-05-30
I currently have 16.04 and 18.04 on my laptop, dual boot. I want to completely reinstall 18.04. 

When installing I get options to install alongside the existing systems, or replace them both with the new installation, or 'Something Else'. If I select 'Something Else' it lists the existing partitions. Is it just a matter of ticking the box next to the 18.04 partition, or is it more complex than that ?

---

### Post by Dennis N on 2019-05-30
You are on the right track with 'Something Else' option. On the partitions screen you get after choosing 'Something Else', when you select the partition to use for the 18.04 install you need give some details on how to use the partition before you are able to continue: click the 'change' button, then specify to format with ext4 filesystem, and to use it as / partition. Then you should be able to click 'Install' to proceed. Fill in your user details, and the rest is automatic.

---

### Post by Rubi1200 on 2019-05-30
Just make sure you have good backups of any important data, even if reinstalling, because this will format and overwrite any data on that particular partition.

---

