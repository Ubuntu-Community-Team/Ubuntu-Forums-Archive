---
title: "[Please Help]: Error in Update Manager"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by diggiewiggie on 2009-03-27
I'm new to linux and experimenting ubuntu netbook remix jaunty,
lately the update manager returns the message 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B81A3FBA47394CE

everytime i try to updating the packages.
please anyone could help me to get through this matter?
i've been googling and all i can get is fixing the same for intrepid,
i doubt it can work for jaunty.

---

### Post by drs305 on 2009-03-27
The procedure is probably the same for jaunty as it is for intrepid. If not, let us know:
```

gpg --keyserver keyserver.ubuntu.com --recv 3B81A3FBA47394CE    
gpg --export --armor 3B81A3FBA47394CE | sudo apt-key add -
sudo apt-get update

```

I just installed Jaunty beta and the codes worked for me.

---

### Post by kanikilu on 2009-03-27
> **drs305 said:**
> The procedure is probably the same for jaunty as it is for intrepid. If not, let us know:
```

gpg --keyserver keyserver.ubuntu.com --recv 3B81A3FBA47394CE    
gpg --export --armor 3B81A3FBA47394CE | sudo apt-key add -
sudo apt-get update

```

I just installed Jaunty beta and the codes worked for me.

I've used both that method, and the "one-liner" ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 3B81A3FBA47394CE
``` that the [PPA help page](https://help.launchpad.net/Packaging/PPA#Adding%20the%20keys%20in%20the%20terminal) suggests.

Not to hijack the thread too much, but do you happen to know if there is a difference between the two?

---

