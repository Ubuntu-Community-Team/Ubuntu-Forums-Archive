---
title: "Ubuntu Unity won't run after upgrade to 22.10"
date: 2022-12-04
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-12-04
Boot repair output at [https://pastebin.ubuntu.com/p/4mZqWQNNZg/](https://pastebin.ubuntu.com/p/4mZqWQNNZg/) 

PC is hp 840 g1 and is my backup laptop.  It is dual boot with Win10 Pro.  Update to Ubuntu Unity 22.10 on my main laptop (DELL Precision 7720) was done without any problems.  It is also dual boot with Win 11 Pro (Insider Build).

I don't understand what I am supposed to do with the boot repair output.  Other dual boot machines upgraded to Ubuntu Unity 22.10 with only minor problems (upgrade wiped out non-snap versions of Firefox)

I run dual boot as some of my clients want things done in Windows with MS Office, Adobe Acrobat and Chrome for Windows.

Thank you,

John

---

### Post by grahammechanical on 2022-12-04
How did you run Ubuntu before the upgrade to 22.10? It seems to me that Windows is installed in BIOS/Legacy/Compatibility Support Mode (CSM) and Ubuntu is installed in UEFI mode. I may be wrong about that but if I am right then that is the reason why you have difficulty dual booting. 

Windows boot loader do not recognise Linux operating systems. So, if the motherboard is set to give boot priority to Windows then there will not be an option to load Ubuntu. What do you mean by "Ubuntu won't run?"

Regards

---

### Post by cigtoxdoc on 2022-12-04
Thank you for your reply

This laptop has been running dual boot Ubuntu /Win 10 at least since 20.04 if not earlier.  It was running fine before the upgrade with 20.04 LTS and Unity 7.6.  So the question remains of how to interpret what the output of boot repair telling me.  What do I do next?  Last resort will be to remove Ubuntu and then reinstall Unity/Ubuntu 20.10 using the download that is available at [https://ubuntuunity.org/download/](https://ubuntuunity.org/download/).  Everything of value is on the exFAT partitions.  Email is all IMAP and current email data are on the DELL laptop and can be moved using the backup and restore functions in evolution.

John

---

