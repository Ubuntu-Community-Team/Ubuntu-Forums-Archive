---
title: "Installing 10.04 on Dell Optiplex 760"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by Tarion on 2010-08-31
Hi,
  As stated, I'm trying to install Ubuntu 10.04 onto a Dell Optiplex 760 wit a Nvidia Geforce9300 GE card.  I believe this card came with the computer, and from what I can tell this computer is [Ubuntu Certified]("http://webapps.ubuntu.com/certification/hardware/200909-4092/").

  When booting from a live CD (64-bit), before reaching the boot menu (with the try, install, memtest, disk check options) the computer waits for 3 minutes (180 seconds) and then displays the following:

```
udevd[85]: worker [95] unexpectedly returned with status 0x0100
udevd[85]: worker [95] failed while handling '/devices/pci0000:00/0000:00:00.0'
udevadm settle-timeout of 180 seconds reached, the event queue contains:
 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 (766)
 /sys/devices/pci0000:00/0000:00:1f.2 (819)
 etc 
```

or something similar.  I tried to work around this by installing 8.04 and following upgrade instructions, and it all seemed to go well (though I had to install an ethernet driver), until it rebooted from the upgrade to 10.04, and gave a similar error.  attempting this was probably dumb, but I was hoping it would carry over whatever drivers or software let it work in 8.04 to 10.04 but this is apparently not the case.  I did let 8.04 install updates before I told it to upgrade.  I've seen similar posts were ubuntu is able to boot if apci is turned to off at boot, but I'm not sure I can do this.  Any help is appreciated, Thanks

---

### Post by Tarion on 2010-09-01
So, I fixed it. :o

For anyone else who runs into this sort of problem, here's how I did it.  I foreshadowed it a bit in my previous post when I said something about acpi.

If you didn't manage an install and/or you're booting from a live CD, and it gets stuck before it even gets to the boot menu, hit F6 when the cd reaches the purple screen with the human and the keyboard. (it might not NEED to be F6, but that's what worked for me so I'm sticking to it), this should bring up the usual boot menu with all the options for what to do with the live CD.  Here press F6 again, and boot options will come up.  The "acpi=off" option should allow you to boot.  Some of the others probably will too (nolapic worked for me), see [this site]("https://wiki.ubuntu.com/DebuggingACPI") for details.  Now you can install if you want to, though the boot options were still wrong for me when I did this, and the install wouldn't boot.  To fix that read on.

If you already managed to install (as I did with the upgrade option), you can change the temporary boot options by going to the grub menu, selecting the version you want to boot, and pressing e on it. In these boot options, add "acpi=off" to the end of the line that starts with "linux".  The should enable you to boot into your installation.  

If grub doesn't show up, hold "Shift" while booting, and it will. (grub probably won't show up without this if you only have one installation.  If you upgraded 8.04 like I did it might)

Lastly, you need to make this change permanent.  Once booted, navigate to /etc/default/ and edit the "grub" file.  
```
sudo nano grub
```
nano or... use your favorite editor.  I can't handle the magic that is vim.  Try gedit if you don't like terminal.  Find the line that says "GRUB_CMDLINE_LINUX=""", change it to 
```
GRUB_CMDLINE_LINUX="nolapic"
```
or whatever boot option worked for you. 

You should now have a booting Ubuntu 10.04.  If you want to know more about boot options, check [grub2]("http://ubuntuforums.org/showthread.php?t=1195275") out.

Hope this helps out other people who were as confused as I was.

---

### Post by wbrb on 2011-02-05
While I managed to get Lucid 64-bit installed without too much fuss -"nolapic" fixed my problem where my optiplex 755 hang on restarting.

---

