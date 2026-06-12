---
title: "Installing Precise Pangolin Xubuntu 12.04 on M3A32 mobo"
date: 2012-08-29
forum: Installation &amp; Upgrades
---

### Post by doktorOblivion on 2012-08-29
Let me first start with saying that I was finally able to install 12.04 on a system with a M3A32 mobo, however my attempts to do this using a CD-R or DVD were in vain.

Here are my observations:
1.) regardless of how you burn a CD-R or DVD, using k3b or other applications, even on Win7, I could not get the hard media to boot.  In most cases I got a blank screen, even after disabling APCI.
2.) using the old boot from fd did not work, received the same message as booting from some CDs.
3.) therefore, I had to burn a bootable image to pendrive.  To do this I had to use LinuxLive USB creator.  Once booted I had to disable APIC, APCI and other optional boot properties via F6.
4.) after a full install, the system would not boot properly, preferring to scamble my screen, awaiting input that it could never receive since I could not type in any input field.
5.) boot in recovery mode, then it boot using basic Super-VGA mode.  The first thing I did was install the latest NVIDIA driver and rebooted.
6.) was able to login normally.  Just a question of loading apps and configuring the system after that.

---

