---
title: "problem with Alternate CD install"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by confused1 on 2008-02-16
i have tried numerous times with the Live CD to no avail. When I try the Live CD I end up with the, much talked about black screen, with the cursor in the top left portion of the screen and no allowable input.

i have downloaded the alternate CD twice, from different locations within the ubuntu website and burned with nero 6. Both times upon install, I get these same exact problems.

Warning
file:///cdrom/pool/main/x/xkeyboard-config/xkb-data-0.9-4ubuntu3_all

couldn't download zlib1g

No installable kernel was found in the defined apt sources

manually install one later

Select and installsoftware
Installation step failed

An installation step failed: Install the base system

Grub Installation failed

LILO package failed to install to target/

running "/sbin/lilo" failed with area code1

Installl the Lilo boot loader on Harddisk

you will need to boot manually with the Kernel 
on partition /dev/hdb1 and root = /dev/hdb1 passed as kernel argument

I have :
ASUS P3V4X mobo with 800MHz processor
528MB RAM 
32MB Video Card  Diamond Stealth
Memorex 54-24-52 burner
:confused:

---

### Post by zvacet on 2008-02-16
Did you cheked [md5sum](https://help.ubuntu.com/community/HowToMD5SUM) and burn iso image as slower as you can and cheke disc for errors?if some of this things are not right download same iso from torrent and point download to the folder with your existing iso.That way torrent will just chek your iso and if it find corrupted files replace them with good ones.After that burn iso and agagin chek md5sum and after you burn iso on CD chek for errors.If everything is O.K. go for install.

---

### Post by Pumalite on 2008-02-16
Clean your burner's lens, just in case.

---

### Post by confused1 on 2008-02-16
I downloaded winmd5sum and it is showing that the sums are not equal that is, if i'm using it right,
and being a noob.

could you suggest a good site within the US to download from- I figured Georgia Tec. would be ok.

thanks for the help-

---

### Post by Pumalite on 2008-02-16
Download an iso from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below sign 'Start Download'

---

### Post by confused1 on 2008-02-16
yea Pumalite  i never bother'd  to get one of those lens cleaners. I did have 2 failed burns at 2x though so maybe i should pick one up- I thought they were hype.

---

### Post by confused1 on 2008-02-16
that's where Iv'e been getting my downloads from; I've downloaded from:

Rochester Institute of Technology
Columbia University
Michigan
Ga Tec:(

---

### Post by Pumalite on 2008-02-16
Not all your downloads can be bad. Clean the lens or get a new burner.

---

### Post by Herman on 2008-02-16
About ways to md5sum your downloaded .iso files, cleaning optical lenses and other things, [Pre-install Page]("http://www.users.bigpond.net.au/hermanzone/p17.htm") .

I agree with zvacet, using torrent is much better than just downloading files through our web browsers.
I like using the wget command too, [Download very large files with the wget command]("http://users.bigpond.net.au/hermanzone/p5.htm#Download_very_large_files_with_the_wget").

Regards, Herman :)

---

### Post by confused1 on 2008-02-16
hey I appreciate the extra input and info.
I download 3 ISO alternates all from the ubuntu site from different locations and not one of them shows an equal check sum with MD5sum. I also downloaded MD5Summer, but unfortunately all I can get this
thing to do is check its own files.
Anyway, i'm downloading at an average speed of 300KB/s with an average download time of 28 minutes and i'm not having much luck-

Are there any other check sum apps. that are easy to use and can be downloaded from trusted sites-

I remember once upon a time Download Accelerator- along with adware of course-

Thanks again

PS:

I have Ubuntu installed on a newer computer and it works great, but trying to get it installed on this one is turning out to be a pain.

If this keeps up, I will grab the P5WD2 Prem with the 3GHZ  P4 Prescott (hotbox) out of storage 
and turn the airconditioning on.:lolflag:

---

### Post by Pumalite on 2008-02-16
You will have no problems with that one; provided you have a good Nvidia AGP card,

---

