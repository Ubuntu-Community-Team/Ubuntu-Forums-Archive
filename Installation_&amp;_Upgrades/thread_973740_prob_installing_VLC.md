---
title: "prob installing VLC"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by bilol on 2008-11-07
Hi,
I am very new to Linux. To install VLC when I am getting the following error .Please help.

```
scott@scott-desktop:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vlc

```

---

### Post by Gyruss on 2008-11-07
VLC contains code which implements technologies which are patented in many countries, meaning if you use a copy of that code you may owe patent royalties to the owners of the patents in those countries. As a result, Ubuntu can't take the legal risk of distributing it with their core repositories.

You need to go into Synaptic Package Manager, go to options and add the Multiverse repository to the list. Then do an update and try to install it again.

VLC has their own little page on this:
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by Ellaine on 2008-11-07
Here is everything you would want:
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

### Post by DustofDust on 2008-11-09
[http://www.videolan.org/security/sa0810.html](http://www.videolan.org/security/sa0810.html)

> Security Advisory 0810

Summary           : Buffer overflows in VLC RealText and CUE demuxers
Date              : November 2008
Affected versions : VLC media player 0.9.5 down to 0.5.0
ID                : VideoLAN-SA-0810
CVE reference     : CVE-2008-xxxx, CVE-2008-xxxx

Details

When parsing the header of an invalid CUE image file or an invalid RealText subtitle file, stack-based buffer overflows might occur.
Impact

If successful, a malicious third party could trigger execution of arbitrary code within the context of the VLC media player.
Threat mitigation

Exploitation of this issue requires the user to explicitly open a specially crafted file.
Workarounds

The user should refrain from opening files from untrusted third parties or accessing untrusted remote sites (or disable the VLC browser plugins), until the patch is applied.

Alternatively, the VCD and Subtitles plugins (libvcd_plugin.* and libsubtitle_plugin.*) can be removed manually from the VLC plugin installation directory. However, this will prevent use of subtitle files and Video CD altogether.
Solution

VLC media player 0.9.6 addresses this issue. Patches for older versions are available from the official VLC source code repository 0.9-bugfix branch.
Credits

These vulnerabilities were reported by Tobias Klein.
References

The VideoLAN project
    [http://www.videolan.org/](http://www.videolan.org/) 
VLC official GIT repository
    [http://git.videolan.org/?p=vlc.git](http://git.videolan.org/?p=vlc.git) 
Tobias Klein
    [http://www.trapkit.de/advisories/](http://www.trapkit.de/advisories/) 

History

3 November 2008
    Vendor notification.
4 November 2008
    Internal patches for VLC development version and 0.9-bugfix tree.
5 November 2008
    Initial security advisory.
    VLC media player 0.9.6 released.

Rémi Denis-Courmont,
on behalf of the VideoLAN project


i just looked around but only the buggy and vulnerable 0.9.4 is in the repository of multiverse!

---

