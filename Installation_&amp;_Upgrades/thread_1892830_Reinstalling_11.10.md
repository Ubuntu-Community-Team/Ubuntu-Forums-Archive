---
title: "Reinstalling 11.10"
date: 2011-12-08
forum: Installation &amp; Upgrades
---

### Post by got2av8 on 2011-12-08
I have a laptop with 11.10 installed.  Due to a PEBKAC error, the normal boot sequence now only goes as far as the logo and freezes.  In recovery mode, command line is available and as far as I can determine fully functional.

Since the computer worked just fine until the user goofed around with it, rather than spending days chasing down whatever the error is I'd like to do a fresh install.

1) Is there a way to force a reinstall of the current release from the command line? Seems to me this would be the easiest.

If not, I have a live disc on USB that works, but this particular machine dual-boots Windows Vista and the owner wants to keep that.  I'm not familiar with the dual boot install process, so...

2) Installing on the existing partition, I assume I choose
     Installation type: something else
then from the partiton menu, the existing Ubuntu partition is
     /dev/sda6
Does this need a mount point selected? Do I use '/'? '/boot'? 
Where it offers a dropdown for 'Device for boot loader installation', do I select /dev/sda (the main hard disc), or one of the other partitions? should this be sda6, the same as the Ubuntu location?

I've never had a reason to do a reinstall on an existing partition before, and I'd kind of like to not screw it up, as this isn't my computer.  ANY advice appreciated, thanks.

---

### Post by fantab on 2011-12-08
> **got2av8 said:**
> 1) Is there a way to force a reinstall of the current release from the command line? Seems to me this would be the easiest.

If not, I have a live disc on USB that works, but this particular machine dual-boots Windows Vista and the owner wants to keep that.  I'm not familiar with the dual boot install process, so...

2) Installing on the existing partition, I assume I choose
     Installation type: something else
then from the partiton menu, the existing Ubuntu partition is
     /dev/sda6
Does this need a mount point selected? Do I use '/'? '/boot'? 
Where it offers a dropdown for 'Device for boot loader installation', do I select /dev/sda (the main hard disc), or one of the other partitions? should this be sda6, the same as the Ubuntu location?

I've never had a reason to do a reinstall on an existing partition before, and I'd kind of like to not screw it up, as this isn't my computer.  ANY advice appreciated, thanks.

Recovery is not easiest as it take a long time. IMO it will be easier to re-install Ubuntu. 

Yes you have to choose "something else" option, select the /dev/sda6 and format it using ext4 and " / " mount point. (I hope you already have SWAP partition, if not create one).
Yes you have to **install boot loader to /dev/sda ONLY**.

[Read HERE]("http://members.iinet.net.au/%7Eherman546/p23.html") for more info on dual boot.

---

