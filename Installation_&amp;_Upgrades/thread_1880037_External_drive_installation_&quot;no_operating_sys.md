---
title: "External drive installation &quot;no operating system found&quot;"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by sdrsdrsdr on 2011-11-12
Hi all,
I have been trying to install 11.10 on an external drive.
I am running windows 7 x64 as my primary OS.
I go through the installation procedure for Ubuntu and it seems to go ok until I restart and then I get the error msg "no operating system found". I have set my bios settings to read from external drive. I have 4 partitions set on the installation drive /boot, swap, / and /home. I have set the boot loader to the external drive.
any help appreciated

---

### Post by rpms on 2011-11-19
Me too. This is my first try with linux and is a real bummer. After 2 tough days no boot with ubuntu 11.10 desktop. I just get the same "no operating system found" as you do. In this case the drive is internal. Should be dead simple. I use an empty disk, disconnected the only other HDD and used all the installer defaults. Installing from USB. The files look ok on the HDD.
But no o/s is found when trying to boot from it. Drag.

I will let you know if I can solve this. Good luck!

---

### Post by dniMretsaM on 2011-11-19
Use a tool like GParted and check to make sure boot flags are set to the correct partition.

---

### Post by rpms on 2011-11-19
Thank you [dniMretsaM]("http://ubuntuforums.org/member.php?u=1268161") for the super fast reply. 
 
I was just on a last go-round with Ubuntu and was already downloading a debian package when I tried the 32-bit ubuntu version. All previous attempts were with the 64-bit. [COLOR=darkred]*Is that just for AMD?? *[/COLOR][COLOR=black]The _32-bit worked_ right away. And the boot menu permits booting with windows 8 or ubuntu. Nice![/COLOR]
 
Would prefer 64-bit. In the future the version will likely be more successful.

---

### Post by oldfred on 2011-11-19
Grub does not use boot flag, but some BIOS will not let you boot unless you have a boot flag on a primary partition. 

Or it could be that you have not installed the grub2 boot loader to the MBR of the external drive?

The 64Bit is for both Intel & AMD cpus. 

If you want to know what is installed where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install mawk

---

### Post by dniMretsaM on 2011-11-19
> **rpms said:**
>  [COLOR=darkred]*Is that just for AMD??*[/COLOR]

No, the reason it's called AMD64 is because AMD was the first to make a 64 bit processor and the name just kind of stuck.

---

