---
title: "Installing OpenVPN 2.5.9 on Ubuntu 24.04 LTS"
date: 2024-07-30
forum: Installation &amp; Upgrades
---

### Post by misiaala on 2024-07-30
Hello,

i cannot find any way on how to install this older openvpn 2.5.9 version on my ubuntu. Dies anyone have any documentation about this?
Thanks in advance!

---

### Post by currentshaft on 2024-07-30
> **misiaala said:**
> Hello,

i cannot find any way on how to install this older openvpn 2.5.9 version on my ubuntu. Dies anyone have any documentation about this?
Thanks in advance!

Clone the source code at that revision and run make?

What problem are you trying to solve with this version of openvpn?

---

### Post by misiaala on 2024-08-01
Hi, i'm trying to circumvent the topic that openvpn >2.6 is not allowing connections to SHA1 gateways. But i still need this for some months.

And sorry, i have no idea on how to "clone the source code at that revision and run make".

---

### Post by currentshaft on 2024-08-01
> **misiaala said:**
> Hi, i'm trying to circumvent the topic that openvpn >2.6 is not allowing connections to SHA1 gateways. But i still need this for some months.

And sorry, i have no idea on how to "clone the source code at that revision and run make".

wget [https://build.openvpn.net/downloads/releases/openvpn-2.5.9.tar.gz](https://build.openvpn.net/downloads/releases/openvpn-2.5.9.tar.gz)

tar xf openvpn-2.5.9.tar.gz

cd openvpn-2.5.9

./configure

make

sudo make install

You may need to install additional libraries such as liblzo2-dev, etc.

However, I strongly advise against running an older version of OpenVPN, because it is full of vulnerabilities which will put your computer at risk, possibly including giving the remote server code execution capability to your local system.

---

### Post by misiaala on 2024-08-02
While typing in "./configure" i get "checking additionally if OpenSSL is available and version >= 1.0.2...configure: error: OpenSSL version too old". 
That's the reason why i asked here this question on how to install older versions.

---

### Post by currentshaft on 2024-08-02
> **misiaala said:**
> While typing in "./configure" i get "checking additionally if OpenSSL is available and version >= 1.0.2...configure: error: OpenSSL version too old".
That's the reason why i asked here this question on how to install older versions.

You'll have to modify the source code you downloaded to make it work.

But it's honestly a waste of time. You need to update to a modern version of openssl and openvpn.

---

