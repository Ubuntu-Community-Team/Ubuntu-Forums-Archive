---
title: "The Ubuntu install disc wont show on Windows laptop"
date: 2016-05-03
forum: Installation &amp; Upgrades
---

### Post by Dsoslglece on 2016-05-03
[FONT=Helvetica]Hi,[/FONT]
[FONT=Helvetica]I’ve got a problem with installing Ubuntu on the laptop of a friend.[/FONT]
[FONT=Helvetica]it is a HP Compaq 6715s[/FONT]
[FONT=Helvetica]There was Vista on it.[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]I first added some RAM (made 2 GB instead of 512 MB, and then proceeded to install Ubuntu 15.10 with a DVD.[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]No chance to have that DVD appear to be able to install it.[/FONT]
[FONT=Helvetica]I went then in the BIOS and changed the boost to optical disc… nothing.[/FONT]
[FONT=Helvetica]I tried then from an usb DVD player (after changing the BIOS), same thing.[/FONT]
[FONT=Helvetica]then I tried with another install disc for XP and it appeared fine, so I installed it knowing that even if older it was probably not as bad as Vista and that I may have more chance with a less tortuous mind of a system. [/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]So, from this newly installed XP, I tried again with Ubuntu 15.10… nothing. so I tried some other Ubuntu versions 14, 13.10, 13.04, even 12… some were 32 bits, some 64, but none worked.   [/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]I must add that I am sure those DVD are fine, since I used them myself to install Ubuntu on my Mac and also on some other friend's computer…[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]I verified a few times that the choices I made in the BIOS were correctly saved, and they are. But when restarting the machine, whatever I choosed, it finishes with M$ starting on. [/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]I’ve thought of erasing completely the hard disc and then installing whatever I want, but it says nowhere how to do this on this machine… maybe starting a new install of let say XP, but stopping it as soon as the HD is erased, and then trying it again to boot from an install Ubuntu DVD… it wouldn’t be able then to use anything else.[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]I would be very appreciative of some new ideas, since me brain feels a bit empty for the moment…[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]Thanks in advance [/FONT]

---

### Post by RobGoss on 2016-05-03
Hello and welcome, Are you trying to install just Ubuntu on this laptop?

Depending on what kind of Laptop it is you will probably have to go into your **BIOS **and change the boot order to get your machine to boot from that DVD drive 

You might even be able to install Ubuntu from a **USB **drive if you have one. Some machines will boot if you press the **F12,** or maybe **F10 **depending on the machine, You should want to look up your machine to see what's needed to get this installation going as far as boot order

---

### Post by buzzingrobot on 2016-05-03
> **Dsoslglece said:**
> 
[FONT=Helvetica]I went then in the BIOS and changed the boost to optical disc&#8230; nothing.[/FONT]
[FONT=Helvetica]I tried then from an usb DVD player (after changing the BIOS), same thing.[/FONT]
[FONT=Helvetica]then I tried with another install disc for XP...[/FONT][FONT=Helvetica]

[/FONT]Don't have an answer for you, since the machine is obviously able to boot from a DVD.   If you can use a USB stick, you might try Rufus, which is a freeware Windows utility to create bootable USB sticks. ([https://rufus.akeo.ie/](https://rufus.akeo.ie/)) I've used it on 7 and 10, and the site says it XP-compatible. I've used it and it works.

If you do get something to boot, and you want to do away with Windows altogether, you don't really need to delete it or reformat before installing Ubuntu.  The partitioner in the installer will do that for you.

---

### Post by Dsoslglece on 2016-05-03
Thanks for your answers&#8230; Yes I know that when installing it erases the HD, but if I was thinking of erasing it first, it was simply to avoid any intervention of an already installed system&#8230; I may also try to do the install from my Mac by connecting the two computers with firewire or usb&#8230; but it may be a bit more tricky than doing the same with two machines of the same type&#8230; so, maybe from one of the windows (XP, Win7 or 10) installed on my Mac, or even the Ubuntu or Kubuntu also installed there ?&#8230; I certainly wont leave that bone before it is cracked!

---

### Post by oldfred on 2016-05-03
You do not install from Windows. You can install to a totally blank drive.
If system was originally Vista, it probably can boot from a flash drive.

You have to boot directly from BIOS into DVD or flash drive where you have your Ubuntu.
 Write image or burn image (which extracts ISO and installs boot loader) not copy ISO as one large file to flash or DVD. 

        [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) 
            [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows) 
    
System my not be new enough to run full Ubuntu. Depends a lot on what video. 
Older systems work much better with Lubuntu or Xubuntu.
       [https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)
Kubuntu, Edubuntu, Xubuntu, Mythbuntu, UbuntuStudio, Lubuntu, Ubuntu GNOME, Ubuntu Kylin, Ubuntu MATE 
[http://xubuntu.org/](http://xubuntu.org/)
[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by Dsoslglece on 2016-05-04
Thanks OldFred for the data, it gives me much to experiment with, and I will do. It may also explain why it wouldn't install on that not too new box, even if not this old&#8230;

---

### Post by Dsoslglece on 2016-05-10
So, I did try a few things, made experiments…
Finally I managed to install Kubuntu 14.04 from a disc (Must say that with a USB key it never worked). But there is still something not optimum there, since when doing the update (security update), when restarting it just doesn't restart or rather it goes to the first window where one sees, one by one appearing: an image of the HD, the system config, etc… but it stops after showing the disc and turns black. The only possibility then is to reinstall it again, what it does easily.
But, if not doing the update,  it works otherwise fine, and can be stopped, started, restarted without problem.

I'm going to try now to install Xubuntu as a trial from a disc, and if it works, and since it is a more recent version, I could just let it replace Kubuntu.

Thanks again for the advice

---

### Post by Dsoslglece on 2016-05-12
Hi everyone…
So, here is the continuation of the story.
I tried and succeded installing xubuntu, but I must say that it looks very limited by comparison to Kubuntu… 

I also tried to install Ubuntu (from a DVD and from a usb stick (32 GB) but it fails in mid operation, and more, it finally showed a kernel panic!
so I tried to revert to Kubuntu 14.04 (the one that I did succeed in installing quite a few times), and the same kernel panic showed up now…
[IMG]http://i66.tinypic.com/3025p9w.png[/IMG]


So I managed to install again the xp system as I had done at the beginning, but I really have to install something more pro and more secure than this!

So, to summarize: I get now a laptop with xp installed, and whatever version of kubuntu I try to install creates a kernel panic. I may try again with xubuntu, anyways better than any Win, but must first localize the DVD among the few dozens I burned!

Is it maybe possible for the BIOS to need a debugging? and if so, how to do this?
Or else? I must say that I don't see!

Thanks

---

### Post by oldfred on 2016-05-12
Both Kubuntu & Ubuntu are more for newer computers. You need more RAM, and more powerful gpu for graphics.

I would try Xubuntu or Lubuntu which work better with lighter weight or older systems.

---

### Post by Dsoslglece on 2016-05-12
Thanks Oldfred, Well, I will try lubuntu&#8230; I did already try xubuntu, but it seems rather minimal as a system and I didn't feel much enthousiastic about it&#8230; hopefully it'll be better with lubuntu&#8230;
but, I am surprised that it could react as it did with Kubuntu (the pict of the kernel panic has disappeared now from my previous post), after all, this tin can of a laptop was running on vista; it has a speed of 2.19 GHz and at the time it had then only 512 MB RAM (now it is 2 GB)&#8230; also, Kubuntu 14.04 worked fine, and it's only when updating that it didn't work, and later even did every time a kernel panic. I think the pict didn't stay in my previous message since it may have been to big, I try now a bit smaller:

[IMG]http://i68.tinypic.com/30bnrs3.png[/IMG]

---

### Post by oldfred on 2016-05-12
You should attach screenshots/photos. Not everyone has high speed Internet and it can create issues.
And you should shrink any photo that is posted as screens do not have that resolution anyway.

Easy to attach with Forum's advanced editor and paperclip icon.

---

### Post by Dsoslglece on 2016-05-12
So, I got the lubuntu install on a DVD (made according to rules!) and asked for just trying it from the DVD… got soon exactly the same kernel panic as before (except when installing XP) So, at the moment, it still runs on xp.
I also investigated about the amount of RAM possible on this laptop, and it is 4Go (but I must verify that there is a second slot… I didn't see it when changing the RAM)… if this is possible, maybe then it'll be enough (4 GB RAM and 2.19 GHz is not bad really)  
So, here my last question again: can't it be that the BIOS has something wrong?

---

### Post by oldfred on 2016-05-12
Other than making sure you have newest BIOS from vendor, you cannot change BIOS.

Some systems do need work arounds for BIOS issues and then a boot parameter is often used.

I do not know about AMD systems, but you may need nomodeset boot parameter.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown and other boot parameters
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Dsoslglece on 2016-05-13
Hello again&#8230;
here are the last developments&#8230; after more trials in many directions, including GRUB, I decided to make some tests of the machine&#8230;

It says that it is OK, but the memory test showed an error, it says this:

Memory: 2048 MB

_Memory test_

Failure address:  76E176E8

Sent model:  AAAAAAAA
Received.... AAAAAADA

So, next thing I'll contact the vendor for this RAM bar&#8230; it looks as if the source had been found&#8230;

I'll keep you informed anyway

---

### Post by ubfan1 on 2016-05-13
Did you ever run a memory and disk ckeck on that computer?  2G should be enough for Xubuntu or Lubuntu, but only if it good ;^)

---

### Post by Dsoslglece on 2016-05-13
Ben oui ! c'est juste ce que je dis dans le message précédent&#8230;

Sorry I didn't realize that I answered in French it just came back to my mind quite later, so I'm coming back to correct it!!

Well yes! it's just what I said in the previous post&#8230;

---

