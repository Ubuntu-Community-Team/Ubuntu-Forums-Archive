---
title: "SD Partitions and Performance"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by a_posse_ad_esse on 2010-09-19
Hello all.  I'm doing a fresh install on my netbook and have purchased an 8GB SD card to expand storage space.  I'm curious as to which directories can be mounted on the SD card without affecting performance as the write times and such are much lower on the card.

I know that /home and /tmp can be mounted there.  Any other suggestions?  Thanks

---

### Post by sikander3786 on 2010-09-19
I think it will be better to have all your personal data on the SD Card i., make it a storage drive without tinkering with the mount points and the install itself. Still if you want to, mount /home to the SD card.

---

### Post by a_posse_ad_esse on 2010-09-19
Thank you for your reply.  I would have liked to just have everything on the card (it is 8GB and the SDD in the machine is only 4GB), but the performance decrease is really unacceptable.

My thinking is that write times won't affect (much) the /home directory as you say because it is only files that are being accessed rather than program libraries, etc.  /tmp would also work because it is just temporary storage that needn't be accessed all that much.  I'm just at a loss if a third partition (the maximum number per drive) can be put on there that doesn't have a lot of read/write activity to ease some of the congestion on the main SDD.

---

### Post by sikander3786 on 2010-09-19
You can definitely have /home and /tmp on the new SD card. It wouldn't slow down the whole install to a great extent. You can really try it and decide yourself. I haven't had such type of experience so am unable to say anything about slow downs. Might be some one experienced steps in.

---

### Post by maestrobwh1 on 2010-09-19
Or you could recover a heap of space on the SSD:

Keep in mind that both of these have some "risk" involved: because if you don't follow the directions completely, you will lose /usr

[http://po-ru.com/diary/linux-liposuction-or-xubuntu-in-under-a-gig-on-the-eee-pc/](http://po-ru.com/diary/linux-liposuction-or-xubuntu-in-under-a-gig-on-the-eee-pc/)

and

[http://wiki.archlinux.org/index.php/Maximizing_performance#Compressing_.2Fusr](http://wiki.archlinux.org/index.php/Maximizing_performance#Compressing_.2Fusr)

The latter is for arch linux.  I am not sure if aufs is enabled in the default/generic kernel... if it is, it is the way to go.  Last I knew, union is enabled in the standard Ubuntu kernels.

1.  You will recover about a Gig (yes, a Gig) of space on your SSD (only issue is that you might need to make the first squashfs on another device, boot using a usb or cdrom distro and move it to the HD after removing /usr.  It needs probably about a Gig of space to make the usr.sqfs directly on the HD.  If you have that much space, you do have a bit of a safety net because if it doesn't work out, you could boot back into another OS and undo the changes.  Once you blow away /usr, it would be trickier to fix things if anything goes wrong.

2. Running /usr compressed runs much faster.  There are reasons for this, and someone else with the theory could explain better as to why.

I actually have a Debian based OS (soon to be called Aurora, currently called EEEBuntu), running off of an SD card using this method on my EEEPC 701 (sounds like you have the same machine).  It is slower than running off the internal SSD but faster than running a non compressed install to an SD card.  I used to have Kubuntu installed this way on the SSD.

Then again, you might want to check out EEEBuntu: EB4 is the Beta release of Aurora.  It has some features that are enhanced on your EEE.  You could also install it to the SD card (remember to make it install the boot loader to the SD rather then the SSD when you get to that step).  The only issue there is that neither union or aufs is available in the kernel by default, but it will be when released as Aurora.  One of the devs there had me test a celeron kernel, and built aufs into it as per my request.  If you have an interest, mail me @ [email]maestro_bwh@yahoo.com[/email] and I can send you the link for that particular kernel.

EB4/Aurora allows for some MAJOR power saving on battery with the EEE series, and if you have the 701, it creates a virtual resolution of 800x600 for this particular machine along with native 800x480.  Nice when you have programs that force half the window off of the 480 screen.

[http://www.auroraos.org/](http://www.auroraos.org/)

Remember to do a full upgrade before compressing:-)

---

### Post by a_posse_ad_esse on 2010-09-19
I do have an Eee 701.

Thanks for the replies, I'll see what I can come up with.

---

