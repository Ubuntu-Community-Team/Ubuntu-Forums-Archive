---
title: "Grub help"
date: 2012-08-07
forum: Installation &amp; Upgrades
---

### Post by cps5155 on 2012-08-07
So I had recently had win7 and ubuntu 12.04 installed on seperate partitions of my laptop. Customized ubuntu to basically macbuntu and everything was solid. Ended up having problems with some win7 drivers and after BSOD I decided to reformat. 
 
Second time through win7 is working again and all is good. Unfortunately I've lost my GRUB bootloader for ubuntu/win7 choice when I turn my laptop on. I like GRUB a little more than I do win7's boot menu so my question is, is it possible to bring back GRUB without re-installing ubuntu? All partition and files from ubuntu (pre-win7 reformat) are still good. boot/grub still exists and also files inside there look good to, how do I tell windows to use the bootloader located in the other partition in /boot/grub (or wherever correct file location is)?
 
Any help is appreciated

---

### Post by drs305 on 2012-08-07
cps5155,

Welcome to the Ubuntu Forums.

If your Grub files are all still intact and you can't boot directly into Ubuntu, you can restore GRUB by booting a LiveCD with the same version you installed. Then open a terminal and run the following command.

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

This assumes Ubuntu is on sda5, you don't have a separate /boot partition, and your boot drive is sda. Change the values as necessary and do not use the partition number in the second command.

This should point your boot back to the Grub files. If Windows isn't on the menu when you reboot (if it boots directly to Ubuntu), run "sudo update-grub" so Grub can search for and find your other OS and add it to the boot menu.

---

### Post by cps5155 on 2012-08-07
Awesome! That brought back my GRUB and all my files were still intact and operable. Good start, now that brings another problem. when I choose my default boot (Win7) it comes up with a black screen saying 
 
"error: no such device: 688282078281DA48
 
Press any key to continue..."
 
So I press a key and then it brings up the windows boot manager where I select Win7 (only OS in the list). Win7 boots fine and works, but this step wasn't there previously and could cause me some worry down the road. Anything known to fix said step? Maybe I have to change the settings in GRUB for the default and tell it to look at the new win7 OS? just throwing it out there

---

### Post by drs305 on 2012-08-07
I don't know if that is a Windows error or GRUB. I don't use Windows so if it's the former I can't help much.

At the GRUB menu, highlight Windows and press 'e' to edit the entry. If there is a 'search' line, try using the cursor keys to move to that line and remove it (or any line containing the UUID from the error message). Then try booting with F10 or CTRL-x to see if you still get the error message. Let us know if this action helps - it's not persistent, which means the change is temporary.

---

### Post by cps5155 on 2012-08-07
There in fact was a 'search' line and removing it temporarily booted into windows without such error message. Next (and hopefully final question) is how can I remove or even comment out said line permenantly? pressing 'e' to edit brings up all options and 'search' line is in middle.
 
```
 
setparams 'Windows 7 (loader) (on /dev/sda1)'
 
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root688282078281DA48
chainloader +1

```

---

### Post by drs305 on 2012-08-07
I can figure out and give you the modifications necessary to the /etc/grub.d/30_os-prober file so that the change is retained any time the 'update-grub' command is executed, but there is an easier method.

Copy the entire Windows menuentry (what you posted, but without the 'search' line) to /etc/grub.d/40_custom. Paste it below the existing lines. Save the file. 

Next, make 30_os-prober unexecutable so that it doesn't create a duplicate Windows menuentry. And then update GRUB so the 40_custom menuentry is added to the boot menu.
```
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
```

---

### Post by cps5155 on 2012-08-07
I've edited /etc/grub.d/40_custom using the terminal command 
 
sudo gedit /etc/grub.d/40_custom
 
and then appended the end of the file to look like the entire windows menuentry without the 'search' line. After doing the terminal commands mentioned above, i rebooted and this time no windows 7 option was present in the GRUB and after using 'e' to edit the GRUB the command looks entirely different than previous. As if it didn't update grub to use the 40_customs file.

---

### Post by cps5155 on 2012-08-07
Apparently by giving execute permissions back to root for /etc/grub.d/30_os-prober and modifying the /etc/grub.d/40_custom to mimic the windows menu entry without the 'search' line then re-updating grub allowed this to work without error. win7 is back on the grub menu as a choice and boots into win7 without any errors now. So i guess I didn't need to change the permissions in the first place?
 
Anyways, it works now thank you very much for the help and guidance

---

### Post by drs305 on 2012-08-07
It's possible the 40_custom file is not executable, although by default it should be. You can ensure it is with the following. I've added the command to make 30_os=prober executable again, as it's better to have 2 Windows entries than none at all.  ;-)
```

sudo chmod +x /etc/grub.d/40_custom /etc/grub.d/30_os-prober
```

Please post the content of /boot/grub/grub.cfg and /etc/grub.d/40_custom if it still isn't adding the Windows entry.

---

### Post by oldfred on 2012-08-07
If you reinstalled Windows it probably created a new partition  with a new UUID.

So try this just to see what happens, if not back to drs605's details.

sudo update-grub

You also have to run the above after any of the edits to 40_custom anyway.

---

### Post by drs305 on 2012-08-07
*oldfred* picked up something I missed. I never had you run 'update-grub' after reinstalling Grub to the MBR and rebooting. Reviewing the thread there is a good chance you never ran it prior to disabling 30_os-prober. That may be all you need to do to get the correct UUID into the Windows menuentry. Just make sure the 30_os-prober script is executable (+x) before running 'update-grub'.

Thanks for pointing this out *oldfred*.

---

### Post by cps5155 on 2012-08-08
After I made 30_os-prober executable again and updated grub like both are saying, it seems to have fixed the problems. Thank you very much for the quick replies and assistance

---

### Post by Glynnux on 2012-08-16
> **drs305 said:**
> cps5155,

Welcome to the Ubuntu Forums.

If your Grub files are all still intact and you can't boot directly into Ubuntu, you can restore GRUB by booting a LiveCD with the same version you installed. Then open a terminal and run the following command.

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

This assumes Ubuntu is on sda5, you don't have a separate /boot partition, and your boot drive is sda. Change the values as necessary and do not use the partition number in the second command.

This should point your boot back to the Grub files. If Windows isn't on the menu when you reboot (if it boots directly to Ubuntu), run "sudo update-grub" so Grub can search for and find your other OS and add it to the boot menu.


THANK YOU, THANK YOU, thank you, thank you, thank you drs305 !
I must not hold conversations about dog food whilst installing Burg! It's probably installed on HDOG.... :)

---

