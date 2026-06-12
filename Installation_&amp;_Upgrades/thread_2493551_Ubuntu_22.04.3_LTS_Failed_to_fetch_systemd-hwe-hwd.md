---
title: "Ubuntu 22.04.3 LTS Failed to fetch systemd-hwe-hwdb all 249.11.3"
date: 2023-12-18
forum: Installation &amp; Upgrades
---

### Post by zacw001 on 2023-12-18
[COLOR=#0C0D0E][FONT=-apple-system]I got an error when trying to install Chrome on Ubuntu 22.04.3 LTS.
[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Error:[/FONT][/COLOR]
```

The following NEW packages will be installed:
  fonts-liberation google-chrome-stable libgbm1 libu2f-udev libwayland-server0
  systemd-hwe-hwdb udev
0 upgraded, 7 newly installed, 0 to remove and 17 not upgraded.
Need to get 2,453 kB/107 MB of archives.
After this operation, 351 MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu jammy/main amd64 fonts-liberation all 1:1.07.4-11 [822 kB]
Get:2 /tmp/google-chrome-stable_current_amd64.deb google-chrome-stable amd64 120.0.6099.109-1 [105 MB]
Get:3 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libwayland-server0 amd64 1.20.0-1ubuntu0.1 [34.3 kB]
Get:4 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgbm1 amd64 23.0.4-0ubuntu1~22.04.1 [33.1 kB]
Get:5 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 udev amd64 249.11-0ubuntu3.11 [1,557 kB]
Get:6 http://archive.ubuntu.com/ubuntu jammy/main amd64 libu2f-udev all 1.1.10-3build2 [4,190 B]
Err:7 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 systemd-hwe-hwdb all 249.11.3
  404  Not Found [IP: 185.125.190.36 80]
Fetched 2,450 kB in 3s (712 kB/s)

E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/s/systemd-hwe/systemd-hwe-hwdb_249.11.3_all.deb  404  Not Found [IP: 185.125.190.36 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

[COLOR=#0C0D0E][FONT=-apple-system]Reproduce:[/FONT][/COLOR]
```

sudo apt-get update
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb -P /tmp
sudo apt-get install -y /tmp/google-chrome-stable_current_amd64.deb

```

Version:
```

[COLOR=#555555][FONT=Menlo]PRETTY_NAME="Ubuntu 22.04.3 LTS"NAME="Ubuntu"VERSION_ID="22.04"VERSION="22.04.3 LTS (Jammy Jellyfish)"VERSION_CODENAME=jammyID=ubuntuID_LIKE=debianHOME_URL="[/FONT][/COLOR][https://www.ubuntu.com/](https://www.ubuntu.com/)[COLOR=#555555][FONT=Menlo]"SUPPORT_URL="[/FONT][/COLOR][https://help.ubuntu.com/](https://help.ubuntu.com/)[COLOR=#555555][FONT=Menlo]"BUG_REPORT_URL="[/FONT][/COLOR][https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)[COLOR=#555555][FONT=Menlo]"PRIVACY_POLICY_URL="[/FONT][/COLOR][https://www.ubuntu.com/legal/terms-and-policies/privacy-policy](https://www.ubuntu.com/legal/terms-and-policies/privacy-policy)[COLOR=#555555][FONT=Menlo]"UBUNTU_CODENAME=jamm
[/FONT][/COLOR]
```

How to solve it? Thanks.

---

### Post by MAFoElffen on 2023-12-18
It is installed, but I was able to reproduce your error...
```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 3 not upgraded.
Need to get 2,908 B of archives.
After this operation, 0 B of additional disk space will be used.
Ign:1 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 systemd-hwe-hwdb all 249.11.3
Err:1 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 systemd-hwe-hwdb all 249.11.3
  404  Not Found [IP: 91.189.91.39 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/systemd-hwe/systemd-hwe-hwdb_249.11.3_all.deb  404  Not Found [IP: 91.189.91.39 80]
E: Some files failed to download

```
But if I go to a mirror, I was able to download it:
```

mafoelffen@Mikes-ThinkPad-T520:~/Downloads$ wget -N -t 5 -T 10 http://mirrors.kernel.org/ubuntu/pool/main/s/systemd-hwe/systemd-hwe-hwdb_249.11.4_all.deb
--2023-12-18 17:59:55--  http://mirrors.kernel.org/ubuntu/pool/main/s/systemd-hwe/systemd-hwe-hwdb_249.11.4_all.deb
Resolving mirrors.kernel.org (mirrors.kernel.org)... 2604:1380:45e3:2400::1, 139.178.88.99
Connecting to mirrors.kernel.org (mirrors.kernel.org)|2604:1380:45e3:2400::1|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://mirrors.edge.kernel.org/ubuntu/pool/main/s/systemd-hwe/systemd-hwe-hwdb_249.11.4_all.deb [following]
--2023-12-18 17:59:55--  http://mirrors.edge.kernel.org/ubuntu/pool/main/s/systemd-hwe/systemd-hwe-hwdb_249.11.4_all.deb
Resolving mirrors.edge.kernel.org (mirrors.edge.kernel.org)... 2604:1380:45d1:ec00::1, 147.75.199.223
Connecting to mirrors.edge.kernel.org (mirrors.edge.kernel.org)|2604:1380:45d1:ec00::1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2978 (2.9K) [application/octet-stream]
Saving to: &#8216;systemd-hwe-hwdb_249.11.4_all.deb&#8217;

systemd-hwe-hwdb_24 100%[===================>]   2.91K  --.-KB/s    in 0s      

2023-12-18 17:59:56 (272 MB/s) - &#8216;systemd-hwe-hwdb_249.11.4_all.deb&#8217; saved [2978/2978]

```
That would download it to the current folder, where you would do
```

sudo dpkg -i systemd-hwe-hwdb_249.11.4_all.deb

```
to install it.

---

### Post by zacw001 on 2023-12-18
Thank you, mate.

I replaced [COLOR=#FF0000][FONT=Menlo]archive.ubuntu.com[/FONT][/COLOR][FONT=Menlo] with [/FONT][COLOR=#FF0000][FONT=Menlo]us.archive.ubuntu.com[/FONT][/COLOR][FONT=Menlo]. And replaced [COLOR=#FF0000]apt-get[/COLOR] with [COLOR=#FF0000]apt[/COLOR]. [/FONT][FONT=Menlo]Not sure why that works, but [/FONT][FONT=Menlo]the issue was fixed. 

[/FONT]> [COLOR=#3B3B3B][FONT=Menlo]sudo sed -i [COLOR=#A31515]'s|[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jammy-updates|[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy-updates|g'[/COLOR] /etc/apt/sources.list

sudo apt -y update
[/FONT][/COLOR]


---

