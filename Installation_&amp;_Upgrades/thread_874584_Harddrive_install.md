---
title: "Harddrive install"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by rules on 2008-07-30
Hi all

I have been trying to get my laptop too tripple boot, but for some reason or another my cd/dvd drive seems to be "fussy" with some cds.

So far (actually always :) ) I have XP going on the first partition and Suse 9.1 on the last partition. For some reason those are the only OS cds I can get to work. My newer Suse and Ubuntu cds just don't want to play with. I have tried burning new cds but still nothing.

The plan now is to install direct from the harddrive. Only problem is I have no clue how to accomplish this. I have read a few posts, but apparently I'm not smart enough to understand what it is that I need to do :)

Is there anyone that can guide me through this, step by step?

Thanks.

---

### Post by Partyboi2 on 2008-07-30
Another option you could try is [[COLOR=Blue]unetbootin[/COLOR]]("http://lubi.sourceforge.net/unetbootin.html") It will grab the files you need from the net as you install, so you will not need to access the cdrom

---

### Post by rules on 2008-07-30
Thanks, great app. I have 2 problems though.

For some reason my laptop can't boot from usb and I dare not install Ubuntu over the net (have a capped dsl connection).

Is there no way to get it to run/install of the hdd?

Thanks.

---

### Post by Partyboi2 on 2008-07-30
download the linux version of unetbootin and install it. Then at the main menu screen choose "Diskimage" and use the path to hardy 8.04.1-desktop iso, If you use the alternate cd iso you will find that at the early stages of the install it will ask for the cd rom, which you don't have, so stick with the desktop version. Once you have selected the path, down the bottom where it says "type" select "Hard disk" then press "ok" it will "extract and copy files and install a boot loader, then it will ask you to reboot. When you have rebooted choose unetbootin from the list and proceed to install ubuntu.

---

### Post by rules on 2008-07-31
Thanks a million, finally figured it out. I had to use the windows version as the linux one did not want to work (when clicking on it, nothing happened). I had to use my c drive as the imaginary cd (it didn't give me the option to use any other drive), rebooted and installed Ubuntu. 

The only problem is/was, Grub loaded the wrong settings for windows, but this I could just fix from Ubuntu, it did unfortunately mess up some of the windows boot files (boot.ini) so now I just need to figure out how to fix that.

Thanks again.

---

