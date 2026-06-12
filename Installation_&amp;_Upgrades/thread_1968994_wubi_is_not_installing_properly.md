---
title: "wubi is not installing properly"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by Lancro on 2012-04-29
I cant install a full installtion because of the efi issue, and im trying wubi install, but it doesnt download the iso, so I tried to execute it in another directory away from the iso, it downloads something, dont lnow what, and then it restarts the computer to show the message...

/ubuntu/winboot/wubildr.mbr missing or corrupt

I checked and the file is there, so it should be corrupt, how can I install ubuntu 12.04 with wubi?.

Thanks.

---

### Post by oldfred on 2012-04-30
You are having your issues. See your other thread for some more efi suggestions.

I am not sure wubi works with efi. wubi boots thru the Windows boot loader and updates XP's boot.ini or Windows Vista/7's BCD. With efi, I do not think you have those as you are booting with efi.

---

