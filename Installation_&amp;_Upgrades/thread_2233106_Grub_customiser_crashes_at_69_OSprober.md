---
title: "Grub customiser crashes at 6/9 OSprober"
date: 2014-07-06
forum: Installation &amp; Upgrades
---

### Post by lift_test on 2014-07-06
12.04 is running on a fairly old machine that has had several different HD configurations.  It will boot into Ubuntu or XP fine but I want to change the default to ubuntu and also delete many older versions that apply to non existant HDs.  as the title says it crashes every time when loading the OS prober.  Any suggestions please?

---

### Post by yancek on 2014-07-06
If you have entries for systems which are no longer installed, you could try just running:  sudo update-grub and see what the output is.  Are you saying that os-prober starts but then fails?  What happens, error or warning messages?  Is the bootloader the Ubuntu 12.04 Grub?  What does the "6/9" in your title refer to?

Making Grub the default is different.  If you are using the 12.04 Grub as the bootloader, I would expect it to be the default unless it was changed.  If you are indeed using the Ubuntu 12.04 bootloader to boot, you can boot 12.04 and use this command:  sudo gedit /etc/default/grub to open that file.  There should be the line below near the top of the file: 

```
GRUB_DEFAULT=0
```

The zero means it will default boot the first menuentry in grub.cfg.  If you want to boot a different one, count the menuentries til you get to the one you want.  In this instance, Grub counts from zero, so for the fifth menuentry you would put a number 4.

---

### Post by yancek on 2014-07-06
If you have entries for systems which are no longer installed, you could try just running:  sudo update-grub and see what the output is.  Are you saying that os-prober starts but then fails?  What happens, error or warning messages?  Is the bootloader the Ubuntu 12.04 Grub?  What does the "6/9" in your title refer to?

Making Grub the default is different.  If you are using the 12.04 Grub as the bootloader, I would expect it to be the default unless it was changed.  If you are indeed using the Ubuntu 12.04 bootloader to boot, you can boot 12.04 and use this command:  sudo gedit /etc/default/grub to open that file.  There should be the line below near the top of the file: 

```
GRUB_DEFAULT=0
```

The zero means it will default boot the first menuentry in grub.cfg.  If you want to boot a different one, count the menuentries til you get to the one you want.  In this instance, Grub counts from zero, so for the fifthe menuentry you would put a number 4.

I don't use Grub Customizer so that may be part of the problem.  You can run os-prober from a terminal:  sudo os-prober

---

### Post by lift_test on 2014-07-06
The 6/9 refers to the bottom line of the customiser which states 1 of nine loading etc it always crashes at 6 of nine  ie Os prober.

vic@oldfaithful:~$ sudo update-grub 
[sudo] password for vic: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-65-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-65-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-64-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-64-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-61-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-61-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-60-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-60-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-58-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-58-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-57-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-57-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-56-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-56-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-52-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-52-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-51-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-51-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-49-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-49-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-48-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-48-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-45-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-45-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-44-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-44-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-41-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-41-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-40-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-40-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-39-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-39-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-38-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-38-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-37-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-37-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-36-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-36-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-34-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-34-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-33-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-33-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-32-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-32-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Ubuntu 12.04.1 LTS (12.04) on /dev/sda2
Found Ubuntu 10.10 (10.10) on /dev/sda5
done
I thought that you weren't supposed to edit grub directly in 12.04 but I'm probably wrong.

---

### Post by grahammechanical on 2014-07-06
Grub-customizer is most likely tripping up because of the large number of Linux kernels that have been collected. You can test to make sure that the latest 2 or 3 kernels work fine by booting into them from the Grub menu. I am referring to vmlinux-3.2.0-65; vmlinuz-3.2.0-64 and vmlinuz-3.2.0-61. Once you have made sure that they work and get you to a desktop you can remove all the other kernels in that list from vmlinuz-3.2.0-23 to vmlinuz-3.2.0-60.

Synaptic Package manager will do that for you. Search for each image and mark it for complete removal. That will leave just 3 kernels in the boot menu and that should not trip Grub-customizer up.

You may need to run

```
sudo update-grub
sudo grub-install /dev/sda
```

that should also put Ubuntu 12.04 on top of the list if of course you are doing all this from 12.04 and not 10.10. By the way update-grub is just a script that runs a grub utility called grub-mkconfig. And it is that grub utility that does all the work of detecting other operating systems and populating the grub configuration files and then uses those file to create grub.cfg. From the Grub manual

> Normally, grub-mkconfig will try to use the external os-prober program, if installed, to discover other operating systems installed on the same system and generate appropriate menu entries for them.

We do not edit grub.cfg but we can edit the other grub configuration files such as /etc/default/grub.

Regards.

---

### Post by mörgæs on 2014-07-06
Ubuntu 12.04 is not the best choice for an old computer. One option is to delete all Buntu systems, possibly leaving XP though it's unsupported, and install Lubuntu 14.04 in the free space. Remember to choose 'something else' during install.

---

### Post by lift_test on 2014-07-12
> **mörgæs said:**
> Ubuntu 12.04 is not the best choice for an old computer. One option is to delete all Buntu systems, possibly leaving XP though it's unsupported, and install Lubuntu 14.04 in the free space. Remember to choose 'something else' during install.
Not too sure about that, 12.04 was a bit rude about the graphics hardware when it was installed.

---

### Post by lift_test on 2014-07-12
> **grahammechanical said:**
> Grub-customizer is most likely tripping up because of the large number of Linux kernels that have been collected. You can test to make sure that the latest 2 or 3 kernels work fine by booting into them from the Grub menu. I am referring to vmlinux-3.2.0-65; vmlinuz-3.2.0-64 and vmlinuz-3.2.0-61. Once you have made sure that they work and get you to a desktop you can remove all the other kernels in that list from vmlinuz-3.2.0-23 to vmlinuz-3.2.0-60.

Synaptic Package manager will do that for you. Search for each image and mark it for complete removal. That will leave just 3 kernels in the boot menu and that should not trip Grub-customizer up.

You may need to run

```
sudo update-grub
sudo grub-install /dev/sda
```

that should also put Ubuntu 12.04 on top of the list if of course you are doing all this from 12.04 and not 10.10. By the way update-grub is just a script that runs a grub utility called grub-mkconfig. And it is that grub utility that does all the work of detecting other operating systems and populating the grub configuration files and then uses those file to create grub.cfg. From the Grub manual


We do not edit grub.cfg but we can edit the other grub configuration files such as /etc/default/grub.

Regards.
Thanks for info, sorry to be dense but package manager seems to list an old one if I search for it but marking for removal is greyed out.  I'm typing eg "vmlinuz-3.2.0-23" into the search box, it shows up in the "All" pane but not in any other pane.

---

