---
title: "Grub troubles with Fedora 15"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by Drainy on 2011-05-25
Hey,

So tonight I installed Fedora 15 to give it a try (and to have a look at Gnome 3)
Anyway, it nerfed up my grub2 install, which was expected to an extent, previously when this has happened I have run the update-grub2 command which usually fixes everything.
This time it doesn't help, mainly because it has installed grub1 which only recognises windows and fedora on the system!
I have located that the ubuntu partition is still safe and well at /dev/sda5 and the windows MBR is at /dev/sda1. I assume that ubuntu booted from grub in sda.
Fedora is located in /dev/sdb3.

Now is there a reason that grub is no longer detecting Ubuntu? I did install grub2 to try and regain some access but all that has done is effectively create a submenu on the grub1 menu which only links to fedora again!

Thanks for any help or pointers. All other topics or discussions on this are either quite general or don't help me resolve this.

---

### Post by wojox on 2011-05-25
Did you reinstall grub2 from a [Live-CD?]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by Drainy on 2011-05-25
No, I did it from fedora.
I assumed it would probe in the same way that it would have from an Ubuntu environment and still detect the same.

Is this likely to give a different result then?
May have to figure out which unmarked disc is my Ubuntu disc!

---

### Post by coffeecat on 2011-05-25
No, unfortunately Fedora's grub does not probe for other OSs the way Ubuntu's does. Fedora has always been this way. I think the Fedora devs expect that the typical Fedora user is happy hand-editing legacy-grub's menu.lst. Or perhaps the Fedora devs don't believe that the typical Fedora user would use any other distro. :?

Whatever... What I do is to let the Fedora installer install its version of grub, then edit menu.lst on my first boot into Fedora to include an Ubuntu entry. Then I boot into Ubuntu and run grub-install and update-grub to get Ubuntu's grub menu back with an entry for Fedora.

When you've worked out which unmarked disc is which for re-installing grub2, a warning. The versions of grub2 in the various Ubuntu releases are different: 1.98 in Maverick, 1.99 in Natty and earlier versions in Lucid and Karmic. There are subtle but important differences between them. It will be safer to use the same version CD as your permanent installation for re-installing grub. I hope that version is not Karmic, as your personal details are telling us at the moment. :|

---

### Post by Drainy on 2011-05-25
Ah that makes sense. 
Ok I will have a dig. I currently have 10.10, just haven't updated my profile yet! :)

Thanks for the advice. I will post back on the results.
Out of interest, how did you edit the menu.lst to include Ubuntu? I did have a look at this but obviously I went in armed with such things as /dev/sda etc and it works on hdd(0,1) or similar

---

### Post by coffeecat on 2011-05-25
> **Drainy said:**
> Out of interest, how did you edit the menu.lst to include Ubuntu? I did have a look at this but obviously I went in armed with such things as /dev/sda etc and it works on hdd(0,1) or similar

A year's experience of using Gentoo. ](*,)You learnt how to do such things or you didn't have a working system. :wink: 

Actually, the form is (hd0,0) which is equivalent to sda1. In legacy grub that is. In grub2, sda1 comes out as (hd0,1), just to keep you on your toes, or grub2 does allow forms such as (/dev/sda,msdos1). 

If you really want to know more, here's the legacy grub manual:

[http://www.gnu.org/software/grub/grub-legacy-support.en.html](http://www.gnu.org/software/grub/grub-legacy-support.en.html)

But you may prefer to simply re-install grub2 from the Ubuntu CD. :)

---

### Post by Drainy on 2011-05-26
Hey,

So I've been trying to reinstall grub2 and have managed to nerf any kind of boot loader at all :/

I have got as far as chrooting inside the live disc after mounting everything but I am getting the following error when I try to chroot into my existing system;
```
chroot: failued to run command `/bin/bash': Exec format error
```

If anyone has any ideas I would be glad to hear them

---

### Post by coffeecat on 2011-05-26
> **Drainy said:**
> [/CODE]If anyone has any ideas I would be glad to hear them

Yep! You shouldn't need to chroot. Have a look here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Steps 1 to 6 under "SIMPLEST - Copy GRUB 2 Files from the LiveCD" will do it. Just bear in mind what I said earlier about using the same minor version of grub2.

---

### Post by Drainy on 2011-05-26
Cheers.
That is the third set of install instructions I found for grub2 with a live disc and they worked.
However, it detected windows and Ubuntu but not Fedora! How could I add Fedora manually?
I have the /dev location

Thanks again for the reinstall link

---

### Post by beew on 2011-05-26
I have had Fedora 15 installed in a multiboot system with Ubuntu 11.04 and Ubuntu 10.10 and Fedora 14 and qomo (no Windows) I didn't have any problem installing, but you have to choose setting up partition manually (or advanced option, forget what t is called) and then you can install in the partition you choose provided you have set up the partition beforehand, and then choose not to install grub and everything would be fine (so in my system Maverick retains control of grub)

Now since installed it crashed a lot and has been dead on me twice, --still haven't reinstalled yet. But that is a different issue.

---

### Post by Drainy on 2011-05-26
Well I used custom setup because I have a pretty complicatedish arrangement of hard discs and partitions.
I don't recall the boot loader option but in all honesty I would probably have left Fedora to install it on the principle that it might have detected the other OSes and installed itself.

Now the problem is that it the reinstall of grub has only found Ubuntu and Win7 :/

---

### Post by wojox on 2011-05-26
> **Drainy said:**
> Well I used custom setup because I have a pretty complicatedish arrangement of hard discs and partitions.

You have a RAID set up?

---

### Post by beew on 2011-05-26
> **Drainy said:**
> Well I used custom setup because I have a pretty complicatedish arrangement of hard discs and partitions.
I don't recall the boot loader option but in all honesty I would probably have left Fedora to install it on the principle that it might have detected the other OSes and installed itself.

Now the problem is that it the reinstall of grub has only found Ubuntu and Win7 :/

I didn't install grub for Fedora because I wanted Ubuntu to detect and boot other OSes (after installing a new OS boot into Ubuntu and run sudo update-grub)

---

### Post by coffeecat on 2011-05-27
> **Drainy said:**
> Cheers.
That is the third set of install instructions I found for grub2 with a live disc and they worked.
However, it detected windows and Ubuntu but not Fedora! How could I add Fedora manually?
I have the /dev location

Thanks again for the reinstall link

I've not come across grub2's os-prober failing to find Fedora before. Let's have a look at your setup. Link:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script in Ubuntu as described there and post the contents of the RESULTS.txt in code tags. We might be able to see why Ubuntu is not detecting Fedora or at the very least the information will be there to create a Fedora stanza in your 40_custom file.

---

### Post by Drainy on 2011-05-27
Right, all sorted.

Thanks for all the help!

I didn't run update-grub once I got back into Ubuntu under the assumption (yes another assumption! I won't be making any of these again) that when I reinstalled grub it did another probe.
Clearly my original grub install was never overwritten during my 3 or so attempts to and the one I saw when I finally successfully ran the install was my original one.

Running update-grub threw Fedora onto the list.

Thanks again!

---

### Post by coffeecat on 2011-05-27
> **Drainy said:**
> I didn't run update-grub once I got back into Ubuntu under the assumption (yes another assumption! I won't be making any of these again) that when I reinstalled grub it did another probe.
Clearly my original grub install was never overwritten during my 3 or so attempts to and the one I saw when I finally successfully ran the install was my original one.

That explains it. I was mystified by the fact that update-grub didn't detect Fedora when in fact update-grub didn't have a chance to detect Fedora. :)

The command grub-install that you ran from the live CD merely re-installs grub code to the mbr and embedding area, pointing to your Ubuntu root partition. The command update-grub parses all the executable files in /etc/grub.d/, runs os-prober if 30_os-prober is executable, and recreates grub.cfg which itself generates the grub menu when you first boot.

Good luck with that triple boot!

---

