---
title: "Installing Ubuntu on Vista"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by G-Izzat on 2007-03-25
Hi there,guys. I'm new here.

I'm quite interested with the ubuntu 7.04 Beta.
I've downloaded the iso and will now burn it to a cd.

But I've a few questions I want to ask. I've Vista Business on my notebook and only have one volume and around 60gb available. What am I suppose to do now? I've heard about partitioning the hard disk.
Will do that after getting some replies.

If I install ubuntu 7.04beta, I will be able to update to the final release easily,right?
What other things should I know about installing Ubuntu on my notebook?

Hope you guys can help me as I will really appreciate it.

Thanks.

---

### Post by confused57 on 2007-03-25
You might want to read through this thread:
[http://www.ubuntuforums.org/showthread.php?t=391186](http://www.ubuntuforums.org/showthread.php?t=391186)

---

### Post by ssican on 2007-03-25
See also this How to:  [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by G-Izzat on 2007-03-25
**Thanks for the links, guys.**

I just bought a sony vaio SZ series with Vista pre-installed on it (around 60gb left,I think) with only one partition (C:).

So, first, I have to resize the Vista partition using the Vista Disk Manager, then I can just install Ubuntu on the new partition, right?

By the way, after installing ubuntu 7.04 beta, will I be able to use the motion eye camera that the notebook has? Or will I have to find the drivers first?

I'm sorry for asking so many questions. I did some research on how to install it and all, but I'm still a bit worried. I do know that I want to try and use Linux from now on.

And I guess I have to back-up everything on my notebook on a DVD then.

---

### Post by Jose Catre-Vandis on 2007-03-25
Just tested out "Shrink Volume" on Vista Ultimate. I had a 25GB partition, of which 14Gb was used. Vista offered 7.5GB to shrink so I took the offer and clicked Go. Only took about a minute (good!) and then presented me with unallocated space. All done within the OS. Have not rebooted yet :-) [edit] all booted up fine :-)

Still suggest you back everything up, and have a recovery CD to hand, but this looks like a good feature of Vista, for those seeking to dual boot on their newly purchased but single partition vista PC.

You will find the Computer Management here:

Control Panel (Classic View) > Administrative Tools > Computer Management > UA check > Click on Disk management in the left hand tree.

Then right click on your Vista partition, and select Shrink Volume. Vista will do a check, then offer you space to shrink.

---

### Post by rushkoff on 2007-03-26
And, as I've learned, if you just install Ubuntu 6.10 on a Windows Vista (vaioG1, in my case) without doing that, the GRUB wont' recognize any WindowsVista partition. 

So I don't think I'm going to be able to boot up with any of my Windows stuff again. 

I'm glad there's nothing really important in there - but my wireless modem card only worked on Vista. (More motivation to get/write a script that makes the KPC650 work...)

---

### Post by G-Izzat on 2007-03-26
Successfully installed it on my Vaio SZ43. Wi-Fi works well on 7.04 Beta. Have to find a way on how to make the camera works and the fingerprint thingy.
And also,I'm in Stamina mode. Tried to reboot with Speed Mode,but doesn't work. Any solution? It also detects my Vista partition and I can start Vista normally via GRUB.

Also, at the GRUB menu,there's 2 kernel for ubuntu. 2.6.20-13 and 2.6.20-12.
Tried to modify the filesystem,but I've no permission to do that. Why is this?

---

### Post by Sjoram on 2007-03-26
> **G-Izzat said:**
> Tried to modify the filesystem,but I've no permission to do that. Why is this?

Do you mean parts of your Linux system? Some parts have permissions set so that only root can use.  You will need to open terminal and type sudo nautilus to get root access to file system within GUI.

---

### Post by esodin on 2007-03-26
> **G-Izzat said:**
> Tried to modify the filesystem,but I've no permission to do that. Why is this?

I think you just answered your own question!

In linux some actions/commands require "root" access. That's why some programs will ask you for your password from time to time (just like Vista does now). If you want to run commands as "root" from the terminal you need to use the prefix "sudo". Now be sure what you're doing before you start using "sudo". Linux is not very forgiving when you use sudo, if you inadvertently tell the system to wipe your disk - it will, and there is now way back.

Good Luck

---

### Post by Unhindered on 2007-03-27
> **rushkoff said:**
> And, as I've learned, if you just install Ubuntu 6.10 on a Windows Vista (vaioG1, in my case) without doing that, the GRUB wont' recognize any WindowsVista partition. 

So I don't think I'm going to be able to boot up with any of my Windows stuff again. 

If you computer came with Vista, it's likely new - if you want to start over and try to keep Vista and Ubuntu, and it sounds like some might have found a way to do it, the manufacturer may replace the computer or fix it for you. That's what I'm doing as the Ubuntu 6.1 auto-install wasn't prepared for Vista, and it couldn't boot at all. I need windows for compatibility on a few programs (Quickbooks, some SSH/SFTP software), so HP is going to replace the hard drive for me, with a fresh Vista install.

---

### Post by G-Izzat on 2007-03-27
Anyone can explain to me how to implement the Speed/Stamina feature of the SZ series on Linux? Read a couple of threads regarding it, but can't seem to be sure on what to do. I've a Geforce Go 7400 and the Intel one.

---

