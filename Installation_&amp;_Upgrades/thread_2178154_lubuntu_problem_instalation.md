---
title: "lubuntu problem instalation"
date: 2013-10-02
forum: Installation &amp; Upgrades
---

### Post by mhm770 on 2013-10-02
Hi

I want to install Lubuntu in my old laptop - Dell, AMD 64 , 2GB RAM

but i have this error:

[B][COLOR=#333333][FONT=Ubuntu]no text casper/vmlinuz: file not found

[/FONT][/COLOR][/B][COLOR=#333333][FONT=Ubuntu]any help pls [/FONT][/COLOR]**[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR]**

---

### Post by ajgreeny on 2013-10-02
When do you see that error?
Can you boot to the live system and then try installing from that or do you not get that far?

---

### Post by mhm770 on 2013-10-02
i see the error when i boot and the Lubuntu DVD try to install lubuntu , i dont know what you means for LIVE SYSTEM :confused:, im not a expert

---

### Post by Lars Noodén on 2013-10-02
Did you burn from a complete disc image?  You can usually see the what the MD5 checksum for your file is in the burning program.  You can check what it was supposed to be here: [http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/)  In the file MD5SUMS or SHA256SUMS.

In general, using a torrent is the most reliable way of getting disc images if you have that option available.  FTP and HTTP work, of course,  but then you have to manually verify that you got the disc image whole and uncorrupted in transmission.

---

### Post by mörgæs on 2013-10-02
If your computer supports booting from USB it's a safer approach than CD/DVD.

---

### Post by walterorlin on 2013-10-02
It is probably a bad download or a bad burn. Check Md5sums. If you have the disk you can also get to it at the menu with check disk for the livecd.

---

### Post by mhm770 on 2013-10-02
when i boot the computer , the first error i get is: ERROR READING SECTOR 337344, then : **[COLOR=#333333][FONT=Ubuntu]no text casper/vmlinuz: file not found[/FONT][/COLOR]**

---

### Post by ajgreeny on 2013-10-02
Then it is either a bad download or a bad burn to DVD.

Check your .iso file against the md5sum list at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes") and if it does not match, download again; if it does match perfectly just reburn again at the slowest speed available on your DVD drive.

---

### Post by mhm770 on 2013-10-02
ok thanks !

---

