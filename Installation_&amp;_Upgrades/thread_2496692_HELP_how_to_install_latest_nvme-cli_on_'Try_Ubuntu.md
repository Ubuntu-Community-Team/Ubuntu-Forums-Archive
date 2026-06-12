---
title: "HELP: how to install latest nvme-cli on 'Try Ubuntu'"
date: 2024-04-08
forum: Installation &amp; Upgrades
---

### Post by ddoubleuc on 2024-04-08
Hi Gang,

When I run 'sudo apt install nvme-cli', I typically get nvme-cli-1.6 or earlier I think, whereas nvme-cli-2.8 appears to be latest. What command/s will install latest nvme-cli?

Having said that, the latest NVME Express Base Spec is Rev 2.0d (Jan 24), so if nvme-cli-1.6 or earlier comply with 2.0d, does latest version matter?

I know 'Try Ubunutu' means reinstalling nvme-cli on every reboot but I'm happy with that for the time being.

Thanks for considering

---

### Post by MAFoElffen on 2024-04-08
If you 'need' that version: A little patience. Wait until April 25th, 2024. (17 days).

Ubuntu Noble 24.04 LTS releases on that Date. The nvmvi-cli package in it is version 2.8-1build2 on the latest source code.

---

### Post by ddoubleuc on 2024-04-09
Thanx MAFoE...

Just for general knowledge though ... if I wanted to install a more recent version of any particular program than the result from cmd ''sudo apt install <program name>', what, if any, most simple command might I use?

---

### Post by MAFoElffen on 2024-04-11
For general knowledge, answering generically:
The usually way would be to go to the project's website and see if they have a facility to installer that newer version. Sometimes that might be in a .deb file (either available for download, or in their repo), an install script, or a source in a tar ball, where you would have to compile it yourself. 

Others, Members might have compiled and packaged newer versions of things into .deb files, into their personal Ubuntu PPA. These PPAs are usually (personally) member supported. Have patience with those. It is a lot of work, and volunteered, on their own, shared with the community.

---

### Post by ddoubleuc on 2024-04-20
Thanx MAFoE for your ongoing patience and wisdom

---

