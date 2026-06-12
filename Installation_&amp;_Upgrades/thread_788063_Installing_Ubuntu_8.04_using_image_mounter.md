---
title: "Installing Ubuntu 8.04 using image mounter"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by RyuHendrabusa on 2008-05-09
Hello all!

This is my first post here and I was wondering if it is possible to install Ubuntu using WUBI (install alongside WinXP) through an image mounter like Power ISO or Alcohol 120%. 

I tried this a few times but after I rebooted my machine and logged on to Ubuntu from the OS selection screen, a progress bar tells me it is installing the system and at halfway, it fails.

Few weeks ago, I dropped my laptop and the CD drive is not working properly, so I can't use the LiveCD to install Ubuntu.

Thanks for your help!:)

---

### Post by MusicMastaMike on 2008-05-09
Apparently you should be able to install by mounting the .iso.  Check this out:
[http://www.thetechjuice.com/2008/03/install-ubuntu-hardy-heron-with-wubi.html](http://www.thetechjuice.com/2008/03/install-ubuntu-hardy-heron-with-wubi.html)

---

### Post by RyuHendrabusa on 2008-05-09
Thanks for confirming!

The thing is, although it tells me that the installation has failed, Ubuntu loads up after the error message and I can use it. However, the top panel tells me I am running as a Live session user and I don't know what this means. Does it mean that the system thinks I am running from LiveCD?

Here's a screenshot of the installation error that I've got.

[IMG]http://images.ryuhendrabusa.multiply.com/image/2/photos/51/500x500/1/DSC00269.JPG?et=pMaR937v6Sc5S%2CnBdplu4w&nmid=95246430[/IMG]

---

### Post by MusicMastaMike on 2008-05-09
Yes, that means it's running as a LiveCD.  When you boot up Ubuntu, is there an "Install" icon on the Desktop?  If so, I would try that.  I haven't used wubi personally, but I'm guessing that maybe it installs some essential files to the hard drive, or copies over the iso in order to let you install from the hard drive.

---

### Post by RyuHendrabusa on 2008-05-09
Yeah, there is the install icon there. I'll give that a shot!
Thanks:)

---

### Post by MusicMastaMike on 2008-05-09
Awesome, let me know how it goes!

---

### Post by RyuHendrabusa on 2008-05-10
After the installation failed, I ran as Live session user from the ISO file. I tried running the install icon as suggested above but it wouldn't let me install because there are already files in C:/ubuntu/disks/boot

I tried this over 5 times, I think. (LOL)
It just won't install successfully.

Help! :)

---

### Post by MusicMastaMike on 2008-05-10
I would try one of the methods listed on this page if I were you:
[https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd](https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd)

Best of luck!

---

### Post by RyuHendrabusa on 2008-05-11
Thanks!:)

Hmm, I tried using Unetbootin. Everything seems smooth until I reached the partitioning part. I selected the first option which allows me to keep my WinXP and installs Ubuntu on the other partition. 

The partitioning process failed, it tells me that the hard drive hasn't been modified and when I boot into WinXP, my C: drive icon is missing, replaced by the standard 'unknown file' icon. Thankfully, my C: drive is still accessible from 'My Computer'.

Anyone has any suggestions? I really want Ubuntu on my laptop~
The installation through Wubi was very successful on my desktop computer though.

---

### Post by RyuHendrabusa on 2008-05-16
I finally got Heron installed on my laptop!
The previous times failed because the ISO was faulty and I didn't do MD5SUM on them. :lolflag: (Mark of a noobie)

Anyway, thanks a lot for your help ,MusicMastaMike!

Cheers~:)

---

### Post by producer on 2008-05-16
I'm trying to find the md5 checksum on this .iso, but I can't find it on the site.  Where did they put it please?

---

### Post by zvacet on 2008-05-16
[Here]("http://hr.releases.ubuntu.com/hardy/MD5SUMS")

---

### Post by producer on 2008-05-16
Thanks.  Much appreciated,  Where are they kept, (so I don't have to bother you next update).

---

### Post by zvacet on 2008-05-16
When you choose where you want to download from you will see MDSUMS.Basicly you can find them on every download page(mirror).

---

### Post by producer on 2008-05-16
Ah.  I saw it there but didn't write it down.  It was a few days before I was ready to burn the disc.  Then I didn't go back to the download page because I didn't want to start another download and I thought it would.  Anyway they do match and the disc is burned.  All is well in this project.  Thanks again.

---

