---
title: "Unable to boot from install CD after crash during partitioning"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by johnfrith on 2012-05-06
Hi, thanks for reading.

I checked md5sum on 12.4 desktop iso (64 bit - I have a Clevo laptop with Core2 Duo processors). 
Repartition drive for fresh install.
Program crashed during re-partitioning (no idea why). 
Rebooted from live cd, but just get black screen and repetitive whirring like it's trying and failing to read CD.
Tried various old CD's to see if they worked, but got the same, apart from 1 cd from which I managed to install 10.04.
Still 12.04 live cd won't boot
Created 32 bit desktop live cd, but same problem - black screen
Booted Boor-Repair Cd, which started (and still does) by giving loads of error messages such as
"buffer I/O errors on dev sr0, logical block xxxxx"
Eventually got to splash screen where I did standard repair and got output (see link [HERE]("http://paste.ubuntu.com/970907/")) (Sorry couldn't work out how to paste)
Both 12.04 boot discs still don't work

No idea what's going on underneath the hood myself - any help would be appreciated.

---

### Post by oldfred on 2012-05-06
It sounds like either CD was not written correctly or CD drive is failing. I would double check that ISO downloaded was correct and that you burned to CD at slowest speed allowed.

 Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Do you have flash drive and does your system boot from flash? I find flash easier, although some have issues. Flash also installs faster and you do not burn coasters, just rewrite it.

---

### Post by johnfrith on 2012-05-08
Thanks for the post oldfred.
 
I had been doing the md5sum, although I guess it could have been corrupted at the cd write stage. I forgot to mention that the DVD drive was working fine other than the install.
 
I hadn't considered installing from a USB, which I have now done. Many many further problems, but that's for a fresh thread! Thanks again for you advice.

---

