---
title: "Windows in a Virtual Box"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by jerryk1234 on 2011-05-10
Hello,

    I'd like to install Ubuntu 10.10 on my main desktop.  However, there are a few things that I use constantly that are available only in Windows.  I envision installing Windows 7 to run inside virtualbox.   Has anybody done this?  Mostly I'm worried about the Microsoft piracy protection, even though my copy of Windows is legally purchased, and it would essentially be on the same PC.

   Thanks in advance,

                                          - Jerry Kaidor ( [EMAIL="jerry@tr2.com"]jerry@tr2.com[/EMAIL] )

---

### Post by sv87411 on 2011-05-10
I run both Windows XP and Vista in virtual machines in VirtualBox 3.12 installed in Ubuntu 10.10 64bit and they both run just fine. I am sure VirtualBox 4.06 would work just as well, I just haven't upgraded yet because I don't feel it's stable enough yet.

I also need Windows for business payroll software and so need to maintain an environment for that. I run two XP VMs - one for official business work and one for 'messing around'.

I created the Vista VM recently as the company that provides my payroll software are stopping support for XP. I used the OEM Vista business license that came with my laptop (immediately removed when I put Ubuntu on it straight out of the box). Vista product activation worked fine using the license key printed on the underside of my laptop. The performance score in Vista isn't great at 1.0, but it's the VMs graphics that mainly let it down.

My laptop is a Lenovo R61e with dual core 2.1Ghz and 2Gb RAM and I allocated 512Mb to my XP VMs and 768MB to the Vista VM. The VMs boot very quickly and I have never had any issues once the VirtualBox guest additions are installed in the VM.

I think Ubuntu as your primary OS and Windows in VMs is the best solution rather than the other way around. ;)

I hope this helps.

---

