---
title: "Fails to boot after initial install"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by HydenPLainsite on 2008-01-18
Making a test server on an old IBM Aptiva PC (wasn't good for anything else). 

Downloaded and installed Ubuntu Server 7.10 Live CD reverted to a "text mode install" but made it through the process OK.

Also Installed prior to initial boot:
DNS
LAMP
MailServer
OpenSSH

Fails to boot successfully the first time.
- ACP Bios age fails cutoff (1998 not 2000)
- Fails to load a serial driver module as it may corrupt an eprom but it keeps moving forward in the boot process
- Gets to a login prompt but does not wait, it starts loading bind and the rest of the boot process
- Hangs when it gets to "running local boot scripts (/etc/rc.local)

That's as far as we get.

My theories
The beast I am trying to run it on is too old or does not have enough resources to run as a server (I ran the venerable Red Hat 9 on it previously).

It's just a testing server so I don't care if I have to reformat it or anything.
Any suggestions on getting it to boot?
Hyden

System Info (Yes I really am trying to run it on this box that I call the beast):
Pentium II 350 MHz
96 MB RAM
8.4 GB IDE Hard Drive
4096 KB Video Ram

It groans when it is running ;-)

---

### Post by HydenPLainsite on 2008-01-18
OK I think I may have found the problem. Maybe someone can confirm.

Looks like I should pay more attention to the minimum install requirements. The system does not have enough ram for a regular install. It also is slower than the required 500 MHz.

It appears I could try using xUbuntu installed with an Alternate CD installation disk.
If you have any suggestions let me know.
Hyden

---

### Post by Partyboi2 on 2008-01-18
> **Server Edition**

 While it is possible to install the Server release on a "legacy machine" (e.g. a 75 MHz [Pentium]("http://en.wikipedia.org/wiki/Pentium") with 32 MB of RAM),[[71]]("http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29#_note-55") the "minimum requirements"[[72]]("http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29#_note-SystemRequirements") for good performance are:[LIST]
[*]300 MHz x86 processor
[*]64 MB of [RAM]("http://en.wikipedia.org/wiki/RAM") [[73]]("http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29#_note-ServerGuide710")
[*]500MB of disk space [[73]]("http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29#_note-ServerGuide710")
[*]VGA graphics card capable of 640x480 resolution
[*]CD-ROM drive[/LIST]I think you should be able to install the server version.
This might be of interest
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
If you are able try updating your bios, which should sort out > ACP Bios age fails cutoff (1998 not 2000)

---

