---
title: "Grub is not installed..."
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by funguygordy on 2011-08-03
I recently secure erased my SSD, and reloaded windows 7.  I also have a large hdd for storage.  I just put ubuntu 10.04 back onto the ssd, but cannot boot into it for some reason.  I booted the live cd again, and ran " ```
 sudo grub 
``` but it says that grub is not installed, to install try apt-get install grub.  When I do this, it says it is unable to fetch some archives.  I did notice that ```
 sudo fdisk -l 
``` showed the previously mentioned storage hdd as a boot point, along with the desired /boot partition under ubuntu.  I have gone through every guide I could find, anyone know why this would be happening?


EDIT:
I finally was able to boot into grub, and then into ubuntu.  However, now when I chose windows 7 from grub I get "DIQWL is missing, press ctrl+alt+del to restart.  A google search returned absolutely nothing on this "DIQWL" problem.

---

### Post by oldfred on 2011-08-03
Do not know if this will show anything or not, as once grub has chainloaded to windows, windows is in charge.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by YesWeCan on 2011-08-03
Is there anything unusual about your Windows 7? Special applications, anything like that?
Grub overwrites about 50 sectors between the MBR and the start of the first partition. Very occasionally, certain Windows apps, usually nefarious, write things in this "no mans land". Just a thought.

---

### Post by funguygordy on 2011-08-07
> **YesWeCan said:**
> Is there anything unusual about your Windows 7? Special applications, anything like that?
Grub overwrites about 50 sectors between the MBR and the start of the first partition. Very occasionally, certain Windows apps, usually nefarious, write things in this "no mans land". Just a thought.

It was a normal install.  I ended up doing yet another secure erase, partition, and install.  I did everything exactly the same as I always have, and it worked.  I have no clue what was up with that error.

---

