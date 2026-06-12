---
title: "install from customized live usb session"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by timbao on 2012-02-17
Hi,Sorry if this is asked but my search didn't find a match :)

I used a Ubuntu Desktop 11.10 CD to make a startup disk a 8G bytes live usb startup stick with persistent and used for a couple of days. I am not a newbie to Ubuntu -actually I've been using for years. The reason I want to keep it temporarily on USB stick is that I have a very small SSD(30GB only) and there's a Windows 7 there. Now the persist casper-rw has my customization settings, package updates(and removals). My question is: if I use the usb stick(created from live CD and contains persistence) to boot and install, will the installation to HDD contains
  a) content from both casper/filesystem.squashfs and casper-rw
  -OR- 
  b) simply only the clean original system casper/filesystem.squashfs?

Thanks in advance for any comments =D>

---

### Post by efflandt on 2012-02-17
It will not have any programs that you installed to persistent data, the only thing that would carry over to the install would be certain system settings like timezone and network settings (like wireless security, etc.).

---

