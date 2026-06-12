---
title: "Cannot boot into Ubuntu from Windows boot loader"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by Paragon009 on 2011-04-16
I created a dual partition install of Windows 7 Pro x64 (first) and then Ubuntu 10.04 (second).
 
For the Windows, my HD was configured as follows:
 
sda1: 100 GB NTFS Reserved System 
sda2: 450 GB NTFS for Windows 7
 
For the Ubuntu install, it was configured as follows:
 
Extended partition:
sda5: /root (15 GB)
sda6: swap (15 GB)
sda7: /home (90 GB)
 
During the Ubuntu install, I chose the "Advanced" option and decided to install GRUB 2 boot loader on sda5 (/root).
 
The reason I did this is because I did not want GRUB 2 to be the boot loader. Instead, I wanted to use the Windows boot loader.
 
Ideally, I am looking to have a **Windows** boot menu with Windows 7 and Ubuntu 10.04 on it. I followed the instructions [on here]("http://www.rightnowintech.com/2010/08/use-windows-bootloader-to-boot-windows.html"), but they didn't help, at all.
 
My current situation is that when I boot up, the computer skips a boot menu altogether (no list of OS's to choose) and simply boots straight into Windows 7.
 
I cannot access Ubuntu, at all. The only time I had access to it was when I did the Ubuntu install.
 
So, how can I fix this? I know there is a 512 MB file that is used to allow Windows to "see" or boot Ubuntu. But, that's about it.

---

### Post by Dutch70 on 2011-04-16
Edit: Just skip this post then, I'll leave it here in case it comes in handy later. 
As far as the link you're using, I would have left it after it said...
> You find GRUB ugly right? Everyone does. It's supposed to be better and cleaner, but it is so restricted and hard to edit.
That statement is just totally incorrect, maybe it wasn't at the time it was written, but it is now. 

----------------------------------------------
AFAIK, you have to use Grub2 to boot Ubuntu.
Lets have a look at your boot info script.

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]

Then open a terminal (Cntrl+Alt+T) and run the following command...
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just click the # symbol in the toolbar & paste it between [CODE] [ /CODE] tags.

---

### Post by hayashi on 2011-04-16
> **Paragon009 said:**
> I created a dual partition install of Windows 7 Pro x64 (first) and then Ubuntu 10.04 (second).
 
For the Windows, my HD was configured as follows:
 
sda1: 100 GB NTFS Reserved System 
sda2: 450 GB NTFS for Windows 7
 
For the Ubuntu install, it was configured as follows:
 
Extended partition:
sda5: /root (15 GB)
sda6: swap (15 GB)
sda7: /home (90 GB)
 
During the Ubuntu install, I chose the "Advanced" option and decided to install GRUB 2 boot loader on sda5 (/root).
 
The reason I did this is because I did not want GRUB 2 to be the boot loader. Instead, I wanted to use the Windows boot loader.
 
Ideally, I am looking to have a boot menu with Windows 7 and Ubuntu 10.04 on it. I followed the instructions [on here]("http://www.rightnowintech.com/2010/08/use-windows-bootloader-to-boot-windows.html"), but they didn't help, at all.
 
My current situation is that when I boot up, the computer skips a boot menu altogether (no list of OS's to choose) and simply boots straight into Windows 7.
 
I cannot access Ubuntu, at all. The only time I had access to it was when I did the Ubuntu install.
 
So, how can I fix this? I know there is a 512 MB file that is used to allow Windows to "see" or boot Ubuntu. But, that's about it.

How long is boot screen up for (i.e. has it defaulted to 0 seconds)? It may be something to do with installing GRUB 2 on a different partition (although I doubt this) but either way, have you tried placing it in its default position? Finally, what happens if you swap the partitions around?

Those were just a few things I could think of although they're fairly basic responses. All the same, I hope one of them solves the issue or gives you an idea on what to do.

EDIT: The above response will probably give you a more thorough idea of what's wrong with your boot. I can't believe I didn't think of it..

---

