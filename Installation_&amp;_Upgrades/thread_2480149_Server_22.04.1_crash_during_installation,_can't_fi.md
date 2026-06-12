---
title: "Server 22.04.1 crash during installation, can't find a solution"
date: 2022-10-20
forum: Installation &amp; Upgrades
---

### Post by finnrickerzz on 2022-10-20
I'm at a loss right now, allow me to preface by saying I've tried two different USB devices, flashed the install media a lot and also verified, also tried both with and without installing the update that the installer prompted me to install, but every time it fails while installing grub. I've also tried many random troubleshooting steps people have suggested online (such as disconnecting from the internet)

I'm not too experienced with linux in general, and reading the crash report is way beyond by scope but I found the point where it failed in the .crash which is seen below: (full .crash [here]("https://cdn.discordapp.com/attachments/1032382576112967832/1032382578998640671/1666208521.985448360.install_fail.crash"))

 ```
2022-10-19 19:41:37,968 DEBUG root:39 start: subiquity/Install/install/curtin_install/cmd-install/stage-curthooks/builtin/cmd-curthooks/configuring-bootloader: configuring target system bootloader
 2022-10-19 19:41:37,968 DEBUG root:39 start: subiquity/Install/install/curtin_install/cmd-install/stage-curthooks/builtin/cmd-curthooks/install-grub: installing grub to target devices
 2022-10-19 19:42:00,366 ERROR root:39 finish: subiquity/Install/install/curtin_install/cmd-install/stage-curthooks/builtin/cmd-curthooks/install-grub: FAIL: installing grub to target devices
 2022-10-19 19:42:00,366 ERROR root:39 finish: subiquity/Install/install/curtin_install/cmd-install/stage-curthooks/builtin/cmd-curthooks/configuring-bootloader: FAIL: configuring target system bootloader
 2022-10-19 19:42:00,366 ERROR root:39 finish: subiquity/Install/install/curtin_install/cmd-install/stage-curthooks/builtin: FAIL: running 'curtin curthooks'
 2022-10-19 19:42:00,367 ERROR root:39 finish: subiquity/Install/install/curtin_install/cmd-install/stage-curthooks: FAIL: configuring installed system
 2022-10-19 19:42:01,985 ERROR root:39 finish: subiquity/Install/install/curtin_install: FAIL: Command '['systemd-run', '--wait', '--same-dir', '--property', 'SyslogIdentifier=subiquity_log.2311', '--setenv', 'PATH=/snap/subiquity/3698/bin:/snap/subiquity/3698/usr/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/subiquity/3698/bin', '--setenv', 'PYTHONPATH=:/snap/subiquity/3698/lib/python3.8/site-packages', '--setenv', 'PYTHON=/snap/subiquity/3698/usr/bin/python3.8', '--setenv', 'SNAP=/snap/subiquity/3698', '--', '/snap/subiquity/3698/usr/bin/python3.8', '-m', 'curtin', '--showtrace', '-vvv', '--set', 'json:reporting={"subiquity": {"type": "journald", "identifier": "curtin_event.2311.3"}}', '-c', '/var/log/installer/subiquity-curtin-install.conf', 'install', 'cp:///tmp/tmp9a3o0m_3/mount']' returned non-zero exit status 3.
 2022-10-19 19:42:01,985 DEBUG subiquitycore.common.errorreport:384 generating crash report
 2022-10-19 19:42:02,056 INFO subiquitycore.common.errorreport:406 saving crash report 'install failed crashed with CalledProcessError' to /var/crash/1666208521.985448360.install_fail.crash

```

can anyone help me find the issue here?

---

### Post by MAFoElffen on 2022-10-21
Does the computer BIOS boot as Legacy CSM or UEFI? What is the computer?

---

### Post by finnrickerzz on 2022-10-22
UEFI, its a HP Compaq 8200 Elite. BIOS is a bit old (J01 v02.15) however and is from 2011, cant seem to find a newer ROM image online without having to use their windows application that updates ir. SKU is A2K17ET#ABU if it helps you determine anything

---

### Post by MAFoElffen on 2022-10-22
It would be in your best interest to update the ROM BIOS. There are Windows Boot images that are available just to do that...

When you are booted in the Ubuntu 22.04 Server Live Install, in the partitioner, You should indicate the EFI partition that will be the UEFI boot partition. 

Is the disk empty with no partitions? Does it have a GPT or MBR partition table?

---

### Post by finnrickerzz on 2022-10-22
not exactly sure what you mean for any of this, but when booting up without selecting the live boot it does boot up from the disk i was trying to install to and prompts for login from a user called localhost, i'm guessing the installation is incomplete.

In terms of upgrading the BIOS, i've spent hours trying to figure out where to find a ROM and managed to extract the ROM from the windows utility installer just for it to not work, I'll put the old drive in the server with W10, update the BIOS with the utility, try again and report back. I'm hoping the new BIOS will fix this.

---

### Post by finnrickerzz on 2022-10-22
yeah nope, upgraded bios to v2.28 and nothing. v2.29 is a couple years newer but apparently has some kinda hanging issue for restarting so im not sure if its worth the risk for it to potentially not work.

---

### Post by MAFoElffen on 2022-10-22
Boot from an Ubuntu Desktop LiveCD and could you please post /var/log//installer/subiquity-client-debug.log from the system to an Ubuntu pastebin? (paste.ubuntu.com) Then post the link to that here in a post...

---

### Post by finnrickerzz on 2022-10-24
Those files don't seem to be present when booting on the desktop LiveCD, and I tried installing wondering if that was what you meant and interestingly enough the setup worked flawlessly (although that log file still isn't there) At this point I've put way too many hours into trying to fix this and I think I'll just settle for doing a guiless ubuntu desktop installation unless you think that's a bad idea for something acting as a server.

---

### Post by yancek on 2022-10-24
>   prompts for login from a user called localhost, i'm guessing the installation is incomplete.


When you see localhost, have you tried entering the user name you created during the install and hitting the Enter key to get a password  prompt?  Since you have no GUI, you would be booting in level 3 and that's what I usually see when I boot a system in level 3.

---

### Post by MAFoElffen on 2022-10-25
If you install as GUI desktop... Test it to make sure the install went okay, then if your goal is still "Server Edition", then do
```

sudo apt install ubuntu-server

```
That will convert the "Edition" back to a true console "Ubuntu Server Edition". 

There are so many ways to get to a goal in Linux. LOL

Edit:
One note, all my servers have 'openssh-server' installed as a minimum. Then I have a post-install script of console-only apps and an on-demand minimal-X instance with some lightweight GUI apps that I just use during maintenance. (Just me).

---

### Post by finnrickerzz on 2022-10-26
wow really, it's that easy? Always forget how linux just works in some aspects. Alright then that's perfect. While we're here what management/maintenance/monitoring utilities do you recommend? Or is there a list somewhere you can recommend? Just looking to set it up as a plex, web and file server.

---

### Post by MAFoElffen on 2022-10-27
I'm old-school and have my own project call The Ama-Gi Project, which is a Console-based Ubuntu Distribution. It has some basic console-based applications (with a Text menu) and then an on-demand X-instance with some a light-weight desktop and some light-weight GUI applications. Which means, the Desktop exits back to console. So I have some experience working in console. It is still in test/development. I did update it for 22.04 LTS. It was meant as a LiveCD to rescue installed Linux systems. That is where the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") is from...

My management strategy for Linux Servers is remote ssh management from a Linux Workstation, where I can ssh into servers and run scripts for management of. Easy enough to paste things into a graphical terminal session that is logged into my server's. Though, I have a bit of scripting experience. 

I would start here at this Sticky in the Server section: 
[Useful Links on Servers, System Administration, and Security.]("https://ubuntuforums.org/showthread.php?t=1046738")

Then I would start a thread asking your question on a Server Management or Service Monitoring recommendation, in the "Server Section". Everyone has their own favorites.

---

