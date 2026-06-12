---
title: "Need to Install Xp on separate drive"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by wingryder on 2010-01-12
Very new to Ubuntu.. I have two drives..installed. One is empty. I want to install Xp on this empty drive so I can run both operating systems.  When I remove power to this empty drive.. Ubuntu wont boot...even though it is first in bios.  (I was hoping they were stand alone so my messing with this xp install would not mess up the Ubuntu in any way. )
My Grub screen does include windows2000/xp.as a option.  Maybe it will work after the install. If not Bios boot selection is fine with me.

So do I just unplug the Ubunto HD and install the xp on the empty drive or is there more to it than that?

Thanks for helping out a real newbe..

wingryder

---

### Post by darkod on 2010-01-12
If removing power to this "empty" drive stops ubuntu from booting, it's not exactly empty. I would guess grub2 bootloader went to that drive.
Do not disconnect any drive right now. Go into BIOS and set the windows drive (now called empty) as first in boot order. If the drives are different size you will easily know which is which.
After that install XP on that drive. It will put the windows bootloader on the MBR of the drive.
Check if XP is working fine and then go into BIOS again and set the ubuntu drive as first in boot order now.
You will probably not be able to boot ubuntu yet. Boot with the ubuntu cd, Try Ubuntu option and follow the guide here to reinstall grub2 to your ubuntu drive:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you are using 9.10 that means grub2 so be careful to follow the procedure for 9.10, not for 9.04. That should sort it out. Leave the ubuntu drive as first in boot order and that will bring up grub2 which should offer option for ubuntu and xp. If at start the grub menu doesn't show XP in it, boot ubuntu (from the hdd) and in terminal execute:
sudo update-grub

---

### Post by wingryder on 2010-01-14
Thanks darkod..

 I will give that a try.  My Ubuntu is 8.04  the Hardy Heron version. I will post results in a day or so.

thanks again

wingryder

---

### Post by wingryder on 2010-01-15
Ok here is a update. I installed XP on the "empty" drive. Call it Drive2.  
Installation went fine till it finished.. then xp would not boot.  In desperation I switched bios order to Drive 1 to see if Ubuntu would boot.  It did not but XP did.

So now I have Drive C and Drive F (not sure where assignment came from).  Drive F has Windows Xp on it.. but the boot info must be on Drive C.  ( No bootloader comes  up giving me options. )   From my reading other posts.. I think restoring the XP bootloader would be the easier route but not confident enough to jump in. 

thank you for sharing your expertise.

wingryder

---

### Post by Leppie on 2010-01-15
please download meierfra's script (link is in darkod's signature) and run it and post the generated RESULTS.txt.
you can use an ubuntu livecd for this.

---

