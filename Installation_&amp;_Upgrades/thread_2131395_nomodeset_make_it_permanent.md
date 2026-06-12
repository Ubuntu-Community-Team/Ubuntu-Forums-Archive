---
title: "nomodeset make it permanent"
date: 2013-04-01
forum: Installation &amp; Upgrades
---

### Post by GWild on 2013-04-01
Hello.

I have run into this issue with my attempt to install 12.04 LTS.  The video is corrupted, so I have no way to navigate /etc/default/ and edit the grub file then run update-grub once the system is loaded.

Is it possible to, say, boot from a live DVD, mount my system, then make the change?  If possible, what are the steps to do so?

Thanks.

---

### Post by schragge on 2013-04-01
Try to change into text console by pressing **Ctrl**+**Alt**+**F2**, log in, and edit the file from there with
```
sudo nano /etc/default/grub
```

---

### Post by GWild on 2013-04-01
> **schragge said:**
> Try to change into text console by pressing **Ctrl**+**Alt**+**F2**, log in, and edit the file from there with
```
sudo nano /etc/default/grub
```

Thanks for the response.

In my initial post I failed to mention that I did attempt that step, but it did not provide a usable interface.  

If I am being shown a usable console I am not aware of it because the video remains corrupted when I attempt Ctrl-Alt Fx (not F7).


Thanks.

---

### Post by steeldriver on 2013-04-01
Well I guess you *could* do it from a live CD using chroot, but imo it would be simpler to drop to the grub edit mode during boot (press shift during boot to get the grub menu - if you don't display it by default and then 'e' to edit the boot command line), add nomodeset there (to apply it for the current session), and then edit /etc/default/grub once the session boots

---

### Post by GWild on 2013-04-01
> **steeldriver said:**
> Well I guess you *could* do it from a live CD using chroot, but imo it would be simpler to drop to the grub edit mode during boot (press shift during boot to get the grub menu - if you don't display it by default and then 'e' to edit the boot command line), add nomodeset there (to apply it for the current session), and then edit /etc/default/grub once the session boots

Unfortunately pressing the shift key at boot has no effect, so I am unable to access the grub menu.

---

### Post by smudgy on 2013-04-01
> **GWild said:**
> Unfortunately pressing the shift key at boot has no effect, so I am unable to access the grub menu.

Knoppix will get you able to mount your filesystem and edit the file. But could you not do that anyway in 12.04  Recovery Mode with the Live CD?

As of linux kernel 3.9 there will be no more easy boot parameter nomodesetting for us by default ;)  So there will be problems with many distros including 12.1 >> No way round that without kernel recompile taking out the no UMS config that is put in by default. So its a minor edit to a config file and then recompile or so i understand. When I get round to it I'll try to put up a post. Stuff on [tuxgarage]("http://www.tuxgarage.com/2011/07/upgrade-video-drivers-through-ppas.html") and [phoronix]("http://www.phoronix.com/scan.php?page=news_item&px=MTI2ODA")


(By the way intially I never really got anywhere with Ubuntu and ran with openSUSE until problems with their latest release. However 12.04.2 seems to be a truly excellent release especially via xubuntu live cd. just had some fiddles with xorg.conf dual head editing out the superfluous 3rd screen etc and also replaced gksu with gksu-polkit which is blindingly fast and does not require a lengthy pause as it is instant! then created a ~/.bash_aliases file with my aliases so i don't have to type all of gksu-polkit ;)  )

---

### Post by GWild on 2013-04-01
> **smudgy said:**
> Knoppix will get you able to mount your filesystem and edit the file. But could you not do that anyway in 12.04  Recovery Mode with the Live CD?

As of linux kernel 3.9 there will be no more easy boot parameter nomodesetting for us by default ;)  So there will be problems with many distros including 12.1 >> No way round that without kernel recompile taking out the no UMS config that is put in by default. So its a minor edit to a config file and then recompile or so i understand. When I get round to it I'll try to put up a post. Stuff on [tuxgarage]("http://www.tuxgarage.com/2011/07/upgrade-video-drivers-through-ppas.html") and [phoronix]("http://www.phoronix.com/scan.php?page=news_item&px=MTI2ODA")


(By the way intially I never really got anywhere with Ubuntu and ran with openSUSE until problems with their latest release. However 12.04.2 seems to be a truly excellent release especially via xubuntu live cd. just had some fiddles with xorg.conf dual head editing out the superfluous 3rd screen etc and also replaced gksu with gksu-polkit which is blindingly fast and does not require a lengthy pause as it is instant! then created a ~/.bash_aliases file with my aliases so i don't have to type all of gksu-polkit ;)  )

I did also attempt to modify /etc/default/grub via the recovery option of the Live CD, but the change did not persist after reboot.  I attempted this multiple times as a matter of fact.

I suppose I could try knoppix.  Or maybe I'll rtm as to how to chroot to the drive with the system so I can attempt the change that way.  

Thanks for the response.

---

### Post by wildmanne39 on 2013-04-01
Moved to own thread.

---

### Post by GWild on 2013-04-06
> **GWild said:**
> I did also attempt to modify /etc/default/grub via the recovery option of the Live CD, but the change did not persist after reboot.  I attempted this multiple times as a matter of fact.

I suppose I could try knoppix.  Or maybe I'll rtm as to how to chroot to the drive with the system so I can attempt the change that way.  

Thanks for the response.


Solved.  As it turns out, I was not performing the /etc/default/grub edit and update-grub process properly when using the rescue system option of the LiveCD.

I used the LiveCD, went into rescue system, mounted the root file system, opened a shell in the root file system, mounted /boot, made the /etc/default/grub nomodeset edit, then ran update-grub.

The step I missed was typing "exit" to exit the root file system shell.  Once I did this the changes were made (and persisted) and I was able to boot the system with video.


Thanks to those who responded.

---

