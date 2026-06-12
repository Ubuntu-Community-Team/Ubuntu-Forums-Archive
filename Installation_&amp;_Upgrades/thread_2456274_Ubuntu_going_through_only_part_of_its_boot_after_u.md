---
title: "Ubuntu going through only part of its boot after update"
date: 2021-01-08
forum: Installation &amp; Upgrades
---

### Post by deelumal on 2021-01-08
Hello,

I'm new to the forum but not new to the ubuntu. I have used it for around five years with no major issues. However, this morning I updated 20.04 with seemingly nocus updates but to be honest once I saw Firefox and Chrome. There were other updates but to be honest, I didn't pay any attention. That will not happen again. It is a dual-booted system with Xubuntu on the other side. This is the first time that an update HAS EVER nuked my system. However, I am able to utilize recovery so we know it is there where it is supposed to be for sure. l can't figure out why it is getting a point in booting and then giving me a flashing prompt and just sits there with a black screen. It is ubuntu's version of BSOD except it comes in the color black. BTW, next time I will wait a year to upgrade.

---

### Post by deelumal on 2021-01-08
Oh, I was getting an error message that I reported to ubuntu before the latest update. I have never had to report errors with a new install.

---

### Post by deelumal on 2021-01-08
ii linux-image-generic-hwe-20.04       5.8.0.36.40~20.04.21
amd64 Generic Linux kernel image

---

### Post by rbmorse on 2021-01-08
The blinking cursor on an otherwise blank screen during initialization probably means that GRUB can't find a valid / (root) partition at the location/UUID indicated in GRUB's setup. 

My first guess is that you are running one or both O/S in legacy BIOS mode and the update messed with the boot sector in the MBR.  

Second guess:  If your machine is setup so both O/S run in EFI mode, boot into EFI setup and make sure the first entry in the boot drive selector is pointed at the correct ESP.  If you have more than one, try the other one.

---

### Post by deelumal on 2021-01-08
Which is strange to me as Xubuntu is booting fine. Secondly, as I mentioned before, it boots ubuntu in recovery mode. Lastly, I just checked to make sure, this system is legacy all the way there is no UEFI on this machine.

---

### Post by Impavidus on 2021-01-08
There are several threads on the forum now about problems with 20.04 with hwe, which just moved to the 5.8 kernel.

Can you use the grub menu to boot in recovery mode? (Apparently, you can.) Can you use the grub menu to boot an older kernel? Do you actually need the hwe kernel (5.8), or does your system work fine with the standard kernel on 20.04 (5.4)?

Your Xubuntu system may be using a different kernel. Maybe it's behind on its updates, or maybe it uses the standard kernel, not the hwe kernel.

If you don't remember which packages were upgraded, look in the logs:```
grep " upgrade " /var/log/dpkg.log
```

---

### Post by deelumal on 2021-01-08
Thank you and the other responder first. It is partially booting but will only boot completely in recovery mode. Here are my grub options

These are my options

5.4.0-59-generic
5.4.0-59-generic (recover mode)
5.4.0-58-generic
5.4.0-58-generic (recover mode)

It looks like my option may be to revert -- which I have never done before -- because this computer is going to someone that I am donating my time to refurbishing it for her. A person with health issues and unable to work or even live normally because of her health issues. A former Windows 7 computer. I don't want her to be in this position so I may want to revert such that it NEVERS updates to newest kernel. The question is security in that regard. If we never update will security be a concern as this version is good for five years? I would not want to walk her through reverting over the telephone.

---

### Post by Impavidus on 2021-01-09
In that case I suggest you stick to the standard (5.4) kernel for 20.04 and don't install the hwe (5.8) kernel. That will install security patches, but won't install any big upgrades, so it's less likely to break. In my experience, it's very uncommon (but not impossible) to get a broken system on a simple kernel patch. Unless you've got some reason not to use the generic kernel, make sure you have the package **linux-generic** installed and not the package **linux-generic-hwe-20.04**. Also remove any packages automatically installed as dependencies of the hwe package, thas is, kernel and header packages with versions 5.8.something. In your case it appears that the 5.8 kernel was partially installed.

Fixing problems by phone must be even harder than by forum.

---

### Post by deelumal on 2021-01-09
Well, for my money, this is a catastrophic software failure that at this time is not worth trusting to my clients. While I am still positive about ubuntu overall, this is definitely something to make me rethink the idea that it is the best solution for all hardware. First, I had a really hard time making WiFi work. I resolved that after a day and a half of research and trial and error. I finally removed what I thought was the offending kernel but it still leaves me with a partial boot that I had before kernel update and/or the update that I accepted through the desktop. I have had enough success from ubuntu to not throw it in the pile of junk but going forward if I think that the hardware is too old to handle it I'll go with a distro created to work with older hardware. In this case, today, I will install 18.04 and move forward.

Thanks for all your help!

---

### Post by deelumal on 2021-01-09
> **Impavidus said:**
> In that case I suggest you stick to the standard (5.4) kernel for 20.04 and don't install the hwe (5.8) kernel. That will install security patches, but won't install any big upgrades, so it's less likely to break. In my experience, it's very uncommon (but not impossible) to get a broken system on a simple kernel patch. Unless you've got some reason not to use the generic kernel, make sure you have the package **linux-generic** installed and not the package **linux-generic-hwe-20.04**. Also remove any packages automatically installed as dependencies of the hwe package, thas is, kernel and header packages with versions 5.8.something. In your case it appears that the 5.8 kernel was partially installed.

Fixing problems by phone must be even harder than by forum.

No idea when it was updated other than the updates that I installed with those other updates. As I stated, I will be much more careful, next time to read ALL the updates going forward, but the issue would still be whether my client's will be able to do same.

---

### Post by Impavidus on 2021-01-10
It appears that the Ubuntu 20.04 installer (but not the Xubuntu 20.04 installer) installs the hwe kernel series by default. I'm quite sure that's the cause of some additional instability.

---

### Post by deelumal on 2021-01-10
I tend to agree Impavidus but even after installing 18.04 I am getting this notice which I got in 20.04, "System program problem detected: Do you wan to report the problem now?" keeps notifying after desktop loads. In addition, there are video issues during boot but are resolved once I get into desktop and it looks fine. Consequently, I think that there is some instability with the hardware and ubuntu as I already mentioned the broadcom wifi issues. Xubuntu has been rock solid EVEN after I screwed up the boot after using Gparted to add more space to that side. I resolved that with the Supergrub disk. I definitely will be making a donation. This is the worst install ever but I have two other installs that work beautifully: 1 desktop and 1 laptop both dual booted. One with Win7 and the other with Win10. 

Thanks for your feedback as it has been very helpful!

---

