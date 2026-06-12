---
title: "Ubuntu 9.10. No 'side by side' option"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by KowalPL on 2010-03-09
Hello. New to the forums so hope you will understand if I dosay something wrong and correct me ;]

Trying to install Ubuntu 9.10 from burned CD. Everything is fine until I get to the part of choosing 'where' is Ubuntu supposed to go. On this machien I am also running Win XP and it has to stay that way. 

My issue is that the installer doesn't offer me 'Install side by side' option. It only does it when I plug in my external hard drive which I am using for totally different thing (storing video/music files), and when it does that, it insists on installing onto it, instead on the actual physical hard drive inside of the machine.

Here is what I get:
[[IMG]http://img121.imageshack.us/img121/8127/screenshot1am.th.png[/IMG]]("http://img121.imageshack.us/i/screenshot1am.png/")
I obviously don't want to wipe clean my main hard drive.

The only other option left is the second one. Here is what I get when I go there:
_[[IMG]http://img411.imageshack.us/img411/1170/screenshot2et.th.png[/IMG]]("http://img411.imageshack.us/i/screenshot2et.png/")_

Anyone knows how to solve it so I can get Ubuntu onto my hard drive inside of the machine? The used 'unknown' drive is an unused space on that drive (deleted old partition using Windows tool).


Hope you know what I mean. If not, please just say so and I will try to make it clearer. Looking forward towards hearing you.

PS: I know barely anything about 'How do things in Ubuntu' work at the moment (although I have used it before, but just to browse the net etc.) so please don't use really high tech Ubuntu language as I will be unlikely to know what to do.



Thanks for all your help ;]

---

### Post by pricetech on 2010-03-09
I can't decipher the images, but that's just my old eyes I'm sure.

Anyway, here's a link to the Community Documentation covering Dual Boot.  If you don't find all your answers there, feel free to ask for more info.  I think you'll find the forums to be a friendly place.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by psusi on 2010-03-09
Looks to me like you already have sda3 and sda4 partitions created for Ubuntu, so install it there.

---

### Post by KowalPL on 2010-03-09
Yeah so I am now at the part of the installation process which starts straight after the boot. I get a black screen for a while (not that short of a while). After some time I get this:

(initramfs)mount: mounting /dev/sda3 on /isodevice failed: Invalid argument
Cannot mount /dev/sda3 on /isodevice


Any ideas?

---

### Post by KowalPL on 2010-03-11
Bump... Really need some help please and considering amount of topics this forum gets bump might be necessary (I couldn't find anything saying bumps are not allowed).

---

### Post by psusi on 2010-03-11
Are you doing a wubi install or something?  Normally there is no part of the install after reboot.  Once the install is complete you reboot and should be running Ubuntu.

---

### Post by presence1960 on 2010-03-11
you already have 4 primary partitions on your internal disk so therefore you can not create another partition. That is why the side by side option is not displayed.

---

### Post by Arand on 2010-03-11
Do you know what is on the sda3 partition?
Is it important? -> Removable?
- Arand

EDIT:

Does it happen to be the case that windows vista/7 is installed on sda3 and you're using a dual-boot windows system at the moment?

---

### Post by KowalPL on 2010-03-11
sda3 is the partition I created using Windows built-in tool. It's a partition of the built in physcial main drive. I created it specifically for Ubuntu. It already has Ubuntu instalation data on it. I get the error mentioned above when 'Ubuntu' is chosen from the boot-up menu at machine start up. It says it will install rest of Ubuntu and after soem time I get that error (what's weird is that I sometiems get it after half a second and sometiems after few minutes).

---

### Post by Arand on 2010-03-11
As a general rule, ubuntu can't be installed to an NTFS/FAT32 partition, which is what I'm assuming windows has created on sda3.

So if the sda3 partition is indeed an "empty" one you intend to install ubuntu to, you'll need to either remove it and let ubuntu handle the partition creation, or use the manual partitioning to reformat it to ext(3/4 depending on preference):

###THIS WILL REMOVE EVERYTHING THAT IS CURRENTLY ON THE sda3 PARTITION!!###
In the second screenshot of yours, select the sda3 partition and click "change". Select "use as ext4" (or ext3 if you have particular preferences, ext4 is the default)
Then edit the mountpoint to read "/" (should be first option in drop-down)
The "format" checkbox should be automatically selected.

From there I think the rest should just work. Just click forward.
 
- Arand

---

### Post by KowalPL on 2010-03-11
Worked! When I tried doing such a thing before it gave me some 'no /root device' or soemthing but it worked the way you told me ;] Thanks a lot!

---

