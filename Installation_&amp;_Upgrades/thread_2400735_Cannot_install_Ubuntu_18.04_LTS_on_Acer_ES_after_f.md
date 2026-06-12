---
title: "Cannot install Ubuntu 18.04 LTS on Acer ES after following almost all help in forum."
date: 2018-09-09
forum: Installation &amp; Upgrades
---

### Post by hecome on 2018-09-09
[SOLVED]

I can't install Ubuntu on an Acer laptop, not even after following many of the suggestions on this forum.

[B]Acer Aspire ES 17 - ES1-732-C6HK
Intel Celeron Processr N3350
Intel HD Graphics
8GB DDR3 L memory
1TB HDD[/B]

This computer came with Win10, but ideal should only have Ubuntu on it.

**Installer medium is USB-drive made with Rufus on a Win7 system and the latest Ubuntu 18.04.**

The standard installation of a clean Ubuntu only disk stalls on Grub2, non of the described methods resolve this problem so far. Other instructions don't seem to fit my system as suggested options are not available.
Still the computer starts without a problem in 'try' version from the installation USB.
I managed to get **boot-repair** running in the hope to have some data for the Ubuntu specialists, but while running also boot-repair crashes on Grub reinstall.

---

### Post by 0N3 on 2018-09-09
Are you installing in UEFI or CSM / Legacy?

---

### Post by hecome on 2018-09-10
> **0N3 said:**
> Are you installing in UEFI or CSM / Legacy?

Thanks for the quick response 0N3, i was installing in UEFI. In the mean time i had a look at [https://askubuntu.com/questions/862946/unable-to-install-ubuntu-on-acer-aspire-es1-533](https://askubuntu.com/questions/862946/unable-to-install-ubuntu-on-acer-aspire-es1-533) 
I followed the instructions under answer 3, not easy if you are not familiar with Linux, so i had to retry some steps but got there in the end. The system is booting from internal HDD. Now i have to see what other stuff is needed on this computer.

Again the Ubuntu community proves to me that non-commercial cooperation works, thanks all.

---

### Post by oldfred on 2018-09-10
Use of rEFInd or using the "Windows Boot Mananger" label may work.
But UEFI boot with Acer requires "trust" setting in UEFI. This is unique to Acer but seems to apply to all models.
Many Acer also need UEFI update.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator) 
   Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by hecome on 2018-09-11
Thanks Oldfred for your response. 

In the mean time I managed to solve the problem. In fact I used many of you posts to try,  before I added my case.
I have to make clear here that the original HDD had been formatted, as windows no longer would be required on this computer.
You could say also this was a clean install, unless formatting 'left something behind', which I don't think.

I tried almost all of your treads about trust settings, alas this particular machine ill not activate nor show any of the choices to link to or appoint a trusted file, partition or disk. So that was a no go.
Links concerning the Acer Cloudbooks have to do wwith the same secure files. I have no Cloudbook nor access to any secure files, see point 1.
Link concerning downgrading UEFI/BIOS the machine is bought only a few month ago, the linked tread is from 2016. I don't think it concerns new computers and ruled this method out, but kept it in mind for 'you never know'.

Then I found [https://askubuntu.com/questions/8629...aspire-es1-533]("https://askubuntu.com/questions/862946/unable-to-install-ubuntu-on-acer-aspire-es1-533") this solved the install and booted Ubuntu. Since then the machine runs a supposed, the only thing remaining is that after the 'Shut down' command from the GUI, the system ends with a text screen stating shut down lines ending with '... reboot: power down' but the computer dosn't power down, it just ended the routine nothing more.

---

### Post by oldfred on 2018-09-11
The Cloud boot link shows the UEFI screens, and is the same in almost all Acer.

Many older threads had users downgrade UEFI to older version as they had a bug and you could not set trust. But that thread is a user reporting that UEFI upgrade then worked. But many systems still have that older UEFI that has issues.
So many users, particularly those who do not see correct screens after setting password need the UEFI update from Acer.

---

