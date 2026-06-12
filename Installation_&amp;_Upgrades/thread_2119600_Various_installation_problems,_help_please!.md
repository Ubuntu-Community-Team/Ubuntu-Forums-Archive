---
title: "Various installation problems, help please!"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by rossotorres on 2013-02-24
I am beyond desperate right now. I hope that you can help me!

I've been trying to install Ubuntu on my 64 bit machine for about two weeks now. But either Ubuntu or my computer are acting up.

Here's a list of what I tried and what the results were:

**Ubuntu 12.04 LTS and 12.10**

[LIST=1]
[*]On a CD: Trying to boot from the boot menu always results in an error message: "**/caspter/vmlinuz file not found"**
[*]On a bootable USB-stick: When enabling "nomodeset" in the boot options, it successfully boots to the desktop most of the time. Without "nomodeset", either a strange and distorted view of the Ubuntu desktop appears, or the monitor turns off/goes black and will stay like that until I restart the computer.
[/LIST]
Note: Both methods gave me errors during the bootscreen, saying that some file along the lines of "microcode" was missing. This error didn't stop the booting process, though.



**Kubuntu 12.04 LTS and 12.10**[INDENT]On a bootable USB-stick: It installs and boots just fine, until the desktop is supposed to appear. The whole screen seems to be offset, pushing windows into one end of the screen and making them come out on the other end. Just completely weird.


[/INDENT]I am completely hopeless right now, considering that I already kicked my Windows 7 off the computer.


I'll gladly give you all required information about the computer. All I know right now is that the processor and the graphics card are made by AMD, I'll investigate a little more.


Please help :(

---

### Post by gordintoronto on 2013-02-24
What brand and model of computer? Laptop or desktop? Memory? Video adapter? CPU? If it's a desktop, monitor brand and model, connected how? You can get some of this information by opening Terminal, and running the command:
lspci

If your computer requires nomodeset, you should specify it when booting Kubuntu from the hard drive.

---

### Post by darkod on 2013-02-24
Try downloading new ISO file, and make a new cd on low speed (4x or 8x). Don't burn at max speed since that can make errors even without telling you. Try downloading by torrent because it checks for corruption during download.

If you need nomodeset to load the live mode correctly, you can do the install but you will need nomodeset again on first boot to get the OS loaded and activate the video driver.
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

But video issues don't explain the /casper/vmlinuz error. That file should be on the cd as part of the ISO. That's why I suspect a corrupt ISO or damaged burning, too fast.

Todays CDs and burners accept up to 56x but never burn an OS install cd on more than 4x, 8x, or similar.

---

