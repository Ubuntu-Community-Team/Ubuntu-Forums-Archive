---
title: "Unattended upgrades doesn´t work on Ubuntu 22.04.3"
date: 2024-03-12
forum: Installation &amp; Upgrades
---

### Post by magarpol on 2024-03-12
Hi all, I have the following system on which the unattended upgrades doesn´t work:

OS: Ubuntu 22.04.3
kernel: 5.15.0-89-generic

**50-unattended-upgrades** file:
```

Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}";
        "${distro_id}:${distro_codename}-security";
        // Extended Security Maintenance; doesn't necessarily exist for
        // every release and this system may not have it installed, but if
        // available, the policy for updates is such that unattended-upgrades
        // should also install from here by default.
        "${distro_id}ESMApps:${distro_codename}-apps-security";
        "${distro_id}ESM:${distro_codename}-infra-security";
//      "${distro_id}:${distro_codename}-updates";
//      "${distro_id}:${distro_codename}-proposed";
//      "${distro_id}:${distro_codename}-backports";

};

// List of packages to not update (regexp are supported)
Unattended-Upgrade::Package-Blacklist {
//      "vim";
//      "libc6";
//      "libc6-dev";
//      "libc6-i686";
};


```

 **20-auto-upgrades** file:
```

APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Unattended-Upgrade "1";

```

[B]apt list --upgradable
[/B]```

base-files/jammy-updates 12ubuntu4.6 amd64 [upgradable from: 12ubuntu4.4]
containerd.io/jammy 1.6.28-1 amd64 [upgradable from: 1.6.26-1]
coreutils/jammy-updates 8.32-4.1ubuntu1.1 amd64 [upgradable from: 8.32-4.1ubuntu1]
dns-root-data/jammy-updates,jammy-updates 2023112702~ubuntu0.22.04.1 all [upgradable from: 2021011101]
docker-buildx-plugin/jammy 0.13.0-1~ubuntu.22.04~jammy amd64 [upgradable from: 0.11.2-1~ubuntu.22.04~jammy]
docker-ce-cli/jammy 5:25.0.4-1~ubuntu.22.04~jammy amd64 [upgradable from: 5:24.0.7-1~ubuntu.22.04~jammy]
docker-ce-rootless-extras/jammy 5:25.0.4-1~ubuntu.22.04~jammy amd64 [upgradable from: 5:24.0.7-1~ubuntu.22.04~jammy]
docker-ce/jammy 5:25.0.4-1~ubuntu.22.04~jammy amd64 [upgradable from: 5:24.0.7-1~ubuntu.22.04~jammy]
docker-compose-plugin/jammy 2.24.7-1~ubuntu.22.04~jammy amd64 [upgradable from: 2.21.0-1~ubuntu.22.04~jammy]
dpkg/jammy-updates 1.21.1ubuntu2.3 amd64 [upgradable from: 1.21.1ubuntu2.2]
firmware-sof-signed/jammy-updates,jammy-updates 2.0-1ubuntu4.5 all [upgradable from: 2.0-1ubuntu4.4]
iptables/jammy-updates 1.8.7-1ubuntu5.2 amd64 [upgradable from: 1.8.7-1ubuntu5.1]
language-pack-en-base/jammy-updates,jammy-updates 1:22.04+20240212 all [upgradable from: 1:22.04+20230801]
language-pack-en/jammy-updates,jammy-updates 1:22.04+20240212 all [upgradable from: 1:22.04+20230801]
libcups2/jammy-updates 2.4.1op1-1ubuntu4.8 amd64 [upgradable from: 2.4.1op1-1ubuntu4.7]
libgpgme11/jammy-updates 1.16.0-1.2ubuntu4.2 amd64 [upgradable from: 1.16.0-1.2ubuntu4.1]
libip4tc2/jammy-updates 1.8.7-1ubuntu5.2 amd64 [upgradable from: 1.8.7-1ubuntu5.1]
libip6tc2/jammy-updates 1.8.7-1ubuntu5.2 amd64 [upgradable from: 1.8.7-1ubuntu5.1]
libiptc0/jammy-updates 1.8.7-1ubuntu5.2 amd64 [upgradable from: 1.8.7-1ubuntu5.1]
liblxc-common/jammy-updates 1:5.0.0~git2209-g5a7b9ce67-0ubuntu1.1 amd64 [upgradable from: 1:5.0.0~git2209-g5a7b9ce67-0ubuntu1]
liblxc1/jammy-updates 1:5.0.0~git2209-g5a7b9ce67-0ubuntu1.1 amd64 [upgradable from: 1:5.0.0~git2209-g5a7b9ce67-0ubuntu1]
libmm-glib0/jammy-updates 1.20.0-1~ubuntu22.04.3 amd64 [upgradable from: 1.20.0-1~ubuntu22.04.2]
libnss-systemd/jammy-updates 249.11-0ubuntu3.12 amd64 [upgradable from: 249.11-0ubuntu3.11]
libpam-systemd/jammy-updates 249.11-0ubuntu3.12 amd64 [upgradable from: 249.11-0ubuntu3.11]
libsystemd0/jammy-updates 249.11-0ubuntu3.12 amd64 [upgradable from: 249.11-0ubuntu3.11]
libudev1/jammy-updates 249.11-0ubuntu3.12 amd64 [upgradable from: 249.11-0ubuntu3.11]
libxtables12/jammy-updates 1.8.7-1ubuntu5.2 amd64 [upgradable from: 1.8.7-1ubuntu5.1]
linux-firmware/jammy-updates,jammy-updates 20220329.git681281e4-0ubuntu3.29 all [upgradable from: 20220329.git681281e4-0ubuntu3.23]
ltrace/jammy-updates 0.7.3-6.1ubuntu6.22.04.1 amd64 [upgradable from: 0.7.3-6.1ubuntu6]
modemmanager/jammy-updates 1.20.0-1~ubuntu22.04.3 amd64 [upgradable from: 1.20.0-1~ubuntu22.04.2]
motd-news-config/jammy-updates,jammy-updates 12ubuntu4.6 all [upgradable from: 12ubuntu4.4]
open-vm-tools/jammy-updates 2:12.3.5-3~ubuntu0.22.04.1 amd64 [upgradable from: 2:12.1.5-3~ubuntu0.22.04.4]
python-apt-common/jammy-updates,jammy-updates 2.4.0ubuntu3 all [upgradable from: 2.4.0ubuntu2]
python3-apt/jammy-updates 2.4.0ubuntu3 amd64 [upgradable from: 2.4.0ubuntu2]
python3-distupgrade/jammy-updates,jammy-updates 1:22.04.19 all [upgradable from: 1:22.04.17]
python3-gpg/jammy-updates 1.16.0-1.2ubuntu4.2 amd64 [upgradable from: 1.16.0-1.2ubuntu4.1]
python3-update-manager/jammy-updates,jammy-updates 1:22.04.18 all [upgradable from: 1:22.04.10]
systemd-hwe-hwdb/jammy-updates,jammy-updates 249.11.5 all [upgradable from: 249.11.4]
systemd-sysv/jammy-updates 249.11-0ubuntu3.12 amd64 [upgradable from: 249.11-0ubuntu3.11]
systemd/jammy-updates 249.11-0ubuntu3.12 amd64 [upgradable from: 249.11-0ubuntu3.11]
tcpdump/jammy-updates 4.99.1-3ubuntu0.2 amd64 [upgradable from: 4.99.1-3ubuntu0.1]
ubuntu-release-upgrader-core/jammy-updates,jammy-updates 1:22.04.19 all [upgradable from: 1:22.04.17]
udev/jammy-updates 249.11-0ubuntu3.12 amd64 [upgradable from: 249.11-0ubuntu3.11]
update-manager-core/jammy-updates,jammy-updates 1:22.04.18 all [upgradable from: 1:22.04.10]

```
any ideas on what´s happening? many thanks for the replies.

---

### Post by ian-weisser on 2024-03-12
Your Unattended Upgrades settings show the default setting: ONLY security upgrades from the Ubuntu repos and nothing else.

Your list of available upgrades does not seem to show any of those.  That list is all non-security bugfixes OR non-Ubuntu.

So the result would seem to be appropriate. Unattended Upgrades is handling what it's set to handle.

Did you want different settings? If so, what?

---

### Post by magarpol on 2024-03-13
> **ian-weisser said:**
> Your Unattended Upgrades settings show the default setting: ONLY security upgrades from the Ubuntu repos and nothing else.

Your list of available upgrades does not seem to show any of those.  That list is all non-security bugfixes OR non-Ubuntu.

So the result would seem to be appropriate. Unattended Upgrades is handling what it's set to handle.

Did you want different settings? If so, what?

Thanks for your reply.

I managed to find the main problem by adding another line for available upgrades. Now the **apt list --upgradable** looks like this:

```

Listing... Done
containerd.io/jammy 1.6.28-1 amd64 [upgradable from: 1.6.26-1]
docker-buildx-plugin/jammy 0.13.0-1~ubuntu.22.04~jammy amd64 [upgradable from: 0.11.2-1~ubuntu.22.04~jammy]
docker-ce-cli/jammy 5:25.0.4-1~ubuntu.22.04~jammy amd64 [upgradable from: 5:24.0.7-1~ubuntu.22.04~jammy]
docker-ce-rootless-extras/jammy 5:25.0.4-1~ubuntu.22.04~jammy amd64 [upgradable from: 5:24.0.7-1~ubuntu.22.04~jammy]
docker-ce/jammy 5:25.0.4-1~ubuntu.22.04~jammy amd64 [upgradable from: 5:24.0.7-1~ubuntu.22.04~jammy]
docker-compose-plugin/jammy 2.24.7-1~ubuntu.22.04~jammy amd64 [upgradable from: 2.21.0-1~ubuntu.22.04~jammy]

```

Somehow I can´t find a way to unattended those Docker upgrades. I tried with:

```

"origin=Docker,codename=${distro_codename},label=Docker CE";

```

but it does nothing, so I don´t know what I´m missing with that.

---

### Post by deadflowr on 2024-03-13
You need the correct origin and suite entries
You can find those in the InRelease file for the repository in the /var/lib/apt/lists directory.

They must be separated by a colon enclosed in quotes. and end with a semicolon.
Properly something like
```
"ubuntu:jammy";
```
It has to be the exact origin name as shown in the InRelease file.

An example if you installed brave browser's repo and wanted to it run to unattended-upgrade updates,
it's origin is Brave Software and it's suite is stable so it's entry would be
```
"Brave Software:stable";
```

You'll have to find your Docker repo info yourself.

Good luck

---

### Post by ian-weisser on 2024-03-13
See [https://askubuntu.com/a/1286233/19626](https://askubuntu.com/a/1286233/19626) for how to figure out the correct Origin and Section.

I wrote it back in 2020, and it's still the same.

---

### Post by magarpol on 2024-03-15
> **ian-weisser said:**
> See [https://askubuntu.com/a/1286233/19626](https://askubuntu.com/a/1286233/19626) for how to figure out the correct Origin and Section.

I wrote it back in 2020, and it's still the same.

Amazing guide, thanks a lot.

However the Ubuntu 22 that I´m working with doesn´t have the file:

```
/etc/apt/sources.list.d/icinga-main-focal.list
```

but I managed to find something similar, or the same, but in another location here:

```
ls -l /var/lib/apt/lists/ | grep docker
-rw-r--r-- 1 root root    48847 Mar 12 11:15 download.docker.com_linux_ubuntu_dists_jammy_InRelease
-rw-r--r-- 1 root root   191332 Mar  7 20:43 download.docker.com_linux_ubuntu_dists_jammy_stable_binary-amd64_Packages
```

```
cat /var/lib/apt/lists/download.docker.com_linux_ubuntu_dists_jammy_InRelease | grep Origin
Origin: Docker
```

However I´m struggling to find the right section to it as there are spaces after the URL:

```
cat /etc/apt/sources.list | grep docker
deb [arch=amd64] https://download.docker.com/linux/ubuntu jammy stable
# deb-src [arch=amd64] https://download.docker.com/linux/ubuntu jammy stable
```

So this doesn´t work:

```
 "${distro_id}Docker:${distro_codename}-jammy stable"; 
```

---

### Post by ian-weisser on 2024-03-15
If the Origin is "Docker", then the Origin is not "${distro_id}Docker"

---

### Post by magarpol on 2024-03-18
> **ian-weisser said:**
> If the Origin is "Docker", then the Origin is not "${distro_id}Docker"

Thanks again for your reply, I think I´m clearly not understanding how to compose the new line, I tried the following, separately:

```

"${distro_id}:${distro_codename}-Docker:jammy stable";
"${distro_id}:${distro_codename}Docker:jammy stable";
"${distro_id}:${distro_codename} Docker:jammy stable";
"${distro_id}Docker:jammy stable${distro_codename}";

```

But none of them works, when I ran **unattended upgrades --dry -debug** it throws a lot of errors.

---

### Post by deadflowr on 2024-03-18
You need to cut the $distro parts, those are internal reference shorthands that are referencing the current distro's information.
Useless for when adding an external repository.
You only need the Docker:Suite part

In the end it should all look something like this
```
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}";
        "${distro_id}:${distro_codename}-security";
        // Extended Security Maintenance; doesn't necessarily exist for
        // every release and this system may not have it installed, but if
        // available, the policy for updates is such that unattended-upgrades
        // should also install from here by default.
        "${distro_id}ESMApps:${distro_codename}-apps-security";
        "${distro_id}ESM:${distro_codename}-infra-security";
//      "${distro_id}:${distro_codename}-updates";
//      "${distro_id}:${distro_codename}-proposed";
//      "${distro_id}:${distro_codename}-backports";
         [B]"Docker:stable";
[/B]
};
```

assuming that the suite is stable.
You can double check that with
```
grep Suite: /var/lib/apt/lists/download.docker.com_linux_ubuntu_dists_jammy_InRelease
```

---

