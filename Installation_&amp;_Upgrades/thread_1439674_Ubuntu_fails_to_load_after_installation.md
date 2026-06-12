---
title: "Ubuntu fails to load after installation"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by arkadeep on 2010-03-26
I have a compaq nx6120 laptop
512ram
160gb hdd
1.77 ghz processor

i'm very new to linux so please bear with me....i recently installed openSUSE on my laptop....like a week ago...i really liked it but i couldn't figure out most of the things....so i thought of changing to ubuntu for its ease of use....so i started the install and chose to keep them both side by side....i gave 80gb to ubuntu and around 68 or something to openSUSE......after that everything went well and the installation went alright.....

but once i rebooted to start ubuntu,
the screen said grub loading
and then showed this error

error: no such device: 128588ae-ebdb-4c5e-8664-5db7aec79fae
Press any key to continue...

and i do press a key, it takes me back to the boot screen and every time i chose ubuntu, this error keeps appearing....

so i would like to ask that what is the problem and how to solve it???

any help highly appreciated
thanks in advance

-arkadeep

---

### Post by dstew on 2010-03-26
Do you get the grub menu? Is it after you choose Ubuntu that you get the error message? If so, it probably means that grub is mis-configured. It seems the partition grub is looking for by that UUID cannot be found.

If you have only one disk, do you know which partition Ubuntu is in (like /dev/sda1 or /dev/sda2)? If so, you can edit the menu entry for Ubuntu "on the fly" by pressing 'e' at the opening menu. Select the line(s) with the UUID that is not working. Hit 'e' again to edit the line. Substitute /dev/sda1 or whatever the Ubuntu partition is for the UUID if the problem is in the kernel line. If the problem is in the root= line, you need to use grub-designation for that parameter. So, instead of /dev/sda1, you would use (hd0,1). Hit return to save the edit, then 'b' to boot. Does that work?

---

### Post by arkadeep on 2010-03-27
thanks a lot for replying!
but now the menu isn't even showing

---

