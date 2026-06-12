---
title: "Problems with Update Manager and public keys"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by blueshift9 on 2010-12-03
For 9 days now I have been getting errors when trying to run Update Manager saying that ALL my keys are missing. Any ideas?

```
W: GPG error: http://archive.canonical.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com maverick-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991

```

---

### Post by wangsuda on 2010-12-03
Cool! I know this one! I can help. Here's what you do:
Type this command into the terminal ("Applications > Accessories > Terminal")
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys *ADD KEY NUMBERS HERE*
```
And then add the hexadecimal numbers to the command (please leave a space between your number and the word "keys"). For example, to add your public keys, I would enter
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5 16126D3A3E5C1192 40976EAF437D05B5 A040830F7FAC5991
```
If the code doesn't work with all the hex numbers together, then split it into separate commands:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5   
``````
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192  
``````
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys   A040830F7FAC5991
``````
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  40976EAF437D05B5 
```
That should work.

---

### Post by byStanderone on 2010-12-03
...you can try a gpg key update: [http://ubuntuforums.org/showthread.php?t=299708](http://ubuntuforums.org/showthread.php?t=299708)

---

### Post by sikander3786 on 2010-12-03
For this one,

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991

I think you'll need this command as well.

```
wget -q -O - http://dl.google.com/linux/linux_signing_key.pub | sudo  apt-key add -
```

---

### Post by blueshift9 on 2010-12-03
Thanks a million guys!

---

### Post by NewUserFF on 2012-02-22
> **wangsuda said:**
> Cool! I know this one! I can help. Here's what you do:
Type this command into the terminal ("Applications > Accessories > Terminal")
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys *ADD KEY NUMBERS HERE*
```
And then add the hexadecimal numbers to the command (please leave a space between your number and the word "keys"). For example, to add your public keys, I would enter
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5 16126D3A3E5C1192 40976EAF437D05B5 A040830F7FAC5991
```
If the code doesn't work with all the hex numbers together, then split it into separate commands:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5   
``````
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192  
``````
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys   A040830F7FAC5991
``````
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  40976EAF437D05B5 
```
That should work.
it also works for me. thanks!

---

