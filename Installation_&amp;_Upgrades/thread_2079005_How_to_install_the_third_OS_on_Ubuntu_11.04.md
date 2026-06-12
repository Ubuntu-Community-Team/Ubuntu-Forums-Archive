---
title: "How to install the third OS on Ubuntu 11.04"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by shinokada on 2012-11-01
I run Ubuntu 11.04 and Windows 7(Norwegian) on a Dell  Latitude. Now I would like to install Windows 7 (Japanese). I googled to  find how to install the third OS on Ubuntu, but not able to find one.
  Could anyone tell me how to do or website explaining how to do it?
  Thanks in advance.

---

### Post by 2F4U on 2012-11-01
> **shinokada said:**
> I run Ubuntu 11.04 and Windows 7(Norwegian) on a Dell  Latitude. Now I would like to install Windows 7 (Japanese). I googled to  find how to install the third OS on Ubuntu, but not able to find one.
  Could anyone tell me how to do or website explaining how to do it?
  Thanks in advance.

What exactly do you mean? Install the second Windows 7 besides the existing and Ubuntu, i. e. triple-boot, or run the second Windows 7 from Ubuntu? In the second case you could do that by using e. g. VirtualBox, which is a virtualization environment that allows you to run guest systems on your main system, i. e. you would be running Ubuntu and Windows 7 would run inside the VM, but both would run in parallel.

---

### Post by shinokada on 2012-11-01
Thanks 2F4U,

I have to run a Japanese accounting system on Windows Japanese. I used the virtual box, but it seems a bit slow. So that's why I want to run Windows7 or 8 Japanese.

---

### Post by mörgæs on 2012-11-01
By the way, 11.04 is out of support. Best is to delete this one and do a fresh install of 12.04 or 12.10.

---

### Post by shinokada on 2012-11-01
Can I upgrade to 12.04 without affecting other OS?

---

### Post by mörgæs on 2012-11-01
The upgrade will not affect Windows, it will only wreck Ubuntu. 

Joke aside, Ubuntu upgrades are always risky. Go for a fresh install in stead.

---

### Post by oldfred on 2012-11-02
An install of Windows will overwrite the MBR, so have liveCD or USB to be able to repair Ubuntu.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Windows normally moves all the boot files from a second install into the first install. Then grub can only find one install to boot. If you want separate boot entries in grub you have to install separately.


To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

