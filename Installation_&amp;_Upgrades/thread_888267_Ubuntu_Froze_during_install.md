---
title: "Ubuntu Froze during install"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by lazulilasher on 2008-08-12
Hi

First, I am completely new to the Linux thing and pretty much to installing Operating Systems in general....and I did something very wrong.

So, I downloaded Ubuntu and burnt the CD image. Then I went ahead and installed. And the installation froze 1/2 way through (and keeps freezing at 45% of copying files). The CD-ROM drive just stops. So, I tested for errors on the CD and there was 1 error. I imagine that this is most likely the problem. 

Now, I'm stuck with the LiveCD version of Ubuntu (and it's very nice, by the way! Sleek, good color scheme, etc) and I can't boot into any operating system except the LiveCDversion. Thus, I can't download and burn another copy of Ubuntu.

Is there anything that I can do? Or am I just going to have to live with the nice LiveCD version?

Thanks, and yes, I know I should have checked the CD before installing....

Lazulilasher

---

### Post by Partyboi2 on 2008-08-13
> Is there anything that I can do? Or am I just going to have to live with the nice LiveCD version?
You can boot the live cd and download ubuntu, remembering to check the [[COLOR=Blue]md5sum [/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")Then copy the iso over to a usb stick and take it to another PC (family, friends, internet cafe) that can burn the iso to cd.
Or
You can order a free copy of ubuntu from [[COLOR=Blue]shipit[/COLOR]]("https://shipit.ubuntu.com/") this will take up to 6 weeks to be delivered.
Or
Maybe see if you can  install ubuntu using a usb stick. See [[COLOR=Blue]here[/COLOR]]("http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html")

---

### Post by SkonesMickLoud on 2008-08-13
When you reburn the .iso (as it sounds like you're going to have to do) make sure you check the MD5sum and burn at 4x or less.

---

### Post by lazulilasher on 2008-08-13
Right. One of the things I was going to try and do, as well, was download the .iso to a new partition I created in Gparted and boot from that.

However, when I create a partition in Gparted and I can't write to it. Actually, last night I read another post where someone found out how to write to the petition, it was some "sudo" command. Just one line and then they were able to write to the partition. I tried their instructions and it worked well.

Problem was I hadn't made the partition large enough. So, now I have the same problem again:

How can I enable write access on a new partition I created in Gparted?

Thanks ;)

---

### Post by lazulilasher on 2008-08-13
Oh. Just figured out how to access the new partition. I used nautilus.

This is kind of neat that I'm learning a bit about Linux during my travails of installation. 

Now, I'm just keeping fingers crossed I'll be able to boot from that partition.

---

