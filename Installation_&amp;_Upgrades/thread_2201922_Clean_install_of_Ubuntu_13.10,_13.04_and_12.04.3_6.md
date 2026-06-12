---
title: "Clean install of Ubuntu 13.10, 13.04 and 12.04.3 64 fails"
date: 2014-01-26
forum: Installation &amp; Upgrades
---

### Post by William_Valentin on 2014-01-26
This is something you really have to look into.  If Ubuntu is to succeed on the desktop a clean installation should be a straight forward process.  I attempted in install each of the above versions on a Lenovo ThinkCentre M71e with an Intel i3 processor and 4 GB of memory. The install seems to work flawlessly but when the final reboot is done you are presented with an error:No bootable disk found or something to that effect 
There is nothing wrong with the hardware as 64 bit versions of Fedora, Mint, and Zorin install and boot flawlessly.  By clean Install I mean erase the hardisk and install the OS so its on you.  Please fix this I know you can because others have.](*,) I have a 32 bit version of Ubuntu 10.04 it clean installs and boots and will upgrade to 12.04.03 no problem but its a 32 bit version running on a 64 bit system.  What gives I wondered. So I downloaded 13.10 32bit to see if I could do a clean install with it and Surprise it installed and booted up.

---

### Post by frank18 on 2014-01-26
> **William_Valentin said:**
> This is something you really have to look into.  If Ubuntu is to succeed on the desktop a clean installation should be a straight forward process.  I attempted in install each of the above versions on a Lenovo ThinkCentre M71e with an Intel i3 processor and 4 GB of memory. The install seems to work flawlessly but when the final reboot is done you are presented with an error:No bootable disk found or something to that effect 
There is nothing wrong with the hardware as 64 bit versions of Fedora, Mint, and Zorin install and boot flawlessly.  By clean Install I mean erase the hardisk and install the OS so its on you.  Please fix this I know you can because others have.](*,) I have a 32 bit version of Ubuntu 10.04 it clean installs and boots and will upgrade to 12.04.03 no problem but its a 32 bit version running on a 64 bit system.  What gives I wondered. So I downloaded 13.10 32bit to see if I could do a clean install with it and Surprise it installed and booted up.

I have same model except it's an i5 and also have installed all those distros in 32bit never tried 64bit, i heard the problem is not the pc but the distro itself in 64bit is unstable!

---

### Post by ajgreeny on 2014-01-27
> **frank18 said:**
> I heard the problem is not the pc but the distro itself in 64bit is unstable!
Where did you hear that?  I suspect it is all heresay and apocryphal stories of people who have had problems of one sort or another, but I do not think there is anything to suggest that 64bit systems are any more unstable than 32bit.

@ William:-
How are you trying to install the system?  Are you using the manual partitioning "Something Else" but not setting a mountpoint for the root partition of /, which if omitted, would give the type of error you've seen.

---

### Post by oldfred on 2014-01-27
When you install the 32 bit version, you are installing in BIOS boot mode. The 64 bit version may be installed in either BIOS or UEFI boot mode.

Now old version.
 [https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS](https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS)

But I have not seen your specific model, but many are posting about buggy UEFI from Lenovo.
      
 Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)

 Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

Another user posted this:

 > Lenovo's  buggy EFI Bios is will not boot from a DVD at all unless you enable 'legacy' (which you can't do because it screws with Windows 8!)
 The work around was to turn ON 'Legacy' boot mode in the BIOS and turn OFF "secure-boot" mode from locking out Ubuntu), and also make sure to turn OFF 'Legacy' SATA AHCI to ATA.
Then I installed Ubuntu from a USB stick (because these settings would only boot the Ubuntu installer from USB, but not DVD). 

 Another lenovo solution copy grubx64.efi to bootx64.efi & boot hard drive not anyother entry
[http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470](http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470)

---

### Post by frank18 on 2014-01-27
[QUOTE=ajgreeny;12911886]Where did you hear that?  I suspect it is all heresay and apocryphal stories of people who have had problems of one sort or another, but I do not think there is anything to suggest that 64bit systems are any more unstable than 32bit.



thanks ajgreeny;for your reply to my post, well you maybe right and pull for it to be true! as i said i never tryed it but i would like to, maybe when 1410lts is out in April and will let you know how  my Lenovo Thinkcenter M71e Intel core (TM) I5 2400CPU 3.1ghz ram 3.8gb with ATI video card HD6450 will handles it.


by the way what do we gain with version 64bit over 32bit ?i  mostley use my pc to stream live sports events?

---

### Post by oldfred on 2014-01-27
Even on low memory systems, 64 bit may be faster.
 32-bit vs. 64-bit Ubuntu 13.04 Linux Performance with only 1GB of RAM & most tests better with 64bit Mac Mini
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1)

 Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)


Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

With PAE you can address more memory, but only in chunks, or it has to swap in and out memory to use it. With 64 bit you directly address that memory.

---

### Post by frank18 on 2014-01-28
Hi guys today i took a chance and installed Ubuntu 1404  Trusty Tahr 64bit and must say so far so good, it was a little tricky cause of the Ati amd fglrx drivers.

---

### Post by frank18 on 2014-01-28
> **frank18 said:**
> Hi guys today i took a chance and installed Ubuntu 1404  Trusty Tahr 64bit and must say so far so good, it was a little tricky cause of the Ati amd fglrx drivers.

In april there will be a LTS edition! will i be able to upgrade or i have to install from scratch?

---

