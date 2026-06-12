---
title: "Wubi w/ 9.10 failing on Dell 14z"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by paulmops on 2009-12-12
I just received a Dell 14z with Windows 7. I installed Ubuntu onto a flash drive, and which works well. Unfortunately, this feels excessively slow. So, I installed Wubi, and now I see an odd screen when I attempt to fire up Ubuntu (from the wubi install, not the flash drive). 

When I boot up, I get an option between Win7 and Ubuntu. I select Ubuntu, and 3 commands flash on screen really fast (too fast to read). Then a GRUB prompt appears, and nothing happens.  

I try the command "boot", and receive a message about no Kernel being present. I'm fairly new to linux, and would love to learn more. Wubi seems like a great introduction. Unfortunately, I can't get it to work :(

Ideas and suggestions are appreciated.

---

### Post by donnellymp on 2009-12-21
@paulmops I have the same laptop and run Ubuntu 64-but Ubuntu Karmic on it with no problems. It sounds like you already managed to install the restricted driver for the wireless, so I won't bore you with those details.

If you need Windows for a few things and have a Windows 7 CD from dell, I'd install Ubuntu on the laptop and then run Windows 7 in a virtual machine on VMWare or Virtualbox (see [http://ubuntuforums.org/showthread.php?t=1345489](http://ubuntuforums.org/showthread.php?t=1345489)). (So basically the opposite of what you're doing now.) You can grab the Ubuntu file for free here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads). This way you can run Windows 7 as needed (for Adobe apps or iTunes, say), but use Ubuntu for everything else. 

The other alternative is installing Ubuntu and, during the install, setting up your laptop to dual boot Windows and Ubuntu so you can switch back and forth.

Hope this helps.

---

