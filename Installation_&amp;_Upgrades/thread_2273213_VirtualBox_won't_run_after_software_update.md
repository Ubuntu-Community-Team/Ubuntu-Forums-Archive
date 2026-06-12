---
title: "VirtualBox won't run after software update"
date: 2015-04-11
forum: Installation &amp; Upgrades
---

### Post by Allister_Graham on 2015-04-11
I updated VirtualBox a few days ago along with some other software two days ago using the software updater. Today, I tried to run VirtualBox from the launcher. It simply failed to start. I use Ubuntu 14.10.

When I tried to run it from the terminal, I got the following error message:
```
VirtualBox: Error -610 in supR3HardenedMainInitRuntime!VirtualBox: dlopen("/usr/lib/virtualbox/VBoxRT.so",) failed: /usr/local/lib/libcurl.so.4: undefined symbol: SSLv2_client_method


VirtualBox: Tip! It may help to reinstall VirtualBox.
```

So, that's just what I did. I ran the following command:
```
sudo aptitude reinstall virtualbox
```

Then I got the following error message:
```
Need to get 0 B/15.9 MB of archives. After unpacking 0 B will be used.(Reading database ... 369621 files and directories currently installed.)
Preparing to unpack .../virtualbox_4.3.18-dfsg-2ubuntu2_amd64.deb ...
Unpacking virtualbox (4.3.18-dfsg-2ubuntu2) over (4.3.18-dfsg-2ubuntu2) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.0.2-2) ...
Setting up virtualbox (4.3.18-dfsg-2ubuntu2) ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                    [ fail ]
```

That failed, so I purged VirtualBox using the following command:
```
sudo apt-get purge virtualbox
```

This succeeded, so I installed VirtualBox once again using this command:
```
sudo apt-get install virtualbox
```

This worked. But when I tried to run Virtualbox from the terminal, I got a new error message:
```
VirtualBox: Error -610 in supR3HardenedMainInitRuntime!VirtualBox: dlopen("/usr/lib/virtualbox/VBoxRT.so",) failed: /usr/local/lib/libcurl.so.4: undefined symbol: SSLv2_client_method


VirtualBox: Tip! It may help to reinstall VirtualBox.
```

What do I do now?

EDIT: I tried the packages on the VirtualBox website, but when I try to launch VirtualBox now, I still get the same error message.

---

### Post by dino99 on 2015-04-11
i've often got issue with the ubuntu virtualbox packages; so now i'm using the [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
so purge the installed one (sudo apt-get purge virtualbox*) before reinstalling after updating the archive with the oracle link

---

### Post by Allister_Graham on 2015-04-11
Thanks.

---

