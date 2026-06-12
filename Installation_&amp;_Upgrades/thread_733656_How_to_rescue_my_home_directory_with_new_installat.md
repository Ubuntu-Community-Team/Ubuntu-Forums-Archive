---
title: "How to rescue my home directory with new installation?"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by sofasurfer on 2008-03-24
I had a WindowsXP/Ubuntu dual boot machine.

I moved my hard drive to a new machine. Now nothing boots. Ubuntu would get to the splash screen and instead of a text box where I enter my username there is only a verticle line which I think is the left hand edge of the text box, which never finished being drawn in. Anyway, this is as far as it goes.

I tried an Ubuntu live CD which also will not boot.

I tried rescue mode which did nothing.

Now I have reinstalled Windows but I still have a non-accessable Ubuntu OS. I will be happy to reinstall it but I want very much to get my configuration notes out of my Home directory. Is there ANY way to do this? It seems to me that when I used to reinstall I would be asked if I wanted to used the existing partitions and whether or not I wanted to format them. I do not see that option now.

I have everything on one partition except for the swap partition.

Any ideas?

---

### Post by Kiri on 2008-03-24
Use a livecd to access the disk and copy the old /home directory to somewhere on your windows partition.

Or you could install fs-driver in windows and access the ext3 disk that your old linux install is on so that you can copy the /home folder that way.

---

### Post by housam on 2008-03-24
Check your Bios to make the cd bootable . then try to restore Grub using [[COLOR="Red"][COLOR="Red"]_this guide _[/COLOR][/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?")
Or dwonload this driver [[COLOR="Red"]_http://www.fs-driver.org/_[/COLOR]]("http://www.fs-driver.org/")to see ubuntu files through windows and try to reach the /home dir. and copy past to ntfs partition ( I assume windows ) .  this may work

---

### Post by sofasurfer on 2008-03-24
Housam.
[http://www.fs-driver.org/](http://www.fs-driver.org/) did it. 

It said that it would access ext2 file system and by following the instructions in the FAQ's I could access ext3 files. 

I just installed it. Looked for the program but it was no where to be found. Then I found that I did not need to even run the program I just looked at my file tree and there were all my linux files., snug as bugs in a rugs.

I've been looking for Linux access from Windows for a long time. THIS IS IT.

Great tool.
Thanks...

---

### Post by sofasurfer on 2008-03-24
I've made a lot of progress with the above issue but I still am having the problem getting Ubuntu to boot. 

As stated above...
Ubuntu will boot up to the splash screen and instead of a text box where I enter my username there is only a verticle line which I think is the left hand edge of the text box, which never finishes being drawn in. Anyway, this is as far as it goes.

What is causing this problem. For lack of any other possible explaination I am wondering if I have a damaged CD which is not doing a perfect install.

What else would cause this? It happened on 3 differant installation attempts. Always the same problem.

Any ideas?

---

### Post by gtdaqua on 2008-03-24
The Ubuntu CD image should be written at low speed (24x or less). Burning the image at 48x or 52x could result in a corrupt image! Installation might hang on and off.

---

### Post by housam on 2008-03-24
> **gtdaqua said:**
> The Ubuntu CD image should be written at low speed (24x or less). Burning the image at 48x or 52x could result in a corrupt image! Installation might hang on and off.

24x is still too high. 2x or 4x is the suitable burning speed.

---

### Post by housam on 2008-03-24
> **sofasurfer said:**
> 

What else would cause this? It happened on 3 differant installation attempts. Always the same problem.


Check the live cd for errors and also make the [[COLOR="Red"]_MD5sum check_[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM").

---

