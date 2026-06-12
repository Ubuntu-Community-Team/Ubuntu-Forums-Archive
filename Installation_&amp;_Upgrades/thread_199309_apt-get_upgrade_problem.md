---
title: "apt-get upgrade problem"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by shalinmangar on 2006-06-18
I've been trying to upgrade packages through apt-get and for the last few days, I can't download the updated packages. I have tried reloading the repositories and I have no trouble browsing the net or downloading other stuff. But all apt-get upgrades are failing with the following message:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.8.18-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.8.18-0ubuntu1_i386.deb)
  Bad header line [IP: 85.133.25.7 80]

And so on...

I am using Ubuntu 6.06 with both gnome and kde installed. Is anybody else experiencing the same thing? Any workarounds?

*Sorry if I am posting in the wrong forum. I am a newbie in these forums.*

---

### Post by linuchsan on 2006-06-18
try this: sudo apt-get update -o Debug::Acquire::http=true
What does it say?

---

### Post by shalinmangar on 2006-06-18
Here is the complete output from your given command:

[SIZE="1"]Ign file: dapper Release.gpg
Ign file: dapper Release
Ign file: dapper/main Packages
Ign file: dapper/restricted Packages
Err file: dapper/main Packages
  File not found
Err file: dapper/restricted Packages
  File not found
44% [Connecting to archive.ubuntu.com (85.133.25.7)]GET /ubuntu/dists/dapper/Release.gpg HTTP/1.1
Host: archive.ubuntu.com
Connection: keep-alive
Range: bytes=188-
If-Range: Wed, 31 May 2006 19:02:10 GMT
User-Agent: Debian APT-HTTP/1.3


GET /ubuntu/dists/dapper-updates/Release.gpg HTTP/1.1
Host: archive.ubuntu.com
Connection: keep-alive
Range: bytes=188-
If-Range: Sun, 18 Jun 2006 18:36:06 GMT
User-Agent: Debian APT-HTTP/1.3


44% [Waiting for headers]HTTP/1.1 206 Partial Content
Age: 382795
Accept-Ranges: bytes
Content-Range: bytes 188-188/189
Date: Wed, 14 Jun 2006 17:33:18 GMT
Content-Length: 1
Content-Type: text/plain; charset=UTF-8
Warning: 113 netcache "Heuristic expiration"
Server: Apache/2.0.54 (Ubuntu)
Last-Modified: Wed, 31 May 2006 19:02:10 GMT
ETag: "c14545-bd-4151a3044f080"
Via: 1.1 netcache (NetCache NetApp/6.0.2)

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
97% [Waiting for headers]-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.1 (GNU/Linux)

Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
97% [Working]GET /ubuntu/dists/dapper/Release HTTP/1.1
Host: archive.ubuntu.com
Connection: keep-alive
If-Modified-Since: Wed, 31 May 2006 19:02:10 GMT
User-Agent: Debian APT-HTTP/1.3


97% [Waiting for headers]iD8DBQBElhutQJdur0N9BbURAtvBAJ9toDRS9r8eaefGZeF0gLtfHMf75gCgozvH
Bg0sxu9OKy9a62m7G9vhut8=
=3Nij
-----END PGP SIGNATURE-----
HTTP/1.1 304 Not Modified
Etag: "c14544-87be-4151a256bd700"
Date: Fri, 16 Jun 2006 16:21:07 GMT
Warning: 113 netcache "Heuristic expiration"

Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
96% [Working]GET /ubuntu/dists/dapper-updates/Release HTTP/1.1
Host: archive.ubuntu.com
Connection: keep-alive
If-Modified-Since: Sun, 18 Jun 2006 18:36:06 GMT
User-Agent: Debian APT-HTTP/1.3


96% [Waiting for headers]HTTP/1.1 200 OK
Age: 31
Date: Mon, 19 Jun 2006 03:52:45 GMT
Content-Length: 30903
Content-Type: text/plain; charset=UTF-8
Server: Apache/2.0.54 (Ubuntu)
Last-Modified: Mon, 19 Jun 2006 03:31:47 GMT
ETag: "c144d0-78b7-4168b67f1aec0"
Via: 1.1 netcache (NetCache NetApp/6.0.2)

Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [30.9kB]
99% [Working]                                                                                                      922B/s 0sGET /ubuntu/dists/dapper/main/binary-i386/Packages.bz2 HTTP/1.1
Host: archive.ubuntu.com
Connection: keep-alive
If-Modified-Since: Thu, 08 Jun 2006 12:23:09 GMT
User-Agent: Debian APT-HTTP/1.3


GET /ubuntu/dists/dapper/restricted/binary-i386/Packages.bz2 HTTP/1.1
Host: archive.ubuntu.com
Connection: keep-alive
If-Modified-Since: Sun, 18 Jun 2006 18:24:17 GMT
User-Agent: Debian APT-HTTP/1.3


GET /ubuntu/dists/dapper/universe/binary-i386/Packages.bz2 HTTP/1.1
Host: archive.ubuntu.com
Connection: keep-alive
If-Modified-Since: Thu, 08 Jun 2006 15:06:07 GMT
User-Agent: Debian APT-HTTP/1.3


GET /ubuntu/dists/dapper/multiverse/binary-i386/Packages.bz2 HTTP/1.1
Host: archive.ubuntu.com
Connection: keep-alive
If-Modified-Since: Sun, 18 Jun 2006 18:24:53 GMT
User-Agent: Debian APT-HTTP/1.3


99% [Waiting for headers]                                                                                         4155B/s 0sHTTP/1.1 304 Not Modified
Etag: "c14717-973d0-415b58c014540"
Date: Sun, 18 Jun 2006 19:21:32 GMT

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
99% [Waiting for headers]                                                                                         4155B/s 0sGET /ubuntu/dists/dapper-updates/main/binary-i386/Packages.bz2 HTTP/1.1
Host: archive.ubuntu.com
Connection: keep-alive
If-Modified-Since: Sun, 18 Jun 2006 18:23:23 GMT
User-Agent: Debian APT-HTTP/1.3


GET /ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.bz2 HTTP/1.1
Host: archive.ubuntu.com
Connection: keep-alive
If-Modified-Since: Sun, 18 Jun 2006 18:31:44 GMT
User-Agent: Debian APT-HTTP/1.3


GET /ubuntu/dists/dapper-updates/universe/binary-i386/Packages.bz2 HTTP/1.1
Host: archive.ubuntu.com
Connection: keep-alive
If-Modified-Since: Sun, 18 Jun 2006 18:23:24 GMT
User-Agent: Debian APT-HTTP/1.3


GET /ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.bz2 HTTP/1.1
Host: archive.ubuntu.com
Connection: keep-alive
If-Modified-Since: Sun, 18 Jun 2006 18:31:44 GMT
User-Agent: Debian APT-HTTP/1.3


HTTP/1.1 200 OK
Age: 30
Date: Mon, 19 Jun 2006 03:52:53 GMT
Content-Length: 4571
Content-Type: text/plain; charset=UTF-8
Server: Apache/2.0.54 (Ubuntu)
Last-Modified: Mon, 19 Jun 2006 03:24:12 GMT
ETag: "c14582-11db-4168b4cd2ef00"
Via: 1.1 netcache (NetCache NetApp/6.0.2)

Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages [4571B]
99% [3 Packages bzip2 0] [Waiting for headers]                                                                    4155B/s 0sHTTP/1.1 304 Not Modified
Etag: "c14736-2581ee-415b7d2d1b5c0"
Date: Sun, 18 Jun 2006 19:22:30 GMT

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
99% [Waiting for headers]                                                                                         4155B/s 0sHTTP/1.1 200 OK
Age: 31
Date: Mon, 19 Jun 2006 03:52:53 GMT
Content-Length: 95156
Content-Type: text/plain; charset=UTF-8
Server: Apache/2.0.54 (Ubuntu)
Last-Modified: Mon, 19 Jun 2006 03:24:48 GMT
ETag: "c14572-173b4-4168b4ef84000"
Via: 1.1 netcache (NetCache NetApp/6.0.2)

Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages [95.2kB]
94% [4 Packages 88250/95.2kB 92%]                                                                                 8349B/s 0sHTTP/1.1 200 OK
Age: 30
Date: Mon, 19 Jun 2006 03:53:08 GMT
Content-Length: 36574
Content-Type: text/plain; charset=UTF-8
Server: Apache/2.0.54 (Ubuntu)
Last-Modified: Mon, 19 Jun 2006 03:23:18 GMT
ETag: "c14539-8ede-4168b499af580"
Via: 1.1 netcache (NetCache NetApp/6.0.2)

Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [36.6kB]
98% [5 Packages 34272/36.6kB 93%]                                                                                 9554B/s 0sHTTP/1.1 200 OK
Age: 30
Date: Mon, 19 Jun 2006 03:53:12 GMT
Content-Length: 14
Content-Type: text/plain; charset=UTF-8
Server: Apache/2.0.54 (Ubuntu)
Last-Modified: Mon, 19 Jun 2006 03:31:44 GMT
ETag: "c500b2-e-4168b67c3e800"
Via: 1.1 netcache (NetCache NetApp/6.0.2)

Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
99% [Waiting for headers]                                                                                         9554B/s 0sHTTP/1.1 200 OK
Age: 31
Date: Mon, 19 Jun 2006 03:53:12 GMT
Content-Length: 8363
Content-Type: text/plain; charset=UTF-8
Server: Apache/2.0.54 (Ubuntu)
Last-Modified: Mon, 19 Jun 2006 03:23:19 GMT
ETag: "c1455f-20ab-4168b49aa37c0"
Via: 1.1 netcache (NetCache NetApp/6.0.2)

Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages [8363B]
99% [Waiting for headers]                                                                                         9554B/s 0sHTTP/1.1 200 OK
Age: 30
Date: Mon, 19 Jun 2006 03:53:13 GMT
Content-Length: 14
Content-Type: text/plain; charset=UTF-8
Server: Apache/2.0.54 (Ubuntu)
Last-Modified: Mon, 19 Jun 2006 03:31:44 GMT
ETag: "c500b2-e-4168b67c3e800"
Via: 1.1 netcache (NetCache NetApp/6.0.2)

Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages [14B]
Fetched 176kB in 33s (5275B/s)
Failed to fetch file:///mnt/dapper/dists/dapper/main/binary-i386/Packages.gz  File not found
Failed to fetch file:///mnt/dapper/dists/dapper/restricted/binary-i386/Packages.gz  File not found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
[/SIZE]

---

### Post by linuchsan on 2006-06-19
Can i see your sources.list?

---

### Post by shalinmangar on 2006-06-19
[QUOTE=linuchsan]Can i see your sources.list?[/QUOTE]

This is the contents of my /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

---

### Post by linuchsan on 2006-06-19
Did you do an apt-get update first?
Or try a mirror from your country.

---

### Post by shalinmangar on 2006-06-20
[QUOTE=linuchsan]Did you do an apt-get update first?
Or try a mirror from your country.[/QUOTE]

I did apt-get update but that doesn't change anything much. Last night most of the updates were downloaded successfully except for two packages:

[SIZE="1"]Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main libgtk2.0-0 2.8.18-0ubuntu1
  Bad header line [IP: 85.133.25.7 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main desktop-file-utils 0.10-1ubuntu13
  Bad header line [IP: 85.133.25.7 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.8.18-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.8.18-0ubuntu1_i386.deb)  Bad header line [IP: 85.133.25.7 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/desktop-file-utils/desktop-file-utils_0.10-1ubuntu13_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/desktop-file-utils/desktop-file-utils_0.10-1ubuntu13_i386.deb)  Bad header line [IP: 85.133.25.7 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/SIZE]

How do I change the mirror?

---

### Post by linuchsan on 2006-06-20
like [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) or [http://de.archive.ubuntu.com/](http://de.archive.ubuntu.com/)  in the sources.list, it depends where you are from.

---

### Post by shalinmangar on 2006-06-20
[QUOTE=linuchsan]like [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) or [http://de.archive.ubuntu.com/](http://de.archive.ubuntu.com/)  in the sources.list, it depends where you are from.[/QUOTE]

I tried changing the mirror to [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) and to [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) but no use. Still the same problem is there. I think that my internet provider's proxy/cache has cached some incorrect response from the server. That must be the reason why those two packages are not being downloaded. I'll just have to wait till it gets cleared.

Many thanks for giving your time and helping me in this.

---

