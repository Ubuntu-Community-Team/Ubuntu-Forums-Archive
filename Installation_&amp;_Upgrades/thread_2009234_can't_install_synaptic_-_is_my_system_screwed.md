---
title: "can't install synaptic - is my system screwed??"
date: 2012-06-24
forum: Installation &amp; Upgrades
---

### Post by BigBaka on 2012-06-24
By way of background,

I had been playing around with various desktop environments as an alternative to Unity (Cinnamon gets my vote) and installed xubuntu. In an attempt to completely get rid of xubuntu I re-installed my 12.04 system today (see the other threads in the install forum) on my partitioned hard drive. I reformatted and reinstalled the /boot and the file system but left the swap and the /home mounts where they were. 

The installation itself went smoothly, but am now having some problems and wondering if they are related. One of them is that I noticed that I don't even have synaptic installed on my system. I tried to install from the package manager and got the following error message

> Requires installation of untrusted packages
The action would require the installation of packages from sources that are not authenticated.

Details
docbook-xml libept1.4.12 librarian0 libvte-common libvte9 rarian-compat sgml-data synaptic 

What is this? When I ran a google of the error details I saw many things coming up about xbunutu and wondered if it might be related to the previous system.

And if it isn't how do I get synaptic installed?

Thanks
BB

---

### Post by BigBaka on 2012-06-24
Oh, and I forgot to mention that there is an option to press "Repair" and by doing so software center then starts 

> Updating cache
Querying software sources

But it's been 10 minutes and nothing happens, the little red bar line showing activity doesn't begin moving, although the progress arrow wheel in the top panel of the software center keeps spinning.

---

### Post by oldos2er on 2012-06-24
Synaptic is no longer installed by default. "sources that are not authenticated" may mean you're missing a gpg key, or you may just need to run ```
sudo apt-get update
``` if you haven't already.

---

