---
title: "PXE Install with LUKS Encryption"
date: 2020-05-15
forum: Installation &amp; Upgrades
---

### Post by helyx-rtanley on 2020-05-15
Hi All.

I have been looking for a way to automate the Ubuntu 20.04 LTS install with the following requirements.

[LIST]
[*]PXE Server to provide install resources (TFTP + HTTPD)
[*]UEFI Install onto Physical laptops.
[*]LUKS Disk encryption is enabled.
[/LIST]

Over the last few day I have been reading that the pressed method has been depreciated in 20.04 LTS. Looking at the new method it is to use a cloud config. ([https://wiki.ubuntu.com/FoundationsTeam/AutomatedServerInstalls](https://wiki.ubuntu.com/FoundationsTeam/AutomatedServerInstalls))

I have a few questions about this as I'm not 100% sure how to go about automating this process and got a bit frustrated trying to do so over the last few days :mad:!

[LIST=1]
[*]How do you provide the cloud-init file via PXE boot configuration?
[*]How would i go about setting up disk encryption via automation? I have not found anything except preseeding.
[/LIST]


Thanks in advance.

---

