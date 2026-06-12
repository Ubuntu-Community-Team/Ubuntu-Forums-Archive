---
title: "[SOLVED] boot multiple ubuntus and windows"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by toobuntu on 2007-03-07
I had an existing installation of Windows XP Pro and installed Ubuntu Dapper, then upgraded to Edgy.  Everything was fine and I had a menu.lst that served me well.

Then I decided to install another instance of Ubuntu for development/testing purposes, and that's when things started to get a bit ugly.  After installing the second Ubuntu, grub was affected in a bad way.

Partition table looks like this:
sda1   Dell utility partition (hidden)
sda2   Windows XP Pro SP2
sda5   Windows pagefile
sda6   Windows MyDocs
sda7   Shared data
sda8   /boot
sda9   /tmp
sda10  /
sda11  /usr
sda12  /home
sda13  Ubuntu-Dapper-testing
sda14  Virtual (for VMware files)
sda15  swap

Windows XP is on sda2, sda5, sda6.  Ubuntu Edgy is on sda8, sda9, sda10, sda11, sda12.  Ubuntu-Dapper-testing is on sda13 (the OS was installed on only this one partition, which would obviously include things like /boot, /, /home, etc.).  Linux swap is sda15 and is shared by both Ubuntus.  sda14 is for storing VMware .vmdk and .vmx files.

After installing the second Ubuntu, I think ubiquity rewrote grub to the MBR, pointing /boot to sda13.  I can manually edit the menu.lst there to put back in the entries for Edgy, but I want the MBR to point /boot to sda8, not sda13, and edit the menu.lst there instead.  sda13 is a testing playground, but sda8 is my actual Ubuntu workstation.  Am I hosed, or is there a way to play around with grub on the MBR?

Can anybody help?

---

### Post by Herman on 2007-03-07
Hello toobuntu,
You should get a [Super Grub Disk]("http://supergrub.forjamari.linex.org/") ready first before working with bootloaders so if you make a mistake you can use the [Super Grub Disk]("http://supergrub.forjamari.linex.org/")
 to boot with to fix the mistake.

Just open a grub shell in your Ubuntu Dapper-testing sda13 operating system by typing 'sudo grub' ```
sudo grub
```Then at the grub>_ prompt, you check to see which filesystems or operating systems are Linux and have grub in them, ```
find /boot/grub/stage1
```and ```
find /grub/stage1
``` Now you specify to grub which operating system's grub stage1 you want have installed somewhere.
```
root (hd0,7)
```Now you tell grub where you want that stage1 installed to, in your case, the MBR.
```
setup (hd0)
```You are done
```
quit
```Now you should be able to boot into your old system again.

Open menu.lst
```
sudo gedit /boot/grub/menu.lst
```Add a grub entry like this at the bottom,
```
title     Ubuntu-Dapper-Testing, Configfile on (hd0,12)
configfile     (hd0,12)/boot/grub/menu.lst
```You should be now able to boot all your operating systems, any problems let me know, I'll be back here later on to check. Good luck.

Regards, Herman. :)

---

### Post by toobuntu on 2007-03-07
Thank you so much, Herman!

I did as you directed, although there was a typo in the line that says:
find /grub/boot/stage1 (should be /boot/grub/stage1)

Interestingly, that returned an Error 13, but I knew my own partition table and so I input the other commands you instructed.  I edited both the menu.lst on sda8 and on sda13, embedding little notes to myself so I'd know which one was being called by grub the next time I rebooted.  It worked!

When I boot into the test distro and run find /boot/grub/stage1 I only get (hd0,12), but when I run find /grub/stage1 I get (hd0,7).  Knowing how the partitions are set up, this does seem right.

Thanks a million for your assistance.  Now I have lost the fear of multibooting.

Next step is to get VMware Server installed on the test distro without breaking networking.  Every time I've installed in in Ubuntu, I've lost my internet and wound up reinstalling the OS....

---

### Post by Herman on 2007-03-07
Hello toobuntu
>  I did as you directed, although there was a typo in the line that says:
find /grub/boot/stage1 (should be /boot/grub/stage1) Sorry about that, yes, you are correct and I was wrong, I have edited the original answer now to make sure no-one else will repeat eh same mistake if they are using that for an example.
> When I boot into the test distro and run find /boot/grub/stage1 I only get (hd0,12), but when I run find /grub/stage1 I get (hd0,7). Knowing how the partitions are set up, this does seem right.Yes, that seems right to me, I remember now that when grub is installed in a /boot partition it's just insdie the partition named boot so it just has a /grub directory. Sorry about that, you are absolutely correct. I will have to edit that to.

You have done very well to have coped with my mistakes and still managed to get the job done successfully. My apologies for any inconvenience. I must have been having a bad morning without even being aware that I was performing badly.

Now that you have it set up that way you should have no more problems multi booting. The good thing about using the configfile command is that it just brings up hte grub menu that is located in the other operating system you want to boot. That menu will be automagically kept up to date by its own operating system, so you now have a maintenance free multiboot setup.
The way some people do it is to copy the boot entry from the other menu.lst and paste it to the menu.lst they want to boot from. That's okay for a while, but it's an entry that is designed to boot the kernel specifically, so it needs to be updated when a new kernel is added. They may be booting an old out of date kernel or even lose their boot if the kernel gets deleted.
The way you have yours now, with the configfile entry, it is worry free.

I don't know anything about VMware server or much about networking, so I hope someone else can help you with those subjects.

Regards, Herman :)

---

### Post by toobuntu on 2007-03-08
> Now that you have it set up that way you should have no more problems multi booting. The good thing about using the configfile command is that it just brings up hte grub menu that is located in the other operating system you want to boot. That menu will be automagically kept up to date by its own operating system, so you now have a maintenance free multiboot setup.
The way some people do it is to copy the boot entry from the other menu.lst and paste it to the menu.lst they want to boot from. That's okay for a while, but it's an entry that is designed to boot the kernel specifically, so it needs to be updated when a new kernel is added. They may be booting an old out of date kernel or even lose their boot if the kernel gets deleted.
The way you have yours now, with the configfile entry, it is worry free.

Ok, I have to admit I cheated a little....  I just copied the boot entries from /boot/grub/menu.lst on sda13 over to /grub/menu.lst on sda8.  How does the configfile work when there are multiple grub entries in the menu.lst it points to?  The automagic menu.lst created on sda13 has the primary kernel, the kernel in safe mode, and mem test.  Will I need to edit the menu.lst default parameters on sda13 so that it only automagically creates/maintains one entry and set the timeout to 0?

---

### Post by Herman on 2007-03-08
Maybe this is too simple for belief, but you don't have to do anything at all to the menu.lst in the menu.lst in Dapper. 

The way it should work is that you should see your grub menu from your (hd0,7)  Edgy Eft /boot partition when the computer boots up and you can select whatever operating systems you like from that menu. At the bottom of the list should be one that says 'Ubuntu-Dapper-Testing, configfile boot on (hd0,12). When you select that your Edgy Eft grub menu should disappear and your Dapper Drake grub menu should be showing. Then you can select any item in that menu.

If you add an entry at the bottom of your Dapper Drake menu.lst to configfile your Edgy Eft grub menu, you will have the option of returning to your Edgy Eft menu when you are booting up.

For example, here is a link to a menu.lst in one of my computers at the moment.  [Fiesty Fawn's new menu.lst]("http://users.bigpond.net.au/hermanzone/p15.htm#Fiesty_Fawns_new_menu.lst"). The machine has four operating systems in it and Windows XP, The operating systems are Ubuntu Edgy Eft, Kubuntu Dapper Drake, Xubuntu Edgy Eft and Feisty Fawn. 
The menu.lst shown for example is my new one in Fiesty Fawn. At the bottom there are configfile entries for the other three Ubuntu operating systems. Each of the other three all have configfile entries for the other three. So I can flick from one grub menu to another in any way I like. They each have their own grub splashimages too. [Add a splashimage to the GRUB menu]("http://users.bigpond.net.au/hermanzone/p15.htm#splash")
So when I'm booting up I see the Ubuntu grub menu from Edgy Eft with the brown spalshimage, then depending on which of the other systems I select I will get that operating system's menu.lst with a neat splashimage for that operating system behind it.
But the splashimages are only for show. The really handy thing about it is that each operating system in the multi boot is booting from its own menu.lst file and has its own kernel entries automagically up to date. I don't have to worry about which one may have recently had a new kernel and whether or not a menu.lst needs to be updated, it's all done automagically.

Did I explain this okay or are you still not sure? Just try adding your own configfile entries to your two menu.lst files and you will understand what I mean very well as soon as you try it out.

Regards, Herman :)

---

