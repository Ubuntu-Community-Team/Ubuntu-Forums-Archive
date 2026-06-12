---
title: "Cannot install Indicator-applet-complete"
date: 2012-04-13
forum: Installation &amp; Upgrades
---

### Post by bipin.nag on 2012-04-13
I am trying to install Indicator-applet-complete for which I need **ppa:jconti/gnome3** repository
but i keep getting 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 52A794126E3AB2D3

I have tried to fix it using
 sudo apt-key adv --recv-key --keyserver keyserver.ubuntu.com 52A794126E3AB2D3

but all i get is this
gpg: requesting key 6E3AB2D3 from http server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Host not found
gpgkeys: http fetch error 7: couldn't connect: No such file or directory
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
gpg: keyserver internal error
gpg: keyserver receive failed: keyserver error

i use a proxy server to access net which i have already set and apt-get update works without a glitch
but because udp is not allowed using the proxy i cannot seem to get gpg work.

in short can anyone please post the pubkey 52A794126E3AB2D3 for me so that i can import
and install the program without hassles

also can anyone suggest any alternatives/solutions 
thank you

---

