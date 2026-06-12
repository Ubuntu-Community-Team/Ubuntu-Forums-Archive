---
title: "cannot boot from HDD"
date: 2011-12-08
forum: Installation &amp; Upgrades
---

### Post by Long Chuen on 2011-12-08
New to Ubuntu.  Been trying to install newest version onto HDD, unsuccessfully.  
Even though I went through the whole installation process, the computer does not offer choice of which operating system to boot from.  Can only press F12, then boot from USB stick.
Sometimes when using Ubuntu, screen goes blank as if asleep, but computer is still running; unable to shut down, so I pull the power cord.
Tried reinstalling and replacing the OS, but it just pretends to go through the whole process, then boots up in Windows again. 
I'm not a computer expert at all so I need help switching over to Ubuntu successfully.
Thanks

---

### Post by oldfred on 2011-12-08
Welcome to the forums.
Pulling the plug often causes issues. 
Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

Is it starting to boot and you have a video issue.

To see if it is a boot issue, post this:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install mawk

This will also run script and may make minor repairs:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

