---
title: "Error when trying to install 24.0.1 LTS"
date: 2024-10-26
forum: Installation &amp; Upgrades
---

### Post by Hishighness on 2024-10-26
Hey all. I'm trying to install Ubuntu 24.0.1 LTS from a USB stick, and it'll start the installation but at the same point every time it stops and says there's an error. Below is the error, and here is [the entire log]("https://pastebin.com/80SUmsj3") if needed. I've been a Windows user the vast majority of my computing life so I'm not as knowledgeable about Linux. I'm actually doing this to try to escape Microsoft, so any help would be appreciated. :)

```
Oct 26 08:27:36 ubuntu subiquity_log.4226[8507]:         Command: ['unshare', '--fork', '--pid', '--mount-proc=/target/proc', '--', 'chroot', '/target', 'apt-get', '--quiet', '--assume-yes', '--option=Dpkg::options::=--force-unsafe-io', '--option=Dpkg::Options::=--force-confold', 'install', '--download-only', 'linux-generic-hwe-24.04'] 
Oct 26 08:27:36 ubuntu subiquity_log.4226[8507]:         Exit code: 100 
Oct 26 08:27:36 ubuntu subiquity_log.4226[8507]:         Reason: - 
Oct 26 08:27:36 ubuntu subiquity_log.4226[8507]:         Stdout: '' 
Oct 26 08:27:36 ubuntu subiquity_log.4226[8507]:         Stderr: '' 
Oct 26 08:27:36 ubuntu subiquity_log.4226[8507]:         Unexpected error while running command. 
Oct 26 08:27:36 ubuntu subiquity_log.4226[8507]:         Command: ['unshare', '--fork', '--pid', '--mount-proc=/target/proc', '--', 'chroot', '/target', 'apt-get', '--quiet', '--assume-yes', '--option=Dpkg::options::=--force-unsafe-io', '--option=Dpkg::Options::=--force-confold', 'install', '--download-only', 'linux-generic-hwe-24.04'] 
Oct 26 08:27:36 ubuntu subiquity_log.4226[8507]:         Exit code: 100 
Oct 26 08:27:36 ubuntu subiquity_log.4226[8507]:         Reason: - 
Oct 26 08:27:36 ubuntu subiquity_log.4226[8507]:         Stdout: '' 
Oct 26 08:27:36 ubuntu subiquity_log.4226[8507]:         Stderr: '' 
Oct 26 08:27:36 ubuntu subiquity_log.4226[8507]:          
Oct 26 08:27:36 ubuntu subiquity_log.4226[8507]: Stderr: '' 
Oct 26 08:27:36 ubuntu subiquity_event.4226[4226]:  executing curtin install curthooks step 
Oct 26 08:27:36 ubuntu subiquity_event.4226[4226]: installing system 
Oct 26 08:27:36 ubuntu subiquity_event.4226[4226]:  
Oct 26 08:27:37 ubuntu subiquity_event.4226[4226]:   curtin command install
```

---

### Post by ajgreeny on 2024-10-27
Nothing very helpful in that output, or not to me though others might see something and I'm using Android tablet at the moment so I'm not going to try viewing the full log.
Did you run the live system from the USB or go straight to the install option? It is always worth running live first to check all seems OK before installing.

Did you check the hashes of the ISO file you used? The instalation always giving an error at the same point seems to point to the ISO being corrupt in some way so it's worth checking that you have a good ISO or downloading again using a torrent

---

### Post by oldfred on 2024-10-27
In addition, what brand/model system, what video card/chip?
UEFI install, how you boot install media is then how it installs.
Dual boot or just Ubuntu?

---

### Post by Rubi1200 on 2024-10-27
Two things to check and try:

1. check network cables or wireless connections are stable during installation

2. try starting from the USB in safe mode (usually the next option below Try or Install)

Let us know if that helps.

---

### Post by Hishighness on 2024-10-27
Looks like it's the USB stick I'm using. Thanks everyone for the help!

---

