---
title: "Installer freezes while &quot;Scanning all devices&quot; in partition editor"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by Emacs User on 2006-08-30
To my miserable dismay I've been unable to install Ubuntu 6.06.

I have a few partitions with different operating systems on my harddrive so I need to select the option to manually edit the partition table in the installer.

The installer then shows a progress meter and a message that it is "Scanning all devices". This runs jerkily for a while before completely locking up - the progress meter and mouse cursor are frozen and no input is accepted. As such, I cannot view any logs to determine what caused the seizure.

I have found a few other references to this problem on the web but no solutions.

As I have already set up and formatted the partitions is there some way to bypass the partition editor and move straight to selecting the mount points?

Alternatively, is there some way I can prevent the installation process from "scanning all devices" by explicitly specifying the harddrive or something?

Or any other suggestions?

Thanks in advance,

Joel

---

### Post by Emacs User on 2006-08-31
I was able to resolve this by disabling the Multimedia Card Reader in my machine and reattempting the installation.

My BIOS did not support disabling the reader so I had to physically it the reader from the motherboard. The installer then ran without incident and Ubuntu was installed.

---

