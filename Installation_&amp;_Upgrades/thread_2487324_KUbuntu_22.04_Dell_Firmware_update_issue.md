---
title: "KUbuntu 22.04 Dell Firmware update issue"
date: 2023-05-30
forum: Installation &amp; Upgrades
---

### Post by LVDave on 2023-05-30
I'm on a Dell Latitude 5480, running KUbuntu 22.04. When updating with the "Discover" program, I have a entry for a "Dell System Firmware" "Upgrade to 1.30.0" 13.1Mb. This entry does not
upgrade when checked. If I click the "upgrade all", the checkbox next to it greys out momentarily, then remains.Thinking that the discover/settings/firmware updates might be misconfigured, I find there is
is a checkmark in the "lvfs-linux vendor firmware service" and "vendor directory-vendor (automatic)". I've tried unchecking these, rebooting, rechecking them, no change. What am I missing here??

Thanks
Dave

---

### Post by oldfred on 2023-05-30
My motherboards do not support fwupdate. So I have not used it.

To see UEFI/BIOS version:
sudo dmidecode -s bios-version

[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)  #Shows your system as 5X80 so all similar models?
sudo fwupdmgr get-devices
sudo fwupdmgr get-updates
sudo fwupdmgr update
fwupdmgr --version

---

### Post by LVDave on 2023-05-30
Thanks!! I found the problem when running the "sudo fwupdmgr get-devices"... In bright red letters, it told me TPM was on.. After turning that crap off, was able to update to latest bios..

---

