---
title: "Double Maverick wtf"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by Kyentei on 2010-10-04
Hello everyone,

Yesterday I installed Ubuntu 10.10 RC (Fresh install) and I could perfectly fine update it. However, after trying to update today, I get the following error:
```

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

```
[FONT=Verdana]Now that's odd. I don't see how that could happen, ánd .. why does it say "a error" and not "an error" ?[/FONT]

[FONT=Verdana]I hope you can help me out here, how do I fix this?[/FONT]

---

### Post by andrewthomas on 2010-10-04
Can you try again to see if you can replicate the error?

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by efflandt on 2010-10-04
What are you trying to update, because usually versions are frozen between between the time that the RC comes out until it is actually released.  Until 10.10 it is released you should be reading or posting about that to the forum [http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385) especially the part about Update Manager and "Partial" updates.

I installed 64-bit 10.10 beta earlier and accidentally did a Partial update before I read that, but it it looks like the removed packages at that time went fine because they were replaced by others.  Then I updated to RC, and have installed packages, but have not done any updates since then.

---

### Post by oldos2er on 2010-10-04
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
```

You may need to wait a while until the server is updated.

---

### Post by Kyentei on 2010-10-07
Thanks for your assistance and sorry for the late reply.
I managed to solve the problem not long after I posted it, as it is a known maverick bug.
The bug is #650525: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-extras-keyring/+bug/650525](https://bugs.launchpad.net/ubuntu/+source/ubuntu-extras-keyring/+bug/650525)
This issue can easily solved by typing the following into your terminal:
```
# apt-get install --reinstall ubuntu-extras-keyring
```

---

