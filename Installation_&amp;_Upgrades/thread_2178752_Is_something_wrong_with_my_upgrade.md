---
title: "Is something wrong with my upgrade?"
date: 2013-10-05
forum: Installation &amp; Upgrades
---

### Post by blake4 on 2013-10-05
I can't update Ubuntu 13.04


[IMG]http://s13.postimg.org/6u9supak7/upgrades.png[/IMG]

[IMG]http://s11.postimg.org/vkc8epts3/upgrades2.png[/IMG]


And with Terminal, I get

> 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Fetched 1,044 kB in 11s (94.3 kB/s)                                            
W: GPG error: [http://www.duinsoft.nl](http://www.duinsoft.nl) debs Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E18CE6625CB26B26
W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch [http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/raring/main/binary-amd64/Packages](http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.


---

### Post by Old_Grey_Wolf on 2013-10-05
You have 3 problems. 
1. from the screenshot I see you have Install from CD-ROM/DVD checked. Uncheck it. 
2. on the Other Software tab uncheck the ppa for the screenlets. 
3. you need to install a GPG Key. Enter these commands 
```
gpg --keyserver keyserver.ubuntu.com --recv E18CE6625CB26B26
gpg --export --armor E18CE6625CB26B26 | sudo apt-key add -
```

---

### Post by blake4 on 2013-10-05
> **Old_Grey_Wolf said:**
> You have 3 problems. 
1. from the screenshot I see you have Install from CD-ROM/DVD checked. Uncheck it. 
2. on the Other Software tab uncheck the ppa for the screenlets. 
3. you need to install a GPG Key. Enter these commands 
```
gpg --keyserver keyserver.ubuntu.com --recv E18CE6625CB26B26
gpg --export --armor E18CE6625CB26B26 | sudo apt-key add -
```

Thank you very much, it worked perfectly!

---

