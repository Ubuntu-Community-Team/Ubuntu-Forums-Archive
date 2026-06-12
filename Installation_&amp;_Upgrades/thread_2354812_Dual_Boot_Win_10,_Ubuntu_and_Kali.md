---
title: "Dual Boot Win 10, Ubuntu and Kali"
date: 2017-03-06
forum: Installation &amp; Upgrades
---

### Post by the1nonly12 on 2017-03-06
Quick question on dual booting. I have Windows 10 on an SSD with a separate HDD for games and programs. I want to install Ubuntu and Kali on a separate HDD. To do this, I plan on disconnecting the SSD and HDD to not mess up my Windows installation and then select the OS I want to boot into during PC start up. By selecting the Linux HDD, will I get the option for either Ubuntu or Kali through Grub?

---

### Post by Bucky Ball on 2017-03-06
> **the1nonly12 said:**
> By selecting the Linux HDD, will I get the option for either Ubuntu or Kali through Grub?

Welcome. Yes. You can add Windows to it as well if you want. Be aware that Kali is not officially supported on these forums. ;)

Unsure what you're getting at with the rest of it. Yea, unplug the Win drives during Ubuntu install to avoid accidentally wiping Win, but not sure what you mean once installed. When you have Ubuntu (and Kali) working as you want, plug in the Win drives, open a terminal and

```
sudo update-grub
```

Reboot and Win should be on the grub list at boot as well.

* It is important you do some research and know what you intend to do prior to actually doing it. (That might sound counter-intuitive, but you'd be surprised how many people just decide to install Ubuntu, launch into it experimenting 'on the fly', sometimes with disastrous results or needing to install eight times to get a working system! Best to have some good idea (and feel at least a little confident about it). :)

You have Win10? _Win10 is installed in UEFI mode_ and so, if you intend have all drives in the machine and all three OSs bootable eventually, *_Ubuntu has to be installed in UEFI mode_* as well. There's somewhere to start with your research. 

(Something to remember is that, on some machines, they will refuse to boot from anything but sda, or the first drive plugged into to slot 1 (SATA). If you're Ubuntu install is to sdb (the second drive) and you are having issues booting to it after install, that might be the issue. Just thought I'd mention in case. Good luck.)

---

### Post by RobGoss on 2017-03-06
In order for you to get the options to boot ether OS, I believe they need to be installed on the same hard drive along with the Grub menu, which gives you the choice to boot each system.

---

### Post by the1nonly12 on 2017-03-06
Sorry if I wasn't clear, I'll have in my system 1 SSD for Windows and 2 HDD's. The SSD and 1 HDD are for Windows OS and programs installed to this. The 3rd HDD will only have on it Ubuntu and Kali. I can select the boot drive by using the boot menu built into the BIOS. This will allow me to select either my SSD or HDD that has Linux on it. My question is whether the Linux HDD will take me to the grub menu to show me Ubuntu and Kali only? I don't want Grub to see my Windows installation or have anything to do with it.

---

### Post by RobGoss on 2017-03-06
If you're going to install Ubuntu and Kali, on The 3**rd HDD**, then yes you should be able to also install the boot loader on the same drive which will give you the Grub menu also

---

### Post by the1nonly12 on 2017-03-06
Thanks, I thought that this would work but wasn't 100% sure. :D

---

### Post by Bucky Ball on 2017-03-06
> **RobGoss said:**
> In order for you to get the options to boot ether OS, I believe they need to be installed on the same hard drive along with the Grub menu, which gives you the choice to boot each system.

You believe wrong. :)

---

### Post by the1nonly12 on 2017-03-06
> **Bucky Ball said:**
> You believe wrong. :)

Thanks, just read your edited post also.

---

### Post by RobGoss on 2017-03-06
> Sorry if I wasn't clear, I'll have in my system 1 SSD for Windows and 2 HDD's. The SSD and 1 HDD are for Windows OS and programs installed to this. 

So these drives will not have any Linux operating systems correct?


> My question is whether the Linux HDD will take me to the grub menu to show me Ubuntu and Kali only? I don't want Grub to see my Windows installation or have anything to do with it.

If this is the case then keep the **Grub boot loader** on the Linux partition / **3rd HDD** if you don't want Windows to use the Grub menu to boot anything but Ubuntu and Kali

From reading your post I get the impression you don't want Windows to have anything to do with the Grub or Linux partitions
 
As mentioned you should do your home work before you attempt this because you will and can, remove your Windows OS as well if not done correctly

---

### Post by oldfred on 2017-03-07
If new UEFI system, you have to install Ubuntu in UEFI boot mode. And then grub only installs to drive seen as sda with UEFI boot.

If old BIOS system, then you need to install Ubuntu in BIOS boot mode and install grub2's boot loader to same HDD as Ubuntu install.
You can use either the old MBR partitioning or the newer gpt partitioning for the Ubuntu drive whether UEFI or BIOS. But Windows only boots from gpt with UEFI and only from MBR with BIOS. Windows since Vista 64 sees Windows formatted partitions on gpt drives, and can use them for data, but will not read Linux formatted partitions.

Either way if Windows 8 or later, you must have fast start up off in Windows for grub to be able to boot Windows.
If Windows drive(s) disconnected, you just need to run 'sudo update-grub' to get Windows boot added to grub menu. But only if same boot mode and only if Windows fast start up off.

Best to use Something Else as install option.
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[URL="https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT"]https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT
[/URL]
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 

      
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond) 
    [URL="https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT"]
[/URL] 
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

