---
title: "Request install method 14.04 encrypted to a second disk dual boot windows"
date: 2014-05-26
forum: Installation &amp; Upgrades
---

### Post by rmoseus on 2014-05-26
Have looked for how to's but have not found.  While I tried LVM, it is not necessary.

Windows is on sda.
sdb has an failed Ubuntu root and encrypted LMV install, but does not accept the correct password.  Ready to format and start over.

Previous user of Linux mint Debian 12 encypted install after lengthy cli and many websites reviewed as I recall, but am wanting something more standardized.
Am a noob with basic understanding of linux, hoping Ubuntu documentation is better.  Details are helpful.

If removing other harddisks has an auto install, advise.  I'd rather unplug a drive than spend hours reading.

Thanks New User wannabe.

---

### Post by oldfred on 2014-05-26
I do not use encryption, but there are two choices. The full drive LVM encryption or the /home encryption.

Better to disconnect Windows drive and even have a full back up of the Windows drive anyway as you always should.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Is system BIOS or UEFI. Whichever you want to install Ubuntu in the same boot mode and how you boot installer is how it installs.

Herman has several examples of LVM installs:
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

