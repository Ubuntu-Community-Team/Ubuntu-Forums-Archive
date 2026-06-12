---
title: "Hard drive wont Boot"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by chris1k94 on 2010-03-09
I recently put together a computer with scrap parts that I have.  It had no operating system on it at all.  I downloaded Ubuntu on a different computer and burned it to a CD (I also verified the hash).  I put the disk in and followed the instructions.  Then when it wanted me to take the disc out and reboot I did so and clicked ok and it rebooted.  I changed the boot order so that 0-HDD was first, and it said that the disk failed and wanted me to put in the system cd.  Anybody have any solutions?

---

### Post by rogue_0111 on 2010-03-09
Run Ubuntu from the CD. Check the HD is showing up. Check to see if any files were installed.

---

### Post by presence1960 on 2010-03-09
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

### Post by chris1k94 on 2010-03-28
Thanks guys for the help, but i think i figured it out.  I tried it on another computer and it worked.  I have came to conclude that it was a result of a bad hard drive.

---

