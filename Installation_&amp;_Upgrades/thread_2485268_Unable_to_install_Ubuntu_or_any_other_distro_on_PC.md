---
title: "Unable to install Ubuntu or any other distro on PC"
date: 2023-03-24
forum: Installation &amp; Upgrades
---

### Post by kovacsakos on 2023-03-24
[COLOR=#232629][FONT=-apple-system]Windows is installed on following PC, but Linux install fails. I have tried multiple distros, all of the installers have stucked on logo screen.[/FONT][/COLOR]
[HTML]CPU
    Intel Pentium E5200 @ 2.50GHz
    Wolfdale 45nm Technology
RAM
    3,00GB Dual-Channel DDR2 @ 403MHz (6-6-6-18)
Motherboard
    ASUSTeK Computer INC. P5QL/EPU (LGA775)
Graphics
    K-700 (1024x768@85Hz)
    1024MB ATI Radeon HD 4600 Series (Sapphire/PCPartner)
Storage
    465GB SAMSUNG HD502HJ ATA Device (SATA )
Optical Drives
    HL-DT-ST DVDRAM GSA-4167B ATA Device
Audio
    High Definition Audio[/HTML]

---

### Post by ubfan1 on 2023-03-24
Have you tried Lubuntu or Xubuntu, a lower requirement dist?  Ubuntu itself has a min ram requirement of 4GB.

---

### Post by guiverc on 2023-03-24
This was also asked at [https://askubuntu.com/questions/1460749/unable-to-install-ubuntu-or-any-other-distro-on-pc?noredirect=1#comment2556120_1460749](https://askubuntu.com/questions/1460749/unable-to-install-ubuntu-or-any-other-distro-on-pc?noredirect=1#comment2556120_1460749)

Basics.
[URL="https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0"]
- Did you verify the ISO after download?[/URL]  

- Did you write the ISO using software that was QA-tested to work with that product/release ?   (If you *clone* the ISO to media you'll have fewer issues, but some software doesn't *clone* meaning the software needs to support the OS/release you're trying to use, or it'll boot on some hardware but not others (ie. boot on uEFI but not legacy, or boot on legacy but not uEFI etc).

- Did you verify the write of ISO to media?  (*this is where I experience most issues*).   How you do this varies on OS/release which you didn't specify.

These steps rule out *procedural* type issues, leaving you with the hardware issues, but you're wasting your time exploring hardware issues until you rule out procedural (*in my opinion, & note I write 200+ ISOs a year to media & thus experience more issues than most*).  The early steps take mere *secs* or at most a *minute*, but save many hours of problem-solving (*also rule out tons of issues* too), and details matter. You've provided none.

FYI:  I used hardware as old as from 2003 in QA of releases up to 19.04, and 2005 for newer releases.

---

### Post by QIII on 2023-03-25
Can you tell us the exact process by which you are trying to install Ubuntu?

---

### Post by coffeecat on 2023-03-25
> **guiverc said:**
> This was also asked at [https://askubuntu.com/questions/1460749/unable-to-install-ubuntu-or-any-other-distro-on-pc?noredirect=1#comment2556120_1460749](https://askubuntu.com/questions/1460749/unable-to-install-ubuntu-or-any-other-distro-on-pc?noredirect=1#comment2556120_1460749)

And also asked at Kubuntu forums: [https://www.kubuntuforums.net/forum/newbie-support/help-the-new-guy/669369-unable-to-install-kubuntu-or-any-other-distro-on-pc](https://www.kubuntuforums.net/forum/newbie-support/help-the-new-guy/669369-unable-to-install-kubuntu-or-any-other-distro-on-pc), and linuxquestions.org: [https://www.linuxquestions.org/questions/linux-general-1/unable-to-install-ubuntu-or-any-other-distro-on-pc-4175723395/](https://www.linuxquestions.org/questions/linux-general-1/unable-to-install-ubuntu-or-any-other-distro-on-pc-4175723395/)

---

### Post by kovacsakos on 2023-03-25
@coffeecat : Yes.

@QIII: I downloaded iso, after that opened Rufus, choosed MBR and left anything else on its default value.

---

