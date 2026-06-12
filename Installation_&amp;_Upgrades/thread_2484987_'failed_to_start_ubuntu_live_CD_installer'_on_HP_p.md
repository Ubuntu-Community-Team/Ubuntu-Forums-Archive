---
title: "'failed to start ubuntu live CD installer' on HP pavillion laptop"
date: 2023-03-16
forum: Installation &amp; Upgrades
---

### Post by nambu123 on 2023-03-16
hi guys, so recently i got a new HP pavillion laptop and decided to install ubuntu 22.04 on it. however during the startup the laptop will fail to start the live iso and therefore i cant install it. weirdly, the exact same usb and iso had no issue installing on another 2 PCs (a lenovo miix 310 laptop and a HP compaq 8100 elite desktop). so im just wondering why the usb wont work on this laptop? has anyone else ran into a situation like this? before anyone mentions, i did try the safe graphics and OEM install options as well, but they had the same outcome. any help would be appreciated.

---

### Post by nambu123 on 2023-03-16
for more information its a hp pavilion notebook 80A2.

---

### Post by naufrsb on 2023-03-16
Hey there, 

It's possible that your problem is related to the UEFI/Secure Boot settings on your HP Pavilion laptop. You can try disabling secure boot, enabling legacy boot, check your USB drive, or you Ubuntu ISO. 

i hope that helps!

---

### Post by tea for one on 2023-03-16
Better not to enable Legacy boot on a new PC.
Certainly, disable Secure Boot and TPM.

Is Windows 11 installed?
Do you wish to keep it?

---

### Post by MAFoElffen on 2023-03-16
Pre-check: Go into the Windows Disk Management to resize partitions to allow enough room for Ubuntu. If you use Linux to do that you will break the Windows Index files, and will have to rebuild them later for Windows... If you are getting rid of Windows, then a lot of this post you can skip.

First, can you get into the UEFI Bios? Check the BIOS firmware version...

See if your HP Notebook is on this list: [https://support.hp.com/us-en/document/c05976754](https://support.hp.com/us-en/document/c05976754)

Those UEFI BIOS Firmware updates also fix a problem where USB drives were not being recognized...

As it notes, you might want to check HP support for your specific model, just to see if there is a newer version.

As I remember, the BIOS settings were "UEFI Native without CSM", secureboot disabled.. (But I have also installed a lot of systems with 22.04.x with secureboot enabled.) 

One other thing is to check the SATA Mode setting and ensure it says AHCI, instead of RAID Mode. If you have Windows and wish to keep it, stop if it says RAID mode, and **don't change it yet.** 

Boot into Windows. Run a cmd prompt as administrator.
```

bcdedit /set {current} safeboot minimal

```
Reboot and go back into the SATA Mode settings. Change RAID to AHCI. Save and reboot.

Boot into Windows. Run a cmd prompt as administrator.
```

bcdedit /deletevalue {current} safeboot

```
Reboot. Start Windows. 

Doing that, Windows will recognize the SATA Mode change and install the correct AHCI drivers... Don't do that or do it in the wrong order... You'll be reinstalling Windows.

Then... Try to boot off the LiveUSB.

---

### Post by guiverc on 2023-03-17
> **nambu123 said:**
> hi guys, so recently i got a new HP pavillion laptop and decided to install ubuntu 22.04 on it. however during the startup the laptop will fail to start the live iso and therefore i cant install it. weirdly, the exact same usb and iso had no issue installing on another 2 PCs (a lenovo miix 310 laptop and a HP compaq 8100 elite desktop). so im just wondering why the usb wont work on this laptop? has anyone else ran into a situation like this? before anyone mentions, i did try the safe graphics and OEM install options as well, but they had the same outcome. any help would be appreciated.

You didn't provide clues as to what 22.04 ISO (ie. Server, Desktop, 22.04? 22.04.1? 22.04.2 or *flavor* etc) , nor importantly what media was used  (*you mention USB which may mean flash media*).

Optical media can be *slow* and *a little problematic*on some devices, thus *flash* media is best.

How the ISO was written also plays a part, eg. I can write an ISO using specific methods so it'll boot perfectly on a hp dc7700/7900 (*which has firmware bugs*) but not other devices, or write it so it'll boot only on BIOS devices but no uEFI (*or vise-versa*). 

Some devices also take >10 minutes to boot media *if cloned or written normally* so did you wait long enough?  To make it boot faster on *devices with firmware bugs* you can write it specific ways to not trigger device *firmware* bugs, but that media will boot on fewer devices as a consequence - ie. how ISO is written matters, and did you wait long enough? (*ie. 15 mins*).  FYI:  The *firmware* issue that causes *slow boots* only impacts *live* media, so once installed there is no issue.

---

### Post by nambu123 on 2023-03-17
so i ended up disabling secure boot and enabling legacy boot but it still doesnt wanna play ball.

(this was in response to someone mentioning i should do those things, i just forgot to quote them)

---

### Post by nambu123 on 2023-03-17
> **tea for one said:**
> Better not to enable Legacy boot on a new PC.
Certainly, disable Secure Boot and TPM.

Is Windows 11 installed?
Do you wish to keep it?

by 'new' i mean new to mean, it was my grandads old laptop that he had since like, 2015/2016 i think
also its running windows 10, which im not really interested in keeping.

---

### Post by nambu123 on 2023-03-17
> **guiverc said:**
> You didn't provide clues as to what 22.04 ISO (ie. Server, Desktop, 22.04? 22.04.1? 22.04.2 or *flavor* etc) , nor importantly what media was used  (*you mention USB which may mean flash media*).

Optical media can be *slow* and *a little problematic*on some devices, thus *flash* media is best.

How the ISO was written also plays a part, eg. I can write an ISO using specific methods so it'll boot perfectly on a hp dc7700/7900 (*which has firmware bugs*) but not other devices, or write it so it'll boot only on BIOS devices but no uEFI (*or vise-versa*). 

Some devices also take >10 minutes to boot media *if cloned or written normally* so did you wait long enough?  To make it boot faster on *devices with firmware bugs* you can write it specific ways to not trigger device *firmware* bugs, but that media will boot on fewer devices as a consequence - ie. how ISO is written matters, and did you wait long enough? (*ie. 15 mins*).  FYI:  The *firmware* issue that causes *slow boots* only impacts *live* media, so once installed there is no issue.

so the iso is the desktop version of jammy jellyfish 22.04.1, the usb itself is a generic flash drive. the iso was written using balena etcher. as for time, usually it'll make it to the 5 minute mark before it mentions it failed to start ubuntu live cd installer.

---

