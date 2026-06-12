---
title: "After upgrade to 20.10 on dual boot laptop: message 'boot image did not authenticate'"
date: 2020-10-23
forum: Installation &amp; Upgrades
---

### Post by Antoon Stessels on 2020-10-23
Hi all,

I updated my laptop from work yesterday, a HP Probook. It runs Ubuntu and Windows 10. Ever since upgrading to Ubuntu 20.10, the grub menu won't load anymore, instead showing the message: 

'Boot image did not authenticate.
Please press enter to attempt boot to next device.'

I have no idea what has happened, since it never happened before and I can't troubleshoot. Either the BIOS settings have automatically switched (back) to secure boot (in which case: why would it do this ... can a distribution upgrade force this?), OR Ubuntu 20.10 no longer needs grubx64.efi to boot, but instead shimx64.efi. What I did find out is that when I boot from file, and I point it towards shimx64.efi, Ubuntu DOES boot.

But it is truly anoying that I don't get the grub menu anymore.

Can anyone explain what has caused this problem and/or help me fix this?

Thanks in advance!

PS: one obvious option would be to check my BIOS settings, but I can't do that, since it is a laptop from work. Someone else has to do this, and I would first like to get an idea of the problem before I have to go to helpdesk. It would even be better if I could fix it myself.

---

### Post by Antoon Stessels on 2020-10-23
PS: this is what the screen looks like:

[https://www.tenforums.com/attachments/installation-upgrade/69446d1485964538t-cant-install-windows-new-ssd-installed-new-win10-laptop-photo.jpg](https://www.tenforums.com/attachments/installation-upgrade/69446d1485964538t-cant-install-windows-new-ssd-installed-new-win10-laptop-photo.jpg)

---

### Post by ajgreeny on 2020-10-23
Windows updates can often re-enable secure boot apparently, so first thing to do is check that, assuming you can still boot to Windows.
I do not use Windows any more so I don't know the details of disabling secure boot, but you definitely need to check that out before making any changes to other settings.

As you can not access the BIOS/UEFI yourself, I also assume that your employer will be aware that you have Ubuntu installed on the machine alongside Windows, otherwise I suspect you would not have been able to install Ubuntu in the first place.

---

### Post by Antoon Stessels on 2020-10-24
Thanks for your help.

Yes, I can still boot to Windows, although I don't ever use it. I can't imagine when Windows could have done an upgrade since I only work in Ubuntu, and that's why it surprises me that secure boot problem has only started happening after my Ubuntu upgrade.

Anyway, you are right, my employer is aware that I'm dual booting and has enabled me to create a second partition with Ubuntu. There is no other way than to go back to the helpdesk and explain that somehow the secure boot has been re-enabled. They are going to have to change the BIOS settings again.

Thanks again.

---

### Post by grahammechanical on 2020-10-24
Microsoft Windows also needs updating. Microsoft provides a database file of trusted boot loaders. A few months ago a serious vulnerability was detected in the Grub boot loader. The vulnerability was fixed along with a few other vulnerabilities but the patched boot loaders (actually a shim of code) had to be certified as trusted by Microsoft. This was done but there was another problem older versions of Ubuntu (indeed all Linux distributions that use a shim) would not have the patched versions of Grub. So, they had to be blacklisted. 

It may be that your system needs an update to the Microsoft secure boot database file to allow secure boot to accept the bootloader in 20.10. Here is the Ubuntu blog article that explains it all. I did not find it an easy read. I think I understand it correctly.

[https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities](https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities)

Paragraph 5 (a long paragraph) explains the complications in fixing this vulnerability. I do not have a UEFI system. If I did I would certainly not disable secure boot. Not after reading this article.

Regards

---

