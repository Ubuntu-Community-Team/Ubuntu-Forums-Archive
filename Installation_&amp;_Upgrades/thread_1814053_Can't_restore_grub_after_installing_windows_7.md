---
title: "Can't restore grub after installing windows 7"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by manilodisan on 2011-07-28
I don't use windows at all but today I had to because they changed my internet provider and the thing wasn't working so I called them. They said they can't troubleshoot unless i'm running windows so I figured it shouldn't be a problem to do a dual boot. Installed win7 and then I used the livedCD (i'm running it now) to restore my grub but I have a big problem when I run:
```
grub-install --root-directory=/mnt/ /dev/sda
```

The code results with an error:
```
grub-probe: error: cannot stat `aufs'.
Installation finished. No error reported
```

So I figured it's just a notice given the fact that the second line says installation finished and I restarted without the liveCD. It doesn't boot in linux or windows either, it just loads a "grub" console which, whatever I type, says: Unknown command.

Any ideas on how to restore my grub and live normal again? :)

---

### Post by oldfred on 2011-07-29
Did you mount partition with boot/grub files first?

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
[COLOR=Red]sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda[/COLOR]
#If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

More info:
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by pritam_par on 2011-08-06
Check out this link for step by step instruction to install Grub
[http://ubuntuforums.org/showthread.php?p=11124764#post11124764](http://ubuntuforums.org/showthread.php?p=11124764#post11124764)

---

### Post by x-D on 2011-08-06
The absolute EASIEST WAY, to (re)install GRUB is to use a little program called Boot-Repair. It does all that work to do with commands in the Terminal to reinstall GRUB for you, and it's really noob friendly, with a simple GUI, that you merely have to indicate which OS you want as your main Operating System etc, IF YOU WANT TO! This is all under advanced options, but really, it's not so advanced, anyway to get Boot-Repair:[U][B]

Do this in the Terminal:[/B][/U]

```

sudo add-apt-repository ppa:yannubuntu/boot-repair

sudo apt-get update && sudo apt-get install -y boot-repair-ubuntu

```Now, run the program (search for it in Unity, or go to: System ----> Administration ----> Boot Repair, in Gnome 2/ Classic Mode in 11.04 Natty Narwhal)

Then, once the program is done reinstalling GRUB (should take at max 2 minutes), do this:

```

sudo update-grub

```This is probably not necessary, but it will just eradicate the potential for any errors, whatsoever!

_**Inf****o for this can be found by:**_

a) going to: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
b) messaging me here.

Hope this helped...

x-D :guitar:

---

