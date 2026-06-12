---
title: "Update problems"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by sidewinder12s on 2010-12-28
I noticed my package info hadnt updated since I installed linux. I ran the package manager to reload it and I got this error in that and terminal.

Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8DB7F87A2B97B7B8
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
Now it will not update at all. Any help?

---

### Post by wojox on 2010-12-28
Sure open a terminal and copy and paste these two commands:

```
gpg --keyserver keyserver.ubuntu.com --recv 16126D3A3E5C1192
```

```
gpg --export --armor 16126D3A3E5C1192 | sudo apt-key add - && sudo apt-get update
```

---

### Post by sidewinder12s on 2010-12-28
Put both those commands in and I still got this error.


Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8DB7F87A2B97B7B8


Also I was having trouble with my Wifi, I have a latest Macbook that has the Broadcom Driver enabled. However, it keeps dropping the signal and will not connect to it right away. Lately it wont connect for like 5 minutes. I have good signal, I am sitting right above the router and it works on the OSX. Should I just make another thread for that?

---

### Post by sidewinder12s on 2010-12-29
Im still getting this error, even after a restart.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8DB7F87A2B97B7B8

---

### Post by Bucky Ball on 2010-12-29
> **sidewinder12s said:**
> Also I was having trouble with my Wifi, I have a latest Macbook that has the Broadcom Driver enabled. However, it keeps dropping the signal and will not connect to it right away. Lately it wont connect for like 5 minutes. I have good signal, I am sitting right above the router and it works on the OSX. Should I just make another thread for that?

Probably a good idea. You will get more specific help. The title of this thead is unrelated to that issue. ;)

---

### Post by sidewinder12s on 2010-12-29
I am still getting the updating error though. Ill post the Wifi trouble somewhere else.

---

### Post by wojox on 2010-12-29
Do the same thing for the other key but swap out the number's.

---

### Post by sidewinder12s on 2010-12-29
Thanks!
That did the trick.

---

