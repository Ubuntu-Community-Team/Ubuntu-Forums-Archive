---
title: "I Get Nuthin'"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by Nohtanhoj on 2009-11-15
I made a really dumb mistake by formatting my Linux partition when I wanted to upgrade, so now GRUB doesn't exist on my MBR and Windows doesn't have a bootloader because of it. I thought simply booting from a Live USB and re-installing Linux would work, but it seems that my boot problem reaches wider than just my hard drive. Currently, I get nothing when trying to boot from Live USB - just a blank screen with a flashing cursor at the top right. 

I've checked my process in making the Live USB: The MD5Sum is correct, and I've tried many different boot-creator utilities. I have tried USB Startup Disk Creator on a buddy's Ubuntu, I've tried UNetBootIn running from Wine on my Mac, and I have tried the command prompt "dd" from my Mac. All of these ways get the same flashing cursor result.

My final thought is that I need to re-flash my hard drive and start over... Any other ideas before I do this?

---

### Post by 23dornot23d on 2009-11-15
[http://images.google.com/images?q=Samsung%20NC20%20cd&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&ie=UTF-8&sa=N&hl=en&tab=wi]("http://images.google.com/images?q=Samsung%20NC20%20cd&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&ie=UTF-8&sa=N&hl=en&tab=wi")

ok..... see why just a flash boot ....... ?

It sounds like you have no cd/dvd drive ......... 

can you attach a USB external CD/DVD one and boot a live CD from it

If you can boot a live cd then at least you can start to see what is left

on the hard drive and see the partitions .......

Then at least you have a chance .... for sorting it out .......

Do you have much valuable information you need back from it ..... ?

or have you customised it in such a way that you need a restore ?

---

### Post by unamanic on 2009-11-15
You don't need to start over with the whole disk, you just need to re install grub, here are some resources (although if this is a fresh install of 9.10 with grub2, I haven't done it before):
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

[http://dailypackage.fedorabook.com/index.php?/archives/158-System-Recovery-Week-Rescue-Mode-and-Reinstalling-Grub.html](http://dailypackage.fedorabook.com/index.php?/archives/158-System-Recovery-Week-Rescue-Mode-and-Reinstalling-Grub.html)

---

### Post by o0splitpaw0o on 2009-11-15
Here’s the quick and easy way to re-enable Grub.

1) Boot off the LiveCD

2) Open a Terminal and type in the following commands, noting that the first command will put you into the grub “prompt”, and the next 3 commands will be executed there. Also note that hd0,0 implies the first hard drive and the first partition on that drive, which is where you probably installed grub to during installation. If not, then adjust accordingly.

```
    
    sudo grub

    > root (hd0,0)

    > setup (hd0)

    > exit
```

Reboot (removing the livecd), and your boot menu should be back.

---

### Post by Nohtanhoj on 2009-11-16
This is exactly the issue. I was more asking what to do when my computer doesn't recognize any Live USB (and yes, I have a Samsung NC20 with no CD drive). I've also tried SuperGrub as a boot disk, and my computer does not recognize it either. 

The weird thing about this, is that a hard drive bootloader issue should NOT effect any boot from other media, such as PXe or USB! It's not even being initialized, for Pete's sake.

I do not have any incredibly important stuff on that computer other than notes for university (it was basically for that and other apps that don't run on my iMac). The notes are trivial stuff that I can re-take without a huge issue, so a clean drive format IS an option.

I'm not so much worried about re-installing GRUB or Karmic, but why my computer does not boot from a media format that does not involve the hard drive is perplexing.

---

### Post by 23dornot23d on 2009-11-16
I hear what you are saying ..... in the past I have repaired computers .... and ....

The only time I have come across a similar problem was when 

the USB had been used ......... so many times ,,,,, the actual USB socket..... had become loose on the MotherBoard ,,,, 
and was not connecting properly ..... all the time ....

But that was a very old machine ,,,,,,,, and this is only a year or so old ...... from what I can find about it .........

_______________________________________________________________

Can you get hold of a external CD drive to try that ..... see if it gives the same problem ....


It could be a hardware fault ...... did it work ok before ..... or have you had problems in the
past with it not working properly ........ ?

I saw the other thread ..... looks like you have already been through a lot of possibilities with this already ......

[http://ubuntuforums.org/showthread.php?t=1324945](http://ubuntuforums.org/showthread.php?t=1324945)

[http://ubuntuforums.org/showthread.php?t=1326776](http://ubuntuforums.org/showthread.php?t=1326776)

This machine should be still under warranty .....also ..... could get them to check it out ....

If it was me ..... I would be looking for someone with a similar machine and a boot flash that 

definately works ..... put it in ..... if you are still getting nowhere ,,,, it could possible be

a hardware fault .........

_____________________________________________________________________

I bet its this .......... 

* if you are not sure here - get someone who does this regular to alter it *

There is always an option to return to default settings ,,,,, too .......
_____________________________________________________________________

You have been in the BIOS and set it to boot from USB Flash ....  I hope...........

( Need to know more about the BIOS boot settings on Mac ..... will return ...... )

The First Boot screen in BIOS should look something like this .....

_[IMG]http://web.mac.com/darkdragoon/stuff/07CABoot.png[/IMG]_


Then after selecting the Boot Device Priority ...... you will get a screen like this .........


[IMG]http://web.mac.com/darkdragoon/stuff/07CABootDevices.png[/IMG]


If you look above ..... a lot are excluded from the boot order ....... 

just a thought ...... push the USB boot order items up that you need to boot from

by going down to the item and then pressing F5 to move it to the TOP ...... F6 moves it

back again .........

_______________________________________________________________

If its not ........... as above ...... have a read here ......

This makes interesting reading ..... see if this helps at all .........

A very similar situation .......

[http://www.sammynetbook.com/plugins/forum/forum_viewtopic.php?23918](http://www.sammynetbook.com/plugins/forum/forum_viewtopic.php?23918)



Ok thats as far as I go ........ with this ...... until a reply comes back

---

### Post by Nohtanhoj on 2009-11-16
I've tried excluding everything from the boot list except my USB stick (which is autodetected by the BIOS when I plug it in), and that doesn't have any effect on the flashing cursor.

I was thinking about going to pick up an external CD drive for the netbook (this would eliminate the USB stick as a variable, as I would be using my 9.10 install disc). Thoughts on this?

---

### Post by 23dornot23d on 2009-11-16
Yep sounds a great idea ..... but as I said earlier ..... 

it would be better to check using someone elses USB CD/DVD drive first ....

Once you know the USB socket is not at fault ..... 

Then I would buy one ..... it will save you lots of messing about in the future
too ..... 

The prices for external USB CD/DVDs varies a lot ....... not sure with MAC .....

but ensure that you get a compatible one ..... hope fully the same as the one
you can get to try it out ........ with ..........

_______________________________________

The last DVD/CD reader and writer I bought was a LG lightscribe double layer
for 40 euros ...... to give an idea ...... of prices ....

Most writers started at around ...........  40 .......

If you want just to read ..... they were as low as ...... 22 euros ..... off Amazon .....

Not sure where you are or What choices you will have ........

But if it was me I would try one out if possible first .....

Then buy one the same as the one I tried out ........

If you do not have this option ....... do some checking on the Model and Type
you intend to buy ...... by searching on the net for people using a similar setup

Best advice I can give at this moment in time ...... as we still do not know if there

is a hardware fault on the USB socket/s ..........

---

### Post by Nohtanhoj on 2009-11-17
Checked using my buddy's flash drive. Same old same old, however... Would this be because his flash drive is the same brand as mine, just a different capacity? (Mine is a Kingston 4GB, his is 1GB).

---

### Post by 23dornot23d on 2009-11-17
[quote]

I've tried excluding everything from the boot list except my USB stick (which is autodetected by the BIOS when I plug it in), and that doesn't have any effect on the flashing cursor.

[quote]

I have just re-read what you said here ..... and think that you might be plugging the USB in after you have turned the computer on ......

( you seem to be plugging it in after you have switched the computer on .............. )

This is the way you should do it ......

  SET the BIOS ..................... to boot from the USB stick ........ switch the computer    >>>      OFF 

1 .......  plug in the USB stick that has the boot information and the live UBUNTU on it ..........

2 .......  then switch  >>>>>  ON        the computer ...... with the USB still plugged into it ...........

3 ........ let me know if it works .....


( it will not work if you plug the USB in after you turn it on )

I hope this helps ......... 

*********************************************************************
BECAUSE .... adding a boot device after it is turned ON >>>>>  is NOT going to work 
*********************************************************************

---

### Post by unamanic on 2009-11-17
My son has an eeePC 1000HE, and his hard drive recently died.   Symptoms were very similar, appeard to freeze on boot with a blinking cursor (although after several minute it cam back with disk could not be read), would not boot from USB, etc.  I isolated it down to the HD by removing it and then I was able to boot from USB drive.Just a thought, hope it helps.

---

### Post by Nohtanhoj on 2009-11-18
You opened up the computer and all? That's not really an option for me, but it's food for thought for sure. I could always take the computer to a repair shop and just get them to replace the drive, but that's a last last resort. Before that would somehow be formatting my internal drive with killdisk or something, then starting from scratch.

---

### Post by unamanic on 2009-11-18
The eeePC has a small panel on the bottom for upgrading/repining the HD and RAM, so for me it was only 3 screw.  Now swapping the default wireless card for an Intel one I had laying around, that was a pain, but the HD was not.  I'm not familiar with killdisk, but if you could get anything to boot your computer, then you would expect Ubuntu would boot as well.

---

### Post by Nohtanhoj on 2009-11-28
Bump for success. I now have my dual boot working. I didn't fix it using any of your methods, I used an external CD drive to boot from my Ubuntu Live CD and re-install. 

The reason I think this worked and the USB didn't work is this: My previously corrupt MBR could have contained instructions on booting from USB (it's the MBR, it makes sense), and in its corrupted state, could not relay those instructions during boot. The CD boot contains its own instructions, and thus I was able to boot from it.

I may be bad and wrong, but my computer works! =D =D

Now to get wireless going.... Stupid Atheros compatibility.

---

### Post by negate on 2009-11-30
I've made a very n00b mistake along similar lines as the TC.  I'm running UNR 9.10 on a Toshiba mini NB205-n310.  I am also trying to do a clean install of 9.10 using a usb pen drive, and am unable to boot from the LiveUSB, instead being sent into a failed PXE boot attempt and then my system stalls.  This is despite all efforts to try different ways of writing the USB (including those that worked before), as well as fiddling with the boot priorities in the BIOS (to no avail).  I'm uncertain what to do, hence my asking here.  
The only thing I believe this could be related to: I originally installed 9.04 on my nb205, and dist-upgraded via ALT-F2 to 9.10 when the RC was released.  I wasn't aware of the changes regarding ext4 and grub2 becoming default, and didn't do a clean install, instead keeping ext3 (hence my desire to clean install now).  At some point I noticed that grub2 wasn't installed, and attempted to install it - only to uninstall it later, realizing I shouldn't have done so (I know - **stupid**).  Since it's had no adverse effect on my computer (other than very slow boot times, the problem) - except that, now, I apparently cannot boot from a USB stick. 
 Can anyone help me isolate the problem/suggest any possible solutions? 
Thanks

---

### Post by negate on 2009-11-30
After reading around more, I came across [this]("https://help.ubuntu.com/community/Grub2"), saying that grub2 is a dummy package, which, even after upgrading to 9.10, will appear to be uninstalled. Perhaps my reinstalling wasn't the source of my current problem?

---

