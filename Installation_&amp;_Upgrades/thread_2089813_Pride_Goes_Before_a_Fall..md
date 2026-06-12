---
title: "Pride Goes Before a Fall."
date: 2012-11-30
forum: Installation &amp; Upgrades
---

### Post by cliff edwards on 2012-11-30
Had 12.04 on my desktop after upgrading, in a dual boot configuration with windows 7, unfortunately a hardware fault meant i had to have a new motherboard and cpu. also had Windows7 reloaded to the whole hard drive afterwards. I thought that as I had loaded ubuntu several years ago, I could do it again.
        I got the Iso download for 12.04 and put on a DVD, put it into my unit tray where it asked me did I wish to load it using Wubi ( This was in Win 7) I said OK, I then ran the disk tried 12.04, managed to send an email etc, etc, thought to myself this is OK . then noticed on the Ubuntu screen a folder with download Unbuntu 12.04. Thinking that this must be the way to do it ,I clicked on it, and followed the setting up instructions.
       Now I find that whilst my hard drive has a volume of approximately the size I allocated I can not access it, I boot straight into Win 7. It is obvious that this is not right, so how can I resolve this?
                  Regards Cliff

---

### Post by Frogs Hair on 2012-11-30
If you are in fact using Wubi you can start here [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If Ubuntu doesn't show up in programs and features in Windows, Open local disk C under computer. There is a remove Ubuntu icon inside the Ubuntu folder.

---

### Post by cliff edwards on 2012-11-30
> **Frogs Hair said:**
> If you are in fact using Wubi you can start here [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If Ubuntu doesn't show up in programs and features in Windows, Open local disk C under computer. There is a remove Ubuntu icon inside the Ubuntu folder.
  First Of all, allow me to thank you for your time and trouble. Apart from two extra partitions of about 180 and 9 gigs ) I allocated about 200 gigs I have nothing saying Ubuntu under my C drive or anywhere else.
       Now, afterwards I dimly remember that when I loaded the original Ubuntu some years ago, I had to go into the Bios and alter it to boot from the disc drive and then follow the process.  Making no excuses it does seem to me to be a little silly to be using a method where those of us that do not do this every day, can if in a demonstration start loading thinking that this must be a more modern way of doing things. I understand from the chap that reloaded Win 7 for me that I can recover the space by deleting the extra Volumes and expanding the Win 7 volume to take up the extra space. However as I am none too sure of where the 9 gigs volume came from I might leave that for now.

---

### Post by bcbc on 2012-11-30
It sounds like you did a normal install, but it didn't install the grub bootloader. Can you boot from the DVD via the BIOS, select "Try Ubuntu" and then give us the output of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")?
 
Thanks

---

### Post by cliff edwards on 2012-12-01
> **bcbc said:**
> It sounds like you did a normal install, but it didn't install the grub bootloader. Can you boot from the DVD via the BIOS, select "Try Ubuntu" and then give us the output of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")?
 
Thanks
  I have looked at my new motherboard and they have a remark saying that they do not do Linux drivers ,go to the chipset vendor. Went to Intel for their H61 express chiopset ,and they do not support Linux drivers, in effect try a 3rd party. I suspect that if I had loaded 12.04 through the disc drive that the drivers in 12.04 would have worked. My new board is a Gigabyte TE-UEFI dual Bios model no H61M-S2 PV, and I think that I could get it to boot from disc. But as I have to take this Tower back to the chap who re-installed Win7 for me next week, I'll chicken out and let him do it for me.
    What with the hardware failure ,the 12.04 install going wrong I'm just waiting for the third strike, my nerves are not what they were. I have a strong suspicion that if I had the boot from disc drive working all would have gone well, but of course I wasn't thinking of this when I had the Win 7 reloaded.
         Thank you for your suggestion.
                                Regards Cliff.

---

### Post by bcbc on 2012-12-01
Okay that makes more sense. With UEFI you need to use a 64bit version of Ubuntu and there are some other things (I haven't done this myself) like having to boot the installer (DVD/USB) in EFI mode... here's something others have written up: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

That link mentions 12.10 - I'm not certain about 12.04 but I reckon it probably has the same support as 12.10 (except if you have the original 12.04 - not the updated 12.04.1 - then it won't work).

---

### Post by cliff edwards on 2012-12-02
> **bcbc said:**
> Okay that makes more sense. With UEFI you need to use a 64bit version of Ubuntu and there are some other things (I haven't done this myself) like having to boot the installer (DVD/USB) in EFI mode... here's something others have written up: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

That link mentions 12.10 - I'm not certain about 12.04 but I reckon it probably has the same support as 12.10 (except if you have the original 12.04 - not the updated 12.04.1 - then it won't work).
  Thank you for the link, I would like to say it is most informative,and I am certain it is. I am just not too sure whether or not my level of expertise is really up to this, when I was younger I was so ignorant of being ignorant that I often achieved things despite my lack of knowledge. At 68 years of age my faculties are not what they were, although I suspect my propensity for impulsive leaps into things best left alone has not diminished by much.
              I shall have to give this some serious cogitation, but in the mean time thank you for your help, it is most kind. I was going to use that awful term " Newbie " but on reflection I think "Old Fart " is more apposite.
                                     Regards Cliff.

---

### Post by bcbc on 2012-12-02
It's not you... when the first heading in the guide is "Installing Ubuntu Quickly and Easily via *Trial and Error*"... it's enough to turn anyone off.

When you boot your computer with the Ubuntu DVD in the tray, do you get the option to "Try Ubuntu"? Or does it boot straight to Windows?

---

### Post by cliff edwards on 2012-12-03
> **bcbc said:**
> It's not you... when the first heading in the guide is "Installing Ubuntu Quickly and Easily via *Trial and Error*"... it's enough to turn anyone off.

When you boot your computer with the Ubuntu DVD in the tray, do you get the option to "Try Ubuntu"? Or does it boot straight to Windows?
  To be honest I haven't tried it again, I went to a chaps website where he was a technical writer. he was offering his experiences with an earlier Gigabyte EFI board, and how he got around the problems he experienced. It was full of jargon and meaningful terms that I got the gist of, but no real understanding, I came away with my head reeling. I then refound the site where I set up my previous Ubuntu from, "Easy Linux Tips Project ". Some Dutch chap being very helpful, and I was struck by the fact that while he obviously updates the info on the site, he did not mention any specific problems of using these UEFI boards. He advises that 64 bit Ubuntu should be used but mainly for it's speed gains, so now I stand conflicted, I ask myself if he really has got the latest on his website? Then I think to myself that these boards have been out as I understand it for about roughly 2 years now, surely he isn't that far behind.
            Now I am thinking perhaps I should get another hard drive added and load Ubuntu to that, what difficulties would I experience if I did? Then I think what if I did change the boot sequence in the bios to load from the disc drive first, and just go for it? Then I think that when I looked through the link you kindly provided, I didn't see anything that implied that you had to load from the disc while it was first in the boot sequence, or was that to be taken "As Read "?  From what I understood, providing you had the 64 bit version with the Grub boot repair on it ,you just put in the drive even if the preference was to boot from the Hard Drive first,and away you go. You no longer need to be booting from the Disc drive first! or is this something I missed in my cursory look through the instructions ?
         So that is how you find me, nerving myself up to change the boot sequence in the Bios, it bears no resemblence to the instructions on my old board, but I think i can work my way slowly through the different jargon. Then if that works I shall look more closely at that link again and i might let my impulsion loose, and go for it.
                           Regards Cliff.

---

### Post by bcbc on 2012-12-03
It would help to have some more diagnostics, because up to now I've made assumptions based on how you've described what happened. e.g. you mentioned Wubi, but that's not always clear cut because it has a different set of options when it loads from a DVD as opposed to running it standalone. Since 12.04 it won't offer to install 'inside Windows' - which is what most people refer to as Wubi.

So that's why I'd like the bootinfoscript results. In order to boot from the Ubuntu DVD you have to change the boot order, no matter what sort of boot techniques you are using. I'd use just the Ubuntu DVD you have, not boot-repair until we know what is going on.

The issue with UEFI, is that it supports both UEFI boot as well as legacy boot (similar to BIOS). It's not clear what setup you have either. I made some more assumptions because Wubi won't work on a UEFI system.

So... maybe you can clear up a few things before booting the Ubuntu CD. From Windows, hit the Start button, type "Add or remove" and hit enter. That should get you to the Control Panel's "Uninstall or change a program" screen. Look down the list and see if there is an Ubuntu entry as shown in attached image.

What this tells us is that you did use Wubi - either a traditional install, or as a "CD boot helper".

---

### Post by cliff edwards on 2012-12-04
> **bcbc said:**
> It would help to have some more diagnostics, because up to now I've made assumptions based on how you've described what happened. e.g. you mentioned Wubi, but that's not always clear cut because it has a different set of options when it loads from a DVD as opposed to running it standalone. Since 12.04 it won't offer to install 'inside Windows' - which is what most people refer to as Wubi.

So that's why I'd like the bootinfoscript results. In order to boot from the Ubuntu DVD you have to change the boot order, no matter what sort of boot techniques you are using. I'd use just the Ubuntu DVD you have, not boot-repair until we know what is going on.

The issue with UEFI, is that it supports both UEFI boot as well as legacy boot (similar to BIOS). It's not clear what setup you have either. I made some more assumptions because Wubi won't work on a UEFI system.

So... maybe you can clear up a few things before booting the Ubuntu CD. From Windows, hit the Start button, type "Add or remove" and hit enter. That should get you to the Control Panel's "Uninstall or change a program" screen. Look down the list and see if there is an Ubuntu entry as shown in attached image.

What this tells us is that you did use Wubi - either a traditional install, or as a "CD boot helper".
    I have checked there is no ubuntu in the programmes, I have also reloaded the original 12.04 disc and re installed Ubuntu using that, it made no difference, there still is no Ubuntu in programmes.In disc management my Hard drive now shows two extra Volumes/partition of the right size. Now despite watching the installation saying that it was installing Grub 2,and then updating it. it does not appear to be there. I boot straight into Win 7. Last night I went to that link and downloaded the ubuntu 64 bit remix. It said that it was 797 MB but only came as 760MB, tried that, it also made no difference. The only oddity is that on the motherboard in the Bios Features it had a Boot mode selector, with Boot to UEFIand Legacy outlined, the next two lines were Uefi and the Legacy only options ,Not wanting to change too much I left it at UEFIand Legacy.
                              Regards Cliff.

---

### Post by cliff edwards on 2012-12-04
> **bcbc said:**
> It would help to have some more diagnostics, because up to now I've made assumptions based on how you've described what happened. e.g. you mentioned Wubi, but that's not always clear cut because it has a different set of options when it loads from a DVD as opposed to running it standalone. Since 12.04 it won't offer to install 'inside Windows' - which is what most people refer to as Wubi.

So that's why I'd like the bootinfoscript results. In order to boot from the Ubuntu DVD you have to change the boot order, no matter what sort of boot techniques you are using. I'd use just the Ubuntu DVD you have, not boot-repair until we know what is going on.

The issue with UEFI, is that it supports both UEFI boot as well as legacy boot (similar to BIOS). It's not clear what setup you have either. I made some more assumptions because Wubi won't work on a UEFI system.

So... maybe you can clear up a few things before booting the Ubuntu CD. From Windows, hit the Start button, type "Add or remove" and hit enter. That should get you to the Control Panel's "Uninstall or change a program" screen. Look down the list and see if there is an Ubuntu entry as shown in attached image.

What this tells us is that you did use Wubi - either a traditional install, or as a "CD boot helper".
I checked the programmes before ie, earlier this morning and there was no sign of Unbuntu, not was there any signin Disc management of any extra Volumes. This is after I went to the link and downloaded the 64 bit remix last night and tried that, the result was nothing. This morning I have reloaded the original 12.04 and sat through the disc self check for any errors, then an installation of Ubuntu, where I watched it say it was installing Grub 2 , then update Grub 2 , carried on the process until it was complete. I now have two extraq volumes on the Hard drive, and still have no Ubuntu in Uninstall/install programmes, etc,etc.. 
                In my motherboard Bios Features I have a Boot  Mode selection , where the top line is outlined UEFI and Legacy, the next down UEFI, and the bottom Legacy. Figuring that if it says it does both ,and not wanting to disturb too much I have left it on the top line.
                                   Regards Cliff

---

### Post by cliff edwards on 2012-12-04
> **cliff edwards said:**
> I checked the programmes before ie, earlier this morning and there was no sign of Unbuntu, not was there any signin Disc management of any extra Volumes. This is after I went to the link and downloaded the 64 bit remix last night and tried that, the result was nothing. This morning I have reloaded the original 12.04 and sat through the disc self check for any errors, then an installation of Ubuntu, where I watched it say it was installing Grub 2 , then update Grub 2 , carried on the process until it was complete. I now have two extraq volumes on the Hard drive, and still have no Ubuntu in Uninstall/install programmes, etc,etc.. 
                In my motherboard Bios Features I have a Boot  Mode selection , where the top line is outlined UEFI and Legacy, the next down UEFI, and the bottom Legacy. Figuring that if it says it does both ,and not wanting to disturb too much I have left it on the top line.
                                   Regards Cliff
Subsequent to my last edition of this Saga, I have gone back into the hard drive Volumes/partitions and deleted those installed by my latest install attempt this morning, recovered the hard drive for Win 7. Then went back into the motherboard Bios Feature, went to Boot Mode Selection and changed it from UEFI and Legacy to Legacy only ( My daring knows no bounds ) then rebooted using the first 12.04 from the other day, I now have the screen where I can choose to load Ubuntu or Windows. I say that I have both ,but the truth is so far I have only checked Ubuntu. Then carried out an update, this took longer than the install as there were 234 to get through.
                  It would seem that with this board, it must be in the Boot in Legacy Mode, it will not work if the selection is to the UEFI and Legacy Mode, or for that matter in UEFI alone Mode.
                         In any case I would like to take this opportunity in thanking you for kindnes and support, I can't imagine that with out them I would have got this far, Thank you.
                                                     Regards Cliff
ps, I have sent several far more detailed replies to your previous replies, but some how or another I was not properly signed in, and in signing in they disappeared into the Ether.

---

### Post by bcbc on 2012-12-04
Edit: ignore this - I didn't read all your posts!

Okay... I still think you may have issues. If windows was booting in uefi mode, and grub is booting in legacy mode, then now windows probably won't boot. The solution may be to boot the DVD in efi mode before installing ubuntu. Anyway... you'll find out soon enough.

---

### Post by cliff edwards on 2012-12-04
> **bcbc said:**
> Edit: ignore this - I didn't read all your posts!

Okay... I still think you may have issues. If windows was booting in uefi mode, and grub is booting in legacy mode, then now windows probably won't boot. The solution may be to boot the DVD in efi mode before installing ubuntu. Anyway... you'll find out soon enough.
I can only assume that Windows was booting in legacy mode as it fired up perfectly at my first attempt after booting into Ubuntu 12.04, I am back into 12.04 at this time trying to remember all that I had in my previous copy of it.
                         best Regards Cliff.

---

### Post by bcbc on 2012-12-04
Great to hear. Enjoy!

---

