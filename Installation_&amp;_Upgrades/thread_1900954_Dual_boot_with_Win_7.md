---
title: "Dual boot with Win 7"
date: 2011-12-27
forum: Installation &amp; Upgrades
---

### Post by Dogzilla1000 on 2011-12-27
I installed UBUNTU 11.10 on a new system with Win 7. I installed for a dual boot, everything in the install went fine. When I re-boot, the computer starts up in Win 7 every time, no boot menu, with an error message about the changed configuration. I tried several times, same results.

It seems that the MBR is locked. There is no help for this on the install disk that I can find. How do I fix this? 

Also, the UBUNTU install CD doesn't give me a way to restore my hard drive back to the same configuration as before. I can use the Windows 7 tool to delete the Linux partitions, then convert those back to a second NTFS virtual drive. But if I can't install UBUNTU, I would like my drive to be in the original Windows configuration. 

I'm not please that the install disk doesn't work, plus it doesn't give me a way to restore my machine. I've used UBUNTU for a long time, and I've really liked it, but this experience is very unpleasant.

---

### Post by oldfred on 2011-12-27
Welcome to the forums.

Some BIOS have a way to lock the MBR to prevent overwriting it. Have you checked BIOS settings.

Otherwise post this from liveCD or USB:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

You can use gparted from liveCD to delete Ubuntu's partitions. You should always use Windows partition tools to resize Windows partition to avoid issues, but not to create partitions as that may cause it to convert to dynamic partitions which do not work with Linux and even some Windows repair tools. After any resize Windows will want to run chkdsk or other repairs.

---

### Post by darkomano on 2011-12-27
It would be simple to add Ubuntu to Windows 7 boot menu.
 
1. Get "ext2fsd". The tool lets you see and copy files from ext2,3,4 partitions.
2. Copy over to Windows 7 the file "/boot/grub/boot.img" in say Windows root folder ("\").
3. Download [Visual BCD Editor]("http://www.boyans.net") and install.
4. Run it. Click on "Create BootSector loader". Amend path and drive to point to "\boot.img".
 
This is the cleanest way of booting a GRUB-2 based OS from Windows 7/Vista.

---

