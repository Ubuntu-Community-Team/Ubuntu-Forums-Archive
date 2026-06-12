---
title: "Help!! booting Ubuntu and Win7"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by Grasber on 2011-04-16
I'm lost here.. I have tried meny things but I always screw it.

I have a primary 160 GB HDD with Win 7 installed.
A secondary 80 GB HDD with: 50GB NTFS, 28 GB ext4 (with Ubuntu) and a 2GB particion for swap.

Initially I had Win 7 installed and I then installed Ubuntu into the second partition. Trough Windows7 I formatted the 50 GB partition in the secondary drive. After that I had problems with grub. I was getting the grub rescue screen that I fixed by booting (manually) into Ubuntu and fixing the fstab file (there was a unit that was trying to be recognized by other name) ([http://ubuntuforums.org/showthread.php?p=10662477](http://ubuntuforums.org/showthread.php?p=10662477)).

After I fixed that I noticed that grub didn't have Windows7 listed. Even using grub-update won't fix the problem. I had to manually add it to the list, but then it would give me a bootmgr not found error.

I sought through internet for an answer and then I decided to make a USB recovery unit for windows 7. I entered the repair console and tried to fix the mbr of the 160 GB HDD. After that I rebooted and grub gave me a bash screen. Now I'm desperate for getting back my Win7 and Ubuntu :(

---

### Post by Dutch70 on 2011-04-16
I would suggest unplugging the Ubuntu hdd and get windows booting first. Then Unplug the windows hdd and get Ubuntu booting. 
Then it would just be a matter doing a grub-update from within Ubuntu.

However if you want someone to take a look at what you've got going on now. Please post your boot info script.

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]

Then open a terminal (Cntrl+Alt+T) and run the following command...
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just click the # symbol in the toolbar & paste it between [CODE] [ /CODE] tags.

---

