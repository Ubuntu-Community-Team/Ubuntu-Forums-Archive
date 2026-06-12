---
title: "systemd-analyze blame  18 minute boot"
date: 2018-07-04
forum: Installation &amp; Upgrades
---

### Post by jimbean on 2018-07-04
systemd-analyze blame

9min 40.805s plymouth-quit-wait.service
    7min 51.031s snapd.seeded.service
         18.256s snapd.service
          6.254s NetworkManager-wait-online.service
          1.415s dev-sda2.device
          1.064s dev-loop15.device
          1.061s dev-loop17.device
          1.058s dev-loop16.device
          1.055s dev-loop19.device
          1.033s dev-loop1.device
          1.029s dev-loop0.device
          1.022s dev-loop18.device
          1.019s dev-loop2.device
          1.018s dev-loop3.device
          1.013s dev-loop20.device
          1.008s dev-loop4.device
          1.001s dev-loop5.device
           987ms dev-loop8.device
           986ms dev-loop10.device
           974ms dev-loop21.device
           967ms dev-loop13.device
           958ms dev-loop22.device
           940ms dev-loop23.device
lines 1-23

any ideas as to what i should do next





i found this thread/post
[https://bugs.launchpad.net/snapd/+bug/1779872](https://bugs.launchpad.net/snapd/+bug/1779872)

---

### Post by TheFu on 2018-07-04
All those slowdowns appear to be related to the new-ish snap service(s).

I'd make a backup of the system, then purge everything related to snap and reboot.  Faster?  
If something doesn't work or the system fails to boot, just restore from the backup. Should take less than 20-30 min if the backups are good.

---

### Post by jimbean on 2018-07-04
ubuntu  is great all i did was to put usb iso in reinstalled in 20 minutes (try that with the alternative operating system)
brand new system again 
i dont know what i did to break it but its working again 
upgrraded and shiny new

---

