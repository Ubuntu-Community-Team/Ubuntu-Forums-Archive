---
title: "Grub isn't loading...."
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by JasonRivers on 2007-02-21
Hi all!

I've been on ubuntu a few days now, and its looking great, fortunately for me, i've left my Gentoo install intact, as i now wouldn't be able to boot anything atall.

I'm getting a little frustrated, I followed this guide [http://www.ubuntuforums.org/showthread.php?t=208855&highlight=gfxboot]("http://www.ubuntuforums.org/showthread.php?t=208855&highlight=gfxboot") to setup gfx boot, followed it step by step, rebooted, and now it isn't even telling me its loading Grub, it just sits and stares at me.

I have added the ubuntu boot settings to my gentoo's grub install on a seperate drive (with the root listed at hd1,0 - because now my Gentoo drive will be drive 0 in grub, and the ubuntu will be drive 1)

and i'm getting file not found, i've copied the kernel and initrd image to the gentoo boot system, and it gave the same error, i then changed the kernel to (hd1,0)/boot/vmlinuz-2.6.17-11-386 and the same with the initrd image, and still getting file not found.

If I can get into my ubuntu setup, then at least I could remove gfxboot and re-install grub.

I really don't want to do a re-install, as its time consuming at the moment, as bot h my 6.06 and my 6.10 disks are corrupt, and so I have to install 5.10 and upgrade it, which takes about a day on its own.

Any help on this would be greatly appretiated.

Jason

---

### Post by bernied on 2007-02-21
I think you should get a [Super Grub Disk](http://forjamari.linex.org/frs/?group_id=61). If you're going to be doing dual-booting and changing bootloaders, you need to have a recovery system anyway.

I suspect that it was this bit in the howto> grub> root (hdx,y)
grub> setup (hdx)that messed you up. This would install the grub mbr onto hdx, now if hdx is not your first bios disk, then you haven't installed the mbr where it needs to go. Where it needs to go is the device that is normally booted by bios, which is generally hd0, but may not be depending on how you have started grub. (If you add a device in order to boot - in my case this might be a usb flash drive - then that device might become hd0, and all others demoted/promoted, so you'd want to install the grub mbr on hd1.)

These things are specific to your system, which is why it is dangerous to follow howtos without understanding what they are doing.

---

### Post by JasonRivers on 2007-02-22
thanks bernied,

i'm afraid though, I do know what I'm doing, the only hard disk I had plugged into my system at the time was my ubuntu one, so, that would be hd0, it has 2 partitions, an ext3 and a swap, pretty simple.

I plugged up my Gentoo disk, so that I could boot into Linux and post the message.

I tried multiple things from there, to try and sort it.

also, I have 4 hard disks, one with ubuntu, one with Gentoo, and one with Vista (forget it, its crap - its only there because i *have* to have it for work) and the other drive is just a data drive. While setting up an OS I will never have any other drive connected other than the one i'm installing onto.

which also means, all my drives, appart from my data drive, have bootloaders, the 2 linux are running Grub, and then the vista drive runs the vista boot loader. the point though, is that the only drive that was plugged into the system, was my ubuntu drive. I didn't get any errors saying "Operating system not found" (which is what I get when it does try and boot from my data disk) I got no grub errors atall, I just got nothing.

I booted from a live CD again, with only my ubuntu drive plugged up, and ran grub from there, putting it into place on the MBR of my Ubuntu drive, this worked fine, I figured I must have missed something, so so tried with grub-gfxboot a second time, and got the same results. and so again, set grub up from the Live CD.

It would be nice to get gfx-boot running, so any views on this problem are still appretiated.

---

### Post by sheepshearer on 2007-02-22
is it possible that /boot/grub/device.map is getting in the way?

i had a hell of a time with:

```
# cat /boot/grub/device.map 
(hd0)   /dev/hda
(hd1)   /dev/hdc
```

so my 1st IDE slave (/dev/hdb) was actually grub hd2.

i've always used lilo in the past, so having more than one config file in a boot loader was a bit of a surprise to me...

---

### Post by dannyboy79 on 2007-02-22
yep, great point. no matter what you think the drives are (hd0 or hd1) it only matters what /boot/grub/device.map says they are. Another thing to look at is that your #groot line is correct as this got changed on me some how once and I for the life of me couldn't get my ubuntu install back up. it turned out that the #groot line within /boot/grub/menu.lst has to call out where grub's files are stored. since my grub's files were installed on a /boot partition on hdc (hda is my dvd writer and hdb is a data fat32 drive), the #groot line had to be (hd2,1) so grub knew where to find device.map and menu.lst etc etc. just somehting to pay attention to. then another weird thing is that my kernel line is kernel          /vmlinuz-2.6.15-26-686 root=/dev/hdc2 ro noapic single
but yet my root line:
root            (hd0,0)
is that because
because within my device.map it states, 
(hd0)   /dev/hdc
(hd1)   /dev/hdd
(hd2)   /dev/sda
hd0 is hdc. wierd hey?? So i don't really understand what the root line is calling out? good luck

---

### Post by bernied on 2007-02-22
> i'm afraid though, I do know what I'm doing, the only hard disk I had plugged into my system at the time was my ubuntu one, so, that would be hd0, it has 2 partitions, an ext3 and a swap, pretty simple.sorry, no offence intended.

---

### Post by dannyboy79 on 2007-02-22
> **JasonRivers said:**
> While setting up an OS I will never have any other drive connected other than the one i'm installing onto.
 

well there is your problem. what is the first drive in your bios, if you have all of them hooked up again? are you saying that after you do a normal install of grub onto the mbr of your ubuntu disk, you reset your computer and grub doesn't come up?? if that's what your saying and you don't have any other disks installed on your computer, and you didn't during the install, then I would say you have a problem with that grub install. if grub gets put into the mbr, then you install grub's files in a folder called /boot/grub on the same parititon that you installed your ubuntu install on, than everything shuold boot no problem!!! your menu.lst should be really straight forward but I have a feeling you are leaving out info. what is all installed on your machine while you're trying to get ubuntu to work? any cd drives, other hard drives? what does the menu.lst and device.map state? after you boot the live cd, you need to find out what ubuntu is calling your drive. is it being called hda hdb or what? then we can fix grub. also, you did go all the way thru the install without any issues?

---

### Post by dannyboy79 on 2007-02-22
if all else fails, use the super grub disk to reinstall grub on your ubuntu mbr because I believe that's what the issue may be. if you're saying that not even a grub menu comes up, then that means that your mbr isn't even booting grub. when you did the ubuntu install, you did chose to install it to the mbr?

---

### Post by dannyboy79 on 2007-02-22
> **JasonRivers said:**
> Hi all!

I've been on ubuntu a few days now, and its looking great, fortunately for me, i've left my Gentoo install intact, as i now wouldn't be able to boot anything atall.

I'm getting a little frustrated, I followed this guide [http://www.ubuntuforums.org/showthread.php?t=208855&highlight=gfxboot]("http://www.ubuntuforums.org/showthread.php?t=208855&highlight=gfxboot") to setup gfx boot, followed it step by step, rebooted, and now it isn't even telling me its loading Grub, it just sits and stares at me.

I have added the ubuntu boot settings to my gentoo's grub install on a seperate drive (with the root listed at hd1,0 - because now my Gentoo drive will be drive 0 in grub, and the ubuntu will be drive 1)

and i'm getting file not found, i've copied the kernel and initrd image to the gentoo boot system, and it gave the same error, i then changed the kernel to (hd1,0)/boot/vmlinuz-2.6.17-11-386 and the same with the initrd image, and still getting file not found.

If I can get into my ubuntu setup, then at least I could remove gfxboot and re-install grub.

I really don't want to do a re-install, as its time consuming at the moment, as bot h my 6.06 and my 6.10 disks are corrupt, and so I have to install 5.10 and upgrade it, which takes about a day on its own.

Any help on this would be greatly appretiated.

Jason


jason, i just read thru several pages on gfxboot, I notices that the first page of the thread is missing the final step, it involves typing grub-install /dev/hda2 or whatever the output was from doing grub> find /boot/grub/stage1 (you need to convert hd0,1 to hda1 and so on and so forth. did you do this? here is the page for reference. [http://www.ubuntuforums.org/showthread.php?t=208855&page=26&highlight=gfxboot](http://www.ubuntuforums.org/showthread.php?t=208855&page=26&highlight=gfxboot)

only trying to help.

---

