---
title: "Vista broken after 11.04-12&gt;04 Gparted upgrade"
date: 2013-01-06
forum: Installation &amp; Upgrades
---

### Post by vector on 2013-01-06
I have been having problems updating on my laptop which was running 11.04,it also wouldnt allow me ot upgrade. Couldnt find certain repos etc so eventually I gave in and decided to install clean a 12.04 live cd.

Before that tho I had noticed I was running out of HD space so I Gparted (12.04 live cd)shrunk the Vista (as I only use it occasionaly).Left it with 10gig free and gained 20g whcih I added to the ext4. This all went fine untill I rebooted. Grub went missing ;(

I went for [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
Which got me back grub but vista still gave error.
[http://paste.ubuntu.com/1502488/]("http://paste.ubuntu.com/1502488/")
Decided to just plough on and install 12.04.

I now have a working grub and 12.04.
Vista tries to boot but then falls back to the recovery screen and no matter what i choose (Startup repair or start windows normally) it just blinks and comes back to that screen. 
Grubs windows recovery enviroment option also seems broke as it ends up in a large error screen, "can not open C:\recovery.dat)


any ideas or is vista beyond repair?
Yea, the usual laptop did not come with disks etc.

---

### Post by vector on 2013-01-06
Digging the whole deeper.
After sending the above post the laptop no longer booted and fell to grub rescue ;(  Possibly trying windows recovery killed grub?

Tried 
[http://askubuntu.com/questions/197833/recovering-from-grub-rescue-crash]("http://askubuntu.com/questions/197833/recovering-from-grub-rescue-crash") Option 0, which failed when it counldt find mount point /mnt/sys

So I ran boot repair
[http://paste.ubuntu.com/1504646/]("http://paste.ubuntu.com/1504646/")

And now there is no Grub just straight into the windows recovery :(

---

### Post by vector on 2013-01-08
reinstalled 12.04
downloaded vista recovery, 
even tho it could not find windows I told it to attempt repair anyway.
I waited and then restarted when prompted.
vista works yay
grub still there yay
12.04 works yaa

Im back to where I was a week ago.
God must love Ubuntu cause i didnt fix this

---

