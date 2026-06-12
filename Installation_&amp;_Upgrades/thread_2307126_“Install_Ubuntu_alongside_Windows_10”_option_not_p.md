---
title: "“Install Ubuntu alongside Windows 10” option not present"
date: 2015-12-22
forum: Installation &amp; Upgrades
---

### Post by MZ667 on 2015-12-22
I am currently using an ASUS X552CL which came pre-installed with windows 8. I had installed windows 7 pro, and then upgraded to windows 10.

I am trying to dual-boot my PC with Ubuntu 14.04.3 LTS (64-bit), but during installation, it says, "This computer doesn't have any OS. What do you want to do?".  Also, if I try the "something else" option, it does not detect my partitions (I had partitioned 30 GB to install Ubuntu using the windows disk management tool). All I see is my hard disk in it's entirety.

Honestly, I am new to this, and have been trying to find solutions for a few days now. Thus far, I have disabled hibernate and faststart.

I have used [FONT=courier new]sudo apt-get install gdisk[/FONT] within the Ubuntu Live desktop, and it finds a valid MBR and a corrupt GPT.

Also, I have found that a BootInfo summary would be useful for people who may assist, so I have generated one using the Boot-Repair tool. Mine can be found here: [http://paste.ubuntu.com/14135768](http://paste.ubuntu.com/14135768) 

Any help will be greatly appreciated.
 Thanks.

---

### Post by Bucky Ball on 2015-12-22
*Thread moved to **Installation & Upgrades**.*

Welcome. You'll have more luck here and splitting your post into paragraphs will further improve your chances of support. Good luck. :)

---

### Post by MZ667 on 2015-12-22
Thanks for the move and advice. :KS

---

### Post by Bucky Ball on 2015-12-22
You need to boot into Windows, switch off hibernation and faststart. You mention hibernation, but not faststart. If not, Windows doesn't really shutdown. You need the machine to shutdown totally. Power off. No OS hibernating (which is what Win would normally do).

Forget about Win disk management partitions. Ubuntu uses EXT4 filesystem which Win knows nothing about. You've probably created NTFS. You only need free space, the install (Something Else when you get there) can take care of the rest.

Can you boot the install media and 'Try Ubuntu'? What happens there? Desktop?

Check in the BIOS that Win is installed in UEFI. Install Ubuntu in UEFI if it is.

---

### Post by MZ667 on 2015-12-22
faststart was disabled along with hibernation, sorry I forgot to mention that.

I had merely "shrunk" my volume, did not format it. 

I did boot the media, and 'Try Ubuntu'. That is how I was able to use the terminal to run gdisk and the Boot-Repair tool (As mentioned earlier).

According to my "system information", Windows is installed in Legacy BIOS mode.
[IMG]https://onedrive.live.com/redir?resid=55F89D746BAA36E7!1171&authkey=!AKsV4L6iBvN18Vc&v=3&ithint=photo%2cpng[/IMG]

---

### Post by Bucky Ball on 2015-12-22
Just checked your bootinfo output. There is no free space there.

Boot to the BIOS with the install media inserted and make sure that is booting in BIOS mode.

Follow whatever Windows is installed in is about it.

---

