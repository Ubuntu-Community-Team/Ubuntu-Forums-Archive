---
title: "Boot disc until Grub can be made to run?"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by Chan on 2005-05-30
I'm having trouble trying to get Grub to install/ run so I can boot Hoary (Ver 5.04).  Until I get that worked out, I'd like to run the installed Hoary, by using a boot disc.  That's the rub:  Where can I find a copy of a boot disc?  And what might I expect to find on that boot disc (in case I might have to generate one)?  I've done an awful lot of looking, but not much finding.

Any help would be appreciated, Thanks, Chan

---

### Post by mingus on 2005-05-30
Chan,

Is the problem that you could not (or did not) install the boot loader at all during installation, or that you can't get grub to run now after the installation?  And if you installed it, was that on the MBR, the root partition, or a boot partition?

The alternatives for booting depend on those answers.

There are generic free boot loaders like Smart Boot Manager and loadlin.  You boot from floppy and then point to a device or partition.  But that device needs to have a boot sector installed, or there is nothing for the loader to hand off to.

You might check out my reply at:
[http://ubuntuforums.org/showthread.php?t=38092](http://ubuntuforums.org/showthread.php?t=38092)
This method will enable you to install the loader wherever you wish to.  If you are having trouble with grub, you can use the same approach to get to lilo.  You could install in the Linux partition sector and then use the above tool to get to that loader, or you can install to a floppy and boot directly from it.

Make sense?

--mingus

---

### Post by Chan on 2005-05-31
In answer to Mingus, when trying to install Hoary, the installation went fine, but I got an error msg when Grub tried to install.  I'm at a loss to recite it verbatim , but I seem to recall that there was some conflict in the MBR?, so Grub wasn't installed, but I believe that the rest of Hoary was.  Since I'm a Newbie to Linux, I don'y know how to confirm that Hoary was installed.  Can either the Live CD, or the Install disk be used to get Hoary started?  or, should I attempt to do another Install over the previous install?,or get into deep water and use a rescue disc / boot loader?

Thanks for your reply, Chan

---

### Post by GTKpower on 2005-05-31
I don't think you need GRUB at all.

The other Linux bootloader is called LILO.  I use GRUB now because it managed to install itself after numerous errors during previous installs.  I used LILO before that, and I was happy with it.  

Right before your Ubuntu install finishes, I think when it asks you whether you want to install the bootloader, click on "go back", and from the new list, just choose to install LILO.

I'm not sure how LILO behaves under a dual-boot situation, but as far as I know it'll work fine.

---

### Post by mingus on 2005-05-31
[QUOTE=Chan]In answer to Mingus, when trying to install Hoary, the installation went fine, but I got an error msg when Grub tried to install.  I'm at a loss to recite it verbatim , but I seem to recall that there was some conflict in the MBR?, so Grub wasn't installed, but I believe that the rest of Hoary was.  Since I'm a Newbie to Linux, I don'y know how to confirm that Hoary was installed.  Can either the Live CD, or the Install disk be used to get Hoary started?  or, should I attempt to do another Install over the previous install?,or get into deep water and use a rescue disc / boot loader?

Thanks for your reply, Chan[/QUOTE]
 Of course you can just start over as GTKpower indicates and choose LILO instead.  Depending on the reason the first boot loader install failed, this may or may not work.  Each boot loader has its own peculiarities.  But this may be simplest to try.  One other advantage of this approach is that Ubuntu only installs the boot loader you choose, i.e., you don't have lilo yet.  This would add it.  In the event that lilo also failed to create the boot sector, you would have both boot loaders available and we can take it from there.

If for whatever reason you would rather check first that ubuntu installed, boot from the CD and type rescue (along with any kernel arguments you used the first time).  You'll be taken thru a series of menus and then dropped into a shell where you will see what was installed.

---

### Post by Chan on 2005-05-31
It apears that I haven't studied enough.  In the last hour or two, I found that I should have completed the parameters for the pre-configuration file that presets the installing components, among which are Grub, and many other things.

Boy, it's a shame that there is no checklist that a 72 year-old Newbies can refer to.  It would seem that something like that could be done nicely with a database like Excel?  Oh well, I have much work to do, (and I thought that after using one of these contraptions for 25 - 30 years would make me SMART!)

Thanks, Mingus.  (Sho' wish I had an address for you.)  Chan ](*,)

---

### Post by mingus on 2005-05-31
You're welcome.

BTW, I'm not all that far behind your 72.  And even after 30 in the Valley (and Roseville), still learning.

You may be amused to know that I've friends & family in yr neighborhood.  I'm from SF, tho far from home now.

Best,

--mingus

---

### Post by Chan on 2005-06-01
It appears that we may have lots of things to talk about.

Care to share your e-mail address by sending it to:
[email]nospamcdann@usamedia.tv[/email]

Thanks, Chan :-#

---

