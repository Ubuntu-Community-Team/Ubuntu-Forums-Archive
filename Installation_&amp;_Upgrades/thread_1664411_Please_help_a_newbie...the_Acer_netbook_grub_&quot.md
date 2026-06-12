---
title: "Please help a newbie...the Acer netbook grub &quot;no such partition&quot; error."
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by byzantophile on 2011-01-10
Hello all.  I am brand new to Ubuntu and really like it.  Please forgive me for posting what I suspect is a problem many others have had...I've been searching this forum for several hours, but can't find a solution that seems to work.  Sorry if this is repetitive, but I just don't understand the fix.

I have an Acer Eee PC 1001PX.  It came with Windows 7 loaded on it.  My friend gave me Ubuntu (I think it was 9.10 but not totally sure) on a flash drive to try, and if I liked it, install.  I tried it, booting from the flash drive, for about a week and then decided this morning to install.

I should have had it replace Windows instead of install Ubuntu on another partition.  My bad--I now realize Windows doesn't like to share power.  Anyway, even with that, the computer did fine booting up with Ubuntu--it offered me a choice of whether to boot with that or Windows.  No problems so far.

This afternoon I was booting up the computer  and guess I accidentally hit the selection to boot Windows instead.  After it tried to boot Windows, nothing would work.  Now I get a blank screen and "error: no such partition," and below that, "grub rescue> ".

My situation is quite similar to this one which was posted a few months ago:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1492072](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1492072)

I cannot access a CD-Rom because this computer has no CD-Rom drive.

I cannot boot from the USB flash drive.  Although I can get in to the settings (via F2) and prioritized the boot-up locations, for some reason it won't boot from there.

No commands will work except for ls, set and insmod.

I have no idea what any of this means--but I tried everything I could do in that thread (and this one, [http://ubuntuforums.org/showthread.php?t=1448479](http://ubuntuforums.org/showthread.php?t=1448479)) but, from what limited amount I understand from these topics, I can't get anywhere unless I can boot from somewhere else--and I can't.

When I type ls here's what comes up:

(hd0) (hd0,msdos4) (hd0,msdos3) (hd0,msdos2,msdos5) (hd0,msdos2,msdos1) (hd0,msdos2,msdos1)

When I type "set" it says:

prefix=(hd0,msdos5)/boot/grub
root=hd0,msdos5

I'm assuming this information is important and I have to set the prefix to something in order for something else to work.

Can anyone tell me what to do from here?  I'd love to get Ubuntu back.

Once again, just to be clear:
[LIST]
[*]I have no CD-Rom drive so I can't load or boot anything from there.
[*]I don't have, and never had, any sort of recovery discs anyway.
[*]I cannot boot from the USB flash drive, even though the computer's settings say that's the preferred source.
[/LIST]

Can anyone help?
:confused:

Thank you very much for your time in reading this.

---

### Post by amsterdamharu on 2011-01-10
Strange that you could boot from the usb before but not anymore now. It would be easier if you can boot your try ubuntu usb and run [the boot info script]("http://sourceforge.net/projects/bootinfoscript/")

First we need to find where grub is installed
type:
set prefix=(hd0,3)/(press tab here)
Does this give you an output?
I am looking for a list that has /boot in the possible values.

Now you could try these commands (here I assume you got boot on (hd0,3):
```
set prefix=(hd0,3)/boot/grub
insmod (hd0,3)/boot/grub/normal.mod
normal
```

If that worked you can try booting Ubuntu (assuming grub and Ubuntu are on (hd0,3))
```
set root=(hd0,3)
linux (hd0,3)/boot/vml(press tab to autocomplete or get a list) root=/dev/sda4
initrd (hd0,3)/boot/init(press tab to autocomplete)
boot
```

---

### Post by byzantophile on 2011-01-10
Thanks, Amsterdamharu, for responding.  I appreciate it.

> **amsterdamharu said:**
> Strange that you could boot from the usb before but not anymore now. It would be easier if you can boot your try ubuntu usb and run [the boot info script]("http://sourceforge.net/projects/bootinfoscript/")

First we need to find where grub is installed
type:
set prefix=(hd0,3)/(press tab here)
Does this give you an output?


Nothing.  I typed "set prefix=(hd0,3)/" and pressed tab...nothing.

I typed the same thing, pressed enter after the /, and I just get another "grub rescue>" line.

> I am looking for a list that has /boot in the possible values. 

Nothing like that came up.

> 
Now you could try these commands (here I assume you got boot on (hd0,3):
[CODE]set prefix=(hd0,3)/boot/grub
insmod (hd0,3)/boot/grub/normal.mod 

I tried this, and after I typed it, it said "error: unknown filesystem."

>  [CODE]set root=(hd0,3) 

Nothing happened, but I did not get an error message.

> linux (hd0,3)/boot/vml(press tab to autocomplete or get a list) root=/dev/sda4 

Nothing happens when I press tab.

I tried pressing enter and it said "Unknown command: 'linux'".

Any thoughts?  Is the computer irretrievably trashed?

---

### Post by Bucky Ball on 2011-01-10
At a cursor (grub rescue>),

```
sudo update-grub

```Did it find Windows? 


If you get beyond grub rescue and to a normal command line, post the output of: 

```
sudo blkid
```

You might also post the result of:

```
uname -r
```I'm taking a guess this is 10.10 with an updated kernel 2.6.35-24? Other guess? Killed the Windows bootloader somehow. That can be reinstalled.

---

### Post by byzantophile on 2011-01-10
Thanks Bucky.

> **Bucky Ball said:**
> At a cursor, 

```
sudo update-grub

```Did it find Windows? 


No.  It said, "Unknown command 'sudo'".

> If not post the output of: 

```
sudo blkid
``` 

Once again, "Unknown command 'sudo'".

I tried "uname -r" and it said, "Unknown command 'uname'".

---

### Post by Bucky Ball on 2011-01-10
I edited my last post when I realised those commands wouldn't work at grub rescue. What about the result of 'update-grub' at the grub rescue? You left that out, the one that should work (without sudo) and your Ubuntu release. 10.10? 10.04 LTS?

---

### Post by byzantophile on 2011-01-10
Bucky, typing "update-grub" at the prompt also results in "Unknown command 'update-grub'".

I'm not entirely certain which version it was but I can find out.  I want to say it was 10.10 but not 100% sure.  My friend loaded it on the flash drive on Dec. 28, so I assume it's pretty recent.

---

### Post by Bucky Ball on 2011-01-11
Did you do an update recently?

---

### Post by byzantophile on 2011-01-11
Meaning, did I install a subsequent update after doing the main Ubuntu installation?  No.  I installed Ubuntu only this morning.

Is there a way to "force" the computer to boot from the USB?  It seems that's the bugaboo, I think I could fix everything if I could only get it to pay attention to the USB flash drive.

I checked the flash drive on another computer--there's nothing wrong with it.  I also checked my boot settings again, and under "Boot Device Priority" the "1st Boot Device" is "Removable Dev."  That's the same setting it was on when it was booting Ubuntu from the flash drive with no problem, while I was doing the trial thing before I did the full installation.

---

### Post by amsterdamharu on 2011-01-11
At what command exactly do you get the "unknown filesystem" error?

I think ls shows you have 5 partitions so if you know on what partition you installed Ubuntu it would be easier.

(hd0,3) means the first hard disk the 4th partition since the first is 0 the second is 1 ....

Now if you know it's on the third partition replace (hd0,3) with (hd0,2) and replace root=/dev/sda4 with root=/dev/sda3

The /dev/sda? is not zero based. Or try out all from 0 to 5 until you get Ubuntu started, then in Ubuntu try to re install grub.

```
sudo apt-get install --reinstall grub2
sudo update-grub
```

---

