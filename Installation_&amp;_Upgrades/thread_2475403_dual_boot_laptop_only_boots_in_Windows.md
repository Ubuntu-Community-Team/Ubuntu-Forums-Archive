---
title: "dual boot laptop only boots in Windows"
date: 2022-05-25
forum: Installation &amp; Upgrades
---

### Post by sysone on 2022-05-25
My Dell laptop has Win 10 and Ubuntu 22.04 but it only boots in Windows. There is no Ubuntu listed in the BIOS.
Somebody suggested that I boot in the installation media, mount my harddrive ubuntu partition and make changes.
So, I entered a new line 'GRUB_DISABLE_OS_PROBER=false', as suggested.
I did it with sudo gedit /etc/default/grub   and it worked fine but it did not let me save it.
Besides, it also said "gedit-encoding not supported".
I would prefer not to have to reinstall Ubuntu and lose what is already installed.
Any suggestions very much appreciated

---

### Post by grahammechanical on 2022-05-25
The change you made might have made a difference if the Grub boot menu was loading and only showing Ubuntu 22.04 and not showing an entry for Windows 10. Or the machine was loading directly into Ubuntu 22.04 without the Grub menu showing. After changing the entries in /etc/default/grub and successfully saving the file we need to run a command so that OS_PROBER detects other operating systems.

```
sudo update-grub
```

It is best to do this from the version of Ubuntu installed on the hard drive.

Regards

---

### Post by oldfred on 2022-05-25
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)   &           
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

It looks like you were not editing the grub in the install, but the version in the installer which cannot be changed.
You would have to chroot into install, edit grub & then run an update to grub inside the chroot.
Lets see what Boot-Repair shows before editing grub via chroot.

---

### Post by sysone on 2022-05-26
Thanks [**[COLOR=#000000]grahammechanical[/COLOR]**]("https://ubuntuforums.org/member.php?u=1087323")**[COLOR=#000000] and[/COLOR]****[COLOR=#C61919][B] **[/COLOR][/B][URL="https://ubuntuforums.org/member.php?u=852711"][COLOR=#C61919][B]oldfred for responding.
I did get into etc/default/grub and made the changes to =false.  
But that file is read-only and did not let [/B][/COLOR][/URL]me save.  
I also got into /Desktop and /Documents and others and copied folders to an external drive (not everything worked).
And I did run boot-repair from the ppa. It wanted me to disable secure boot -which I did. But again claims the same error:'locked NVram'.
I can poste the pastebin file but I would like to know if the read-only file can be changed and saved.

---

### Post by SeijiSensei on 2022-05-26
> **sysone said:**
> I did get into etc/default/grub and made the changes to =false.  
But that file is read-only and did not let me save.
You can't make changes to system files like /etc/default/grub as an ordinary user. You must use sudo like this:
```
sudo nano /etc/default/grub
```

---

### Post by sysone on 2022-05-26
> **SeijiSensei said:**
> You can't make changes to system files like /etc/default/grub as an ordinary user. You must use sudo like this:
```
sudo nano /etc/default/grub
```

As said:
"[COLOR=#000000]I entered a new line 'GRUB_DISABLE_OS_PROBER=false', as suggested.[/COLOR]
[COLOR=#000000]I did it with sudo gedit /etc/default/grub and it worked fine but it did not let me save it."

[/COLOR]I did use sudo  and I just did it manually. Each time it works but it does not let me save.

Is there any way that I can disable the ' read-only ' ?

---

### Post by oldfred on 2022-05-26
If you are in the live installer /etc/grub is part of the live system and is read only.
You have to edit the file in your install which from the live installer will have a different mount.
And to run the grub update, you have to chroot into system.

Best just to run Boot-Repair.
Does you Dell UEFI have some setting besides UEFI Secure Boot on preventing or restricting UEFI changes?
What model Dell?

---

### Post by sysone on 2022-06-01
I reinstalled Ubuntu 22.04 and it's working fine. Some personal files were lost.
And  I have to reinstall many apps.
Thank you all for responding

---

