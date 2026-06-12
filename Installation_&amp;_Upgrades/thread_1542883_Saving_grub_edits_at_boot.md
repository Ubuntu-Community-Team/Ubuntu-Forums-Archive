---
title: "Saving grub edits at boot"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by pmicou on 2010-07-31
EDIT: Problem solved. I replaced "quiet splash" with "acpi=off" and everything works perfectly. Thanks for the advice everyone! 



I have installed Ubuntu 10.04 on a hard-drive partition, but I have yet to have it boot successfully. The boot starts normally, but then the screen goes blank.
I am currently trying this solution:
>  * At install screen press F6 and select nomodeset and install Ubuntu as usual.
* On first boot after install, press e on getting the GRUB bootloader.
* Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
* Press Ctrl and X to boot
* You should now be able to login to your Ubuntu as usual
 

However, it seems that I am unable to get the changes I make in grub (changing "quiet splash" to "nomodeset" in the screen brought up by pressing 'e' when booting) to save (update) correctly. How is this done?
I have tried bringing up the command line and using 'sudo update-grub', but sudo is unrecognised. 

Note: I am using a MacBook 5,2; which has reportedly had some difficulties with Ubuntu requiring a few workarounds.

Edit: The 'Try Ubuntu without installing' option on the CD I burned works absolutely fine, it's just the installed version that does not work.

---

### Post by RTrev on 2010-07-31
You need to edit, as root, the file /etc/default/grub.

```

gksudo gedit /etc/default/grub

```

When it's open, you should find a line which you can edit to look like this:

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet nomodeset splash"

```

Note that I left the quiet and splash in there.  That's optional.  Take them out if you prefer.

Once you've made the change and saved the file, then update your grub:

```

sudo update-grub

```

Sorry, but I have no clue why sudo wouldn't work on your machine.  If you can become root in any way, that would work.  For example, log in via the recovery mode and you should get to a command line as root, so you can just leave out the sudo and gksudo.

HTH,
Bob

---

### Post by pmicou on 2010-07-31
Thanks Bob, unfortunately I get exactly the same problem when trying to boot in recovery mode: a screen that goes blank during the boot process; so I cannot get to those files yet.
The change I tried to make was in the GRUB 1.98 1ubuntu5 screen that is brought up by pressing the 'e' key at boot; but when I press 'ctrl' + 'x' to boot or 'esc' to exit it looks as though my changes are not being brought into effect.

I think the problem is being caused by some driver issue with my nVidia graphics card.

---

### Post by oldfred on 2010-07-31
The e is one time change and you may also have to add the nomodeset to the recovery mode. I would think recovery mode should work without nomodeset.

I installed nvidia driver and have not needed nomodeset after first boot. You have to boot once with the manual edit and then follow RTrev's instructions on editing the grub file that holds configuration settings.

If it did not give you an option to install the nvidia driver look in System, Administration, Hardware drivers and see if it shows the Nvidia driver.

---

### Post by RTrev on 2010-07-31
> **pmicou said:**
> Thanks Bob, unfortunately I get exactly the same problem when trying to boot in recovery mode: a screen that goes blank during the boot process; so I cannot get to those files yet.

Can't you manually edit the grub options at boot time by hitting the "e" key again, only this time on the recovery line?  It should be the last time you'll have to do it if this works.

You should have a boot line that ends with "ro single" if I'm not mistaken.  I think you could just add "nomodeset" to that.

---

### Post by pmicou on 2010-07-31
> **RTrev said:**
> Can't you manually edit the grub options at boot time by hitting the "e" key again, only this time on the recovery line?  It should be the last time you'll have to do it if this works.

You should have a boot line that ends with "ro single" if I'm not mistaken.  I think you could just add "nomodeset" to that.

I have just tried this, same story though. The screen still goes blank.


@oldfred: That's pretty much what I'm planning on doing as soon as it boots correctly.

---

### Post by oldfred on 2010-07-31
Some other places to look for alternatives:

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by pmicou on 2010-07-31
That seems to have done it, thanks.

---

