---
title: "Installed Win7, Grub Gone; Tried to reload Grub2; only have a prompt on boot."
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by bladeofgrash on 2010-01-19
Hi,

After upgrading from Vista to Windows 7, my GRUB menu disappeared. 

I tried to follow instructions here on recovering it at [RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=fullsearch&context=180&value=linkto%3A%22RecoveringUbuntuAfterInstallingWindows%22"), unfortunately forgetting I'd upgraded instead of installing a fresh install of Ubuntu 9.10. Thus now I have a mix of Grub Legacy and 2 in my boot folder (I think). 

When I rebooted, I get this screen:

GNU GRUB Version 1.97 beta4
[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else, TAB lists possible device/file completions]

I take it I have replaced my MBR with Grub 2. 

What should I do? Remove Grub 2 and then find the instructions for Grub Legacy?
Re-install Ubuntu? 

Pete

---

### Post by darkod on 2010-01-19
I'm not that much experienced with grub but I wouldn't say you have a mix of the config files. You just have grub2 initial files on the MBR, and no second stage files to find, hence the message.
If you just follow the instructions for 9.04 and use a 9.04 cd from here, I guess it could work.
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Alternatively download and run the script in my signature and it will show which boot files you have and where. You can do that before trying anything else first, if you want to.

---

### Post by bladeofgrash on 2010-01-19
Yes, [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) Worked! (after I re-installed grub)

Thanks!

---

