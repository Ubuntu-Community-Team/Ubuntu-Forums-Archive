---
title: "Installing Plop on a disk with encryption"
date: 2012-06-21
forum: Installation &amp; Upgrades
---

### Post by Stonecold1995 on 2012-06-21
I have a computer where both / and /home are encrypted with LUKS.  I'd like to install Plops boot manager though.  I'm worried that it will overwrite data when it installs, because the Plop installer runs *before* the encrypted disks are mounted, so I don't think it has any way of knowing that it's about to overwrite encrypted data.  To test this, I installed Kubuntu 12.04 on VirtualBox with full disk encryption, and then installed Plop.  When I reset the VM, Plop started up.  However, when I told Plop to boot from the hard disk, it gave an error saying there is no valid boot signature, asking if it should continue anyway ([screenshot]("http://i49.tinypic.com/35903tf.png")).  When I press "yes", the screen just turns black and stays that way ([screenshot]("http://i49.tinypic.com/ao7cz.png")).

So my question is, how do I install Plot boot manager on a machine with LUKS disk encryption?  I followed the instructions [here]("http://www.plop.at/en/bootmanager/mbrinstall.html"), btw, but it didn't mention anything about disk encryption.

---

