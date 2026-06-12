---
title: "Running update-grub"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by Mattheu on 2011-02-24
I have just installed Ubuntu Studio 10.10 (Maverick) on a machine which already has Jolicloud 1.1 and Ubuntu Studio 10.04 installed, among other things. The new release and swap partition are in the logical partitions sda10 and sda11.

But the new Ubuntu release (10.10) does not appear in the GRUB boot list which is displayed, so I can't boot into it. As far as I can tell from the Grub2 documentation, I now need to run update-grub from the Linux installation which "owns" GRUB to update the list. Is this right?

If so, how do I tell which Linux installation is the "main" one? Is it the one currently displayed at the top of the GRUB list (10.04) or the one installed earliest (JoliCloud)? I am nervous about wrecking the GRUB configuration file, and losing the ability to boot anything.

Any guidance will be welcome.

---

### Post by Rubi1200 on 2011-02-24
Hi and welcome to the forums :-)

 > I now need to run update-grub from the Linux installation which "owns" GRUB to update the list. Is this right?Correct.

> If so, how do I tell which Linux installation is the "main" one? Is it  the one currently displayed at the top of the GRUB list (10.04) or the  one installed earliest (JoliCloud)? The answer is whichever OS was installed last, in most cases, unless you have some other boot configuration. If you installed Ubuntu Studio last and you allowed it to install a bootloader during installation, then it now controls GRUB.

If you chose the option not to do so, then the OS controlling GRUB will be the one installed prior to this install unless...see comments above again.

Is this clear?

Hope this helps.

---

### Post by Mattheu on 2011-02-24
Thank you, that seems clear, but ...

I'm reasonably sure that every time I have installed a new OS (either Ubuntu or JoliCloud) the installer has correctly detected all the other OS's present and I have (rightly or wrongly) selected <Yes> when asked: Install the GRUB boot loader to the master boot record?

In which case, given that the last OS installed was Ubuntu Studio 10.10, that should be the one which owns GRUB. But, as that is the one missing from the GRUB boot list, I can't see how to go into it to run update-grub.

But maybe v10.04 still owns GRUB for some reason, and running update-grub there will solve the problem and do no harm.

So I'm baffled for the moment.

---

### Post by Rubi1200 on 2011-02-24
There is no harm in running update-grub in 10.04 and if it picks up 10.10 then that should answer the question.

But, you can also do the following (can also be run from within 10.04) because maybe the bootloader was not installed correctly:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Mattheu on 2011-02-25
> There is no harm in running update-grub in 10.04 and if it picks up 10.10 then that should answer the question.I have now run update-grub in 10.04,and it found the new OS, and the boot list displayed is now complete.

One reason I wanted this version is that the network configuration tool is available. With 10.04 I was unable to get a network connection, so could not proceed after installation. With 10.10, I now have a network connection configured.

THANKS for the help!

> But, you can also do the following (can also be run from within 10.04) because maybe the bootloader was not installed correctly:> Boot the Ubuntu Live CD/USB.  Choose the option "Try Ubuntu without any changes."I have not thus far been able to do this because my Ubuntu Studio installation USB doesn't seem to offer this option.

---

### Post by oldfred on 2011-02-25
You do not have to run boot script from liveCD. It will work from most Linux installs. So you should be able to download and run the script from whichever version of Ubuntu you are booting. If Studio version is missing any standard apps that boot script expects (and that std installs normally have) then it may give an error message and you can easily download the additional application.

Also which every version of grub/Ubuntu is in the MBR and booting will have its version first in the grub menu, all the others are added at the bottom of the menu.

---

### Post by Rubi1200 on 2011-02-25
Hi Mattheu,
glad you got things sorted out and working the way you want.

You are more than welcome for the help too :-)

As oldfred mentioned you can also run the boot script inside a working Linux install (which I actually mentioned in my last post hidden away in brackets).

Please mark this thread Solved using the Thread Tools near the top of the page if you are satisfied the problem has been taken care of.

Enjoy!

---

