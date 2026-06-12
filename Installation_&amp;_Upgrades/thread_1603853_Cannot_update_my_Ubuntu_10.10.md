---
title: "Cannot update my Ubuntu 10.10"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by painkilleryusuf on 2010-10-23
Hey guys;

I am new to Ubuntu, and love it so far. The problem is that when the Update Manager prompts me to update my system and I put my credentials to update. It will start downloading and then give me this error 

[IMG]http://img535.imageshack.us/img535/5448/screenshotgx.png[/IMG]

here is the text thats inside the Details box:

Failed to fetch [http://kw.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-sso-client/ubuntu-sso-client_1.0.4-0ubuntu1_all.deb](http://kw.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-sso-client/ubuntu-sso-client_1.0.4-0ubuntu1_all.deb) 403  Forbidden
Failed to fetch [http://kw.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2010m-0ubuntu0.10.10_all.deb](http://kw.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2010m-0ubuntu0.10.10_all.deb) 403  Forbidden
Failed to fetch [http://kw.archive.ubuntu.com/ubuntu/pool/main/u/udev/libudev0_162-2.1_i386.deb](http://kw.archive.ubuntu.com/ubuntu/pool/main/u/udev/libudev0_162-2.1_i386.deb) 403  Forbidden
Failed to fetch [http://kw.archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_162-2.1_i386.deb](http://kw.archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_162-2.1_i386.deb) 403  Forbidden
Failed to fetch [http://kw.archive.ubuntu.com/ubuntu/pool/main/u/udev/libgudev-1.0-0_162-2.1_i386.deb](http://kw.archive.ubuntu.com/ubuntu/pool/main/u/udev/libgudev-1.0-0_162-2.1_i386.deb) 403  Forbidden
Failed to fetch [http://kw.archive.ubuntu.com/ubuntu/pool/main/u/utouch-grail/libutouch-grail1_1.0.15-0ubuntu1_i386.deb](http://kw.archive.ubuntu.com/ubuntu/pool/main/u/utouch-grail/libutouch-grail1_1.0.15-0ubuntu1_i386.deb) 403  Forbidden
Failed to fetch [http://kw.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte-common_0.26.0-0ubuntu2_all.deb](http://kw.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte-common_0.26.0-0ubuntu2_all.deb) 403  Forbidden
Failed to fetch [http://kw.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte9_0.26.0-0ubuntu2_i386.deb](http://kw.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte9_0.26.0-0ubuntu2_i386.deb) 403  Forbidden
Failed to fetch [http://kw.archive.ubuntu.com/ubuntu/pool/main/v/vte/python-vte_0.26.0-0ubuntu2_i386.deb](http://kw.archive.ubuntu.com/ubuntu/pool/main/v/vte/python-vte_0.26.0-0ubuntu2_i386.deb) 403  Forbidden
Failed to fetch [http://kw.archive.ubuntu.com/ubuntu/pool/main/s/simple-scan/simple-scan_2.32.0-0ubuntu3_i386.deb](http://kw.archive.ubuntu.com/ubuntu/pool/main/s/simple-scan/simple-scan_2.32.0-0ubuntu3_i386.deb) 403  Forbidden
Failed to fetch [http://kw.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_3.0.5_all.deb](http://kw.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_3.0.5_all.deb) 403  Forbidden
Failed to fetch [http://kw.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox-ubuntuone-music-store/rhythmbox-ubuntuone-music-store_0.1.9-0ubuntu1_all.deb](http://kw.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox-ubuntuone-music-store/rhythmbox-ubuntuone-music-store_0.1.9-0ubuntu1_all.deb) 403  Forbidden


Can anyone please help me?

---

### Post by viralmeme on 2010-10-23
> **painkilleryusuf said:**
> The problem is that when the Update Manager prompts me to update my system and I put my credentials to update. It will start downloading and then give me this error

Sounds like it's being blocked at the firewall, either locally or by your ISP ..

---

### Post by SIGTERMer on 2010-10-23
same problem here.
The problem might be from qualitynet's repository. I keep getting iso hashsum mismatches from them.

but just to be on the safe side, what is your isp? ours is kems.

In any case, I'll post something here when I solve this problem.

---

### Post by SIGTERMer on 2010-10-23
yup, the problem seems to be from qualitynet. use saudi's repo instead: [http://ubuntu.mirrors.isu.net.sa](http://ubuntu.mirrors.isu.net.sa)

it's a bit slower then our local repository but it works.

To switch repositories open synaptic and select repository from the settings menu. then just add saudi's server from the list.

this is only temporary solution until qualitynet gets its act together.

---

### Post by painkilleryusuf on 2010-10-23
Awesome. that did it for me. I am on KEMS btw

---

### Post by finito on 2010-10-24
I am getting the same problem, I contacted Qualitynet they don't know what I am talking about. Well I guessed as much.

Does anyone know who to talk to. The guy who picked up didn't even know what linux is :confused:

Another guy I talked to said it must be corporate account.

[http://ubuntu.qualitynet.net/](http://ubuntu.qualitynet.net/) 

I will keep digging.

---

### Post by finito on 2010-10-24
Contacted Corporate. I talked to a guy in Corporate and explained the situation and forwarded this page to him.

Let's see what happens.

---

### Post by finito on 2010-10-24
Update: recieved a call from Qualitynet Corporate. The problem is fixed.
I wasn't expecting a fix that soon.
Nice one

---

### Post by hasbean on 2010-10-24
Hey finito,

It should be fixed now.  Somehow permissions changed during a sync :(

---

