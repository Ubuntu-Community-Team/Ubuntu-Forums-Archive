---
title: "Problems with some recent upgrades, Apt &quot;Broken Pipe&quot; write error"
date: 2013-09-20
forum: Installation &amp; Upgrades
---

### Post by mcmndrdr on 2013-09-20
Hello all!

I've been having trouble with some recent upgrades. Hopefully someone out there can help me with this one. I get this error when running the upgrades:

installArchives() failed: 
Extracting templates from packages: 62%%
Extracting templates from packages: 100%%
Preconfiguring packages ...


Extracting templates from packages: 62%%
Extracting templates from packages: 100%%
Preconfiguring packages ...


Extracting templates from packages: 62%%
Extracting templates from packages: 100%%
Preconfiguring packages ...


Extracting templates from packages: 62%%
Extracting templates from packages: 100%%
Preconfiguring packages ...
Setting up apt (0.8.16~exp12ubuntu10.14) ...
gpg: Invalid option "--primary-keyring"
gpg: [stdout]: write error: Broken pipe
gpg: build_packet(2) failed: file write error
dpkg: error processing apt (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 apt
Setting up apt (0.8.16~exp12ubuntu10.14) ...
gpg: Invalid option "--primary-keyring"
gpg: [stdout]: write error: Broken pipe
gpg: build_packet(2) failed: file write error
dpkg: error processing apt (--configure):
 subprocess installed post-installation script returned error exit status 2

Please let me know if there is any other information I need to post to help solve this issue.

Thanks all!

mm

---

