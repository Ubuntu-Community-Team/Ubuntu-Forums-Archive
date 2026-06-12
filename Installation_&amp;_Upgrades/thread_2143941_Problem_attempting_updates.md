---
title: "Problem attempting updates"
date: 2013-05-10
forum: Installation &amp; Upgrades
---

### Post by mringer on 2013-05-10
Lubuntu 12.04, I started synaptic and did      ```
 install all updates
```

and got the following errors:

```

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/libnm-gtk-common_0.9.4.1-0ubuntu2.2_all.deb
  404  Not Found [IP: 91.189.92.176 80]


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/libnm-gtk0_0.9.4.1-0ubuntu2.2_i386.deb
  404  Not Found [IP: 91.189.92.176 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_3.2.0.40.48_i386.deb
  404  Not Found [IP: 91.189.92.190 80]

```


Please what should  I do to get round this? Is there a log file somewhere that I should post? thank you.

---

### Post by snowpine on 2013-05-10
Try (from the Terminal):

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by mringer on 2013-05-13
Thank you Snowpine for your reply. Here are the results. I have deleted 
non-error messages in the hope of improving the signal to noise ratio.
```


sudo apt-get update
[...]
Err http://ppa.launchpad.net precise/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages                        
  404  Not Found
[...]

sudo apt-get dist-upgrade
[no visible errors]

sudo apt-get update
[...]
Err http://ppa.launchpad.net precise/main Sources                    
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages
  404  Not Found
[...]

```

---

### Post by plucky on 2013-05-13
> **mringer said:**
> Thank you Snowpine for your reply. Here are the results. I have deleted 
non-error messages in the hope of improving the signal to noise ratio.
```


sudo apt-get update
[...]
Err http://ppa.launchpad.net precise/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages                        
  404  Not Found
[...]

sudo apt-get dist-upgrade
[no visible errors]

sudo apt-get update
[...]
Err http://ppa.launchpad.net precise/main Sources                    
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages
  404  Not Found
[...]

```


That is a different error to your first reply.

Open Software Sources and disable Launchpad PPA as a source and see if that fixes the problem.

Good Luck

---

