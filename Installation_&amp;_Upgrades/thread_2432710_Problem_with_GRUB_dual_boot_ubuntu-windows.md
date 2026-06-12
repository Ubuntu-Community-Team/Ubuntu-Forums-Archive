---
title: "Problem with GRUB dual boot ubuntu-windows"
date: 2019-12-07
forum: Installation &amp; Upgrades
---

### Post by sgunay on 2019-12-07
Dear all
I am having problems with installing ubuntu on my Laptop computer.
In my laptop I have windows 10 installed. 
I try to install ubuntu 18.04.03 LTS on my computer.
However, when I installed, at the beginning system directly boot to the linux.
Probably I have done a mistake which had been done a lot. But I can not fix it now.
Before I had installed ubuntu on my windows desktop computer. A similar problem happened.
Then I had used `boot-repair` program. And I had fixed the same problem. 
But now when I try the recommended button in boot-repair.
System stall with `unhide boot menu. This may require several minutes`
Below is the pastebin
[http://paste.ubuntu.com/p/VtHwGWtm2J/](http://paste.ubuntu.com/p/VtHwGWtm2J/)
Thank you for any help..

---

### Post by yancek on 2019-12-07
Your boot repair output shows that you have an EFI system and you have the windows and Ubuntu files on the EFI partition.  It also shows Grub code in the MBR which should not happen with an EFI install.  The grub.cfg file does not show an entry for windows for whatever reason so the first thing I would do is to boot Ubuntu, open a terminal and run the following to see if a windows entry is created:

```
sudo update-grub
```   

Watch the output for a windows entry.

---

### Post by oldfred on 2019-12-07
Can you directly boot Windows from UEFI boot menu?

Grub only will boot or find to add to boot menu working Windows. That also means Windows cannot be hibernated. Windows with updates will turn fast start up back on which sets hibernation flag, so then grub will not boot it & you have to directly boot from UEFI to turn it off again.
Sometimes grub will not boot Windows because it needs chkdsk. 

If you cannot boot Windows directly from UEFI boot menu and get into its internal repair console or change settings, you will need your Windows repair/recovery flash drive to make repairs.

---

### Post by sgunay on 2019-12-07
Dear yancek
thank you for the answer. the output for the sudo update-grub is the following

Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.0.0-23-generic
Found initrd image: /boot/initrd.img-5.0.0-23-generic
Adding boot menu entry for EFI firmware configuration
done

---

### Post by sgunay on 2019-12-07
Dear oldfred,
thank you for the reply.
When I change the boot priority in the bios utility from 

**ubuntu **to** windows boot manager**

then the computer boot with windows without problem.

**OR**

when I insert a ubuntu 18.04 flash disk and boot from flash disk, and select the windows part then I can also go to Windows.
Otherwise system directly go to the ubuntu without asking anything.
I hope this is what you ask...

---

### Post by oldfred on 2019-12-07
That then sounds like the hibernation flag is set with fast start up on.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by sgunay on 2019-12-07
I disabled the fast start up but nothing changed. 
Do you think grub should be updated with windows option? And how it will be done?

> **oldfred said:**
> That then sounds like the hibernation flag is set with fast start up on.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by oldfred on 2019-12-07
After turning off fast startup in Windows, did you run this so grub2's os-prober could find it?
sudo update-grub

Some NTFS may need chkdsk also if forced shutdown corrupted NTFS. 

From Ubuntu if you click on the NTFS partition does it mount or give the error message on wrong type, etc.

---

### Post by sgunay on 2019-12-07
sudo os-prober
command return with nothing.
from ubunt I click on NTFS parition and it could mount to /dev/sda4

> **oldfred said:**
> After turning off fast startup in Windows, did you run this so grub2's os-prober could find it?
sudo update-grub

Some NTFS may need chkdsk also if forced shutdown corrupted NTFS. 

From Ubuntu if you click on the NTFS partition does it mount or give the error message on wrong type, etc.

---

### Post by oldfred on 2019-12-07
sudo update-grub
not sure if you can directly run os-prober?

---

### Post by sgunay on 2019-12-07
Dear friends,

I find a solution for this problem. And I find it because I am lucky I think.

I write the 

[B]menuentry "Windows 10" {
        insmod part_gpt
        insmod chain
        set root='(hd0,gpt2)'
        chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}[/B]

at the end of "/etc/grub.d/40_custom" file (check the web site [http://www.rodsbooks.com/efi-bootloaders/grub2.html](http://www.rodsbooks.com/efi-bootloaders/grub2.html))
and after that run the command.

**sudo [B]update-grub**
[/B]
this is a bit trial and error. Because you have to determine the right parition. 

It is important here to determine which **gpt**.

And I checked the system with

**sudo fdisk -l**

and figured out that EFI system is at the **sda2**

[B]Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1023999   1021952   499M Windows recovery environment
/dev/sda2    1024000   1228799    204800   100M EFI System
/dev/sda3    1228800   1261567     32768    16M Microsoft reserved
/dev/sda4    1261568 278794239 277532672 132,3G Microsoft basic data
/dev/sda5  278794240 500117503 221323264 105,5G Linux filesystem[/B]

so I write 

**gpt2** in the **40_custom** file as given above. I don't know this is a good way. But it worked.

Also in the **/etc/default/grub** file I erased word **hidden**. So it is only blank like below

**GRUB_TIMEOUT_STYLE=""**

One last thing 
At some point I used the "grub customizer" program. [https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer)
Actually you don't need. But it may help if you cannot succeed.

---

