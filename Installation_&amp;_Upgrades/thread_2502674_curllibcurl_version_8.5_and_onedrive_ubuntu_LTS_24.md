---
title: "curl/libcurl version 8.5 and onedrive ubuntu LTS 24.04"
date: 2024-11-24
forum: Installation &amp; Upgrades
---

### Post by lvazdela on 2024-11-24
Hi,
I am currently using Ubuntu 24.04. I use onedrive v2.5.3-1+np1+1.1
I routinely sync my work with onedrive, it works well, but a message appears with the following legend:
WARNING: Your cURL/libcurl version (8.5.0) has known operational bugs that impact the use of this client.
         Please report this to your distribution, requesting an update to a newer cURL version, or consider upgrading it yourself for optimal stability.

Is it possible to have the most recent version of curl? and if it is not possible, how can I safely upgrade the software by myself?
Thanks
Luis

---

### Post by 1fallen on 2024-11-24
> **lvazdela said:**
> 
Is it possible to have the most recent version of curl? and if it is not possible, how can I safely upgrade the software by myself?
Thanks
Luis

Is it possible yes, is it safe>>> depends on how badly you want stability for 24.04

If it were me I would just ignore The Warning, or upgrade Noble to Oracular 24.10 its in proposed currently
```
[FONT=monospace][COLOR=#000000]apt policy curl [/COLOR]
curl: 
  Installed: 8.5.0-2ubuntu10.5 
  Candidate: 8.9.1-2ubuntu2.1 
  Version table: 
     8.9.1-2ubuntu2.1 500 
        500 https://ppa.launchpadcontent.net/ubuntu-security-proposed/ppa/ubuntu oracular/main amd64 Packages 
 *** 8.5.0-2ubuntu10.5 500 
        500 https://mirrors.tuxedocomputers.com/ubuntu/mirror/security.ubuntu.com/ubuntu noble-security/main a
md64 Packages 
        100 /var/lib/dpkg/status 
     8.5.0-2ubuntu10.4 500 
        500 https://mirrors.tuxedocomputers.com/ubuntu/mirror/archive.ubuntu.com/ubuntu noble-updates/main amd
64 Packages 
     8.5.0-2ubuntu10 500 
        500 https://mirrors.tuxedocomputers.com/ubuntu/mirror/archive.ubuntu.com/ubuntu noble/main amd64 Packa
ges

[/FONT]
```

I'm a tester so I do things I would never suggest to someone that is running a production system.
```
[FONT=monospace][COLOR=#000000]curl | 8.5.0-2ubuntu10    | noble             | source, amd64, arm64, armhf, i386, ppc64el, riscv64, s390x [/COLOR]
 curl | 8.5.0-2ubuntu10.5  | noble-security    | source, amd64, arm64, armhf, i386, ppc64el, riscv64, s390x 
 curl | 8.5.0-2ubuntu10.5  | noble-updates     | source, amd64, arm64, armhf, i386, ppc64el, riscv64, s390x 
 curl | 8.9.1-2ubuntu2     | oracular          | source, amd64, arm64, armhf, i386, ppc64el, riscv64, s390x 
 curl | 8.9.1-2ubuntu2.1   | oracular-security | source, amd64, arm64, armhf, i386, ppc64el, riscv64, s390x 
 curl | 8.9.1-2ubuntu2.1   | oracular-updates  | source, amd64, arm64, armhf, i386, ppc64el, riscv64, s390x 
 curl | 8.11.0-1ubuntu2    | plucky            | source, amd64, arm64, armhf, i386, ppc64el, riscv64, s390x



```
[/FONT]

---

### Post by lvazdela on 2024-11-24
So, Ubuntu 24.04 users must stick with the faulty 8.5 version of curl? I only update the system when a LTS version arrives:confused:

---

### Post by 1fallen on 2024-11-24
The maintainer has another thread with info here: [https://askubuntu.com/questions/1533279/ubuntu-24-04-1-lts-error-message-after-onedrive-update](https://askubuntu.com/questions/1533279/ubuntu-24-04-1-lts-error-message-after-onedrive-update)

---

