---
title: "Kernel panic &amp; crash while upgrading to 16.04"
date: 2021-02-13
forum: Installation &amp; Upgrades
---

### Post by wht-crl on 2021-02-13
[COLOR=#242729][FONT=Arial]While upgrading to 16.04, The system was just frozen. I had to restart and since then, the system is blocked and caps lock light continues blinking. Note that kernel version is 4.4.0.201-generic.


[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I went to grub, Ubuntu advanced option but if I choose any mode of the kernel, 4.4.0-201 generic, or Upstart, or Recovery mode It shows the black screen (see the attached picture) and nothing could unblock.

how to trouble shoot?

Thanks [/FONT][/COLOR]

---

### Post by Impavidus on 2021-02-13
Are you sure you want to troubleshoot this? You upgraded to 16.04, which means you came from an unsupported release (unless you paid for additional support on 14.04). Upgrading from a release that has been long dead is often problematic and I'm not sure I would trust your system to be secure. What's more, 16.04 itself will reach end of life in just 2 months, so that's another upgrade and another opportunity for things to go wrong. And even that, if successful, won't bring you to the latest LTS release.

Troubleshooting a failed release upgrade is rarely worth the effort, even more so if there are more release upgrades in the pipeline. May I suggest a fresh install?

You can use the live disk to create backups, if you haven't done so already. Depending on how you partitioned your system, you may be able to keep your documents, but make sure you've got backups anyway.

---

### Post by wht-crl on 2021-02-13
I would be happy to install a new one if someone like you could guide me step by step how to do starting by a backup. I have partially backed up but prefer to backup properly.

note that the disk is partitioned in 3 parts, Ubuntu, windows and a 3rd partition for a share between 2 systems. Windows is operational and i don&#8217;t want that it be touched nor the share.

---

