---
title: "Video card problem i believe."
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by BewilderedStranger on 2010-02-14
Howdy folks,
I have been thinking that I wanted to try out ubuntu__[]("http://www.linuxnewbieguide.org/content/video-card-driver-problemi-think#") for quite some time now. Well I finally initiated the first steps of the operation and have run into a problem before even getting a glimpse of the desktop[]("http://www.linuxnewbieguide.org/content/video-card-driver-problemi-think#"). Haha typical. I donloaded the iso and burned it and started looking at partitioning everything and I have a question about that as well but I'll get to that in a moment. I decided before I went through all the hassle of installing it and partitioning drives I'd check it out on the live cd. So I restart and boot from the cd and it works up to the black loading screen with the little symbol in the middle then my monitor switches to blue and gives me the no signal message. It never returns. I would assume my video card is not supported or something along those lines. Also I am currently running vista x64 and when I go to shrink my partition I notice that if I shrink my partition it doesn't get very small at all. I think this may be because I have all kinds of media files and things like that on the partition with windows. When I do set this all up I wanna be able to access all of my files from either os. The best option I could think of was to create a new partition and shift everything to it that was important then reload vista Which doesn't sound fun because it is a very messy and buggy oem copy. Anyhow What do you all think are my best options? Or where can I turn for support on such a matter?  I sure would like to kick windows to the curb.

 System Specs:
I7 920
X58 chipset
9gb  Ram 1066 mhz
Visiontek ATI Radeon HD4850

---

### Post by Mark Phelps on 2010-02-14
First of all, you should know that if you do attempt to reinstall Vista, it's likely to fail activation because, once the product key is used, that is recorded by MS and it won't let you activate it again -- without contacting MS directly.

So, you would be better off NOT trying to reinstall Vista.

In terms of shrinking the Vista OS, there are some tips at the link below that might help:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

But, unless you definitely do NOT want to use Vista anymore, do not use the Ubuntu installer to shrink the Vista OS.

And, you are correct in wanting to have an extra data partition for sharing files.  Be sure to set it up as NTFS because MS Windows (surprise!!) is not able to recognize Ext4 partitions.

---

### Post by BewilderedStranger on 2010-02-14
Yeah vista actually is keyed to your mobo so as long as you dont swap it you can reinstall as many times as you want.  I'm up to 4 or 5 now haha.  but the main issue is the driver thing.  I can't figure out how to install ubuntu if i cant even run it off of the live cd.  Seems like my video card isn't supported.  It starts loading after i select the try without making changes then goes blank.  Monitor says no signal.  how do i get the necessary drivers if i can't boot even from the live cd? also will linux read ntfs?        thank you by the way mark.

---

