---
title: "Dual boot on HP EliteBook 6930p w Win7 (64 bit)"
date: 2013-03-04
forum: Installation &amp; Upgrades
---

### Post by Lammis on 2013-03-04
Hi,
As a complete newbie on Linux I want to try out Ubuntu on my laptop. I made an attempt with the windows installer but it failed to boot. I was prompted with the following message: "Try (hd0,0): NTFS5:".
 
When rebooting with Windows i printed out the following content of the Ubuntu directory:

Directory of C:\ubuntu
 
2013-03-03  20:47    <DIR>          .
2013-03-03  20:47    <DIR>          ..
2013-03-03  20:47    <DIR>          disks
2013-03-03  20:31    <DIR>          install
2013-03-03  20:31         2 501 520 uninstall-wubi.exe
2013-03-03  20:47    <DIR>          winboot
               1 File(s)      2 501 520 bytes
               5 Dir(s)  48 693 121 024 bytes free

My question now is if I have used the correct installer for my system? If not - which one should I use?
If i do have the correct installer what else should I do to isolate the problem? What info do you need to help me?

---

### Post by carl4926 on 2013-03-04
The windows installer WUBI? Is that what you mean. It's not a real install. 
Do you want a real install or WUBI?

---

### Post by Lammis on 2013-03-04
> **carl4926 said:**
> The windows installer WUBI? Is that what you mean. It's not a real install. 
Do you want a real install or WUBI?

Hi [COLOR=#000000]carl4926,
I have used the installer for windows that you download from [/COLOR]http://www.ubuntu.com/download/desktop/windows-installer. Why do you ask about WUBI. I did not mention it in my question. What is that?

---

### Post by carl4926 on 2013-03-04
To install Ubuntu properly
Download the .iso  
Burn the image to a CD and boot from the CD

Try Ubuntu first by running it live from the CD (You can use a USB also)

---

### Post by oldfred on 2013-03-05
Most Windows 7 systems are BIOS, but a few were UEFI which uses gpt.

 Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

      [URL="http://www.psychocats.net/ubuntu/wubi"]http://www.psychocats.net/ubuntu/wubi
[/URL]
 [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

 From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.
[URL="http://www.psychocats.net/ubuntu/wubi"]
[/URL]

---

