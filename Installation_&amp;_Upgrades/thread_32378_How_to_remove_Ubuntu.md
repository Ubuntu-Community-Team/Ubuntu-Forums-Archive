---
title: "How to remove Ubuntu?"
date: 2005-05-07
forum: Installation &amp; Upgrades
---

### Post by jorgen_veisdal on 2005-05-07
I've installed it, and have now decided to change to either knoppix or XP, and I was wondering how do you remove it and format the hd?

---

### Post by leviathon on 2005-05-07
If Ubuntu is the only OS on your computer, simply boot off of the OS cd you wish to install and tell the installer to use the entire disk. The installer will format the disk to the filesystem it needs to use.

---

### Post by defkewl on 2005-05-07
Just insert the CD and format the partition where you install Ubuntu and then install your new OS there :)

---

### Post by jorgen_veisdal on 2005-05-07
Which cd? The installation one, or the live one (ubuntu)? It will boot the installation one, but I don't find any boot tools there..

---

### Post by enquiry on 2005-05-07
Some users have reported that the Windows install CD or the command fdisk -mbr (under DOS) does not actually restore the MBR (so they couldn't boot Windows after installing it). To resolve this use this command under Ubuntu (or any other GNU/Linux OS):

dd if=/dev/zero of=/dev/hda bs=512 count=1

After this pop in the boot CD for the OS you'd like to install and boot it.

Remember that you can dual boot Windows with any other OS, so you can have both (removing Ubuntu is not a requirement if you want to install Windows).

---

### Post by jorgen_veisdal on 2005-05-07
I use this command where exaclly? in the GUi or? Seriously man, your saving my ass here..

---

### Post by enquiry on 2005-05-07
[QUOTE=jorgen_veisdal]I use this command where exaclly? in the GUi or? Seriously man, your saving my ass here..[/QUOTE]
You type the command in a terminal (in Ubuntu you get a terminal by going to the menu Applications -> System tools -> Terminal). I forgot to say that you must type sudo before the command, so what you type is:
sudo dd if=/dev/zero of=/dev/hda bs=512 count=1

Remember that this removes the information that the machine needs to start Ubuntu, so there's basically no turning back once you've done this.

---

### Post by jorgen_veisdal on 2005-05-07
so, no sudo nico or stuff like that, just:

sudo dd if=/dev/zero of=/dev/hda bs=512 count=1

---

### Post by enquiry on 2005-05-07
[QUOTE=jorgen_veisdal]so, no sudo nico or stuff like that, just:

sudo dd if=/dev/zero of=/dev/hda bs=512 count=1[/QUOTE]
Yes, that's it.

---

### Post by jorgen_veisdal on 2005-05-07
Thank you so much, I'll keep you posted on how it goes here.

---

### Post by jorgen_veisdal on 2005-05-08
Didn't work.. It still won't boot.. Except the Ubuntu and knoppix cd. It won't boot the xp cd.. have no idea why

---

### Post by enquiry on 2005-05-10
Has it worked before? If so the CD might be damaged. If it's not damaged, follow this link: [http://www.microsoft.com/windowsxp/using/setup/expert/honeycutt_02october07.mspx](http://www.microsoft.com/windowsxp/using/setup/expert/honeycutt_02october07.mspx) and look under the section for "If Your CD Won't Boot" for hints.

---

### Post by Deamor on 2007-08-01
> **enquiry said:**
> Some users have reported that the Windows install CD or the command fdisk -mbr (under DOS) does not actually restore the MBR (so they couldn't boot Windows after installing it). To resolve this use this command under Ubuntu (or any other GNU/Linux OS):

dd if=/dev/zero of=/dev/hda bs=512 count=1

After this pop in the boot CD for the OS you'd like to install and boot it.

Remember that you can dual boot Windows with any other OS, so you can have both (removing Ubuntu is not a requirement if you want to install Windows).

I tried inputting your command and it did not remove ubuntu from my computer... what am i doing wrong?

---

