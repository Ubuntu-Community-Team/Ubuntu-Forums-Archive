---
title: "Ubuntu14.04 source package download error"
date: 2014-06-11
forum: Installation &amp; Upgrades
---

### Post by s_m2 on 2014-06-11
Hi,
I am trying to download the source packages for the ubuntu14.04 cloud image from the manifest....
The Manifest that I am working off of to get the source packages (apt-get -d -q source <package>) is here...
[https://cloud-images.ubuntu.com/releases/trusty/release/ubuntu-14.04-server-cloudimg-amd64.manifest](https://cloud-images.ubuntu.com/releases/trusty/release/ubuntu-14.04-server-cloudimg-amd64.manifest)

I was able to get all the source packages except for the following 7...
linux-headers-3.13.0-27 3.13.0-27.50
linux-headers-3.13.0-27-generic 3.13.0-27.50
linux-headers-generic 3.13.0.27.33
linux-headers-virtual 3.13.0.27.33
linux-image-3.13.0-27-generic 3.13.0-27.50
linux-image-virtual 3.13.0.27.33
linux-virtual 3.13.0.27.33


Any idea why the downloads for these packages repeatedly fails and where else can I get the source packages for the above components?

Thanks a lot in advance.

Srikanth

---

### Post by oldos2er on 2014-06-11
The files you listed don't appear to be on the manifest.

---

### Post by s_m2 on 2014-06-12
Hi Ann,
I double checked again after I saw your reply...it is very much there.....this is the link to the manifest ....
[https://cloud-images.ubuntu.com/releases/trusty/release/ubuntu-14.04-server-cloudimg-amd64.manifest](https://cloud-images.ubuntu.com/releases/trusty/release/ubuntu-14.04-server-cloudimg-amd64.manifest)

Thanks for your time on this.

Srikanth

---

### Post by oldos2er on 2014-06-12
Strange, I searched that page for 3.13.0-27 and found nothing.

---

