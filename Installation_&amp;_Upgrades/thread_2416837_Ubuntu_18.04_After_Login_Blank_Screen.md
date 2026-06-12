---
title: "Ubuntu 18.04 After Login Blank Screen"
date: 2019-04-16
forum: Installation &amp; Upgrades
---

### Post by crazyarjun on 2019-04-16
Hi Folks,

I have installed Ubuntu 18.04, post which I am trying to add it to a domain. Once I join the laptop to domain, I have noticed that at the login screen on the laptop after entering the password the screen goes blank and comes back to login screen again. After changing some settings related to network I thought some file got corrupted hence reimaged the PC and tried joining the PC to domain. Again issue repeated. I tried this for more than 6 times till now but no use. Hence could you guys help with identifying an fixing  the issue?

```

Commands I Use post Installation: 
apt-get update && apt-get upgrade
apt-get dist-upgrade
apt-get install autofs
apt-get install nfs-common
apt-get install nis
apt-get install openssh-server
apt-get install tcsh



```

Output of 'journalctl -b | grep video > video.txt' , 'journalctl -b | grep greeter > greeter.txt'

```

root@localpc:~# uname -a
Linux localpc 4.18.0-17-generic #18~18.04.1-Ubuntu SMP Fri Mar 15 15:27:12 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
root@localpc:~# cat video.txt
Apr 16 17:18:03 localpc kernel: videodev: Linux video capture interface: v2.00
Apr 16 17:18:03 localpc kernel: uvcvideo: Found UVC 1.00 device Integrated_Webcam_HD (0c45:6709)
Apr 16 17:18:03 localpc kernel: uvcvideo 1-1.6:1.0: Entity type for entity Extension 4 was not initialized!
Apr 16 17:18:03 localpc kernel: uvcvideo 1-1.6:1.0: Entity type for entity Extension 3 was not initialized!
Apr 16 17:18:03 localpc kernel: uvcvideo 1-1.6:1.0: Entity type for entity Processing 2 was not initialized!
Apr 16 17:18:03 localpc kernel: uvcvideo 1-1.6:1.0: Entity type for entity Camera 1 was not initialized!
Apr 16 17:18:03 localpc kernel: usbcore: registered new interface driver uvcvideo
root@localpc:~# cat greeter.txt
root@localpc:~#


```


Kindly also let me know what output you want me to post it here.

---

### Post by crazyarjun on 2019-04-26
Hi Guys, anyone knows how to fix this issue?

---

