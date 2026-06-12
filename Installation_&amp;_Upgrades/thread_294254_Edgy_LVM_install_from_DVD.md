---
title: "Edgy LVM install from DVD"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by Naan Yaar on 2006-11-06
I am a recent convert from Gentoo who has been trying to install Edgy from the i386 DVD iso on a HP Pavilion box. I have been using Linux since about '95, starting out with RedHat and then moving on to Gentoo in '02; the main motivation for the switch to Ubuntu is due to the fact that I do not have a lot of time these days to deal with long compiles and potential breakages that can come with a Gentoo update.

I would like to use LVM for / and /home as I had on my Gentoo box previously. I searched through the forums to check whether this is going to be possible in a DVD install but wasn't entirely clear after going through the posts.

Since there is no option to do create the LVMs from the GUI installer, I am assuming that I will do it in the console from the LiveDVD before proceeding with the GUI install. Is this going to work and are there any gotchas that I need to be aware of? Any pointers will be greatly appreciated.

---

### Post by Naan Yaar on 2006-11-07
Anyone?

---

### Post by Naan Yaar on 2006-11-11
The command-line install from the DVD worked beautifully even though the GUI does not allow you to deal with LVMs. One minor wrinkle was that I created the logical volumes in the LiveDVD GUI mode after apt-getting lvm2 and modprobe-ing dm-mod (I had done this before finding that the GUI installer will not install to LVM partitions even if I create them "by hand".) I guess the CLI installer will allow me to create the physical and logical volumes, but I didn't get a chance to do this since I only needed to create the file systems on the pre-existing logical volumes.

I am extremely happy with the speed and "lack of pain" in the install. I am also impressed with how coherent the whole system feels.

---

