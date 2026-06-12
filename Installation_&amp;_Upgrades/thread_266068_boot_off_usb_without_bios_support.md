---
title: "boot off usb without bios support"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by madubuntuer on 2006-09-26
Is it possible for me to make a grub cdrom to  make grub boot breezy off my usb hdd? Also I will be using it on different hardware would that be a problem?

---

### Post by nardusg on 2006-10-17
Hi

Did you solved this problem ? I want to do the same :) I am booting from a usb drive and some pc I use can not boot from I usb device. So a cd with grub would be nice :)

Thank

nardusg

---

### Post by nardusg on 2006-10-17
Discoverd this link :)

[http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html)

Try it, I will give feedback tommorow :)

nardusg

---

### Post by thom83 on 2006-10-17
This link

   [http://www.gap.ien.05.ac-aix-marseille.fr/rre/article.php3?id_article=1562](http://www.gap.ien.05.ac-aix-marseille.fr/rre/article.php3?id_article=1562)

discribes install of ubuntu 6.06 on an usb drive and how to make a boot cd for that usb drive. You can try this method if gnu.org link does not work...

Good luck.

---

### Post by mangurian on 2006-10-17
The instructions in the link above are a bit obscure and they assume you already have a linux environment available.

I believe many of us who are on the fence would move to dual boot if they could use an external drive and boot from CD.  I know I would.  This means I would not have to put grub or any dual boot stuff on my "C:" drive.  It appears to be a "riskless" approach.

The live CD is just too slow to be useful, so a USB approach would be great.

If someone could post a disk image of the "grub" boot disk or provide the required files and the appropriate commands to be used in preparing a cd in a Windoze environment, I am sure many would latch on to it.  I am surprised that the core Ubuntu folks have not found this to be a worthwhile install approach.

---

### Post by thom83 on 2006-10-17
I don't speak english well. But i'll try to translate shortly this install on usb disk.

It is not so risky for your "windows" if you pay attention.

I suppose you know how to use Ubuntu 6.06 CD.

When you are in Ubuntu you connect your usb disk (if it was connected first, you right-click on it and choose "eject" and disconnect an reconnect it).

Then you click on "Install".

You answer to questions about language, location, keyboard, keyboard...

When system asks to select a disk, select external disk (this is the only risky part of install). if you choose the internal disk you will delate it...

If your internal disk is an ide one, your external will probably be /dev/sda. If internal disk in a sata disk, your external disk will be /dev/sdb (probably).

At next step, you choose install on whole external disk.

Ubuntu will create two partition: one in ext2 or ext3 and one swap.

The Install runs automatically. If Ubuntu asks for a place for grub, choose external disk.

When install is finished, let computer stop completely and disconnect external disk.

If you have yet burn your boot cd ( [http://www.gap.ien.05.ac-aix-marseille.fr/rre/ubuntu/grub2.iso](http://www.gap.ien.05.ac-aix-marseille.fr/rre/ubuntu/grub2.iso) ), you can use your new Ubuntu.

In order to do that, you connect your usb disk and then boot your computer with your grub2 cd.

You can also make your own boot cd using Ubuntu 6.06 CD. Follow this link 'LA CRÉATION DU CD DE BOOT POUR LES AMATEURS DE CAMBOUIS)

		[http://www.gap.ien.05.ac-aix-marseille.fr/rre/article.php3?id_article=1562#nb4](http://www.gap.ien.05.ac-aix-marseille.fr/rre/article.php3?id_article=1562#nb4)
		
Code :
	[I]mkdir cd_grub
    	mkdir -p cd_grub/boot/grub
	cp /lib/grub/i386-pc/stage2_eltorito /home/ubuntu/cd_grub/boot/grub
[/I]
then modify /etc/mkinitramfs/modules
	
        *gedit /etc/mkinitramfs/modules*

and add 4 lines at the end of file:
			
	[I]ehci-hcd
	usb-storage
	scsi_mod
	sd_mod[/I]
		    
and save the file and make new initrd :
			
	*mkinitramfs -o /home/ubuntu/cd_grub/boot/initrd-usb.img* 
			
Then	[I]gedit /home/ubuntu/cd_grub/boot/grub/menu.lst
[/I]
You write there :
			
	[I]title Linux on USB DISK
	root (cd)
	kernel /boot/vmlinuz-usb root=/dev/sda1 ro
	initrd /boot/initrd-usb.img
	boot[/I]
		    
Then you make grub.iso like that :

	*mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -o grub.iso cd_grub*
			
Then you burn it.

Enjoy with your Ubuntu on usb disk.

---

### Post by nardusg on 2006-10-18
Hi People

thom83, you are the MAN :mrgreen: Thank you for this little howto, work like advertised :D I have already upgraded to edgy, I boot from a USB drive. I just copyed the images in /boot , edited the menu.lst, and everything worked :)

Thanks again

nardusg

---

### Post by jdpipe on 2006-11-07
> **thom83 said:**
> I don't speak english well. But i'll try to translate shortly this install on usb disk...

As far as I can tell (and I'm not the expert here) there was an important step missing from thom83's instructions.

You need to also copy the 'vmlinuz-usb' file into your cd_boot directory before you run 'mkisofs':

```
cp /boot/vmlinuz-2.6.15-23-386 /home/ubuntu/cd_grub/boot/vmlinuz-usb
```

Here is the link that thom83 referred to (in French), rescued from Google Cache, since the page seems to be inaccessible currently.

> 
LA CRÉATION DU CD DE BOOT POUR LES AMATEURS DE CAMBOUIS [4]

    * forums anglais Ubuntu 

Remarque : Il semble qu’il faille déconnecter tous les disques durs internes pour obtenir un cd de boot parfait, sinon il cherchera sur les différentes machines d’accueil des disques durs qui ont été détectés lors du paramétrage décrit ci-dessous

Relancez une Ubuntu 6.06 avec le cdlive.

Mettez vous en sudo (super utilisateur) pour la suite...

Dans notre répertoire /home/ubuntu (par exemple) nous créons l’arborescence suivante :

mkdir cd_grub

mkdir -p cd_grub/boot/grub

On copie stage2_eltorito dans cd_grub/boot/grub

cp /lib/grub/i386-pc/stage2_eltorito /home/ubuntu/cd_grub/boot/grub
Il reste encore à copier 2 fichiers :

Le premier demande une manipulation préalable, car il faut éditer le fichier /etc/mkinitramfs/modules et ajouter à la fin :

ehci-hcd

usb-storage

scsi_mod

sd_mod
(PNG)

N’oubliez pas de sauvegarder le fichier modifié (sous vim avec :x)

puis lancez la commande mkinitramfs pour obtenir un nouveau initrd :

mkinitramfs -o /home/ubuntu/cd_grub/boot/initrd-usb.img

Il ne vous reste plus qu’à copier dans cd_grub/boot/ le fichier suivant :

cp /boot/vmlinuz-2.6.15-23-386 /home/ubuntu/cd_grub/boot/vmlinuz-usb

Un dernier fichier menu.lst est à construire intégralement dans un éditeur de texte pour préciser les modalité d’amorçage. Il sera enregistré dans /home/ubuntu/cd_grub/boot/grub/menu.lst :

title Linux sur cle USB

root (cd)

kernel /boot/vmlinuz-usb root=/dev/sda1 ro

initrd /boot/initrd-usb.img

boot

-  Contenu des différents répertoires créés :
(PNG)
(PNG)

Et finalement, il nous reste à créer l’image ISO qui nous servira à la gravure ; Tapez la commande en étant dans le répertoire /home/ubuntu/ :

mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -o grub.iso cd_grub

Graver le cd avec votre logiciel habituel, ou faites un clic droit sur le fichier grub.iso et sélectionnez "graver"... et voilà !!!
(PNG)

Remarque  : cette procédure devrait être adaptable sans modification pour faire la même chose avec Linux Edubuntu, Kunbuntu et Xubuntu


[1] nous avions un disque dur USB externe Memup Kwest 2,5" 80Go

[2] vous pouvez avant l’étape 1, déconnecter tous les disques durs du PC (vous les rebrancherez quand l’installation sera finie)

[3] éventuellement tapez sur CTRL + D si un message d’erreur apparaît concernant des disques durs qui n’existent pas sur votre machine d’accueil

[4] nous nous sommes inspirés de 3 sources :

    * forum Linuxfr.org
    * manuel de GRUB 


---

### Post by cw7585 on 2006-11-07
There's a great Howto in the community documentation that gives another version of this "Make a CD that boots to USB, to get around BIOSes that don't support USB boot" plan, like the one above. The page is here:

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

Scroll down to the section that reads, "Using a Linux Kernel", and start from there. That page has been my bible for the last few months. It's clear enough that an Ubuntu newb like me can follow it well.

However, if you're wanting to do this with a laptop, there's a detail missing. Notebook computers that don't support USB booting in BIOS, say pre-2003, are also likely pre-USB 2.0 vintage for their onboard USB ports. Running an OS from cranky old USB 1.1 would be not much better than running from a live CD, speedwise. So, what to do? 

The answer is to get a cheap $20 Cardbus USB 2.0 card to plug the external drive into, and add PCMCIA kernel drivers to the list of USB modules given on the help page that initrd cooks up for burning onto the boot CD. 

Here's the USB ones first, copied from that community help page:

usbcore
sd_mod
ehci_hcd
uhci_hcd
ohci_hcd
usb-storage
scsi_mod

But to get the Cardbus USB 2.0 slot working with this scheme, I add these to the list:

pcmcia_core
pcmcia
yenta_socket
rsrc_nonstatic

... and the external drive springs to life after a brief 10 second CD boot and boots the system into KDE or Gnome , in USB 2.0 glory.

The only downside to this is that I have to create a new boot CD every time I upgrade the kernel, but that only takes a few minutes, and I use the same CD-RW.

---

