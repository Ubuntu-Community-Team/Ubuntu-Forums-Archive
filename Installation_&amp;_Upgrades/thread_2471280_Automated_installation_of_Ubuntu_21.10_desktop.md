---
title: "Automated installation of Ubuntu 21.10 desktop"
date: 2022-01-25
forum: Installation &amp; Upgrades
---

### Post by gombara on 2022-01-25
Hello. I have been trying to automate Ubuntu 21.10 desktop installation with a preseed file. It looks like the said Ubuntu installation medium has no longer isolinux forlder. I think in this case preseed file should be referred in th grub.cfg file. The grub.cfg file I am trying is:

set default=0
set timeout=0

loadfont unicode

menuentry "Ubuntu Auto Install" {
        set gfxpayload=keep
        linux    /casper/vmlinuz file=/cdrom/preseed.cfg auto=true priority=critical fsck.mode=skip debian-installer/locale=en_US console-setup/layoutcode=us quiet ---
        initrd    /casper/initrd
}


Unfortuanately I have not been able to get the automated install going. It just lands into live desktop. The preseed file can be found since syslog etc does not complain about missing file. I have also realized that manual installation I start from the live session desktop pick some variable like user name from my preseed file. Following is that part of my preseed file:

d-i passwd/user-fullname string test
d-i passwd/username string test
d-i passwd/user-password password changeme

I am a bit at lost here. Can someone give me a few pointer where to look for debuggin this etc? Anything would be appreciated.

---

