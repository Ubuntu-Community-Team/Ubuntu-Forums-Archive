---
title: "trouble preseeding 10.04 install from usb"
date: 2012-06-02
forum: Installation &amp; Upgrades
---

### Post by anormous on 2012-06-02
Hi everyone,

I've been trying and failing for a while now as try to use a preseeded usb to install 10.04 server.  I wonder if anyone out there could share some advice.

My goal is to have an automated way of installing 10.04 server using a preseeded USB.
  
What I mean by automated is that I don't have to answer any questions during the install.  If things just install without showing the menu, that's cool.  If you have to choose "install" from the menu, that's cool, too.  What I'm trying to avoid is having to manually type in any boot parameters.
  
Here's what I've done so far:
> downloaded iso -- ubuntu-10.04.4-server-amd64.iso
> created USB installer with usb-creator-kde
> rsync'ed USB (named "lucid") contents to directory (named "ubuntu") -- rsync -a -H --exclude=TRANS.TBL /media/lucid/ /ubuntu/
> used the example-preseed file (now found here: /ubuntu/doc/install/manual/example-preseed.txt.gz) to create a very,very simple preseed called preseed.cfg
> modify initrd:
 -- make a tmp dir to work in /tmp/initrd
 -- cp -a /ubuntu/install/initrd.gz /tmp/initrd
 -- cd /tmp/initrd
 -- extract initrd -- gzip -d < initrd.gz | cpio --extract --make-directories --no-absolute-filenames
 -- remove old initrd -- rm initrd.gz
 -- copy in preseed -- cp /path/to/preseed.cfg /tmp/initrd/
 -- make new initrd -- find . | cpio -H newc --create | gzip -9 > /ubuntu/installer/initrd.gz
> update md5 for initrd here: /ubuntu/md5sum.txt
> copy installer back to USB -- rsync -rlptDH --exclude=TRANS.TBL /ubuntu/ /media/lucid

After this I'm having trouble.

If I don't modify syslinux/syslinux.cfg, when booting I get the installer menu, choose "install", and subsequently get an error saying:
[!!] Detect and mount CD-ROM
Your installation CD-ROM couldn't be mounted.  {Blah blah blah...}
Try again to mount the CD-ROM?

I'm not real clear on what needs changing in syslinux.cfg since my preseed is inside initrd.

If I modify syslinux/syslinux.cfg by coping syslinux/text.cfg to syslinux/syslinux.cfg I get stopped by a boot prompt.  
  
(I should add that, on other hardware, using the text.cfg has worked for me.  I did manage to preseed a 10.04 server install using a USB, but not on my current hardware.)

I've read suggestions saying to add "cdrom-detect/try-usb=true" to the boot prompt. But I haven't figured out how to make that work, and more importantly, manually typing parmeters at a boot prompt will not be practical in my situation.

I would be super grateful if anyone could help me figure this out.

Thank you.

---

