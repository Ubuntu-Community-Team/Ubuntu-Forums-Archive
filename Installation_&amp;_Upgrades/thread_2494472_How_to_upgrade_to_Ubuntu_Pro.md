---
title: "How to upgrade to Ubuntu Pro?"
date: 2024-01-17
forum: Installation &amp; Upgrades
---

### Post by ubontik22 on 2024-01-17
Hello,

I try to install Ubuntu Pro but for some reason I get a message ```
Check Internet connection
```.

Thank you.

---

### Post by MAFoElffen on 2024-01-17
What does this say?
```

pro status

```

---

### Post by ubontik22 on 2024-01-17
> $ pro status
Failed to access URL: [https://contracts.canonical.com/v1/resources?architecture=amd64&kernel=6.5.0-14-generic&series=jammy&virt=](https://contracts.canonical.com/v1/resources?architecture=amd64&kernel=6.5.0-14-generic&series=jammy&virt=)
Cannot verify certificate of server
Please check your openssl configuration..

---

### Post by him610 on 2024-01-18
At the bottom of this article is a link that will take you through the process -
[https://news.itsfoss.com/ubuntu-24-04-lts-support/?ref=itsfoss.com]("https://news.itsfoss.com/ubuntu-24-04-lts-support/?ref=itsfoss.com")

---

### Post by MAFoElffen on 2024-01-18
Please do
```

sudo locale-gen c ca_AD ca_ES.UTF-8 ca_IT ckb_IQ cs_CZ cy_GB.UTF-8 ca_AD.UTF-8 ca_ES@valencia ca_IT.UTF-8 cmn_TW cs_CZ.UTF-8 ca_ES ca_FR ce_RU crh_UA cv_RU ca_ES@euro ca_FR.UTF-8 chr_US csb_PL cy_GB
sudo locale-gen C.UTF-8 
sudo reboot

```
After reboot
```

pro status

```
There was an SLL bug that was related to OpenSSL and Locales. (That was on of the fixes.)
RE: [https://github.com/openssl/openssl/issues/18039](https://github.com/openssl/openssl/issues/18039)

---

### Post by ubontik22 on 2024-01-18
After reboot
> $ pro status
Failed to access URL: [https://contracts.canonical.com/v1/resources?architecture=amd64&kernel=6.5.0-14-generic&series=jammy&virt=](https://contracts.canonical.com/v1/resources?architecture=amd64&kernel=6.5.0-14-generic&series=jammy&virt=)
Cannot verify certificate of server
Please check your openssl configuration.

---

### Post by MAFoElffen on 2024-01-18
Please join this bug as affected: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-advantage-tools/+bug/2044340](https://bugs.launchpad.net/ubuntu/+source/ubuntu-advantage-tools/+bug/2044340)

---

