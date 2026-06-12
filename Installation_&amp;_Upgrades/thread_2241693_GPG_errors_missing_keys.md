---
title: "GPG errors: missing keys"
date: 2014-08-27
forum: Installation &amp; Upgrades
---

### Post by jeftobias on 2014-08-27
Here's the relevant code:
```
W: GPG error: http://ubuntu.wikimedia.org trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: https://download.01.org trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A902DDA375E52366
W: GPG error: http://archive.getdeb.net trusty-getdeb InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
W: GPG error: http://ubuntu.wikimedia.org trusty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://ubuntu.wikimedia.org trusty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://ubuntu.wikimedia.org trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 446C82DC2DD154A1


```

I've tried every fix I can find and nothing works. I'm stumped.

---

### Post by ibjsb4 on 2014-08-27
In terminal:
```
sudo -i
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
exit
```

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+NO_PUBKEY&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+NO_PUBKEY&sa=Search&cof=FORID:9)

---

### Post by jeftobias on 2014-08-28
> **ibjsb4 said:**
> In terminal:
```
sudo -i
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
exit
```

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+NO_PUBKEY&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+NO_PUBKEY&sa=Search&cof=FORID:9)


Doesn't work. Still have gpg errors.

---

### Post by slickymaster on 2014-08-28
Can you please try the following command in the terminal:```
sudo rm /var/lib/apt/lists/* -vf
```After that update your system```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by jeftobias on 2014-08-28
> **slickymaster said:**
> Can you please try the following command in the terminal:```
sudo rm /var/lib/apt/lists/* -vf
```After that update your system```
sudo apt-get update && sudo apt-get upgrade
```

Already tried this twice. Same result. Problem persists. I am currently attempting a couple other solutions I've found in Ubuntu and Debian bug threads. So far, nothing seems to work.

---

### Post by slickymaster on 2014-08-28
Have you already notice this bug: [Bug #1263540]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540")

---

### Post by jeftobias on 2014-08-28
> **slickymaster said:**
> Have you already notice this bug: [Bug #1263540]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540")

Yes. That's one of the threads I referred to above.

After lots of reading, I finally found this: Summary is, remove empty keyrings from "/etc/apt/trusted.gpg.d/"

This solved the problem.

---

