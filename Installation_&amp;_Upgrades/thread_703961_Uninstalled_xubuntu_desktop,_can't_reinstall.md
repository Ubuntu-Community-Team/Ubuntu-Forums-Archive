---
title: "Uninstalled xubuntu desktop, can't reinstall"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by bowlingblogger on 2008-02-21
Hi, I have xubuntu (Gusty 7.10 I think) running on an EEE PC 4g Surf and I'm a complete Linux noob. I was having sound problems so I was following instructions on another site to uninstall and reinstall the driver and in the process gdm and xubuntu desktop were uninstalled. Now when I turn on the computer I don't get any further than the console. I followed the instructions to reinstall (sudo apt-get install gdm ubuntu-desktop). I connect to the repositories and seem to download some things, but I keep getting "could not resolve" and "failed to fetch" errors. I followed instructions in another thread to enable all the repositories in the sources.list file and I still get these errors. Is there something wrong with the servers, or am I just an idiot?

Sorry for the long-winded explanation, and I hope this question hasn't been answered a million times already. Thanks in advance, and for all the great info I've gleaned on these forums already!

---

### Post by taurus on 2008-02-21
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```
Also, it would be real helpful if you include the whole error message.

---

### Post by bowlingblogger on 2008-02-21
I can post the source list as long as I can figure out how...is there a way I can copy it as a text file to a flash drive so I can post it from my desktop?

Here is an example of the errors I am receiving:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gusty/main xubuntu-desktop 2.50
    Could not resolve 'archive.ubuntu.com'

This error is repeated multiple times with different filenames on the end.

Another error I am receiving is "Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/r/restricted-manager/restricted-manager-core_0.33.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/r/restricted-manager/restricted-manager-core_0.33.1_all.deb)  Could not resolve 'archive.ubuntu.com'

This error is repeated as well with different URLs. At the end of the whole string is:

"E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?"

I hope this helps--if not just ask me for more info. Thanks!

---

### Post by bowlingblogger on 2008-02-21
I'm afraid it turns out I am an idiot. My EEE PC was unable to connect to the repositories because it was unable to use the wifi connection. I plugged in an ethernet cable and I was able to download what I needed fine.

Sorry for wasting your time on this one...but thanks for trying!

---

