---
title: "Slow booting after version upgrade."
date: 2018-10-21
forum: Installation &amp; Upgrades
---

### Post by rocco.martinello on 2018-10-21
Hi to all!
 After upgrading to Ubuntu 18.10 from 18.04.1 LTS booting is too long.
 How can I diagnose and fix this problem?
 Thank you in advance for your help!!!

---

### Post by oldfred on 2018-10-22
Were you mounting any partitions in fstab that now have different UUID or are missing. It has to timeout if so.
Have you housecleaned system, both before upgrade & after?

What does this show:
       systemd-analyze 

Only need to see top 10 or so, q to stop ( I now have 7 sec on printer config):
      systemd-analyze blame 
        
If not using snaps, I removed them:
       boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)

---

### Post by rocco.martinello on 2018-10-24
[LEFT]
Hi oldfred and thank you very much for your answer!!!
I deleted the default swap file and set a swap partition created by me. Strangely this partition seems to have no UUID so I set PARTUUID in fstab to make the partition work. This modification works and neither UUID nor PARTUUID were modified.
What do you mean with &#8220;housecleaned&#8221; and how can I do this?

Systemd-analyze shows: ```
 Startup finished in 74us (firmware) + 62us (loader) + 34.474s(kernel) + 57.465s (userspace) = 1min 31.939sgraphical.target reached after 57.386s in userspace 
```
systemd-analyze blame shows:
```
 26.333s plymouth-quit-wait.service         12.671s dev-sda6.device          9.369s udisks2.service          9.098s ModemManager.service          8.656s networkd-dispatcher.service          8.202s dev-loop13.device          7.776s accounts-daemon.service          7.618s dev-loop18.device          7.574s dev-loop21.device          7.574s dev-loop17.device          7.538s dev-loop16.device          7.457s dev-loop14.device          7.457s dev-loop20.device 
```
Thank you in advance for your answer![/LEFT]

---

### Post by oldfred on 2018-10-25
Are you using snaps?
       [https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb)
boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341) 
    
       [https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean)
Do yourself a favor and avoid bleachbit. 
   Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)
[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels) 
   RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

 Caution deborphan will delete anything you manually installed. See comment:

---

