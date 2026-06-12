---
title: "Make installed Ubuntu bootable again?"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by moerl on 2006-09-20
Here's the story:

This afternoon I decided, completely out of the blue, to give Ubuntu another shot. Months ago I tried it once and was left with a very bitter after-taste.. back then, I fought the battle of trying to get my laptop's ATI GFX card to work right in Ubuntu and it was such a PITA that I gave up and gave Ubuntu the boot. I really don't know what happened in the meantime, but it seems Ubuntu has gotten WAY better. It's better than ever from what I can tell. That's a good thing :)

I used it for a little while today and that was all great. I went to work, came back, and wanted to boot back into Windows. But oh? Contrary to my expectations that Ubuntu would automatically setup dual-booting with WinXP, I was only able to boot into Ubuntu. Windows was all gone from my OS choices at boot. So I got a bit concerned, at first. Then, for the first time, I actually used Windows' wonderful recovery console that can be accessed by booting a Windows setup disc. I got everything fixed again and back I am in Windows. PHEW!

But now.. obviously, I can't boot into Ubuntu :/. It's installed, it's there, everything's great, (well, not everything, but that's a different topic), but I have no way of booting Ubuntu.

What can I do to fix this?

By the way.. I'm a fan of Acronis products and have Acronis Disk Director Suite installed. It includes something called the "Acronis OS Selector". I'm guessing that would be the perfect fit as a solution in this case.. the only trouble is that it doesn't detect Ubuntu currently. Probably because it's not represented anywhere in the MBR, in any way.

Once I figure this out I'd like to use Acronis OS Selector to take care of the dual-booting.

Thanks in advance, and sorry for making this longer than it could have been.

---

### Post by ollienz on 2006-09-20
I've got a copy of OS selector as well - works perfectly for me?

For me it scanned the partitions and found the Ubuntu one as bootable despite not being in the MBR.

---

### Post by moerl on 2006-09-20
Hmmmm.. do you have to ACTIVATE OS Selector first for that to work? You shouldn't have to, right? My OS selector is not finding Ubuntu :(

Hmmmm.. I have a feeling that if I got Ubuntu to boot again, OS selector might find it. Don't know. I'll try OS selector again.

Thanks for the post!

---

### Post by moerl on 2006-09-20
Nope.. I'm not having any luck with OS selector. I have no idea how to boot to Ubuntu again :(

---

### Post by wkulecz on 2006-09-20
I've always been very leary and burned more oftne than helped by third party stuff that touches the lowest level parts of any system Norton AV has caused me far more grief over the years than all the virii combined!

Anyways, boot your Ubuntu live CD and reinstall grub to the MBR:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
or:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


Then reboot your Ubuntu and edit /boot/grub/menu.lst to add the "Other" stanza to bootup windows, something like:

title     Windows XP
root      (hd0,0)
savedefault
makeactive
chainloader +1

HTH,
--wally.

---

### Post by wkulecz on 2006-09-20
For some reason I've not figured out, the Ghost install of my cloned Ubuntu system wouldn't boot on the final system I set up.  Got an infinite loop of GRUB GRUB GRUB ... printouts on the screen.



I restored it by booting Knoppix 5.0.1 CD and doing the following:

mount the Ubuntu partition:  clicking the /dev/hda1 icon on the desktop mounts the partition on /media/hda1 and opens a file browser (Knoppix is KDE).  Do opposite (right) click on the desktop icon and choose "Change read-write mode"  Answer yes to "make device writable" dialog.


Open a root shell from Knoppix's "penguin" menu.
In this root shell:

cd /media/hda1/sbin
./grub-install --root-directory=/media/hda1 /dev/hda


I then rebooted and had the cloned Ubuntu system running.  Change hda and hda1 above to your boot drive and Ubuntu partition devices.

Presumably you can do this from the Ubuntu Live-Install CD but I'm used to fixing things with Knoppix, although the mount point may be differnet in Ubuntu.

--wally.

---

### Post by moerl on 2006-09-20
You know, I was thinking.. couldn't booting the Ubuntu LiveCD in rescue mode help me out? I tried to get into rescue mode and no matter what I tried, it wouldn't work. I'm sure I was doing something wrong, but I still can't figure out just what it was I was doing wrong.

On the boot screen of the LiveCD where it gives you booting options and MemTest and all that.. it has a small help system that is controlled with the keyboard's F-keys. Now, help keeps mentioning "the command prompt". That drove me insane because there IS no command prompt anywhere in that environment. When you press F6, you do get a command line you can change, but then what? If you hit "start/install Ubuntu" and modify its default command line switches  just say "boot: rescue" nothing at all will work. So just where is this damn command prompt help keeps mentioning? :(

I guess I won't end up using that, but I'd still just love to know how it WOULD work.

The grub reinstallation sounds like a good idea. I'll still end up wanting to use Acronis OS Selector in the end, but if I get Ubuntu into the MBR by means of installing GRUB.. (I'll have to add Windows to GRUB manually as well, I'm guessing..), Acronis OS Selector might finally recognize my Ubuntu installation.

Thanks

---

### Post by moerl on 2006-09-21
So does anyone have an idea of how I could have Acronis OS Selector recognize Ubuntu? It still doesn't. Actually, I guess I'll try reinstalling GRUB to at least make Ubuntu bootable and THEN see if OS Selector can see it.

---

### Post by tuxcantfly on 2006-09-21
no need to use acronis, ghost, or anything, just reinstall grub

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

once grub is installed, you can edit the menu.lst to add windows and ubuntu to the boot options

---

### Post by moerl on 2006-09-21
I'll try that and report back. Thanks.

---

### Post by moerl on 2006-09-21
Ok. I'm booted into the LiveCD right now and reinstalled GRUB. Where are the instructions for editing the menu.lst so that I can add Windows and Ubuntu to the boot options?

Thanks

---

