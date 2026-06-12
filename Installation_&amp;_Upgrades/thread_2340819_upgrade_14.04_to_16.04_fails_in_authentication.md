---
title: "upgrade 14.04 to 16.04 fails in authentication"
date: 2016-10-22
forum: Installation &amp; Upgrades
---

### Post by paulvha on 2016-10-22
Trying to upgrade with do-release-upgrade -d, the authentication fails :

Get:1 Upgrade tool signature [198 B]                                                                                                                                                                        
Get:2 Upgrade tool [1262 kB]                                                                                                                                                                                
Fetched 1262 kB in 0s (0 B/s)                                                                                                                                                                               
authenticate 'xenial.tar.gz' against 'xenial.tar.gz.gpg' 
gpg exited 127
Debug information: 

gpg: error while loading shared libraries: libusb-0.1.so.4: cannot open shared object file: No such file or directory

Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server. 

Of course I have done apt-get update, apt- upgrade, apt-get dist-upgrade etc etc. All without errors or problems. There is no info in /var/log/dist-upgrade nor any of the other logs I can find
I have looked hours in many forums for more information, but I am stuck now.
Where should these files be stored? is there maybe a permission problem ? 

thanks for any help 
Paul

---

### Post by paulvha on 2016-10-26
The turned out to be a problem with gpg command missing the library. Tried to install it, but the apt-get indicated it was installed already. Decided to install 16.04 from dvd. First it attempted to upgrade, which worked, However I got issues with grub, as I have dual boot and wanted a different OS to start by default. Followed the official procedure but after that Ubuntu did not wanted to start anymore (blue screen forever). Did a complete install of 16.04 and now all is good again.

---

