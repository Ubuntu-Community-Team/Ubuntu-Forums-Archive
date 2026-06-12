---
title: "Revert from grub2 to legacy grub - not a tutorial!"
date: 2009-08-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2009-08-23
Please just go here:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by SuperSonic4 on 2009-08-23
Would nano work for step 2?

---

### Post by kansasnoob on 2009-08-23
> **SuperSonic4 said:**
> Would nano work for step 2?

Probably. I hadn't even thought of it:confused:

It certainly would be nice to simply let installing grub (after removing grub2) just generate it's own menu.lst and then edit it as needed.

I'd anticipated this and since gedit had been randomly crashing I just pre-built a menu.lst to use.

---

### Post by bluesscream on 2009-08-23
just run sudo gedit, mark your file in gui and open it.
Hope they get this ~4weeks-lasting debian bug fixed soon.

---

### Post by kansasnoob on 2009-08-23
> **bluesscream said:**
> just run sudo gedit, mark your file in gui and open it.
Hope they get this ~4weeks-lasting debian bug fixed soon.
But why do you want to downgrade grub? You can edit grub.cfg as well as before menu.lst, but make backups of your system generated files as well as of your customized ones and have a look on your /etc/grub.d.

"But why do you want to downgrade grub?"
As I said above it's just a matter of choice. But to be more specific:

#1. I liked the way startupmanager interacted with legacy grub. As I said, I'm legally blind, which is one of the reasons I choose to do as much as possible with gui's - such as using nautilus-gksu rather than having to learn new file names. Orca's great but it can be very time consuming having to "magnify" all the different files and then having to memorize them is another story.

#2. I normally run a machine with Win XP and no less than 4 Linux OS's multi-booted, quite often as many as 7. On this test drive I get this:

> menuentry "Ubuntu, Linux 2.6.31-6-generic" {
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 00056c85-6d01-4a7c-8d4f-00905dfab659
	linux	/boot/vmlinuz-2.6.31-6-generic root=UUID=00056c85-6d01-4a7c-8d4f-00905dfab659 ro splash #GRUB_DISABLE_LINUX_UUID=true quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-6-generic
}
menuentry "Ubuntu, Linux 2.6.31-6-generic (recovery mode)" {
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 00056c85-6d01-4a7c-8d4f-00905dfab659
	linux	/boot/vmlinuz-2.6.31-6-generic root=UUID=00056c85-6d01-4a7c-8d4f-00905dfab659 ro single splash #GRUB_DISABLE_LINUX_UUID=true quiet
	initrd	/boot/initrd.img-2.6.31-6-generic
}
menuentry "Ubuntu, Linux 2.6.31-5-generic" {
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 00056c85-6d01-4a7c-8d4f-00905dfab659
	linux	/boot/vmlinuz-2.6.31-5-generic root=UUID=00056c85-6d01-4a7c-8d4f-00905dfab659 ro splash #GRUB_DISABLE_LINUX_UUID=true quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-5-generic
}
menuentry "Ubuntu, Linux 2.6.31-5-generic (recovery mode)" {
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 00056c85-6d01-4a7c-8d4f-00905dfab659
	linux	/boot/vmlinuz-2.6.31-5-generic root=UUID=00056c85-6d01-4a7c-8d4f-00905dfab659 ro single splash #GRUB_DISABLE_LINUX_UUID=true quiet
	initrd	/boot/initrd.img-2.6.31-5-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

[B]### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" {
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 3ada934d-ba5c-45e4-bc1b-ae2062df346f
	linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda6
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" {
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 3ada934d-ba5c-45e4-bc1b-ae2062df346f
	linux /boot/vmlinuz-2.6.28-15-generic root=/dev/sda6
	initrd /boot/initrd.img-2.6.28-15-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_otheros ###

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda6)" {
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 3ada934d-ba5c-45e4-bc1b-ae2062df346f
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=3ada934d-ba5c-45e4-bc1b-ae2062df346f ro quiet splash 
	initrd /boot/initrd.img-2.6.28-15-generic
}


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda6)" {
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 3ada934d-ba5c-45e4-bc1b-ae2062df346f
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=3ada934d-ba5c-45e4-bc1b-ae2062df346f ro single 
	initrd /boot/initrd.img-2.6.28-15-generic
}
[/B]
### END /etc/grub.d/30_otheros ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
### END /etc/grub.d/40_custom ###

So I have two Jaunty boot options that don't even need to be there and result in a "non-quiet" boot.

Think what a mess that would be with 4 to 7 other Linux entries along with XP! A menu that would take 2 minutes to scroll through?

#3: grub.cfg begins with "DO NOT EDIT THIS FILE". And, yes I've been reading! But I'm legally blind! So if I prefer legacy grub and that's what I want, that's what I'll use.

I posted this only in hopes that it may help someone else, and I hope I posted plenty of warnings. I'm hardly recommending that everyone revert.

---

### Post by ranch hand on 2009-08-23
I think this may be popular, at least for a while, after the release of 9.10.

Another way to do it would be to uninstall grub2 and use the jaunty repo to get grub-legacy.

I have an installation of Kinky Kitten (9.10)A1 that, while updated daily, has never had a dist-upgrade.  It has all the common files but still runs on grub-legacy.

All that said, as a lover of grub-legacy I have to say that I am getting to like grub2 a bunch.

Your mention of 4-7 other Liux entries did make me smile.  I only have one drive (they all boot seperately) that has only 4 and it boots with grub-legacy.  The other 2 drives have more "entries" than 7 and both are grub2.

The other internal is running 8.  The external dual is running 11.

I will admit to a little trouble but I think that as new file systems come on line, grub2 will prove more flexible than grub-legacy.  I also think that grub2 is very much a "work in progress" and will improve dramatically very fast.

The bug with gedit I get around with screem in my many Kinky variations.  I hope that one gets fixed pretty soon.

---

### Post by bluesscream on 2009-08-23
sorry, kansasnoob, I edited my post 2 minutes before you replied, cause i had not read your text properly. I think that's very important information for developers to lower unfriendly barrieres. But I agree to ranch hand, grub2 in future seems to become more flexible then legacy grub.

---

### Post by kansasnoob on 2009-08-23
> **ranch hand said:**
> I think this may be popular, at least for a while, after the release of 9.10.

Another way to do it would be to uninstall grub2 and use the jaunty repo to get grub-legacy.

I have an installation of Kinky Kitten (9.10)A1 that, while updated daily, has never had a dist-upgrade.  It has all the common files but still runs on grub-legacy.

All that said, as a lover of grub-legacy I have to say that I am getting to like grub2 a bunch.

Your mention of 4-7 other Liux entries did make me smile.  I only have one drive (they all boot seperately) that has only 4 and it boots with grub-legacy.  The other 2 drives have more "entries" than 7 and both are grub2.

The other internal is running 8.  The external dual is running 11.

I will admit to a little trouble but I think that as new file systems come on line, grub2 will prove more flexible than grub-legacy.  I also think that grub2 is very much a "work in progress" and will improve dramatically very fast.

The bug with gedit I get around with screem in my many Kinky variations.  I hope that one gets fixed pretty soon.

I totally agree with what you're saying. Just FYI I did this installation with an Alpha 4 Live CD and grub (legacy version) is still in the repos (this may or may not be true in the final release).

I specifically pointed out that this was NOT a tutorial but rather just what I did and it worked.

I hope someone with more experience and smarts can condense this to a few commands because I expect I'll not be alone in wishing to revert.

Just a personal FYI, I noticed you once said you were a blacksmith (among other things) and I was a mechanic before they started calling us "automotive technicians". I considered a 3# hammer a "tack" hammer - as hammers go:)

Anything smaller is only good for making gaskets and such:lolflag:

---

### Post by ranch hand on 2009-08-23
Hammers are just great.  You can't have too many.

I even have some small ones that I use a bunch.  To move some metal though takes a 4# hammer and and a 300# anvil.

I really like Nautilus.  It is a BIG hammer.

---

### Post by kansasnoob on 2009-08-23
> **bluesscream said:**
> sorry, kansasnoob, I edited my post 2 minutes before you replied, cause i had not read your text properly. I think that's very important information for developers to lower unfriendly barrieres. But I agree to ranch hand, grub2 in future seems to become more flexible then legacy grub.

All's well. We only learn through feedback, and all comments are always welcome.

In many ways this is like the new notify-osd. When it becomes more easily configurable from a gui I'm sure I'll love it, until then I'll revert to the old daemon. As it is, I lack the time to visually focus on it before it disappears (and it would be better if I could keep it at the lower right).

Regardless I find Ubuntu to have the most friendly forums and the most easily modifiable Gnome desktop.

---

### Post by kansasnoob on 2009-08-23
> I really like Nautilus. It is a BIG hammer.

I like that. Maybe I should add that 'nautilus-gksu' makes it like Thor's own hammer! It's all good until that Norse god hammers the whole system.

I've hammered mine more than once.

---

### Post by kansasnoob on 2009-08-26
Not truly an edit but I thought I'd add that until the devs get gedit straightened out you can use leafpad. It's simpler to use than nano or vim and it doesn't require the dependencies of kate or mousepad.

So, if you want to play around like I did, maybe give leafpad a try!

---

### Post by chriskin on 2009-09-24
just wanted to add here that my laptop that hates grub2 boots finely now, after following the steps above i mean
in fact i am writing through karmic now 
thanks :)

---

### Post by kansasnoob on 2009-10-02
Go here:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by kansasnoob on 2009-10-02
Thought I would add that I've found this syntax in menu.lst to be most effective to boot Karmic using legacy grub after grub 2 is removed:

> title		Ubuntu 9.10, kernel 2.6.31-11-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro quiet splash 
initrd		/boot/initrd.img-2.6.31-11-generic
savedefault
boot

title		Ubuntu 9.10, kernel 2.6.31-11-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro single 
initrd		/boot/initrd.img-2.6.31-11-generic
savedefault
boot

as compared to this:

> title		Ubuntu karmic (development branch), kernel 2.6.31-11-generic
uuid		d3d589c9-29e6-463e-9c99-806ec3646dea
kernel		/boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro quiet splash 
initrd		/boot/initrd.img-2.6.31-11-generic

title		Ubuntu karmic (development branch), kernel 2.6.31-11-generic (recovery mode)
uuid		d3d589c9-29e6-463e-9c99-806ec3646dea
kernel		/boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro  single
initrd		/boot/initrd.img-2.6.31-11-generic

No idea why:confused:

---

### Post by kansasnoob on 2009-10-03
Just go here:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by kansasnoob on 2009-10-03
Just go here:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by kansasnoob on 2009-10-08
**[COLOR="Red"]HowTo here:[/COLOR]**

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Someone will undoubtedly ask, "why would I want to revert to legacy grub"? My answer is, "I hope you don't". Grub 2 is the way of the future and I'd bet that a year from now nearly everyone will think of legacy grub as downright prehistoric! If you're new to Ubuntu I believe you'll find Grub 2 to be no more complicated than legacy grub, and the documentation continues to improve. I know 20 months ago legacy-grub was confusing to me.

That said I originally undertook this just as a matter of curiosity. I knew that installing via the Alternate CD allowed installing with no boot-loader at all (or Lilo) and I've since learned that you can do somewhat likewise using the Live CD. Also legacy grub is quite familiar to me and the real beauty of Ubuntu, or Linux in general, is the ability to customize it to your hearts content (yeah, and even break it)! I should note here that I've only been able to test this on i386 since I have no 64 bit machines! [COLOR="RoyalBlue"](I'd appreciate any feedback regarding success or failure following these steps on a 64 bit machine.)[/COLOR]

So, on with business, [COLOR="Red"]please read this in it's entirety before beginning[/COLOR]. If you have any doubts ask questions here on the forums before beginning and make sure you have everything you need! You don't want to get part way through this and find you're unable to complete it! Since we're working on the boot-loader [COLOR="Red"]I recommend at the very least having an Ubuntu Live CD on hand[/COLOR] that you know works (it need not be Karmic) so we can work from it if need be. [COLOR="Red"]If any of these steps fail to complete successfully you will most likely be unable to boot your system![/COLOR] Not to worry though if you have a Live CD, that's briefly explained in Appendix #1, and Appendix #2 describes very briefly how to reverse the steps outlined here.

Some prior knowledge regarding Legacy Grub is helpful and you must know how your system is partitioned, how many drives you have, etc. so I recommend figuring that out before you even begin! The following link is a great resource or, if in doubt, ask questions here at the forums.

[http://members.iinet.net.au/~herman546/p15.html#Re-install_Grub_with_Live_CD](http://members.iinet.net.au/~herman546/p15.html#Re-install_Grub_with_Live_CD)

I will not go into detail about editing the menu.lst here other than providing an example of my own boot entries. *(See Appendix #3)* Again this is a great resource:

[http://members.iinet.net.au/~herman546/p15.html#menu.lst](http://members.iinet.net.au/~herman546/p15.html#menu.lst)

I highly recommend using copy-n-paste to run these commands. *It can also be quite useful to keep a record of what happens in the terminal by simply keeping Abiword or Open Office Word open and "copy-n-pasting" the results of various steps into a document, then saving that document when done. That way if something goes haywire we can use that to troubleshoot what went wrong. I always put a copy in my Yahoo mailbox so I can access it easily from any computer or even the Live CD.*

So, when you're ready, let's begin:

**Step #1: Rename the existing grub directory and create a new one.**

We want to rename the existing /boot/grub directory for use as a backup so go to the Terminal and run the command:

```
sudo mv /boot/grub /boot/grub_backup
```

Now we'll create a new grub directory:

```
sudo mkdir /boot/grub
```

To be certain those two commands were effective you can run the command:

```
ls ~ /boot
```

[I]Note: that's a lower case L.
[/I]
You can see highlighted in the sample output below that we now have both grub and grub_backup in the boot directory:

> lance@lance-desktop:~$ ls ~ /boot
/boot:
abi-2.6.31-11-generic         memtest86+.bin
config-2.6.31-11-generic      System.map-2.6.31-11-generic
**grub**                          vmcoreinfo-2.6.31-11-generic
**grub_backup**                  vmlinuz-2.6.31-11-generic
initrd.img-2.6.31-11-generic

/home/lance:
Desktop    Downloads         Music     Projects  Templates
Documents  examples.desktop  Pictures  Public    Videos

Likewise if you run:

```
ls ~ /boot/grub
```

You should see that the grub directory is currently empty because we haven't reinstalled grub yet.

Alternatively you can go to  Places > Computer > Filesystem > Boot, you should see the folders named "grub" and "grub_backup".

**Step #2: Remove Grub 2 packages, purge configuration files, and install legacy Grub packages.**

[I]Just FYI 'grub-pc' is grub2 and 'grub' is legacy grub.
[/I]
First remove grub2:

```
sudo apt-get --purge remove grub-pc grub-common os-prober
```


You'll be confronted with this text:

> Do you want to have all GRUB 2 files removed from /boot/grub? 
Your system would be then unbootable if you don't install another bootloader.                                                  Remove GRUB 2 from /boot/grub? 
   
**Yes**, you do!          
                  
Now install legacy grub:

```
sudo apt-get install grub
```

You'll notice that installing grub also reinstalls grub-common and os-prober, that's normal behavior, we just wanted to "purge" the configuration files. In fact grub-common and os-prober are marked as automatically installed in Synaptic so they'll be reinstalled with any update. Forced removal (that is unmarking the "automatically installed" option) will result in failed kernel updates.

Now:

```
sudo update-grub
```

You'll be asked if you want to create a /boot/grub/menu.lst - **yes, you do**, so type y and enter!

[I]This would be a good time to create a word document of Terminal progress as recommended above if needed for troubleshooting purposes.
[/I]

**Step #3: Physically install and setup Legacy Grub.**

Now you must actually "install" legacy grub if you're going to use your new legacy grub to boot with and you must know where. In my case I have only one hard drive and I can see how it's recognized by Ubuntu by running the command:

```
sudo fdisk -l
```

(BTW that's a lower case L.) The pertinent part is in bold in this example:

> lance@lance-desktop:~$ sudo fdisk -l
[sudo] password for lance: 

Disk **/dev/sda**: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63056305

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2104    16900348+   7  HPFS/NTFS
/dev/sda2            2883        9729    54998527+   5  Extended
/dev/sda3            2105        2882     6249285   83  Linux
/dev/sda5            4214        5012     6417967+  83  Linux
/dev/sda6            5013        7434    19454683+  83  Linux
/dev/sda7            7435        8199     6144831   83  Linux
/dev/sda8            8200        9576    11060721   83  Linux
/dev/sda9            9577        9729     1228941   82  Linux swap / Solaris
/dev/sda10           2883        4213    10691194+  83  Linux

Partition table entries are not in disk order

Since /dev/sda is where I'd want grub to be installed, I'd run this command:

&#65279;```
sudo grub-install /dev/sda
```

[I]Note: If you're at all unsure about where to install grub then ask for help here on the forums! Better to be sure of what you're doing than to play the trial and error game!
[/I]
Now we need to open a Grub shell as root so run the command:

```
sudo grub
```

[I]Note: I've noticed while working in a grub shell that the enter key in the numerical block of the keyboard doesn't always work properly, so use the enter key just above the right shift key!
[/I]
Then:

&#65279;```
find /boot/grub/stage1
```

That will provide an output like (hd0,2) which you'll need to use in the next step:

&#65279;```
root (hd0,2)
```

You see I've used (hd0,2) from the "find" command, of course you'll use whatever the output was in your specific case. Then:

```
setup (hd0)
```

There I've used the hd0 (that is a zero) from the (**hd0**,2) output from the "find" command.

If correct you should see an output like:

&#65279;> Checking if "/boot/grub/stage1" exists... **yes**
 Checking if "/boot/grub/stage2" exists... **yes**
 Checking if "/boot/grub/e2fs_stage1_5" exists... **yes**
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
 **succeeded**
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
 2 /boot/grub/menu.lst"... **succeeded**
 Done.

*Again, this would be a good time to create a word document of Terminal progress as recommended above just for future troubleshooting purposes because:*

[COLOR="Red"]If that failed you will likely not be able to boot your machine until we get it straightened out![/COLOR]

Next just type:

```
quit
```

To exit the Grub shell.

**If successful you're done! Time to reboot and see what happens. I hope you read this all first and kept a text record of the terminal just in case something went haywire.**

**Step #4: Install Startup Manager and lock package versions if desired.**

Of course if you want to use startupmanager install it:

```
sudo apt-get install startupmanager
```

*But I should say that I've had ongoing problems keeping startupmanager working in Karmic. It's working right now after following the above steps so [COLOR="Red"]I rather think it might be wise to go to Synaptic and choose to "lock version" both "grub" and "grub-common"[/COLOR], but I'm in testing mode so I can't do that right now. Also it seems as though when an update causes startupmanager to stop functioning I can get it working again by doing a --purge remove of "grub-common" and of course then reinstalling the "grub", "grub-common" and "startupmanager" packages. (No need to create or edit a menu.lst, or physically reinstall grub.)*

**[COLOR="Red"]**************************************************[/COLOR]**

**Appendix #1:**

I'd mentioned above being able to "fix" things using a Live CD. I posted briefly about that here:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Of course you'll need to know what partition to mount, what commands to run, etc. And, as mentioned above, this is where a printed record of terminal progress comes in handy! Literally every step necessary to repair or install and setup either legacy grub or grub2 can be completed using a Live CD if you know what to do! Of course if you haphazardly mount the wrong partition you can also destroy things and lose data really fast.

**[COLOR="Red"]**************************************************[/COLOR]**

**Appendix #2:**

OK, so imagine you've changed to legacy grub and now you want to switch back to grub2 (should be self explanatory, same logic applies):

sudo mv /boot/grub /boot/grub_legacy (we already used the name: grub_backup)
sudo mv /boot/grub_backup boot/grub (or sudo mkdir /boot/grub if you want to start fresh)
sudo apt-get --purge remove grub grub-common
sudo apt-get install grub-pc
sudo update-grub
sudo grub-install /dev/sda (replace /dev/sda with your proper destination)

Seems simple without my rambling verbosity, eh? I can now "flip" from one to the other in about 15 minutes - but not blindfolded.

**[COLOR="Red"]**************************************************[/COLOR]**

**Appendix #3**:

This is what my Karmic /boot/grub/menu.lst boot entries look like (of course I had to manually add the lines to boot Win XP, Jaunty, and Mint Gloria):

## ## End Default Options ##

title		Ubuntu karmic (development branch), kernel 2.6.31-11-generic
uuid		d3d589c9-29e6-463e-9c99-806ec3646dea
kernel		/boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro quiet splash 
initrd		/boot/initrd.img-2.6.31-11-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.31-11-generic (recovery mode)
uuid		d3d589c9-29e6-463e-9c99-806ec3646dea
kernel		/boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro  single
initrd		/boot/initrd.img-2.6.31-11-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7 ro single 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title         Linux Mint 7 Gloria, kernel 2.6.28-15-generic
root          (hd0,6)
kernel        /boot/vmlinuz-2.6.28-15-generic root=/dev/sda7 ro quiet splash
initrd        /boot/initrd.img-2.6.28-15-generic
quiet
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title         Linux Mint 7 Gloria, kernel 2.6.28-15-generic (recovery mode)
root          (hd0,6)
kernel        /boot/vmlinuz-2.6.28-15-generic root=/dev/sda7 ro single
initrd        /boot/initrd.img-2.6.28-15-generic
savedefault
boot

**[COLOR="Red"]**************************************************[/COLOR]**

I've found this syntax to work better for adding Karmic to another existing grub menu.lst:

&#65279;title Ubuntu 9.10, kernel 2.6.31-11-generic (on /dev/sda3)
 root (hd0,2)
 kernel /boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro quiet splash 
initrd /boot/initrd.img-2.6.31-11-generic
 savedefault
 boot
 
title Ubuntu 9.10, kernel 2.6.31-11-generic (recovery mode) (on /dev/sda3)
 root (hd0,2)
 kernel /boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro single 
initrd /boot/initrd.img-2.6.31-11-generic
 savedefault
 boot 

Rather than this:

&#65279;title Ubuntu karmic (development branch), kernel 2.6.31-11-generic
 uuid d3d589c9-29e6-463e-9c99-806ec3646dea
 kernel /boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro quiet splash 
initrd /boot/initrd.img-2.6.31-11-generic
 
title Ubuntu karmic (development branch), kernel 2.6.31-11-generic (recovery mode)
 uuid d3d589c9-29e6-463e-9c99-806ec3646dea
 kernel /boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro single
 initrd /boot/initrd.img-2.6.31-11-generic 

No idea why!

---

### Post by fourscore on 2009-10-23
> **kansasnoob said:**
> 
...
Someone will undoubtedly ask, "why would I want to revert to legacy grub"? ... 


Tks for the detailed tutorial. I may give it a shot after upgrading to Karmic as the only place I am getting stuck in Grub2 (note: have successfully installed grub2 in Jaunty)  is changing the size of the window in the grub menu.  I could do this adjustment in old grub so that the  window size fit into the background image.  I have not been able to get the equivalent command in Grub2 for  "viewport" to change the size of the window.  If you can help out with this pls advise.  I have posted the above query in the ubuntu forums without any luck.

---

