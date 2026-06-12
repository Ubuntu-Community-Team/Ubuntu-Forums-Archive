---
title: "Can't boot PC after installing 11.04"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by barraclm on 2011-05-02
I have an Asus P6T WS Pro motherboard with Marvell SE886320 SAS controller (which was acting as a Windows 7 PC).

I removed the RAID array from the SAS drives and wiped them clean (using BIOS utility).  I then installed 11.04 from the Live CD.  It installed just fine, could see both the drives etc.  However, when I reboot, as requested, the PC will not boot from the drive.

Any pointers as to what I can do to resolve this would be welcome.  I really don't want to have to go back to Windows 7!!

Michael Barraclough

---

### Post by majorawesome on 2011-05-02
Did you go into the bios hit the boot tab and hit boot off notebook hard drive? there should be an option in there that is close to that... and remember to take out the cd if you didn't

---

### Post by barraclm on 2011-05-02
Yes - The boot order is set to CD-ROM followed by hard disk.  I remove the CD-ROM and then rebooted.  The message I get is 

Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key_

Michael Barraclough

---

### Post by Dutch70 on 2011-05-02
Hi and welcome to UF

Let's have a look at your boot info script. Someone should be able to help you with it if I can't.

From the live cd, run the following command in a terminal.*(copy&paste)*
```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh; hb=HEAD'
```

That should put the boot info script in your downloads folder. Cut & Paste it to your desktop, and run this command.
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info **between code tags** using the "#" symbol in the tool bar of your next post.

 Again, to put it between code tags, just click the # symbol in the tool bar & paste it between [CODE] [ /CODE] tags. 
Do not skip this step or you will lose the formatting & I doubt if anyone will even look at it.

---

