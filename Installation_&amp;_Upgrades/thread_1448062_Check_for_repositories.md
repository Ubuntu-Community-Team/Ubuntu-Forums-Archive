---
title: "Check for repositories"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by motorhead_1 on 2010-04-06
checking for repositories and sudo apt-get update take ages now to complete and at the end I've the following messsage:

Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C28F899060FD0E97
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 015A66E603E02400


what should I do? I think it's this thing that is slowing the process

---

### Post by mkvnmtr on 2010-04-06
It looks like when you enabled those repositories you failed to download the key. Go back to the tutitorial where you found them and folllow the instrunctions to download the key. 
I do find some of the launchpad repositories download very slowly. Not really anything to do about it.

---

### Post by motorhead_1 on 2010-04-06
Ok I've read that I've to add the keys for those repositories, which are...?

---

### Post by mkvnmtr on 2010-04-06
Only you know where you found those repositories. You will have to go to where you found them and follow the instrunctions to download the key.

---

### Post by motorhead_1 on 2010-04-06
thanks I've posted the question also in the thread where I found these repos 
[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

---

### Post by oldos2er on 2010-04-06
Try ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` where KEYID is the number given after NO_PUBKEY.

---

### Post by motorhead_1 on 2010-04-06
it works, thanks!!!

---

