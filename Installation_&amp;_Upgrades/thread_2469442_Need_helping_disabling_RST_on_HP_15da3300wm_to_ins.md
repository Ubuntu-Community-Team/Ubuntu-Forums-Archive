---
title: "Need helping disabling RST on HP 15da3300wm to install ubuntu"
date: 2021-11-29
forum: Installation &amp; Upgrades
---

### Post by awmorales on 2021-11-29
Hello everyone, 
I've been using Linux for some years now and I have never had this problem installing the OS. I get an error message after selecting my language that says I need to disable RST to install Ubuntu. I've went to bios and there is no option to turn off RST. Ive searched everywhere on the internet to find a solution but have come up short. I do not have windows anymore so I can't access the RST app or CMD to disable. Can anyone point me in the right direction?

---

### Post by ActionParsnip on 2021-11-29
May help
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

---

### Post by awmorales on 2021-11-29
@ActionParsnip Thanks, but I already tried this. I don't have windows installed so I cannot complete the windows configuration steps... I am almost thinking I may have to get a copy of windows10 just to access the cmd and other windows apps to solve this issue.

---

### Post by macguges on 2021-11-29
Could you clarify what you just said, that you don't have Windows installed?  Do you mean that your computer had no Windows installation present before you encountered this error?  Or had you been able to dual boot into either Windows or Linux before now?

It's important to clarify this because you would not want to install Windows at this point only to recover access to Ubuntu.  The instructions in that article are intended for people who want to preserve dual booting into both Windows and Ubuntu, and so the Windows-specific instructions there are only useful for continuing to boot into Windows.  Following those Windows-specific instructions would not get you any closer to booting into Linux.

---

### Post by MAFoElffen on 2021-12-02
If you go into your BIOS firmware settings, what are the available option under 'Storage Options'? Ensure that your select and change the SATA Mode to AHCI.... That is what that said. 

That has to do with what mode the BIOS SATA settings are set to. That has nothing to do with Windows, since you do not have Windows installed.

---

### Post by awmorales on 2021-12-04
So my solution to the problem was to install 18.04 and upgrade to 20.04. For some reason 18.04 doesn't recognize RST so, I was able to do a fresh install and upgrade with no issues.

---

