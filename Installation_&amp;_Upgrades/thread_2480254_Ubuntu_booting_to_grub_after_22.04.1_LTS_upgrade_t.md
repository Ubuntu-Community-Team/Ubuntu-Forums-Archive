---
title: "Ubuntu booting to grub after 22.04.1 LTS upgrade to 22.10"
date: 2022-10-23
forum: Installation &amp; Upgrades
---

### Post by kifou on 2022-10-23
Today I updated from Ubuntu 22.04.1 LTS to Ubuntu 22.10 using *sudo update-manager -d* (updated all packages up to date before that).


Now when I try to boot from the drive I get this message:

```
GNU GRUB  version 2.02
Minimal BASH-like line editing is supported. For the first word, TAB lists possible
command completions. Anywhere else TAB lists possible device or file completions.
grub>
```

Any help to restore the boot process properly?

---

### Post by oldfred on 2022-10-23
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

What brand/model system?

You do have good backups?

---

### Post by kifou on 2022-10-23
This is the error I get from the live ubuntu 22.10 ISO:
```
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt update
Repository: 'deb https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/ kinetic main'
Description:
Simple tool to repair frequent boot problems.

Website: https://sourceforge.net/p/boot-repair/home
More info: https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Adding deb entry to /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-kinetic.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-kinetic.list
Adding key to /etc/apt/trusted.gpg.d/yannubuntu-ubuntu-boot-repair.gpg with fingerprint 3C48D16124B50277AF10D27F32B18A1260D8DA0B
Ign:1 cdrom://Ubuntu 22.10 _Kinetic Kudu_ - Release amd64 (20221020) kinetic InRelease
Hit:2 cdrom://Ubuntu 22.10 _Kinetic Kudu_ - Release amd64 (20221020) kinetic Release
Hit:4 http://archive.ubuntu.com/ubuntu kinetic InRelease                       
Hit:5 http://archive.ubuntu.com/ubuntu kinetic-updates InRelease               
Hit:6 http://security.ubuntu.com/ubuntu kinetic-security InRelease             
Ign:7 https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu kinetic InRelease
Err:8 https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu kinetic Release
  404  Not Found [IP: 185.125.190.52 443]
Reading package lists... Done                               
E: The repository 'https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu kinetic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
Ign:1 cdrom://Ubuntu 22.10 _Kinetic Kudu_ - Release amd64 (20221020) kinetic InRelease
Hit:2 cdrom://Ubuntu 22.10 _Kinetic Kudu_ - Release amd64 (20221020) kinetic Release
Hit:4 http://archive.ubuntu.com/ubuntu kinetic InRelease                       
Hit:5 http://archive.ubuntu.com/ubuntu kinetic-updates InRelease               
Hit:6 http://security.ubuntu.com/ubuntu kinetic-security InRelease             
Ign:7 https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu kinetic InRelease
Err:8 https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu kinetic Release
  404  Not Found [IP: 185.125.190.52 443]
Reading package lists... Done                              
E: The repository 'https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu kinetic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```
```

ubuntu@ubuntu:~$ cat /etc/os-release 
PRETTY_NAME="Ubuntu 22.10"
NAME="Ubuntu"
VERSION_ID="22.10"
VERSION="22.10 (Kinetic Kudu)"
VERSION_CODENAME=kinetic
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=kinetic
LOGO=ubuntu-logo
```

boot-repair is not yet available for kinetic

---

### Post by oldfred on 2022-10-23
You can use a Jammy live installer or download the Boot-Repair ISO which may not be quite as current but will work.

---

### Post by Impavidus on 2022-10-23
It says grub 2.02. That's an old release of grub, used by Ubuntu 18.04. 22.04 is already at 2.06 and so is 22.10. It seems as is you've got an old Ubuntu release in control of grub, failing as that release of Ubuntu was wiped. But you ran an upgrade, not a fresh install. It would be really nice to see the output from boot repair. If you've got a live disk of Ubuntu 22.04, you can run it from there too.

---

### Post by kifou on 2022-10-23
Finally got fixed automatically by tinkering with the boot order on the UEFI BIOS. Just left everything as it was after reordering it and now works every time. It's a weird bug but fixed.

---

### Post by Impavidus on 2022-10-24
Maybe you've got multiple grubs installed and now moved the right one to the top of the boot order. Installing a new grub as part of the upgrade process may have reordered them.

---

### Post by kifou on 2022-11-02
After tinkering with the boot order and basically leaving everything as it was, now says "GNU GRUB version 206" and boots and works perfectly fine. Maybe it's like you say that I have several grub things installed at once. How could I check that? It doesn't look like any UEFI/BIOS error to me... :(

---

### Post by oldfred on 2022-11-02
Boot-Repair report will show where everything is at.

---

### Post by kifou on 2022-11-03
> **oldfred said:**
> Boot-Repair report will show where everything is at.
Can i use Boot-Repair from the regular Ubuntu installation or must I user some live USB operating system?

I run it from my working systems, just to have documentation of my configuration.
And copy it into /home so backup includes it.

---

### Post by oldfred on 2022-11-03
See post #2.
> or any working instal
I have seen where in some cases it may not offer to do repair from a working install. But Report should work.

---

### Post by kifou on 2022-11-06
Boot Repair completed successfully. This is the beginning of the log, is enough or the complete one must be provided?
[ https://paste.ubuntu.com/p/nfVYqM7PSy/]("https://paste.ubuntu.com/p/nfVYqM7PSy/")

---

### Post by ajgreeny on 2022-11-06
We need to see the compiete output to be sure, but how did you manage to copy the link for pastebin and then show only the beginning of the output?

---

### Post by kifou on 2022-11-06
> **ajgreeny said:**
> We need to see the compiete output to be sure, but how did you manage to copy the link for pastebin and then show only the beginning of the output?
I created a new pastebin. The full pastebin contains device UUIDs and other private information that I don't think can publicly disclose. How could I workaround this?

---

