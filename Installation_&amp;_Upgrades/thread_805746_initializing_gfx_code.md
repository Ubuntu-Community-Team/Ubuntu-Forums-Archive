---
title: "initializing gfx code"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by vanwarantion on 2008-05-24
hello,

I am trying to install 8.04 on a laptop (no brand. only "fd12dt" on a backside sticker)
It prints "initalizing gfx code" on screen and hangs while it tries to boot. It freezes so beeps when i try to use keyboard.
I also  tried to install from different usb sticks that i made a non-persistent install and an external usb cdrom drive but it didn't worked.  And i allready tried 3 different cds and a couple of usb sticks, checked md5hash of the iso image. They all worked on another machines.
I also dont think it is because deficient memory (it has 512 plus 256).
Chipset is: intel mobile 82915GM/GMS/910GML.

Sorry for my poor english. I hope i could be comprehensible.

---

### Post by PmDematagoda on 2008-05-24
Did you try running the Alternate CD by any chance?

---

### Post by vanwarantion on 2008-05-24
I tried with Alternate CD. No change.

[Here]("http://img152.imageshack.us/img152/1338/dsci0024xi0.jpg") is the picture of screen.

---

### Post by litmus on 2008-05-26
I have exactly the same problem. We might have the same laptop, mine's a Philips X51, which is a rebadged Twinhead 12d [http://www.twinhead.com.tw/product_notebook/12D.asp]("http://www.twinhead.com.tw/product_notebook/12D.asp"). Mine's a Centrino (Pentium-M) 1.73ghz, with 1GB RAM, 80GB HDD, 12.1" monitor, Intel GMA, so it couldnt be low memory.

I hope someone can come up with the solution to this, i would love to be able to install hardy on this laptop. Gutsy LiveCD runs without problems. Also, i have found out that most of the new versions of different distros (fedora 9, openSUSE) have the same problem with this laptop. I dont know if this a bug with ISOLINUX, or the kernel. All distros with kernels >2.6.22 dont seem to be able to boot.

---

### Post by vanwarantion on 2008-05-26
It seems the laptops are exactly same.

I installed 7.10 and then upgraded. After upgrade i booted with the previous kernel option on the boot menu and disabled the new one from /boot/grub/menu.lst (i just commented related lines)
For now it works.

---

### Post by thkoukas on 2008-06-17
i have the philips x50 (twinhead 12D) and I have the same problem :(:confused:
what can we do????
nobody knows???

---

### Post by orsomannaro on 2008-06-23
Same NB, same problem.

It seem to be an hw problem: I've upgrade from Dapper to Hardy via Internet, but when I reeboot the system the same problem appear.

---

### Post by nabrown on 2008-07-23
Same problem on Philips freevents X50. Tried upgrading and get a hang on reboot. Tried upgrade with alternative cd and hangs at the gfx message. Only way I got it to work after upgrade was to reselect the old kernel.
I originally used the procedure here [http://www.fitzenreiter.de/averatec/index-e.htm](http://www.fitzenreiter.de/averatec/index-e.htm) to install using their "modified" cd. The upgrade was from this system, am happy at present using this system after the upgrade but with the old kernel.

---

### Post by vanwarantion on 2008-07-23
My solution is:
After upgrading from gutsy, try boot with previous kernel option in boot menu. Better disable new one via editing /boot/grub/menu.lst
Just comment the lines related to new kernel that comes with hardy.

Remember this is not a permanent solution.

I also checked [http://www.fitzenreiter.de/averatec/index-e.htm](http://www.fitzenreiter.de/averatec/index-e.htm) and seems like it solves.

---

### Post by thkoukas on 2008-11-28
hello guys!!!! my philips boots normally ubuntu 8.10 which is installed previously in a flash disk on another pc!!!

---

### Post by AndreaT on 2009-01-21
If you Notebook model is the F12DT, you MUST first upgrade your Firmware to version 1.08.
Download the FW package F12DT_R1.08_Generic.zip from the german web site of Twinhead [http://www.twinhead.de/support.html](http://www.twinhead.de/support.html)
Then download the H12YT_BIOS_R1.08.exe from the taiwan web site of Twinhead [http://www.twinhead.com.tw/down_window.aspx?ID=720](http://www.twinhead.com.tw/down_window.aspx?ID=720)

Then follow these instruction:
1)      Firs of all, you must know that the AFUDOS (ver 4.0) provided within your ZIP was not able to upgrade my F12DT notebook.

2)      So I used an upgraded version 4.07 I found in the H12YT_BIOS_R1.08.exe package downloaded from Taiwan web site.

3)      I was careful to run the new AFUDOS with the BAT file of your original ZIP package.

4)      Then I tried to install the normal official Ubuntu 8.10 desktop CD Rom, but it failed quite at the end.

5)      So I installed a patched version for your H12YT notebook that looks a lot similar to the F12DT. 

6)      Well, the installation of this custom version [http://www.fitzenreiter.de/averatec/ubuntu-8.10-desktop-h12y-v2.iso.torrent](http://www.fitzenreiter.de/averatec/ubuntu-8.10-desktop-h12y-v2.iso.torrent) went perfectly and now I have the Ubuntu 8.10 running on my F12DT

Have I nice day.
Regards
Andrea Tarasconi.


> **nabrown said:**
> Same problem on Philips freevents X50. Tried upgrading and get a hang on reboot. Tried upgrade with alternative cd and hangs at the gfx message. Only way I got it to work after upgrade was to reselect the old kernel.
I originally used the procedure here [http://www.fitzenreiter.de/averatec/index-e.htm](http://www.fitzenreiter.de/averatec/index-e.htm) to install using their "modified" cd. The upgrade was from this system, am happy at present using this system after the upgrade but with the old kernel.

---

### Post by thkoukas on 2009-02-04
> **AndreaT said:**
> If you Notebook model is the F12DT, you MUST first upgrade your Firmware to version 1.08.
Download the FW package F12DT_R1.08_Generic.zip from the german web site of Twinhead [http://www.twinhead.de/support.html](http://www.twinhead.de/support.html)
Then download the H12YT_BIOS_R1.08.exe from the taiwan web site of Twinhead [http://www.twinhead.com.tw/down_window.aspx?ID=720](http://www.twinhead.com.tw/down_window.aspx?ID=720)

Then follow these instruction:
1)      Firs of all, you must know that the AFUDOS (ver 4.0) provided within your ZIP was not able to upgrade my F12DT notebook.

2)      So I used an upgraded version 4.07 I found in the H12YT_BIOS_R1.08.exe package downloaded from Taiwan web site.

3)      I was careful to run the new AFUDOS with the BAT file of your original ZIP package.

4)      Then I tried to install the normal official Ubuntu 8.10 desktop CD Rom, but it failed quite at the end.

5)      So I installed a patched version for your H12YT notebook that looks a lot similar to the F12DT. 

6)      Well, the installation of this custom version [http://www.fitzenreiter.de/averatec/ubuntu-8.10-desktop-h12y-v2.iso.torrent](http://www.fitzenreiter.de/averatec/ubuntu-8.10-desktop-h12y-v2.iso.torrent) went perfectly and now I have the Ubuntu 8.10 running on my F12DT

Have I nice day.
Regards
Andrea Tarasconi.

My friend you saved me!!!! (me and my philips X50!!!) it boots now the live cds!!!!
where did you find it????

I would like to say, that I was searching hours how to do this job and I make a usb flash memory bootable with DOS and ran the command "afudos f12d108.rom"

if you want any help on how to make a flash disk bootable I can help you!!!!

Andrea thank you again!

---

### Post by yagolf on 2010-07-12
Hi there!

Any chance you held on to the H12YT_BIOS_R1.08.exe from the taiwan website? It doesn't provide it any more and I'm going crazy trying to fix the same on my x50

it'd be much appreciated

---

### Post by kahamorf on 2010-09-13
Hi guyz.I have the same NB philips freevents x50 and i'll try for the update.Does anyone have the problem with the battery?I cant use my NB if its not in the power and the battery lcd is opening with orange and green light everytime.Why?Sould i change battery or its motherboard?

---

