---
title: "Fails to update Ubuntu to 12.04 from 11.04"
date: 2013-04-07
forum: Installation &amp; Upgrades
---

### Post by exsonic01 on 2013-04-07
I did 'sudo apt-get update' and followed by many messages. 
Final part of the error message says 
```

W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 04A38A9C1B826E04
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I really really hope to update my ubuntu to 12.04. I already changed the download server to best server in US (because I live in Pennsylvania) 
Still not working. Is it the problem occurs because my Ubuntu 11.04 fails to find server or files? 
Please someone help me with those GPG and following errors, regarding launchpad and others. 

Thank you very much in advance :)

---

### Post by José Serra on 2013-04-07
Hi, 11.04 its EOLed... May be you want to take a look to this: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

I would take the fresh install option.

Regards.

---

### Post by Bucky Ball on 2013-04-07
When you open the update manager are you offered an upgrade to 11.10? You could go there then to 12.04. You can't upgrade straight from 11.04 to 12.04 LTS. The LTS versions will upgrade to the next LTS, though. The interim releases only upgrade to the following release (which, in the case of 11.10 is to 12.04 LTS).

I agree with previous poster, though; fresh install would be best (and quickest).

---

### Post by exsonic01 on 2013-04-07
Fresh install means I need to burn 12.04 or higher Ubuntu to empty CD and install that, right? Thank you.

---

### Post by exsonic01 on 2013-04-07
Upgrade manager says that I can upgrade to 11.10, but it fails with same error I written in original message. Thank you anyway. Seems like I need to get a empty dvd or cd....

---

### Post by Bucky Ball on 2013-04-08
Yep, burn to a DVD and boot from that. Most reliable method of getting the ISO is via a torrent. 12.04 LTS is supported until April 2017 and you can upgrade to the next LTS release via update manager at that time (or before if you want, next LTS 14.04 in 2014). Good luck.

---

