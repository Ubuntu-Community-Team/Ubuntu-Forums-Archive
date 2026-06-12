---
title: "Boot error - when booting from USB stick"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2011-08-14
Hi all,

I made 2 4Gb USB sticks in Win7, one with Ubuntu 11.04, and the second with Ubuntu 10.04. But I all I get is a "Boot error". Nothing else. 
I did change my booting order in the BIOS, to accommodate the USB stick.

When I made them I dissactivated my antivirus. 

While I was running the Universal USB Installer it told me it didn't have enough space, but it had already done its task (I think it was formatting the USB drive), then proceeded to the second last task, it finished it ok.

Why could I be getting this error?

Thanks guys,

JDL

---

### Post by varunendra on 2011-08-15
The message most probably means either your USB stick wasn't detected or is not bootable.

If your BIOS has a boot-time boot-device selection menu (most of the BIOS' have it, mostly on the F9, F10, F12, Esc or F8 keys), bring it up by pressing the relevant key and see if your USB key is listed as an option to boot from. If it is listed but still doesn't boot after selecting it from there then it is not bootable. In that case, try manually formatting it to FAT16 (it currently should be in FAT32 format) and retry with the universal installer. Or recreate it with [Unetbootin]("http://unetbootin.sourceforge.net/") this time.

If it is not even detected in the list then either your BIOS does not support booting from USB key, or the key is not getting enough time to get detected. I assume by your mentioning of 'changing boot-order to accommodate USB stick' that the BIOS has a discrete option for booting from USB keys. So now only the other reason is left, i.e., short detection time. In that case, see if there is an option to delay the USB detection time in BIOS. If there is, set it to 5 sec. If there's no such option, try hot-rebooting twice or thrice.

One more thing- If both of your USB sticks are of same brand and model, you may need to try another brand. I've seen many kingston and some other not-so-popular brand/models not being able to boot a computer.

---

### Post by javierdl on 2011-08-15
That was great varunendra :)
I'm sure all this information will come very handy. 
I'll have to wait until tomorrow to try it though :(

Thanks a million varunendra :)

JDL

---

### Post by C.S.Cameron on 2011-08-15
As an alternative to Universal try usb-creator.exe, it is located in the Ubuntu iso.
Unetbootin also makes bootable flash drives.
Other people have had problems with Universal.

---

### Post by javierdl on 2011-08-17
Thanks for joining the help C.S.Cameron :)
I just tried USB Creator, the problem I have is it doesn't see my USB stick :( I had just formatted it with Win7's Win Explorer. At the top part of USB Creator I can choose the ISO file without a problem, but on the lower part where one is to find the removable disk, there's nothing in that window. I can see my USB drive in Win Explorer though. 
Also, when I'm in Ubuntu, it doesn't mount the USB stick. Maybe it's this type of USB stick :(
It's a [Lexar JumpDrive TwistTurn 4Gb]("http://www.lexar.com/products/lexar-jumpdrive-twistturn-usb-flash-drive?category=214"). Staples had'em on special, 3 for $19.99.

I just used the Univ USB Installer again, at least it does see my USB stick. Supposedly it did the installation successfully. I'll try it now.

JDL

---

### Post by javierdl on 2011-08-17
Finally!
This time I moved the USB stick all the way to the top in the order in which the drives are read in the BIOS. I had it after the 2 HDs I have before.
Now we know this Lexar USB stick can be used reliably for this purpose.

Thanks a lot guys :)

JDL

---

