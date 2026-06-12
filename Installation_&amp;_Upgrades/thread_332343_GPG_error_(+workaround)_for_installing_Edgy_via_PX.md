---
title: "GPG error (+workaround) for installing Edgy via PXE netbooting &amp; a local HTTP server"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by dixonp on 2007-01-05
I got Edgy installed via PXE netbooting & a local HTTP server exporting the APT repository present on the ubuntu-6.10-alternate-i386.iso image, but I had to workaround an annoying bug in the installer. The repository was exported like this on the HTTP server:

```

$ mount -o ro,loop ubuntu-6.10-alternate-i386.iso /mnt
$ ln -s /var/www/ubuntu /mnt

```

So the client machine netbooted correctly, I chose the "server-expert" kernel, the installation procedure started without any pb, I selected [http://myserver/ubuntu](http://myserver/ubuntu) as the APT repository, and during the "installation of the base system" step, a generic error msg informed that it just failed. I saw this in /var/log/syslog:

```

Jan  5 23:17:46 debootstrap: Setting up udev (093-0ubuntu18) ...
Jan  5 23:17:46 debootstrap:
Jan  5 23:17:46 debootstrap: Setting up tasksel (2.50ubuntu7) ...
Jan  5 23:17:47 debootstrap:
Jan  5 23:17:47 debootstrap: Setting up pcmciautils (014-1ubuntu2) ...
Jan  5 23:17:47 debootstrap:
Jan  5 23:17:47 debootstrap: Setting up console-setup (1.7ubuntu19) ...
Jan  5 23:17:48 debootstrap: Your console configuration will be updated the next time your system boots.
Jan  5 23:17:48 debootstrap: If you want to update it now, run 'setupcon' from a virtual console.
Jan  5 23:17:48 debootstrap:
Jan  5 23:17:48 debootstrap: Setting up console-tools (0.2.3dbs-62ubuntu10) ...
Jan  5 23:17:49 debootstrap:
Jan  5 23:17:49 debootstrap: Setting up ubuntu-minimal (1.30) ...
Jan  5 23:17:50 base-installer: Get:1 [http://10.216.0.254](http://10.216.0.254) edgy Release.gpg [189B]
Jan  5 23:17:50 base-installer: Ign [http://10.216.0.254](http://10.216.0.254) edgy-updates Release.gpg
Jan  5 23:17:50 base-installer: Ign [http://10.216.0.254](http://10.216.0.254) edgy-security Release.gpg
Jan  5 23:17:50 base-installer: Hit [http://10.216.0.254](http://10.216.0.254) edgy Release
Jan  5 23:17:50 base-installer: Ign [http://10.216.0.254](http://10.216.0.254) edgy-updates Release
Jan  5 23:17:50 base-installer: Ign [http://10.216.0.254](http://10.216.0.254) edgy-security Release
Jan  5 23:17:50 base-installer: Get:2 [http://10.216.0.254](http://10.216.0.254) edgy Release [1874B]
Jan  5 23:17:50 base-installer: Ign [http://10.216.0.254](http://10.216.0.254) edgy Release
Jan  5 23:17:50 base-installer: Ign [http://10.216.0.254](http://10.216.0.254) edgy-updates/main Packages
Jan  5 23:17:50 base-installer: Ign [http://10.216.0.254](http://10.216.0.254) edgy-updates/restricted Packages
Jan  5 23:17:50 base-installer: Ign [http://10.216.0.254](http://10.216.0.254) edgy-security/main Packages
Jan  5 23:17:50 base-installer: Ign [http://10.216.0.254](http://10.216.0.254) edgy-security/restricted Packages
Jan  5 23:17:50 base-installer: Ign [http://10.216.0.254](http://10.216.0.254) edgy/main Packages
Jan  5 23:17:50 base-installer: Ign [http://10.216.0.254](http://10.216.0.254) edgy/restricted Packages
Jan  5 23:17:50 base-installer: Err [http://10.216.0.254](http://10.216.0.254) edgy-updates/main Packages
Jan  5 23:17:50 base-installer:   403 Forbidden
Jan  5 23:17:50 base-installer: Err [http://10.216.0.254](http://10.216.0.254) edgy-updates/restricted Packages
Jan  5 23:17:50 base-installer:   403 Forbidden
Jan  5 23:17:50 base-installer: Err [http://10.216.0.254](http://10.216.0.254) edgy-security/main Packages
Jan  5 23:17:50 base-installer:   403 Forbidden
Jan  5 23:17:50 base-installer: Err [http://10.216.0.254](http://10.216.0.254) edgy-security/restricted Packages
Jan  5 23:17:50 base-installer:   403 Forbidden
Jan  5 23:17:50 base-installer: Hit [http://10.216.0.254](http://10.216.0.254) edgy/main Packages
Jan  5 23:17:50 base-installer: Hit [http://10.216.0.254](http://10.216.0.254) edgy/restricted Packages
Jan  5 23:17:50 base-installer: Fetched 2063B in 0s (34.9kB/s)
Jan  5 23:17:50 base-installer: Reading package lists...
Jan  5 23:17:50 base-installer: Failed to fetch [http://10.216.0.254/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://10.216.0.254/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz)  403 Forbidden
Jan  5 23:17:50 base-installer: Failed to fetch [http://10.216.0.254/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://10.216.0.254/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz)  403 Forbidden
Jan  5 23:17:50 base-installer: Failed to fetch [http://10.216.0.254/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://10.216.0.254/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz)  403 Forbidden
Jan  5 23:17:50 base-installer: Failed to fetch [http://10.216.0.254/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://10.216.0.254/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz)  403 Forbidden
Jan  5 23:17:50 base-installer:
Jan  5 23:17:50 base-installer: W:
Jan  5 23:17:50 base-installer: GPG error: [http://10.216.0.254](http://10.216.0.254) edgy Release: The following signatures were invalid: NODATA 1 NODATA 2
Jan  5 23:17:50 base-installer:
Jan  5 23:17:50 base-installer: W:
Jan  5 23:17:50 base-installer: You may want to run apt-get update to correct these problems
Jan  5 23:17:50 base-installer:
Jan  5 23:17:50 base-installer: E:
Jan  5 23:17:50 base-installer: Some index files failed to download, they have been ignored, or old ones used instead.
Jan  5 23:17:50 base-installer:
Jan  5 23:17:50 base-installer: warning: apt update failed: 100
Jan  5 23:17:50 apt-install: Reading package lists...
Jan  5 23:17:50 apt-install: Building dependency tree...
Jan  5 23:17:50 apt-install:
Jan  5 23:17:50 apt-install: Recommended packages:
Jan  5 23:17:50 apt-install:   mail-transport-agent
Jan  5 23:17:50 apt-install: The following NEW packages will be installed:
Jan  5 23:17:50 apt-install:   mdadm
Jan  5 23:17:50 apt-install: 0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Jan  5 23:17:50 apt-install: Need to get 152kB of archives.
Jan  5 23:17:50 apt-install: After unpacking 463kB of additional disk space will be used.
Jan  5 23:17:50 apt-install: WARNING: The following packages cannot be authenticated!
Jan  5 23:17:50 apt-install:   mdadm
Jan  5 23:17:50 apt-install: E: There are problems and -y was used without --force-yes
Jan  5 23:17:50 main-menu[2723]: WARNING **: Configuring 'base-installer' failed with error code 1
Jan  5 23:17:50 main-menu[2723]: WARNING **: Menu item 'base-installer' failed.

```

The first pb I notice is that the installer tries to access 3 directories: edgy, edgy-updates and edgy-security. But on ubuntu-6.10-alternate-i386.iso, only edgy (and stable, unstable) exists:

```

$ ls /mnt/dists/
edgy  stable  unstable

```

(By the way my webserver was returning 403s instead of 404s for these non-existent directories, but I don't think changing the config to make it return traditional 404s should have changed anything.) Anyway it seems that the fact that edgy-updates and edgy-security are missing isn't a fatal error, so the installer just ignores these missing directories and continues. Then there is this GPG error:

```

GPG error: [http://10.216.0.254](http://10.216.0.254) edgy Release: The following signatures were invalid: NODATA 1 NODATA 2

```

To me this makes no sense because the edgy/Release.gpg signature file for the edgy/Release file has been downloaded correctly, as it can be seen a couple of lines before the GPG error:

```

Get:1 [http://10.216.0.254](http://10.216.0.254) edgy Release.gpg [189B]

```

Even the indicated size of 189 bytes is correct, for the record here is its content:

```

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.1 (GNU/Linux)

iD8DBQBFP2z4RhgUM/u3VFERAuxEAJ9zGjkBDdCuQScy2IHLosHbs7PTHwCfU10a
o44i1NnHBgK4VO1siYRi178=
=BWpo
-----END PGP SIGNATURE-----

```

The above GPG error is then causing the authentication of the mdadm pkg to fail (I was using software raid):

```

Jan  5 23:17:50 apt-install: WARNING: The following packages cannot be authenticated!
Jan  5 23:17:50 apt-install:   mdadm
Jan  5 23:17:50 apt-install: E: There are problems and -y was used without --force-yes
Jan  5 23:17:50 main-menu[2723]: WARNING **: Configuring 'base-installer' failed with error code 1
Jan  5 23:17:50 main-menu[2723]: WARNING **: Menu item 'base-installer' failed.

```

To make it work, I had to (in a shell while the base-installer was running):

```

$ echo 'APT::Get::AllowUnauthenticated "true";' >>/target/etc/apt/apt.conf

```

To me it seems a bug in the way the Release.gpg files are downloaded. Even though edgy/Release.gpg can be downloaded, the fact that edgy-updates/Release.gpg and edgy-security/Release.gpg are missing causes GPG to barf out and **TOTALLY IGNORE** the successfuly downloaded edgy/Release.gpg, therefore preventing **ALL** packages from being authenticated (even the ones that could be authenticated by edgy/Release.gpg).

Is this a known pb ?
Is there a way to tell the installer "don't even bother to try to download edgy-updates and edgy-security" ?

---

### Post by Big_Bob on 2007-01-24
First of all, thanks dixonp for the information provided. After some lengthy trials I have found out, that if you start install with "-y --force-yes" switches, you don't need to modify apt.conf during the install.
I would also like to add my 2 cents for ppl trying this kind of install. My problem was, that I only had access to Windows machine to work as DHCP, TFTP and HTTP server to provide PXE booting and serving the repository.
DHCP/TFTP was no problem with tftpd32.exe, but the HTTP proved, that only Apache was able to provide necessary performance. I've tried several small and simple web servers for Windows, and while they worked (sort of), installation never came through because of timeouts, 404s, etc.
So if someone wants to do a PXE netboot and local HTTP install from Windows only, here's what you need:

[[COLOR="Blue"]tftpd32[/COLOR]]("http://tftpd32.jounin.net/download/tftpd32.303.zip")
[[COLOR="Blue"]Apache for Windows[/COLOR]]("http://httpd.apache.org/download.cgi") (Win32 binary)
ubuntu-6.10-alternate-i386.iso

When configuring DHCP (in tftpd32), do NOT provide default gateway address, otherwise the installer will try to get some package descriptions from the Internet and installation will fail.

When you successfully booted and get the boot prompt enter:

install -y --force-yes

and from there it's installation as usual.

---

### Post by dixonp on 2007-01-25
Thanks for the tip Big_Bob. I really would prefer seeing this installer bug fixed instead, but at least your workaround is more convenient than mine :D

---

### Post by SwissSign_Operations on 2007-08-30
No, this don't works! 
choose-mirror tries with or without route to fetch archive.ubuntu.com/ubuntu/dists/dapper/Release.

I have 3 Install servers, and at one of it I cannot to NAT the name resolution for the intall-client. There can I not to install my machines! This behavior ist hard-coded into /bin/choose-mirror binary!


###
preseed file:

d-i mirror/http/hostname string 10.110.22.20
d-i mirror/http/directory string /ubuntu
d-i mirror/suite string dapper

d-i mirror/http/proxy   string

d-i clock-setup/utc boolean true

d-i time/zone string Europe/Zurich

d-i apt-setup/security_host [http://10.110.22.20](http://10.110.22.20)

d-i apt-setup/local0/repository string http:/10.110.22.20/ubuntu/SwissSign dapper main

d-i pkgsel/install-pattern ~t^ubuntu-standard$

d-i finish-install/reboot_in_progress note
###

---

