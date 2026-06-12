---
title: "error-package-download-failed"
date: 2023-06-25
forum: Installation &amp; Upgrades
---

### Post by David_Partridge on 2023-06-25
Running a normal upgrade, I am getting:

```

Failed to download package files
Check your Internet connection.
Eror Code: error-package-download-failed
Failed to download package files
Check your Internet connection.
Error Detail: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_2.3.1-9ubuntu1.3_amd64.deb 404  Not Found [IP: 185.125.190.39 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups/cups-ipp-utils_2.3.1-9ubuntu1.3_amd64.deb 404  Not Found [IP: 185.125.190.39 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups/cups-core-drivers_2.3.1-9ubuntu1.3_amd64.deb 404  Not Found [IP: 185.125.190.39 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_2.3.1-9ubuntu1.3_all.deb 404  Not Found [IP: 185.125.190.39 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_2.3.1-9ubuntu1.3_amd64.deb 404  Not Found [IP: 185.125.190.39 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_2.3.1-9ubuntu1.3_amd64.deb 404  Not Found [IP: 185.125.190.39 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups/cups-daemon_2.3.1-9ubuntu1.3_amd64.deb 404  Not Found [IP: 185.125.190.39 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups/cups_2.3.1-9ubuntu1.3_amd64.deb 404  Not Found [IP: 185.125.190.39 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_2.3.1-9ubuntu1.3_amd64.deb 404  Not Found [IP: 185.125.190.39 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups/cups-server-common_2.3.1-9ubuntu1.3_all.deb 404  Not Found [IP: 185.125.190.39 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups/cups-ppdc_2.3.1-9ubuntu1.3_amd64.deb 404  Not Found [IP: 185.125.190.39 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_114.0.1+build1-0ubuntu0.20.04.1_amd64.deb 404  Not Found [IP: 185.125.190.39 80]
```

Is something amiss?

---

### Post by #&amp;thj^% on 2023-06-25
I get 404 not found on all those repos you have shown.
Something is for sure amiss, will you show your sources enabled please.
```
inxi -r
```
Also check your systems Time settings to be current.

---

### Post by David_Partridge on 2023-06-25
Here you go:

```
amonra@charon:~$ inxi -r
Repos:
  Active apt repos in: /etc/apt/sources.list 
  1: deb http://archive.ubuntu.com/ubuntu/ focal main restricted
  2: deb-src http://archive.ubuntu.com/ubuntu/ focal main restricted
  3: deb http://archive.ubuntu.com/ubuntu/ focal-updates main restricted
  4: deb-src http://archive.ubuntu.com/ubuntu/ focal-updates main restricted
  5: deb http://archive.ubuntu.com/ubuntu/ focal universe
  6: deb http://archive.ubuntu.com/ubuntu/ focal-updates universe
  7: deb http://archive.ubuntu.com/ubuntu/ focal multiverse
  8: deb http://archive.ubuntu.com/ubuntu/ focal-updates multiverse
  9: deb http://security.ubuntu.com/ubuntu focal-security main restricted
  10: deb http://security.ubuntu.com/ubuntu focal-security universe
  11: deb http://security.ubuntu.com/ubuntu focal-security multiverse
  12: deb http://archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
  Active apt repos in: /etc/apt/sources.list.d/bashtop-monitor-ubuntu-bashtop-focal.list 
  1: deb http://ppa.launchpad.net/bashtop-monitor/bashtop/ubuntu focal main
  Active apt repos in: /etc/apt/sources.list.d/mediaarea.list 
  1: deb https://mediaarea.net/repo/deb/ubuntu focal main
  Active apt repos in: /etc/apt/sources.list.d/x2go-ubuntu-stable-focal.list 
  1: deb http://ppa.launchpad.net/x2go/stable/ubuntu focal main
amonra@charon:~$ 

```

```
amonra@charon:~$ date
Sun 25 Jun 21:10:07 BST 2023
amonra@charon:~$ 

```

---

### Post by #&amp;thj^% on 2023-06-25
Great Info thanks for that! :)
Something got jammed just recently then, would you please now try:
```
sudo mv /var/lib/apt/lists/ /var/lib/apt/lists/.bk

```
Now your update and upgrade should work.
```
sudo apt update && sudo apt upgrade
```

---

### Post by David_Partridge on 2023-06-25
I think you meant:```
sudo mv /var/lib/apt/lists/ /var/lib/apt/lists.bk
```

That worked OK - the proposed command couldn't possibly work I think...

upgrade now running - so far so good :-)

---

### Post by #&amp;thj^% on 2023-06-25
> **David_Partridge said:**
> I think you meant:```
sudo mv /var/lib/apt/lists/ /var/lib/apt/lists.bk
```

That worked OK - the proposed command couldn't possibly work I think...

upgrade now running - so far so good :-)
Re read my post???
Your shown command is the same as mine....lol

---

### Post by David_Partridge on 2023-06-25
You actually wrote:
```
sudo mv /var/lib/apt/lists/ /var/lib/apt/lists/.bk
```

---

### Post by Impavidus on 2023-06-26
It says```
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups/cups-core-drivers_2.3.1-9ubuntu1.3_amd64.deb 404  Not Found [IP: 185.125.190.39 80]
```The current version for that package in the focal repos is 2.3.1-9ubuntu1.4. Your repository information is out of date. Try ```
sudo apt update
sudo apt upgrade
```Maybe the repository was updated right when you checked for updates.

---

### Post by David_Partridge on 2023-06-26
Yes, that's what I did and it worked - thank you.

David

---

