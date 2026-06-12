---
title: "Third-party Software Settings? Jaunty Upgrade"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rmgibbs1861 on 2009-03-29
What should I do after the upgrade with the disabled settings from the upgrade to 9.04 (everything is unchecked).

Thanks,

Rick

---

### Post by anyletter on 2009-04-01
I was wondering this myself.  I checked all Third Party Software boxes in Software Sources and still nothing, even after I restarted Ubuntu

---

### Post by zika on 2009-04-02
did You change intrepid (or whatever was there) to jaunty in repository property lines ...?

---

### Post by GARoss on 2009-04-02
Are Third Party Software boxes normally check or un-checked? Both of mine are un-checked [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner & [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner (Source Code).
The reason I ask is when I tried to +Add *deb [http://ppa.launchpad.net/capitanterrex/ppa/ubuntu](http://ppa.launchpad.net/capitanterrex/ppa/ubuntu) jaunty main* it was checked & I got an error, *W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E931CE221789C97*
My pubkey was active on an alpha Kubuntu version & I'm not sure how to reset it in this version of Ubuntu beta without starting from scratch.

---

### Post by zika on 2009-04-02
> **GARoss said:**
> Are Third Party Software boxes normally check or un-checked? Both of mine are un-checked [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner & [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner (Source Code).
The reason I ask is when I tried to +Add *deb [http://ppa.launchpad.net/capitanterrex/ppa/ubuntu](http://ppa.launchpad.net/capitanterrex/ppa/ubuntu) jaunty main* it was checked & I got an error, *W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E931CE221789C97*
My pubkey was active on an alpha Kubuntu version & I'm not sure how to reset it in this version of Ubuntu beta without starting from scratch.
in Terminal:```
gpg --keyserver subkeys.pgp.net --recv 0E931CE221789C97
gpg --export --armor 0E931CE221789C97 | sudo apt-key add -
sudo apt-get update
```

check them on Your will ... I have checked them and added some ... :)

---

