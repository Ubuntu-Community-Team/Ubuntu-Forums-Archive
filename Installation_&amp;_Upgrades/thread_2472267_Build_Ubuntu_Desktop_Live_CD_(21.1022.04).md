---
title: "Build Ubuntu Desktop Live CD (21.10/22.04)"
date: 2022-02-22
forum: Installation &amp; Upgrades
---

### Post by pdeclercq on 2022-02-22
Hi,
I've been using a nice script from guthub called ubuntu-preseed-iso-generator which (with minor adaptations) does what I need (remaster the ISO with some customizations).
Trying to build the 21.10 and 22.04RC) I run into trouble.
With 20.04 all works fine. It uses isolinux and EFI in a "hybrid" mode (xorriso).
From 21.10 it seems isolinux is not present anymore on the original iso file. The build fails because it is using files from isolinux, and efi.img from /boot/grub/

[https://help.ubuntu.com/community/LiveCDCustomizationand](https://help.ubuntu.com/community/LiveCDCustomizationand)
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

do not help, they do not seem updated with the method currently used to build the ubuntu desktop install iso images for 21.10 and 22.04.

I've tried modifying the xorriso command, but could not get it to create a new iso based on the original iso file.

Thanks for any clues/suggestions (or where to find the appropriate info to build the final iso.

---

### Post by MAFoElffen on 2022-02-23
Ubuntu 20.04 Desktop Used the older debian-installer, which preseed file still worked for. Ubuntu 20.04Server Edition uses the newer Live Installer.

Ubuntu 21.10 Desktop and newer use the newer Live Installer, which uses the Live Installer files in .yaml format (that you linked to) Also, you can install packages with the Server Edition, using cloud-init, where you could install anything to end up with whatever (such as ubuntu-desktop). 
[https://ubuntu.com/server/docs/install/autoinstall-quickstart](https://ubuntu.com/server/docs/install/autoinstall-quickstart)
[https://ubuntu.com/server/docs/install/autoinstall-reference](https://ubuntu.com/server/docs/install/autoinstall-reference)
[https://help.ubuntu.com/community/CloudInit](https://help.ubuntu.com/community/CloudInit)
[https://cloudinit.readthedocs.io/en/latest/](https://cloudinit.readthedocs.io/en/latest/)
[https://cloudinit.readthedocs.io/en/latest/topics/examples.html](https://cloudinit.readthedocs.io/en/latest/topics/examples.html)

---

### Post by pdeclercq on 2022-02-24
Hi [ 						 							 						 					]("https://ubuntuforums.org/member.php?u=1044547") 				 				 					 						 	[**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547")[B][COLOR=#DD4814][B],
[/B][/COLOR][/B]
Thanks for your answer. Unfortunately cloud init is not an option here. We are in an environment where we install using pxeboot, and use a "mirror" repository of ubuntu. Due to the "unguaranteed" availability of an external connection we don't want to rely on "internet" connected soloutions.
The problem stays the same, we want to re-master the Ubuntu Desktop installation iso, and include a "full automatic" installation (using preseed/ubiquity).
This works fine with 20.04, using a "hybrid" state combining isolinux (bios boot) and EFI (secure boot in our case), with a vast amount of documentation available for the "isolinux" way. But how it's currently set-up from Ubuntu 21.10 I don't have a clue how to re-create the iso (after extracting all files from the iso to a temp folder, and customizing).
I don't want to start a discussion about "cloud init" and the "cloud way" of going. We expect the installation to continue even if an interhet connection is not available.
If there is any documentation on how to build the 21.10/22.04 LiveCD image with EFI only boot loader, I'll be (hopefully) on track again.

---

### Post by MAFoElffen on 2022-02-24
The first two links I gave you were for the newer Automatic Installer of the Live Installer. That is what it is now with Ubuntu. Not my choice or prefrence. I'm just the messenger of what has happened (to me also). And you can still build a newer LiveCD, but you need to use what is there and works for it, with it. Sorry, but the choice for using PreSeed was taken away from us. Answers to me were the ability is still there, but it is different, in a different form.

I do PXE boot/installed images for deployments using Fog Server... If you are doing PXE images, then why are you doing preseed in images that supported it? I do transfer of compressed pre-configured, generic images, that take hardly any time to transfer to the target machine. I have scripts that then kick off to grow the partitions to what is there, once the images are on the target machines. I do this at a Computer Recycler, where I recondition machines for resale. I don't have the luxury of any kind of standardization of hardware, as I have to work with what we get. With those, I don't have to play with any automated installs of OS'es (by installing each through an installer), except if I am creating new images for deployment to put onto the deployment server.

We did that in the past. It would take 'forever', especially compared to how we do it now. I played with a lot of different 'methods' before we got to what we have now... Including 'local repo's' and custom ISO's on Easy to boot drives, autmated installs from PXE, etc. Above is what we evolved to. It is now fast and easy.

But that's just me. For commercial customers, I have to use the new 'Automatic Installer' Scripts. Why? Because the ability for me to use my old, trusty 'preseed' scripts with Ubuntu went away. I feel your pain. I do.

---

