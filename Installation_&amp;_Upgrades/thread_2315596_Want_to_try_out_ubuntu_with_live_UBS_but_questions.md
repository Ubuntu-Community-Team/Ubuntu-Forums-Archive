---
title: "Want to try out ubuntu with live UBS but questions about UEFI Bios"
date: 2016-02-29
forum: Installation &amp; Upgrades
---

### Post by nzdreamer55 on 2016-02-29
Hello everyone,

I have an older lap top (4 core processor with 2gb RAM) Running Windows 8.1 x64.  A while back I tried to run Ubuntu from a live USB drive and when I wanted to go back to windows, I had booting issues (not sure what happened so no need to comment).

I think I followed this site

[http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install](http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install)

And when I tried to reboot into windows, my computer could not find the windows OS that was on the hard drive.

So I want to try again, but want to make sure that I won't screw up my windows 8.1 x64 OS.  Just want to see how Ubuntu runs on this lap top.

Can someone point me to a tutorial that would address this situation or anything special that I should consider with using Ubuntu with a computer that has UEFI Bios?

---

### Post by sudodus on 2016-03-01
If you do not change anything in the UEFI/BIOS system (the boot menus), there should be no problem with Windows. If you change something in order to be able to boot Ubuntu, you should *take notes*, and afterwards *change it back* in order to boot into Windows again. Sometimes it helps with a shutdown and a cold boot (while some circuits are not reset completely by reboot). You might even need to take out the battery in some extreme cases.

See this link, particularly the chapter about UEFI (if your computer boots in UEFI mode) and links from there.

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

