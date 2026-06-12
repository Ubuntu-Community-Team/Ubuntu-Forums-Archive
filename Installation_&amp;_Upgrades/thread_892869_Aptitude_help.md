---
title: "Aptitude help"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by Takamori on 2008-08-17
I'm new to using Aptitude and jus to my luck on some of my first use we had a lightning storm which caused a power outage during an install of mine.  When I tried to install ANY packages, I get this:
As a test I tried to install xeyes (even though I know it is installed on my system.

```

Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...
No candidate version found for xeyes
No candidate version found for xeyes
The following packages have been kept back:
  anacron app-install-data-commercial bind9-host initramfs-tools 
  libbind9-30 libcamel1.2-11 libebook1.2-9 libecal1.2-7 libedataserver1.2-9 
  libisc32 libisccc30 libisccfg30 libldap-2.4-2 liblwres30 libnspr4-0d 
  libnss3-1d libpoppler-glib2 libpoppler2 libxslt1.1 
  linux-image-2.6.24-19-generic linux-restricted-modules-2.6.24-19-generic 
  mozilla-thunderbird pciutils poppler-utils python2.5 python2.5-minimal 
  ssl-cert thunderbird update-manager update-manager-core update-notifier 
  update-notifier-common 
0 packages upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
Need to get 0B/166kB of archives. After unpacking 0B will be used.
Writing extended state information...
(Reading database ... 137935 files and directories currently installed.)
Preparing to replace education-common 0.824ubuntu2 (using .../education-common_0.824ubuntu2_i386.deb) ...
Unpacking replacement education-common ...
err 67: Custom distribution education does not exist
dpkg: warning - old post-removal script returned error exit status 67
dpkg - trying script from the new package instead ...
err 67: Custom distribution education does not exist
dpkg: error processing /var/cache/apt/archives/education-common_0.824ubuntu2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 67
err 67: Custom distribution education does not exist
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 67
Preparing to replace education-logic-games 0.824ubuntu2 (using .../education-logic-games_0.824ubuntu2_i386.deb) ...
Unpacking replacement education-logic-games ...
err 67: Custom distribution education does not exist
dpkg: warning - old post-removal script returned error exit status 67
dpkg - trying script from the new package instead ...
err 67: Custom distribution education does not exist
dpkg: error processing /var/cache/apt/archives/education-logic-games_0.824ubuntu2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 67
err 67: Custom distribution education does not exist
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 67
Preparing to replace education-main-server 0.824ubuntu2 (using .../education-main-server_0.824ubuntu2_i386.deb) ...
Unpacking replacement education-main-server ...
err 67: Custom distribution education does not exist
dpkg: warning - old post-removal script returned error exit status 67
dpkg - trying script from the new package instead ...
err 67: Custom distribution education does not exist
dpkg: error processing /var/cache/apt/archives/education-main-server_0.824ubuntu2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 67
err 67: Custom distribution education does not exist
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 67
Preparing to replace education-mathematics 0.824ubuntu2 (using .../education-mathematics_0.824ubuntu2_i386.deb) ...
Unpacking replacement education-mathematics ...
err 67: Custom distribution education does not exist
dpkg: warning - old post-removal script returned error exit status 67
dpkg - trying script from the new package instead ...
err 67: Custom distribution education does not exist
dpkg: error processing /var/cache/apt/archives/education-mathematics_0.824ubuntu2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 67
err 67: Custom distribution education does not exist
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 67
Preparing to replace education-music 0.824ubuntu2 (using .../education-music_0.824ubuntu2_i386.deb) ...
Unpacking replacement education-music ...
err 67: Custom distribution education does not exist
dpkg: warning - old post-removal script returned error exit status 67
dpkg - trying script from the new package instead ...
err 67: Custom distribution education does not exist
dpkg: error processing /var/cache/apt/archives/education-music_0.824ubuntu2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 67
err 67: Custom distribution education does not exist
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 67
Preparing to replace education-networked 0.824ubuntu2 (using .../education-networked_0.824ubuntu2_i386.deb) ...
Unpacking replacement education-networked ...
err 67: Custom distribution education does not exist
dpkg: warning - old post-removal script returned error exit status 67
dpkg - trying script from the new package instead ...
err 67: Custom distribution education does not exist
dpkg: error processing /var/cache/apt/archives/education-networked_0.824ubuntu2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 67
err 67: Custom distribution education does not exist
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 67
Preparing to replace education-physics 0.824ubuntu2 (using .../education-physics_0.824ubuntu2_i386.deb) ...
Unpacking replacement education-physics ...
err 67: Custom distribution education does not exist
dpkg: warning - old post-removal script returned error exit status 67
dpkg - trying script from the new package instead ...
err 67: Custom distribution education does not exist
dpkg: error processing /var/cache/apt/archives/education-physics_0.824ubuntu2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 67
err 67: Custom distribution education does not exist
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 67
Errors were encountered while processing:
 /var/cache/apt/archives/education-common_0.824ubuntu2_i386.deb
 /var/cache/apt/archives/education-logic-games_0.824ubuntu2_i386.deb
 /var/cache/apt/archives/education-main-server_0.824ubuntu2_i386.deb
 /var/cache/apt/archives/education-mathematics_0.824ubuntu2_i386.deb
 /var/cache/apt/archives/education-music_0.824ubuntu2_i386.deb
 /var/cache/apt/archives/education-networked_0.824ubuntu2_i386.deb
 /var/cache/apt/archives/education-physics_0.824ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...
$

```

I tried looking for the error codes but I couldn't find anything.  Anyhelp with this or guides/ FAQs on Aptitude would be useful, thanks for your help.

---

