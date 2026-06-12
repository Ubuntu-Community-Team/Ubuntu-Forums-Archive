---
title: "Can't get rid of «Default Boot Device Missing» message on boot"
date: 2016-11-30
forum: Installation &amp; Upgrades
---

### Post by November Snow on 2016-11-30
I recently bought an Acer Swift 3 ultrabook preloaded with Windows  10, which I wiped out to install Ubuntu 16.04.1 in single-boot. In my  case installs  are generally a breeze, but not this time. Long story  short, I ended up with a «*No Bootable Device*» message on boot. I fixed the problem with Boot-repair. The ultrabook now works perfectly.

  After the repair, however, I kept getting at boot time a blue window with this message : « *Default Boot Device Missing or Boot failed. Insert recovery media and hit any key* ».  Hitting a key would lead me to a Boot Manager with only one entry : 1-  Windows boot manager. Selecting it would then get me to Grub, with the  usual Ubuntu option.

  I searched the net, found this post, [http://Bootable device not found after clean install of Ubuntu 14.04 UEFI](http://Bootable device not found after clean install of Ubuntu 14.04 UEFI) , modified the BIOS-settings as instructed («*Select an UEFI file as trusted for executing*»   and so on), to no avail. The blue rectangle just won&#8217;t go away at  boot. The only change is that there is now a Ubuntu entry in the Windows  Boot manager.


  Secure Boot is enabled. 
  The boot priority order is :

  1- EFI File Boot 0 : Ubuntu
  2- Windows Boot Manager
3- HDD : HF S256G39TND-N210A

The output of ```
sudo efibootmgr -v
``` can be found here: [http://paste.ubuntu.com/23535154/](http://paste.ubuntu.com/23535154/)

By the way, when I modified the BIOS-Settings in the Security tab, I found three .efi files in **HDDO - EFI - ubuntu**. I selected the first one (as suggested), and left the other two untouched: grubx64.efi and MokManager.efi.
 
I could ot course reinstall Ubuntu from scratch, but since I've  already installed a whole bunch of applications, I&#8217;d rather find a  workaround. Besides, I might end up in the same predicament since I still don't understand what I did wrong!

---

### Post by oldfred on 2016-11-30
It looks like your default UEFI boot entry 0001 is fwupx64.efi which is the grub menu entry to get into UEFI.
If you have secure boot on you want to boot shimx64.efi which is 0002 but shown as unknown device.

I think you need to go back into UEFI and set "trust" and a label on shimx64.efi.
The shimx64.efi file works whether secure boot is on or not. Where grubx64.efi only works if secure boot is off.

All models of Acer seem to use the same setting of "trust" which no other vendor seems to use.
       Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 


I also like to copy shimx64.efi to /EFI/Boot and rename to bootx64.efi. And then enable booting the fallback or hard drive boot entry.
And you can use efibootmgr to remove entries in UEFI or add new ones.
see
man efibootmgr
       
 Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B
Delete Ubuntu or any entry
[http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)

---

### Post by November Snow on 2016-11-30
Thanks, oldfred! I'll give it a try later on when I'm back from work.

---

### Post by November Snow on 2016-12-01
@oldfred
Wow! It worked! I went back into UEFI, as you suggested, and set "trust" on the shimx64.efi file. The blue window has disappeared. The ultrabook now boots directly into GRUB. By the way, is there a way to make the ultrabook boot without this GRUB page appearing?
Thanks again!

---

### Post by November Snow on 2016-12-01
@oldfred
Regarding the GRUB page, I found this info at [https://sites.google.com/site/easylinuxtipsproject/grub#TOC-Adapt-Grub:-change-the-timeout](https://sites.google.com/site/easylinuxtipsproject/grub#TOC-Adapt-Grub:-change-the-timeout)
> **[SIZE=3][B]Adapt Grub: change the timeout**[/SIZE][/B]

 7. In the configuration file [COLOR=#0000ff]/etc/default/grub[/COLOR] you can change the timeout of the Grub menu as you please. Note that setting it to **0** won't have effect: the system will reset it to 10 seconds.... A workaround is setting [COLOR=#0000ff]GRUB_TIMEOUT[/COLOR] to **0.1** because the system does accept one tenth of a second.
Afterwards, run [COLOR=#0000ff]sudo update-grub[/COLOR] in order to load the new setting.

I'd like to have your advice on it.

Thanks!

---

### Post by oldfred on 2016-12-01
I set both my UEFI (which also has a time setting on fast boot) and grub to 3 sec each.
Then if need be I have time to press a key to get into UEFI, or to get into grub.

We get users who cannot boot due to some error and then cannot even get into UEFI to change boot order to boot flash drive to make repairs. Systems are designed just to get into UEFI with fast boot on from Windows (or grub now).
Usually cold boot works, but with laptops may not be easy to do a full cold boot with all power off including battery power, so UEFI system is reset to not use fast boot.

---

### Post by November Snow on 2016-12-02
OK!
Thanks again for your help. Have a nice one.

---

