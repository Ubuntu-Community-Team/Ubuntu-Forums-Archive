---
title: "Grud loading missing.. Help me :-("
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by ann pic on 2008-04-22
i got 2 operating system in my cpu. I re-format my windows due to some un-avoided problems. Now i cannot enter to Linux because the grud loader is missing or maybe delibrately un-installed. I cannot choose either windows or linux already. Once i boot my cpu it will directly go to windows operating system. Help me, now i cannot go into Linux environment.

---

### Post by noswal on 2008-04-22
This may help you

[http://ubuntuforums.org/showthread.php?t=193650&highlight=grub](http://ubuntuforums.org/showthread.php?t=193650&highlight=grub)

---

### Post by lswest on 2008-04-22
you can use the how-to i've written (second line of my sig) to re-install GRUB.  Also have a link to another how-to within the one i wrote, as it offers trouble-shooting.  Good luck.

---

### Post by Dr Droid on 2010-03-02
If you have no way of getting a live cd there is a file in windows which can be edited to point to the boot location for a different operating system. I have moved away from windows but i think the file was called boot.ini.   Do a search for that in windows or otherwise right click on my computer and i think it was in the system properties somewhere as well.


Which version of Ubuntu are you running? The difference is that 9.04 uses the legacy grub and 9.10 uses grub 2.  

Either way. Your situation sucks because you need to overwrite the MBR on your booting harddisk. This is sort of simple using an install disk from ubuntu. ignore the install and proceed to just test the OS. Once you are in you can manipulate both files on your windows partition and your new ubuntu partition. Go to the command prompt and try this.

update-grub

then 

grub install <ur device here> 

should be like /dev/sda for sata and i think /dev/hda for IDE (should not be /dev/sda1 or /dev/sda2!!!!!!! just sda!!!!)

if its mounted you can do this to find out which device

cat /mountpoint/fstab 

and match it up with the UUID found by doing this

sudo blkid

that should have updated your grub file and written it to your MBR and you should be able to see both ubuntu and windows from the grub menu. Another option is below


If you have no way of getting a live cd there is a file in windows which can be edited to point to the boot location for a different operating system. I have moved away from windows but i think the file was called boot.ini.   Do a search for that in windows or otherwise right click on my computer and i think it was in the system properties somewhere as well.

---

### Post by presence1960 on 2010-03-02
> **Dr Droid said:**
> 


If you have no way of getting a live cd there is a file in windows which can be edited to point to the boot location for a different operating system. I have moved away from windows but i think the file was called boot.ini.   Do a search for that in windows or otherwise right click on my computer and i think it was in the system properties somewhere as well.
boot.ini is an XP file, Vista/7 use something different. it would be better if the OP ran the boot info script so we can see exactly what is on the machine and it's boot process. Without that info we are all guessing- I would hate to be wrong!

ann pic do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

