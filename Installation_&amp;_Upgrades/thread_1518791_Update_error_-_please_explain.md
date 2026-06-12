---
title: "Update error - please explain"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by JohnBUK on 2010-06-27
I have Ubuntu 10.04 running just fine and whilst I have been using Ubuntu for several months now I still consider myself a relative novice.
I wonder if someone could direct me in simple terms on how to deal with the following message I get when I run "Update Manager"?

Message as follows:-
 "W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61E091672E206FF0"

I do not perceive any problem running my laptop because of this but presumably I'm not getting updates for some of the programs I'm running.
Any help would be gratefully received.
Thank you
JohnB

---

### Post by davidmohammed on 2010-06-27
try copying and pasting the below into a terminal session (answer from [here]("https://answers.launchpad.net/ubuntu-tweak/+question/112289"))

```
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring; gpg --keyserver subkeys.pgp.net --recv 61E091672E206FF0; gpg --export --armor 61E091672E206FF0
```

---

