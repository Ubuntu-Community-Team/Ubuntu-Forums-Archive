---
title: "Installation from USB problem"
date: 2020-07-02
forum: Installation &amp; Upgrades
---

### Post by hhs13 on 2020-07-02
I have built a new machine and trying to install Ubuntu 20.04 LTS. I have followed the steps on website (create USB bootable disk using Rufus). My system detects bootable media and I can see install window in UEFI mode. When I select "install Ubuntu" or "try Ubuntu", system restarts and I am back to select boot device page. It keeps on happening again n again, I tried using a different tool other than Rufus and it still behave same. 

Since it's a new system and nothing is installed, I am bit confused what's happening. I have tried multiple places but not been able to identify the source of problem. I am using MSI Z390A-Pro and i7 processor. I have just installed processor / RAM, no Graphics card. 

Any help would be appreciated. 

Thanks.

---

### Post by ActionParsnip on 2020-07-02
Did you leave unpartitioned space on the internal storage to install Ubuntu to? If not then boot to Windows and shrink your drive to leave unpartitioned space.

Did you MD5 test the ISO you downloaded or use torrents to download the ISO? A bad ISO will make a bad install media. The torrent protocol checks data very well. If you used your browser to download the ISO then I recommend you check the file using this link:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by mIk3_08 on 2020-07-02
[Click Here.]("https://help.ubuntu.com/community/UEFI") It might help.

---

### Post by hhs13 on 2020-07-02
I have installed a new hard drive and haven't done anything on it like partitioning (I am expecting to do partitioning when Ubuntu installation begins, that's how I have done for Windows in past). 
Also I downloaded the file from Ubuntu website directly, so I expect it to be good. Although I have downloaded it twice from same source. But I will try MD5 test.

---

