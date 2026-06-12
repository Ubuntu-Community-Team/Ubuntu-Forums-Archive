---
title: "When updating, missing keys from sources."
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by DinoT1985 on 2010-07-12
I've tried deleting them many times now but I keep getting the error after reboot. I've even tried FSlint to help me out but still no avail.

I'm running Lucid 64bit.

Any help please? I'm new to Ubuntu (few months now)



> GPG error: [http://deb.torproject.org](http://deb.torproject.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B22AB97AF1CDFA9GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D739676F7613768DGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A16033A9A6FE242GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 449F83829320B41CFailed to fetch [http://ppa.launchpad.net/flam3/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/flam3/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by thahir1986 on 2010-07-12
i'm using ubuntu 9.04..we can remove the unwanted update by deleting the url in

#sudo nano /etc/apt/sources.list

but i dont know for lucid lynx...i think it may be same like this......

---

