---
title: "I thing fdisk would be more appropriate ATM"
date: 2009-12-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by caryb on 2009-12-21
apt-get dist-upgrade
The following packages will be REMOVED:
  acpi-support acpid alsa-base alsa-utils anacron apparmor apparmor-utils apport apport-kde at avahi-daemon brltty clamav clamav-base clamav-freshclam console-setup cron
  devicekit-disks dmsetup friendly-recovery fuse-utils googleearth hal ifupdown initramfs-tools kbd kdm klamav knm-runtime lib32nss-mdns libnss-mdns linux-generic
  linux-image-2.6.31-14-generic linux-image-2.6.32-4-generic linux-image-2.6.32-5-generic linux-image-2.6.32-6-generic linux-image-2.6.32-7-generic linux-image-2.6.32-8-generic
  linux-image-2.6.32-9-generic linux-image-generic logrotate network-manager ntfs-3g ntfs-config ntfsprogs pcmciautils plasma-widget-network-manager
  plasma-widget-networkmanagement plasma-widget-networkmanagement-dbg plymouth pm-utils rsyslog sreadahead telepathy-salut ubuntu-minimal ubuntu-standard udev ufw ureadahead
  usb-creator-common usb-creator-kde wine1.2 wireless-crda xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-i128 xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nv xserver-xorg-video-openchrome xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vmware xserver-xorg-video-voodoo
The following NEW packages will be installed:
  libpolkit-qt-1-0
The following packages will be upgraded:
  initramfs-tools-bin kde-l10n-engb kdelibs-bin kdelibs5 kdelibs5-data libatk1.0-0 libatk1.0-data libattica0 libplasma3
9 upgraded, 1 newly installed, 101 to remove and 0 not upgraded.
Need to get 13.8MB of archives.
After this operation, 1,042MB disk space will be freed.
Do you want to continue [Y/n]?

---

### Post by autocrosser on 2009-12-21
NUKE IT:P:P:P

:lolflag:

---

### Post by caryb on 2009-12-21
Nope!

---

### Post by autocrosser on 2009-12-21
Ya--I've been getting that for the last couple of hours---I've got initramfs-tools & initramfs-tools-bin held back right now......:)

---

### Post by ranch hand on 2009-12-22
You don't need all those "images" any way.  Just run it.

Reinstalling is so much fun.

I have one install that usually gets the dist-upgrade just to see what happens.  I, for some reason, let this one pass me by.

Impressive list.  Just chaff that needs swept out.

---

### Post by VMC on 2009-12-22
> **caryb said:**
> apt-get dist-upgrade
The following packages will be REMOVED:
  ...
After this operation, 1,042MB disk space will be freed.
Do you want to continue [Y/n]?

There's one plus here. You get back over a gig of disk space :)

---

### Post by ranch hand on 2009-12-22
> **VMC said:**
> There's one plus here. You get back over a gig of disk space :)
+1

It might have some "small" effect on your boot time though.  I think that is why I didn't run it on my "throw" away OS.

---

### Post by caryb on 2009-12-22
We are a bunch of weak sissies :lolflag:


Cary

---

### Post by autocrosser on 2009-12-22
Got to admit that life is never boring.........

---

### Post by wilee-nilee on 2009-12-22
The missing packages have been added.

---

### Post by Gina on 2009-12-22
> **ranch hand said:**
> Reinstalling is so much fun.Oh yes, it comes as second nature now :lolflag:

---

### Post by phillw on 2009-12-22
> **Gina said:**
> Oh yes, it comes as second nature now :lolflag:
That reminded me... a few days since i rsync'd my 10.04 /home over to its backup :-)

I guess i should grab a current alpha1 image ... I still have the rc of the alpha as my only 'fall-back' to re-install with - But, I know it works :popcorn:

Phill.

---

### Post by Gina on 2009-12-22
> **phillw said:**
> That reminded me... a few days since i rsync'd my 10.04 /home over to its backup :-)

I guess i should grab a current alpha1 image ... I still have the rc of the alpha as my only 'fall-back' to re-install with - But, I know it works :popcorn:

Phill.I forgot to keep a backup of the last daily ISO that worked on my AMD64 :(  I do have Lucid working on my P4 though.  It's unlike me not to keep a backup of everything :redface:

---

### Post by phillw on 2009-12-22
> **Gina said:**
> I forgot to keep a backup of the last daily ISO that worked on my AMD64 :(  I do have Lucid working on my P4 though.  It's unlike me not to keep a backup of everything :redface:

One of these days ... not sure which one .... I'll get around to tidying up my Grub2 menu ... I have all the 9.10 kernels on there, most of the recent 9.04 ones along with whatever 10.04 ones that have been issued -- oh, and my Vista area hiding at the bottom ;-)

More 'kernels' than a coconut farmer :lolflag:

I'll go 'make usb boot' now onto my 2GB usb stick, while the going is good :-)

Phill.

---

### Post by ranch hand on 2009-12-22
> **phillw said:**
> One of these days ... not sure which one .... I'll get around to tidying up my Grub2 menu ... I have all the 9.10 kernels on there, most of the recent 9.04 ones along with whatever 10.04 ones that have been issued -- oh, and my Vista area hiding at the bottom ;-)

More 'kernels' than a coconut farmer :lolflag:

I'll go 'make usb boot' now onto my 2GB usb stick, while the going is good :-)

Phill.
Now see, if you would just create a 06_custom file, using 40_custom as a template, and entries like this;
[/code]
echo "Adding Lounge on sda7" >&2 
cat << EOF
menuentry "Lounge on sda7" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
EOF
[/code]
They would never need updated as they boot to the newest kernel on the defined partition.

They will also be on the top of your menu.

I disable the grub.d files above 10_linux (remove permission to be executable).  I like to have it for some reason, don't need it either.  I ca nboot to recovery by hitting "e" and removing the "quite splash" and replacing it with single.

---

### Post by phillw on 2009-12-22
> **ranch hand said:**
> Now see, if you would just create a 06_custom file, using 40_custom as a template, and entries like this;
[/code]
echo "Adding Lounge on sda7" >&2 
cat << EOF
menuentry "Lounge on sda7" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
EOF
[/code]
They would never need updated as they boot to the newest kernel on the defined partition.

They will also be on the top of your menu.

I disable the grub.d files above 10_linux (remove permission to be executable).  I like to have it for some reason, don't need it either.  I ca nboot to recovery by hitting "e" and removing the "quite splash" and replacing it with single.

Thanks, I have read drs305's stuff on Grub2, so do know how to tidy it all up, and the removal of the executable bit is by far the easiest one, untill I get around to a full un-install of the kernels in synaptic - I'm just toooo busy playing with other stuff to get around to it.:lolflag:

[http://flurdy.com/docs/postfix/#intro](http://flurdy.com/docs/postfix/#intro)  is next - but as he's prepping instructions for 10.04 & canonicals cloud images, I'm just installing 9.10 variant to see if I can break it :)

Phill.

---

### Post by Gina on 2009-12-22
> **ranch hand said:**
> Now see, if you would just create a 06_custom file, using 40_custom as a template, and entries like this;
[/code]
echo "Adding Lounge on sda7" >&2 
cat << EOF
menuentry "Lounge on sda7" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
EOF
[/code]
They would never need updated as they boot to the newest kernel on the defined partition.

They will also be on the top of your menu.

I disable the grub.d files above 10_linux (remove permission to be executable).  I like to have it for some reason, don't need it either.  I ca nboot to recovery by hitting "e" and removing the "quite splash" and replacing it with single.That's a useful idea :):)  Thank you - I'll  save that :)

---

### Post by ranch hand on 2009-12-22
The link in my sig should get you going on that.

That post includes a lot of links to good grub2 info.  From folks actually using it and experimenting on it.
drs305's main How To is the second link.  Herman's real good stuff is first for no real reason.  They are the best two sources of in depth info.

---

### Post by Gina on 2009-12-23
> **ranch hand said:**
> The link in my sig should get you going on that.

That post includes a lot of links to good grub2 info.  From folks actually using it and experimenting on it.
drs305's main How To is the second link.  Herman's real good stuff is first for no real reason.  They are the best two sources of in depth info.Yes I did follow your links a little while ago and remember reading that method but couldn't remember where I'd seen it.  Anyway, I have it now, saved on my NAS drive in my Ubuntu Info folder :)

---

### Post by ranch hand on 2009-12-23
> **Gina said:**
> Yes I did follow your links a little while ago and remember reading that method but couldn't remember where I'd seen it.  Anyway, I have it now, saved on my NAS drive in my Ubuntu Info folder :)
I take it that, like me, you have way too much information stored to ever get through.

I have trouble just keeping up with what I have to do.  Sometimes education just has to wait.

---

### Post by Jordanwb on 2009-12-23
> **caryb said:**
> After this operation, 1,042MB disk space will be freed.

Just save the time and "rm -rf /" (but seriously don't do that)

---

### Post by phillw on 2009-12-23
> **ranch hand said:**
> I take it that, like me, you have way too much information stored to ever get through.

I have trouble just keeping up with what I have to do.  Sometimes education just has to wait.

You and me both !! I have a sub-section containing "How-To's" - It's maddening when a problem dies down in occurrences and you forget the link to the solution :-(

drs305 is also the author of [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)  Which was ammended after I ::cough:: used it and messed up ;-)

[http://www.vpolink.com/blog.php?b=2](http://www.vpolink.com/blog.php?b=2)  has my blog on it - can't recall the thread on here for it. For people asking what can go wrong when you update to grub2, I send them to my blog :-D

Phill.

---

### Post by VMC on 2009-12-23
> **phillw said:**
> You and me both !! I have a sub-section containing "How-To's" - It's maddening when a problem dies down in occurrences and you forget the link to the solution :-(

drs305 is also the author of [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)  Which was ammended after I ::cough:: used it and messed up ;-)

[http://www.vpolink.com/blog.php?b=2](http://www.vpolink.com/blog.php?b=2)  has my blog on it - can't recall the thread on here for it. For people asking what can go wrong when you update to grub2, I send them to my blog :-D

Phill.

Oh god. I must be a charter member of this club. The last few posts reminded me of myself. I find a interesting link. Try to remember to go back or forget to bookmark it, or it I do bookmark it, I fail to save it externally, and re-format that partition.

I have been keeping up mostly using TomBoy notes. But it has issues regarding backkups.

---

### Post by phillw on 2009-12-23
> **VMC said:**
> Oh god. I must be a charter member of this club. The last few posts reminded me of myself. I find a interesting link. Try to remember to go back or forget to bookmark it, or it I do bookmark it, I fail to save it externally, and re-format that partition.

I have been keeping up mostly using TomBoy notes. But it has issues regarding backkups.

make a partition called  /temp-home  Then, when you're ready to nuke an install mount /temp-home on /media/

```
 sudo rsync -aS /home/. /media/temp-home/. 
```And swap target & destination round to get it back.

Not sure what others do - but it works for me as 10.04 is not allowed access to my /home partition.
I just rsync'd by /home partition onto my 10.04 installation when I 1st made it, which brought over all my bookmarks, passwords etc (kewl for pidgin :-) )

/edit - of course - you could do the same with a usb stick !!

Phill.

---

### Post by VMC on 2009-12-23
Actually I do have it but readily available like when you rsync. I use partclone.ext4 and clone my partition. I find it much faster to restore whole partitions, but harder to access unless I actually re-image it.

But what I was referring to was my memory and not the process.

For years I used Acronis True Image and it was great to access individual files, and extremely fast on both clone and re-image. Not any more. They don't support newer Linux FS's.

---

### Post by caryb on 2009-12-23
That will learn me to check the spelling of my topic :lolflag: I thought this post would get 1 reply then die a natural death:rolleyes:


Cary

---

### Post by phillw on 2009-12-23
> **caryb said:**
> That will learn me to check the spelling of my topic :lolflag: I thought this post would get 1 reply then die a natural death:rolleyes:


Cary


 Maybe it should be put as development request .... ```
sudo fdisk -y /human/old_brain_cells
```So, we're *nearly* on topic 

:lolflag:

---

### Post by phillw on 2009-12-23
> **VMC said:**
> Actually I do have it but readily available like when you rsync. I use partclone.ext4 and clone my partition. I find it much faster to restore whole partitions, but harder to access unless I actually re-image it.

But what I was referring to was my memory and not the process.

For years I used Acronis True Image and it was great to access individual files, and extremely fast on both clone and re-image. Not any more. They don't support newer Linux FS's.

For my ~home I do use rsync, for full system backups i use tar. It was good then, and can't be beaten - File systems come .... file systems go .... tar just keeps on working.

Remember, brain cells come, brain cells go --- fat cells live forever :popcorn:

Next time any of you good people have a bit of time to spare, could you have a read of [http://www.vpolink.com/showthread.php?t=170](http://www.vpolink.com/showthread.php?t=170)  I'm trying to get it so newcomers who want to 'roll up their sleeves' can do a good backup and learn a bit more about how their partitioning etc "lives" on their computers.

Any constructive criticism is welcome. I * thought * I'd just be doing a quick re-hash of the excellent thread [http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)  But when I've chatted 1-2-1 with people, it's the getting them to understand what / how partitioning is that seems to be the greater problem.

I'm not sure if I'd ever get it to the standards required for the Ubuntu wiki area but I'd be happy to re-tune it. It's possibly overly verbose and my writing style is "we need to do this" and not "the user then is required to do this"

Phill.
(Hmmm... now off topic - Sorry)

---

### Post by VMC on 2009-12-24
> **caryb said:**
> That will learn me to check the spelling of my topic :lolflag: I thought this post would get 1 reply then die a natural death:rolleyes:Cary

At least your a good sport about it.

BTW, how did it all turn out? Did you just start over or find a workable solution.

---

### Post by caryb on 2009-12-24
> BTW, how did it all turn out? Did you just start over or find a workable solution.

There is an old saying patience is a virtue well I guess I'm not very virtuace the next day the dependencies were there & all was good again.


Cary

---

### Post by Gina on 2009-12-24
> **ranch hand said:**
> I take it that, like me, you have way too much information stored to ever get through.

I have trouble just keeping up with what I have to do.  Sometimes education just has to wait.Yes, absolutely!!

---

