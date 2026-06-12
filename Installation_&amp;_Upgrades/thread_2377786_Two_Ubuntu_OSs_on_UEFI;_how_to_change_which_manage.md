---
title: "Two Ubuntu OSs on UEFI; how to change which manages grub?"
date: 2017-11-16
forum: Installation &amp; Upgrades
---

### Post by ajgreeny on 2017-11-16
Can one of you UEFI gurus please help me figure out how I can install 18.04 to a UEFI system that already has a working 16.04, but retain grub being managed by 16.04, not 18.04.

I think I need to use efibootmgr, but as is sometimes the way with man pages, **man efibootmgr** is not as helpful as I would wish; either that or I am not very good at reading and understanding man pages.

My current system has both an unused 14.04 and my current 16.04 on a single hard disk.  I wish to install 18.04 on the 14.04 root partition, keeping my current /home partition as it is, but I will mount it using fstab as a data partition in 18.04, and then use symbolic links to the data folders to avoid any potential config problems between 16.04 and 18.04.

I want 16.04 to retain grub management, not for it to move to 18.04 which I am certain is what will happen at installation of 18.04.
Can I still boot to 16.04 from the 18.04 grub menu and from 16.04 run ```
sudo grub-install /dev/sda
``` as I could with a BIOS system, or does that no longer work?

---

### Post by kansasnoob on 2017-11-16
According to my own notes (which i haven't used in nearly a year) you'd boot into 16.04 and run:

```
sudo apt-get install --reinstall grub-efi
```

Followed by:

```
sudo grub-install /dev/sd**[COLOR="#FF0000"]X[/COLOR]**
``` where [COLOR="#FF0000"]**X**[/COLOR] is changed to the proper drive

```
sudo update-grub
```

But my memory stinks and my notes could be wrong :(

---

### Post by oldfred on 2017-11-16
I think the reinstall of grub from 16.04 may work.

The the real issues is that all versions/flavors (except Kubuntu)  of Ubuntu use one UEFI entry /EFI/ubuntu for booting.
But it turns out the only difference is the 3 line /EFI/ubuntu/grub.cfg configfile (chain type entry) that looks like this:

```
search.fs_uuid 5c1e1a3f-261f-4da5-a0c2-8f479b3039de root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

I have installed multiple Ubuntus in UEFI mode and quickly learned to back up my ESP partition. 
But then learned it really was just the three lines above. Sometimes now I restore a backup of just grub.cfg or other times just edit the grub.cfg with correct UUID & partition.

If in an install the ESP is mounted with 0077 permissions and you cannot edit grub.cfg. I think they probably changed from defaults to 0077 for security reasons, but I change back to defaults. Boot-Repair will also change it to defaults so it can edit entries in the ESP. You should be able to edit from live installer. I now immediately edit back to main working install before leaving the live installer, and then in main working system add or update it to boot new install. I do not use os-prober, but 40_custom entries.

 # /boot/efi was on /dev/sda1 during installation
14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat    defaults        0       1
16.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    umask=0077      0       1

---

### Post by ajgreeny on 2017-11-16
Wow! Thanks both for useful info.

I noticed the three line grub.cfg file in the efi folder of my current 16.04 and wondered if that was what I needed to edit after the 18.04 install but could find no information anywhere in any documentation so that suggestion of yours, oldfred to back up the /efi partition and restore it, or even simply edit the line with the uuid in it makes total sense.

I did not have this problem last time I updated my OS as I waited till 16.04 had been released for about two months to iron out its bugs but this time I want to install 18.04 at this early stage and keep on updating through its development, thus making use of my old 14.04 partition which is currently redundant.

I will report back the success or failure of this action as soon as I have done the installation. Thanks again.

---

### Post by rbmorse on 2017-11-16
Rod Smith's rEFInd was made for this situation.  It will find all the valid .efi boot stanzas on the machine and present them in a colorful (and user configurable) boot selector/menu.  It's so easy it can be used on Macs. 

[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)

rEFInd may be in the Ubuntu repository -- definitly has a ppa that can be added to make it easy to maintain with standard repository  management tools.

---

### Post by ajgreeny on 2017-11-17
I installed Xubuntu-18.04 this afternoon without a problem, and as was expected that OS then took over grub.
I had already backed up my /boot/efi/ folder from 16.04 in order to restore the grub.cfg file from that, so I did not go with rEFInd, about which I know absolutely nothing, so rather than give myself even more possible problems I did exactly what [COLOR="#FF0000"]oldfred[/COLOR] suggested and restored the grub.cfg file from 16.04; very simple to do and needless to say, it did exactly what I wanted.

Thanks again for the info oldfred; it has added quite a lot to my understanding of UEFI boot procedures, which when explained the way you did, are really very straightforward, making this change of my grub-management OS dead easy.

---

### Post by oldfred on 2017-11-17
I think I have said for several years that I wanted to try rEFInd, but have not gotten around to it. 
Grub2 has worked & I understand it pretty well, but still learning.

I installed several other distributions just to see how they handle grub. 
Debian does not do UEFI secure boot and is then a lot simpler. 
Fedora let me directly install grub to sdb.
Some of the distributions do not use the 3 line link to grub.cfg in the install, but put the fully configured grub into the ESP.
And Fedora had this:
      >  The grub2-efi package installs a prebaked grubx64.efi on the EFI System partition, which looks for grub.cfg on the ESP in /EFI/fedora/ whereas the grub2-install command creates a custom grubx64.efi, deletes the original installed one, and looks for grub.cfg in /boot/grub2/. 



Ubuntu's grubx64.efi is also prebaked to look for grub.cfg in /EFI/ubuntu.
I was able to change in /etc/default/grub     this line:
#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR='Ubuntu16.04_Zesty'

And have had full reinstall of grub create new UEFI entry using that name, but it still uses the /EFI/ubuntu/grub.cfg, so changing grub distributor entry does not do much.

---

### Post by ajgreeny on 2017-11-17
> #GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR='Ubuntu16.04_Zesty'
That must have been interesting ;) since 16.04 is not Zesty but Xenial, but typos aside, as I'm sure that was, I have been using that edit of the DISTRIBUTOR line for several years now.

I found the trick in some of the Ubuntu notes about grub configuration in the days when I was still on a BIOS machine with many different versions of Ubuntu OSs with all the DEs to test, which without that edit all showed as Ubuntu in the grub menu and was not much help in knowing which was which; very confusing.

---

### Post by oldfred on 2017-11-17
Good thing oldfred never has typos. :)

Fortunately that is not really used anyway, so not critical.

---

