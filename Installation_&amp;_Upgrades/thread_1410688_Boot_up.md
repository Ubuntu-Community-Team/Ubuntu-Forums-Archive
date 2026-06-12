---
title: "Boot up"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by fillyo on 2010-02-19
Hi,

I am completely new to Ubuntu, I just installed it on my spare hard drive to try out. After a day of playing around, I wanted to boot back to Win 7.  So, I go into my bios and reorder my hard drives, and I figure I would just boot into Win 7 since that is my first hard drive in my boot priority.  Well, the Ubuntu menu comes up, regardless of priority of hard drives.  While this is not a bad feature to be able to choose, I am not sure I want to do this every time I boot up.  It there a way to get rid of option?  Also, will this go away if I disconnect the hard drive that has Ubuntu installed on it?

---

### Post by stlsaint on 2010-02-19
> **fillyo said:**
> Hi,

I am completely new to Ubuntu, I just installed it on my spare hard drive to try out. After a day of playing around, I wanted to boot back to Win 7.  So, I go into my bios and reorder my hard drives, and I figure I would just boot into Win 7 since that is my first hard drive in my boot priority.  Well, the Ubuntu menu comes up, regardless of priority of hard drives.  While this is not a bad feature to be able to choose, I am not sure I want to do this every time I boot up.  It there a way to get rid of option?  Also, will this go away if I disconnect the hard drive that has Ubuntu installed on it?

Yes that menu you see is Grub. The bootloader for ubuntu. It will get very annoying fast if you continue to switch bios hdd order everytime you want to boot into a different os everytime instead of just choosing one at startup. To answer your question yes that menu will go away if you remove the hdd containing ubuntu. A better option will be to let grub stay where it is(which seems to be on the mbr of your master hdd) and just choose which os you want to boot into at reboot using bootup manager in ubuntu. That way after you reboot your system should boot directly into whatever os you tell it without having to go thru grub. But when you reboot after being in windows you will see grub again.

---

### Post by fillyo on 2010-02-19
Can I eliminate the mbr on my hard drive that contains windows 7 so I can choose which OS i want to boot through my bios, since its not like I am running each one every day.

---

### Post by presence1960 on 2010-02-19
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page and all credit is his.

---

