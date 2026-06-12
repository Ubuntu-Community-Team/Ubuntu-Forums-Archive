---
title: "Ubuntu 12.04 upgrade chaos"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by chortle on 2012-04-27
I started an upgrade, from 11.10 to 12.04, yesterday. I had a couple of power outages, shut down, started up and told ubuntu to go on with "partial" update. I did this twice, and it seemed to keep going, trying to download all 1900-ish files. I had to go out a few hundred files from the end of the "get packages" bit. 

When I came back, hours later, the power was out. I don't know if installation finished. Downloading of files may have completed. I don't know if it needs user input at that point. 

When I turn on the system now I can't get to the startup screen.

If I choose Ubuntu 3.0.0-17-generic I get a blank screen.

If I choose Ubuntu 3.0.0-17-generic (recovery mode) I go to a menu with various options. But it is screwed. If I press the down arrow it sometimes goes to the option below, other times nothing happens, other times I go to a screen with Ubuntu 11.10 and a light sequence under it (like it is loading, but never gets anywhere).

Sometimes I can select the options.

I can't start the internet from that option.
The command prompt won't display what I type, and sometimes deletes characters. e.g. I type df<carriage return> but it takes f<carriage return>. I managed to df and found that the SSD I boot from is there, as is an external storage HDD, but not the old /home 1TB drive.

sudo apt-get update (when I managed to get that to run) says failed to resolve archive.ubuntu.com.

BTW, when I try to run older versions of Linux, from the grub menu, I have the same problems.

What should I do? I am at work now. Should I download 12.04 onto a memory stick, boot that and upgrade from there again? Will I lose anything?

---

### Post by Finalfantasykid on 2012-04-28
I wonder if grub simply did not get updated or something.  You might be trying to boot with a kernel which is no longer on the computer.  You might be able to fix this by loading a live cd and doing a update-grub, you may need to do a [chroot]("http://ss64.com/bash/chroot.html") for that to work mind you.

---

### Post by carl4926 on 2012-04-28
> I had a couple of power outages, shut down, started up and told ubuntu to go on with "partial" updateYou didn't expect everything to be OK after this... surely!

---

### Post by carl4926 on 2012-04-28
> **Finalfantasykid said:**
> I wonder if grub simply did not get updated or something.  You might be trying to boot with a kernel which is no longer on the computer.  You might be able to fix this by loading a live cd and doing a update-grub, you may need to do a [chroot]("http://ss64.com/bash/chroot.html") for that to work mind you.

Indeed, this is a good starting point.
Or just do a new install and put everything back in place from your backup

---

### Post by Finalfantasykid on 2012-04-28
> **carl4926 said:**
> Indeed, this is a good starting point.
Or just do a new install and put everything back in place from your backup

That might end up being easier, because who knows what else might have gone wrong during the upgrade.

---

### Post by sanderj on 2012-04-28
> **chortle said:**
> 

What should I do? I am at work now. Should I download 12.04 onto a memory stick, boot that and upgrade from there again? Will I lose anything?

If you could try an upgrade indeed. And if that does not work:
Boot from a live CD/USB, and copy files you want to keep to an external USB-stick/harddisk. Then do a *fresh* install.

---

### Post by chortle on 2012-04-28
> **sanderj said:**
> If you could try an upgrade indeed. And if that does not work:
Boot from a live CD/USB, and copy files you want to keep to an external USB-stick/harddisk. Then do a *fresh* install.

This is what I will do. I've loads of spare space on the attached drives.

Thanks everyone, for coming to my aid in my time of need!

---

### Post by chortle on 2012-04-28
Problem solved. I installed over the top of the spagged installation having grabbed the contents of my encrypted /home directory and saved a copy of the archived packages I'd downloaded.

Was very pleased to find that I had my old desktop when I booted up. I hadn't needed to extract my /home folder. Using the same user name Ubuntu pointed me at the same home directory.

Thanks for all your support.

---

### Post by carl4926 on 2012-04-28
> **chortle said:**
> Problem solved. I installed over the top of the spagged installation having grabbed the contents of my encrypted /home directory and saved a copy of the archived packages I'd downloaded.

Was very pleased to find that I had my old desktop when I booted up. I hadn't needed to extract my /home folder. Using the same user name Ubuntu pointed me at the same home directory.

Thanks for all your support.
Good to hear that positive result

---

