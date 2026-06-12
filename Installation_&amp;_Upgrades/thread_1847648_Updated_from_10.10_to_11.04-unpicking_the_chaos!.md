---
title: "Updated from 10.10 to 11.04-unpicking the chaos!"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by sean lyon on 2011-09-21
OK acer aspire 5332 ran perfectly on 10.10

updated to 11.04 using update manager-wantd newer firefox and the office package looked better

had screen backlight issues-reported as a bug now. 

However- and its a BIG HOWEVER! during the initial " it boots and runs but its lost the screen" panick that ensued i had tried to boot from a live cd of 11.04 stabbing about in the dark quite literally, it seems as the disk had started to install when i had used the power button and [return] to get out.
files and folders are all there-well my user files etc the boot sector is not as it should be and i dont want to do any more damage by trying another install 

 booting from a live cd of 10.04 has the laptop running lovely i can access all my original files and folders by mounting the HD through disk utility but its not a long term proposition

so good people what do i do now?
main problem is that starting the laptop initiates grubb, any option of installing any of the choices on the HD end up ultimately in:- 
"mounting /sys    /root/sys failed no file or folder"
"mounting /proc   /root/proc failed no etc..."

looking about in the root of the HD there seems to be two root folders - mount point according to disk utility has mount point as being " /media/.ba0r4b29..........." this folder contains the following folders:-

boot, cdrom, home, lost&found, media, mnt, opt, root, selinux, srv, tmp ubiquty-apt-clone, usp, var

media folder in this case is empty.

if you go up the tree from "media /ba0r4b29...... "you go to filesystem which contains bin, boot, cdrom, dev, etc, home, lib, media, mnt, opt, proc, rofs, root, sbin, selinux, srv, sys, tmp. vsr  and 2 dead links "intr.img" and "vmlinuz"

Im guessing that the ba0r4b29...... is the original mount point and has some of its files erased by the aborted install and that "file system"  that contains all the same files and some extras are the loaded files from the cd in another partition?
file browser shows them in the side pain as two differing HDs

so what do i do to get the laptop to boot from HD again? bearing in mind i like things simple ie sit down hit power button - up comes "My computer"-simple is good its why i came over to Ubuntu in the first place. dont want to go through endless options.

then if that works how do i go back to the older kernel that worked with 10.10 in fact how do i go back to 10.10  if thats possible -oh why did  ever leve you Meerkat!  ;)
Thanks
Sean

*EDIT*
Having just read Mörgæs sticky at the top of this page i must hang my head in shame having not looked into it or done any of his excellent advice just jumped in trusting Ubuntu to work flawlessly,,,,as usual.

---

### Post by mörgæs on 2011-09-22
Thanks. Good to know that it helped.

---

### Post by sean lyon on 2011-09-27
Fixed!
booted with CD of 10.4 mounted the old partition
backed home folder to a USB and clean re install of 10.10 all is well again and I'm a bit wiser

---

### Post by mörgæs on 2011-09-27
Good, please mark the thread 'solved' using 'thread tools'.

---

