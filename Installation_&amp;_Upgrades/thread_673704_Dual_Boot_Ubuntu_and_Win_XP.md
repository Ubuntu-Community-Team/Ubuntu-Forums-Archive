---
title: "Dual Boot: Ubuntu and Win XP"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by kacike76 on 2008-01-20
Hi: 

I am currently running a Dell Dimension 8200 with 1.7 GHz x86 Intel Processor, 256 MB of RAM and two WD IDE HD's (80GB and 60GB). First and foremost: I am a newbie to Ubuntu. I had been running XP until recently on my 80 GB HD and decided to experiment with Ubuntu 6.06, so i installed it on my secondary drive (60GB).  I followed the instructions posted on this website: [http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu](http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu)
As the author recommended, i configured my 80 GB HD (with Win XP already installed) as the slave and my blank 60 GB drive as the master. I booted of the Ubuntu 6.06 Live CD and installed on the 60 GB drive.  Installation seemed to go flawlessly.  I rebooted my PC after the install and Ubuntu 6.06 boots fine, but when i try to boot of XP in GRUB boot loader i get the following error: **error 21: selected disk does not exist **.  I may also add that i set up my XP disk with 4 NFTS partitions.
Concerned about the integrity of the existent data in my XP disk i removed the Ubuntu drive and configured the XP disk as the master and Win XP didn't boot.  However, when i reversed the configuration to make the XP HD the master and the Ubuntu drive the slave XP comes up fine.  My XP installation is still ok, but i am not able to have a dual boot system as this reverse configuration of XP as the master and Ubuntu as the slave doesn't give me an option at boot time.  I decided to try a newer version of Ubuntu to see if this would help any, and installed Ubuntu 7.10 over the previous 6.06 install to no avail. In fact, this just made my problem worse as my current screen configuration only supports a resolution of 1024x768 and it seems i am unable to display ubuntu 7.10 at the login in prompt.  Is it possible to change the screen resolution before booting to Ubuntu 7.10? I am still unable to select win XP professional from the GRUB boot loader when running 7.10.  

Thank you very much for any advise.

---

### Post by torgrot on 2008-01-21
Dell uses cable select hard drive cables.  So you can't use master and slave jumper setting on the drives reliably.  The drive at the end of the cable is the master and the drive in the middle of the cable is the slave.  Change the jumpers on the drives to Cable Select, connect your windows drive to the end of the cable and try to boot windows.  If it does move the Windows drive to the middle connector on the cable and connect the Ubuntu drive to the connector on the end of the cable.  Reboot and hit F2 to go into the bios.  Make sure that both drives are detected.  Reboot again, hopefully into Ubuntu.  Once that is done check this  link to find the steps to update menu.lst with the correct parameters.  [http://users.bigpond.net.au/hermanzone/p15.htm#Fiesty_Fawns_new_menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#Fiesty_Fawns_new_menu.lst)

torgrot

---

### Post by kacike76 on 2008-01-21
Thanks for the info.  Followed the first part of your directions with no problems.  Windows boots fine when both jumpers are in cable select and the Win XP disk is made the master (by plugging to the end cable).  However, when the Linux disk is the master and i go into BIOS the windows drive is not detected.  Should i reinstall Ubuntu with this new hardware configuration....that is with the Ubuntu drive as the master and the Windows XP as the slave both with the jumper on cable select?  Or else how do i get BIOS to see my XP drive? 

Again, thanks

---

### Post by torgrot on 2008-01-21
In the bios try selecting both drives to auto detect, bios should detect them both then.  Save and exit.  It should boot into Ubuntu then.

torgrot

---

### Post by kacike76 on 2008-01-21
My current BIOS version (A04) only sees the drive that is configured as Master.  I am currently looking at at a possible BIOS upgrade but don't know if there is one for my old system.  I don't see the slave drive to be able to "auto detect." Any other thoughts?

Thank you
Kacike

---

### Post by confused57 on 2008-01-21
On my Dell, I had to go set the slave drive controller to "Auto" in bios:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

I see torgrot has already suggested this.

---

### Post by kacike76 on 2008-01-21
Yes! problem fixed.  That was easy....i feel pretty stupid now.  Thanks a lot guys.  Now that i can use my dual boot system... i have two other issues/questions: 

1) i use a KVM switch that attaches to my PC via USB, is there a way to enable this at the GRUB window so that i can select what OS to boot while connected to the KVM

2) More importantly, i am unable to see the login in window when booting into Ubuntu...it seems that my monitor is complaining it can display whatever resolution is configured by default.  My monitor supports 1024x768.  Is there a way to change the display resolution settings of Ubuntu before booting into the OS

Thank you, 
Kacike

---

### Post by confused57 on 2008-01-21
> **kacike76 said:**
> Yes! problem fixed.  That was easy....i feel pretty stupid now.  Thanks a lot guys.  Now that i can use my dual boot system... i have two other issues/questions: 

1) i use a KVM switch that attaches to my PC via USB, is there a way to enable this at the GRUB window so that i can select what OS to boot while connected to the KVM

2) More importantly, i am unable to see the login in window when booting into Ubuntu...it seems that my monitor is complaining it can display whatever resolution is configured by default.  My monitor supports 1024x768.  Is there a way to change the display resolution settings of Ubuntu before booting into the OS

Thank you, 
Kacike

You can remove any higher resolutions in your xorg.conf...open a terminal(Applications---Accessories---Terminal):
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
make 1024x768 your highest resolution

I'm not sure about your KVM switch, you might be able to go into bios and see if you have something like "USB Legacy" , that you can try enabling.

---

### Post by Anadhi on 2008-05-05
Hello, just today I installed ubuntu 7.10 in my BenQ S41 laptop, the installation itself was no problem, until I rebooted and saw no option to dual boot to windows xp. I wonder if I have done something wrong? 

I follow this guide ([http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)).

The author said, to make the windows xp available in the Grub boot screen, we must type "4" in the default.

Honestly I'm not sure about this, because intially, my windows xp was installed in D:\ instead C:\. After resizing the partition, I allocate 4 gb for Linux and created another swap in dev/sda9

My windows installation file is in sda5, does that mean instead of type "4" in the grub's defaultnum, I must write 5?

---

### Post by Oriolo on 2008-05-05
Hi Anadhi!
The default number has nothing to do with the partition on which windows is installed. The number relates to the entry number in the grub menu list, which stands for the OS you want your machine to boot unless you tell it otherwise.
You should edit your grub menu by entering in a terminal:
> sudo gedit /boot/grub/menu.lst
In the file that opens (be careful when you edit it!) look for the line that looks something like:
> title		Microsoft Windows XP Home Edition
and count which number of "title" it is, starting from 0. For instance, if there are 4 instances of "title" before that one, then you should make the default 3.
If there is no entry for window xp, then you should add one. In my menu.lst it is:
> title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1 
but of course it depends on the your configuration and you'd rather check what exactly you should add there.

---

### Post by Anadhi on 2008-05-05
Hi Oriolo, thanks for the explanation, I have checked the menu.lst, but I don't seem to find it anywhere, after the "End default options" I only found this line:
```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1f770a29-e383-4a85-910b-f32996631f8a ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1f770a29-e383-4a85-910b-f32996631f8a ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


```

I dont really understand it, but I suppose it happens because the ubuntu alter the mbr which is vital to the windows xp? To be honest I dont remember whether ubuntu gave me choice to write something or not, but I could be wrong.

Also it appears, normally all dual-boot computer have that line, is it safe I just pasted it in the menu.lst, and change the value into "4"?

Thanks in advance for the explanation, I really am newbie, so I hope you don't mind If I might ask too much.

---

### Post by Dharmaboy on 2008-05-16
> **confused57 said:**
> You can remove any higher resolutions in your xorg.conf...open a terminal(Applications---Accessories---Terminal):
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
make 1024x768 your highest resolution

I'm not sure about your KVM switch, you might be able to go into bios and see if you have something like "USB Legacy" , that you can try enabling.

Hey Guys I am trying this on a Toshiba Satellite 1800. I know the lcd goes to 1024x768 as I am dual booting with XP, and that M$ OS does it no problem with the Trident Cyblade XP card. But in Kubuntu, i am now stuck at resolutions UNDER 800x600.

The above code does nothing. just a warning that overwriting can cause issues. I have already backed up my xorg.conf file in the same folder using a different thread as a guide.

Any ideas why I cant change anything using the reconfigure xserver-xorg past the stupid keyboard layout questions? I get nothing for trying to change or put a resolution in place.

thanks in advance.

---

### Post by confused57 on 2008-05-16
> **Dharmaboy said:**
> Hey Guys I am trying this on a Toshiba Satellite 1800. I know the lcd goes to 1024x768 as I am dual booting with XP, and that M$ OS does it no problem with the Trident Cyblade XP card. But in Kubuntu, i am now stuck at resolutions UNDER 800x600.

The above code does nothing. just a warning that overwriting can cause issues. I have already backed up my xorg.conf file in the same folder using a different thread as a guide.

Any ideas why I cant change anything using the reconfigure xserver-xorg past the stupid keyboard layout questions? I get nothing for trying to change or put a resolution in place.

thanks in advance.

I had to install Nvidia drivers with Hardy & use nvidia-settings in order to change my resolution...since you don't have Nvidia, you might try:
```
xfix
gksudo displayconfig-gtk
```

---

