---
title: "I Want To Totally Switch To Ubuntu On My Laptop"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by CharleyGnarly on 2011-06-13
I have been using Ubuntu on one of my laptops, and I *really* like it. 
So, I want to utilize my entire hard drive for Ubuntu. I want to totally get rid of Windows.
What would be the proper way to do it? I already have an Ubuntu disc ready to go. Ultimately I would like to just get rid of Windows and then add that extra space to Ubuntu. That way all of the stuff I have loaded (pics, updates, apps, etc.) will still be there.

---

### Post by raja.genupula on 2011-06-13
for that hardrive do you wanna go  for new installation, formatting entire HD or just installing ubuntu with out any data loss

---

### Post by akand074 on 2011-06-13
Do you want your files from Windows to remain? Or do you already have Ubuntu installed and just want to get rid of Windows? If you only have Windows, I'd backup all your data and let the Ubuntu installer use the whole disk and then put the files back on. If you already have both, then just transfer your stuff over to your Ubuntu partition and then wipe Windows and set it as free ext4 space. Though, reinstalling Ubuntu is so easy and quick that I'd recommend you wipe and reinstall Ubuntu using the whole disk.

---

### Post by sidzen on 2011-06-13
Download [System Rescue CD 1.3.5]("http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/1.3.5/")

Boot to it.  

After it boots, SysRescCD wants you to hit defaults (hit Enter) a couple times. When you end up at the multi-colored prompt on the page asking user to enter either "startx" or "wizard," type in the following command

[PHP]dd if=/dev/zero of=/dev/sda bs=4096 conv=notrunc,sync[/PHP]

This will destroy all trace of any Windows File System, wiping your entire hard drive with zeros.  It will take a while, depending on the size of your hard drive, so go make a sandwich or something. When it's done, you'll see some statistics after a statement that there is no "more space on drive" and the size of your hard drive.

Don't bail out yet!

At the same prompt, type in the desired "startx" and Enter
This brings up the XFCE mouse then a yellow-colored terminal.
In the yellow-colored terminal, type the command "gparted".

Partition your hard drive.

---

### Post by CharleyGnarly on 2011-06-13
Excellent. I am off to give it a try. I will report back later.

---

### Post by Thewhistlingwind on 2011-06-13
If your just looking for total data massacre, no bits will be saved, just go ahead and install ubuntu, it takes, thirty minutes, max.

---

### Post by mörgæs on 2011-06-14
Sidzens approach is good, if you have some confidential data that must be thoroughly erased, but it is not necessary in order to free all space on the drive. 

If the latter is the aim, just install Ubuntu an choose 'use entire drive for Ubuntu' or something similar. Welcome aboard!

Remember to back up all your important files to a separate USB drive and remove it during installation.

---

### Post by CharleyGnarly on 2011-06-17
I now have Ubuntu installed onto my laptop, and Windows is completely gone. I just booted off of the disc, and did the total install thing. Worked like a champ.
Thanks for the help.

---

