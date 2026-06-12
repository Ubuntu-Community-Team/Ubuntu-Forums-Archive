---
title: "Lot's of 403 Forbidden this morning using apt"
date: 2016-02-26
forum: Installation &amp; Upgrades
---

### Post by DigiAngel on 2016-02-26
Topic says it....very strange:
```
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://ppa.launchpad.net trusty InRelease
Ign http://www.inetsim.org binary/ InRelease
Ign http://extras.ubuntu.com trusty InRelease
Ign http://security.ubuntu.com trusty-security Release.gpg
Ign http://packages.elasticsearch.org stable InRelease
Ign http://ppa.launchpad.net trusty InRelease
Ign http://www.inetsim.org binary/ Release.gpg
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://extras.ubuntu.com trusty Release.gpg
Ign http://security.ubuntu.com trusty-security Release
Ign http://packages.elasticsearch.org stable InRelease
Ign http://ppa.launchpad.net trusty InRelease
Ign http://www.inetsim.org binary/ Release
Ign http://extras.ubuntu.com trusty Release
Ign http://us.archive.ubuntu.com trusty-updates InRelease
Ign http://security.ubuntu.com trusty-security/main Sources/DiffIndex
Ign http://packages.elasticsearch.org stable Release.gpg
Ign http://ppa.launchpad.net trusty InRelease
Ign http://www.inetsim.org binary/ Packages/DiffIndex
Ign http://extras.ubuntu.com trusty/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com trusty-backports InRelease
Ign http://download.draios.com stable-amd64/ InRelease
Ign http://ppa.launchpad.net trusty Release.gpg
Ign http://extras.ubuntu.com trusty/main amd64 Packages/DiffIndex
Ign http://packages.elasticsearch.org stable Release.gpg
Ign http://us.archive.ubuntu.com trusty Release.gpg
Ign http://security.ubuntu.com trusty-security/restricted Sources/DiffIndex
Ign http://download.draios.com stable-amd64/ Release.gpg
Ign http://ppa.launchpad.net trusty Release.gpg
Ign http://extras.ubuntu.com trusty/main i386 Packages/DiffIndex
Ign http://packages.elasticsearch.org stable Release
Ign http://security.ubuntu.com trusty-security/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com trusty-updates Release.gpg
Ign http://ppa.launchpad.net trusty Release.gpg
Ign http://download.draios.com stable-amd64/ Release
Ign http://packages.elasticsearch.org stable Release
Ign http://security.ubuntu.com trusty-security/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com trusty-backports Release.gpg
Ign http://download.draios.com stable-amd64/ Packages/DiffIndex
Ign http://ppa.launchpad.net trusty Release.gpg
Ign http://us.archive.ubuntu.com trusty Release
Ign http://security.ubuntu.com trusty-security/main amd64 Packages/DiffIndex
Ign http://packages.elasticsearch.org stable/main amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net trusty Release
Ign http://us.archive.ubuntu.com trusty-updates Release
Ign http://security.ubuntu.com trusty-security/restricted amd64 Packages/DiffIndex
Ign http://packages.elasticsearch.org stable/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net trusty Release
Ign http://us.archive.ubuntu.com trusty-backports Release
Ign http://security.ubuntu.com trusty-security/universe amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net trusty Release
Ign http://us.archive.ubuntu.com trusty/main Sources/DiffIndex
Ign http://security.ubuntu.com trusty-security/multiverse amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net trusty Release
Ign http://us.archive.ubuntu.com trusty/restricted Sources/DiffIndex
Ign http://packages.elasticsearch.org stable/main amd64 Packages/DiffIndex
Ign http://security.ubuntu.com trusty-security/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty/universe Sources/DiffIndex
Ign http://security.ubuntu.com trusty-security/restricted i386 Packages/DiffIndex
Ign http://packages.elasticsearch.org stable/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty/multiverse Sources/DiffIndex
Ign http://security.ubuntu.com trusty-security/universe i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty/main amd64 Packages/DiffIndex
Ign http://security.ubuntu.com trusty-security/multiverse i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty/restricted amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex
Ign http://www.inetsim.org binary/ Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex
Ign http://www.inetsim.org binary/ Translation-en
Ign http://us.archive.ubuntu.com trusty/multiverse amd64 Packages/DiffIndex
Err http://www.inetsim.org binary/ Packages
  403  Forbidden
Ign http://us.archive.ubuntu.com trusty/main i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty/restricted i386 Packages/DiffIndex
Ign http://download.draios.com stable-amd64/ Translation-en_US
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty/universe i386 Packages/DiffIndex
Ign http://download.draios.com stable-amd64/ Translation-en
Ign http://us.archive.ubuntu.com trusty/multiverse i386 Packages/DiffIndex
Err http://download.draios.com stable-amd64/ Packages
  403  Forbidden
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex
Ign http://extras.ubuntu.com trusty/main Translation-en_US
Ign http://extras.ubuntu.com trusty/main Translation-en
Err http://extras.ubuntu.com trusty/main Sources
  403  Forbidden [IP: 91.189.92.152 80]
Ign http://us.archive.ubuntu.com trusty-updates/main Sources/DiffIndex
Err http://extras.ubuntu.com trusty/main amd64 Packages
  403  Forbidden [IP: 91.189.92.152 80]
Ign http://us.archive.ubuntu.com trusty-updates/restricted Sources/DiffIndex
Err http://extras.ubuntu.com trusty/main i386 Packages
  403  Forbidden [IP: 91.189.92.152 80]
Ign http://us.archive.ubuntu.com trusty-updates/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com trusty-updates/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com trusty-updates/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty-updates/main i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty-updates/universe i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages/DiffIndex
Ign http://packages.elasticsearch.org stable/main Translation-en_US
Ign http://packages.elasticsearch.org stable/main Translation-en
Ign http://packages.elasticsearch.org stable/main Translation-en_US
Ign http://packages.elasticsearch.org stable/main Translation-en
Err http://packages.elasticsearch.org stable/main amd64 Packages
  403  Forbidden [IP: 184.73.173.133 80]
Err http://packages.elasticsearch.org stable/main i386 Packages
  403  Forbidden [IP: 184.73.173.133 80]
Err http://packages.elasticsearch.org stable/main amd64 Packages
  403  Forbidden [IP: 184.73.173.133 80]
Err http://packages.elasticsearch.org stable/main i386 Packages
  403  Forbidden [IP: 184.73.173.133 80]
Ign http://us.archive.ubuntu.com trusty-backports/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com trusty-backports/restricted Sources/DiffIndex
Ign http://us.archive.ubuntu.com trusty-backports/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com trusty-backports/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com trusty-backports/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty-backports/main i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty-backports/universe i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages/DiffIndex
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Err http://ppa.launchpad.net trusty/main amd64 Packages
  403  Forbidden
Err http://ppa.launchpad.net trusty/main i386 Packages
  403  Forbidden
Err http://ppa.launchpad.net trusty/main amd64 Packages
  403  Forbidden
Err http://ppa.launchpad.net trusty/main i386 Packages
  403  Forbidden
Err http://ppa.launchpad.net trusty/main amd64 Packages
  403  Forbidden
Ign http://security.ubuntu.com trusty-security/main Translation-en_US
Ign http://security.ubuntu.com trusty-security/main Translation-en
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US
Err http://ppa.launchpad.net trusty/main i386 Packages
  403  Forbidden
Ign http://security.ubuntu.com trusty-security/restricted Translation-en
Err http://ppa.launchpad.net trusty/main amd64 Packages
  403  Forbidden
Ign http://security.ubuntu.com trusty-security/universe Translation-en_US
Err http://ppa.launchpad.net trusty/main i386 Packages
  403  Forbidden
Ign http://security.ubuntu.com trusty-security/universe Translation-en
Err http://security.ubuntu.com trusty-security/main Sources
  403  Forbidden [IP: 91.189.91.15 80]
Err http://security.ubuntu.com trusty-security/restricted Sources
  403  Forbidden [IP: 91.189.91.15 80]
Err http://security.ubuntu.com trusty-security/universe Sources
  403  Forbidden [IP: 91.189.91.15 80]
Err http://security.ubuntu.com trusty-security/multiverse Sources
  403  Forbidden [IP: 91.189.91.15 80]
Err http://security.ubuntu.com trusty-security/main amd64 Packages
  403  Forbidden [IP: 91.189.91.15 80]
Err http://security.ubuntu.com trusty-security/restricted amd64 Packages
  403  Forbidden [IP: 91.189.91.15 80]
Err http://security.ubuntu.com trusty-security/universe amd64 Packages
  403  Forbidden [IP: 91.189.91.15 80]
Err http://security.ubuntu.com trusty-security/multiverse amd64 Packages
  403  Forbidden [IP: 91.189.91.15 80]
Err http://security.ubuntu.com trusty-security/main i386 Packages
  403  Forbidden [IP: 91.189.91.15 80]
Ign https://apt.dockerproject.org ubuntu-trusty InRelease
Err http://security.ubuntu.com trusty-security/restricted i386 Packages
  403  Forbidden [IP: 91.189.91.15 80]
Err http://security.ubuntu.com trusty-security/universe i386 Packages
  403  Forbidden [IP: 91.189.91.15 80]
Err http://security.ubuntu.com trusty-security/multiverse i386 Packages
  403  Forbidden [IP: 91.189.91.15 80]
Ign https://apt.dockerproject.org ubuntu-trusty Release.gpg
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/main Translation-en
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en
Ign https://apt.dockerproject.org ubuntu-trusty Release
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en
Ign http://us.archive.ubuntu.com trusty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty-updates/main Translation-en
Ign http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com trusty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com trusty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Ign http://us.archive.ubuntu.com trusty-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/main Translation-en
Ign http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Ign http://us.archive.ubuntu.com trusty-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com trusty-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Err http://us.archive.ubuntu.com trusty/main Sources
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty/restricted Sources
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty/universe Sources
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty/multiverse Sources
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty/main amd64 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty/restricted amd64 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty/universe amd64 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty/main i386 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty/restricted i386 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty/universe i386 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty/multiverse i386 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-updates/main Sources
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-updates/restricted Sources
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-updates/universe Sources
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-updates/multiverse Sources
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-updates/main amd64 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-updates/main i386 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-updates/universe i386 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-backports/main Sources
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-backports/restricted Sources
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-backports/universe Sources
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-backports/multiverse Sources
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-backports/main i386 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Ign https://apt.dockerproject.org ubuntu-trusty/main amd64 Packages/DiffIndex
Err http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-backports/universe i386 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
  403  Forbidden [IP: 91.189.91.23 80]
Ign https://apt.dockerproject.org ubuntu-trusty/main i386 Packages/DiffIndex
Ign https://apt.dockerproject.org ubuntu-trusty/main Translation-en_US
Ign https://apt.dockerproject.org ubuntu-trusty/main Translation-en
Err https://apt.dockerproject.org ubuntu-trusty/main amd64 Packages
  gnutls_handshake() failed: A TLS packet with unexpected length was received.
Err https://apt.dockerproject.org ubuntu-trusty/main i386 Packages
  gnutls_handshake() failed: A TLS packet with unexpected length was received.
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/main/source/Sources  403  Forbidden [IP: 91.189.91.15 80]

W: Failed to fetch http://www.inetsim.org/debian/binary/Packages  403  Forbidden

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources  403  Forbidden [IP: 91.189.92.152 80]

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages  403  Forbidden [IP: 91.189.92.152 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/source/Sources  403  Forbidden [IP: 91.189.91.15 80]

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages  403  Forbidden [IP: 91.189.92.152 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/source/Sources  403  Forbidden [IP: 91.189.91.15 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/source/Sources  403  Forbidden [IP: 91.189.91.15 80]

W: Failed to fetch http://download.draios.com/stable/deb/stable-amd64/Packages  403  Forbidden

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/main/binary-amd64/Packages  403  Forbidden [IP: 91.189.91.15 80]

W: Failed to fetch http://packages.elasticsearch.org/elasticsearch/1.5/debian/dists/stable/main/binary-amd64/Packages  403  Forbidden [IP: 184.73.173.133 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/binary-amd64/Packages  403  Forbidden [IP: 91.189.91.15 80]

W: Failed to fetch http://packages.elasticsearch.org/elasticsearch/1.5/debian/dists/stable/main/binary-i386/Packages  403  Forbidden [IP: 184.73.173.133 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/binary-amd64/Packages  403  Forbidden [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/binary-amd64/Packages  403  Forbidden [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/source/Sources  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://packages.elasticsearch.org/logstash/1.5/debian/dists/stable/main/binary-amd64/Packages  403  Forbidden [IP: 184.73.173.133 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/main/binary-i386/Packages  403  Forbidden [IP: 91.189.91.15 80]

W: Failed to fetch http://ppa.launchpad.net/gift/stable/ubuntu/dists/trusty/main/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/binary-i386/Packages  403  Forbidden [IP: 91.189.91.15 80]

W: Failed to fetch http://packages.elasticsearch.org/logstash/1.5/debian/dists/stable/main/binary-i386/Packages  403  Forbidden [IP: 184.73.173.133 80]

W: Failed to fetch http://ppa.launchpad.net/gift/stable/ubuntu/dists/trusty/main/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/source/Sources  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/binary-i386/Packages  403  Forbidden [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/binary-i386/Packages  403  Forbidden [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-amd64/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://ppa.launchpad.net/remnux/stable/ubuntu/dists/trusty/main/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-amd64/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://ppa.launchpad.net/remnux/stable/ubuntu/dists/trusty/main/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-amd64/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-i386/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://ppa.launchpad.net/sift/stable/ubuntu/dists/trusty/main/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-i386/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-i386/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://ppa.launchpad.net/sift/stable/ubuntu/dists/trusty/main/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/source/Sources  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/source/Sources  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/source/Sources  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-amd64/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-amd64/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-i386/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-i386/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/source/Sources  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/source/Sources  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/source/Sources  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/source/Sources  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-amd64/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-amd64/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-amd64/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-amd64/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-i386/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-i386/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-i386/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-i386/Packages  403  Forbidden [IP: 91.189.91.23 80]

W: Failed to fetch https://apt.dockerproject.org/repo/dists/ubuntu-trusty/main/binary-amd64/Packages  gnutls_handshake() failed: A TLS packet with unexpected length was received.

W: Failed to fetch https://apt.dockerproject.org/repo/dists/ubuntu-trusty/main/binary-i386/Packages  gnutls_handshake() failed: A TLS packet with unexpected length was received.

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Is this a mirror issue or something else?  Thanks for any help.

---

### Post by Frogs Hair on 2016-02-26
I have experienced a failure to connect to Ubuntu servers once or twice and  would try again later.  Another option open Software & Updates>Ubuntu Software and change sever settings.

---

