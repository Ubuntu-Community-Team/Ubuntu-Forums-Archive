---
title: "Installation failure with 13.04"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by AmpersUK on 2013-05-04
[FONT=arial]I downloaded **13.04**. Burned **iso** file to DVD. Ran disk. 

Checked the checksum gave clean bill of health. OK. 

Loaded 13.04. Everything seemed to run smoothly.

Waited till drive door opened, removed DVD.

Fired up the computer.

Received following message, exact case:

[COLOR=#0000ff][B][FONT=courier new]error:file '/boot/grub/i386-pc/normal.mod' not found.
grub rescue>[/FONT][/B][/COLOR]

Computer completely dead.

I repeated the whole operation three times before writing here.

Any clues to what I type in here, please, anyone?

Ampers.[/FONT]

---

### Post by ubfan1 on 2013-05-04
Looks like bug 1155993.  From comment #4, try running update-grub, update-grub2 and grub-mkconfig (just to be sure, it didn't work with only update-grub).

---

### Post by AmpersUK on 2013-05-06
They all gave 'Unknown command'

This is where I typed them:

grub rescue> update-grub
Unknown command 'update-grub'

None of the three worked and all gave the same error message

 Never had this problem in Windows, other than 3.1 but that was long ago.

 I am running on a Samsung RF711 which was OK with 12.10 and 12.05.

---

### Post by fantab on 2013-05-06
Sounds to me like a bad burn. Burn again and use lower burn speed settings. If you have USB drive use it to burn your .iso so that you don't waste DVD's.

---

### Post by AmpersUK on 2013-05-09
> **fantab said:**
> Sounds to me like a bad burn. Burn again and use lower burn speed settings. If you have USB drive use it to burn your .iso so that you don't waste DVD's.

I have tried two burns to DVD and twice to a 16GB USB stick.

I think the boot sector has been destroyed.

Not sure what I can do about it. A pity as my £850 laptop is now a load of scrap metal and I am loathe to dump it.

---

### Post by fantab on 2013-05-09
Have you check the downloaded .iso with [MD5SUM Check]("https://help.ubuntu.com/community/HowToMD5SUM")? 

Did you Laptop come with any pre-installed OS? Newer Machines that come with Windows 8 pre-installed use UEFI and Secure Boot features that require certain manual intervention on our part to install ubuntu/linux.

---

### Post by AmpersUK on 2013-05-09
> **fantab said:**
> Have you check the downloaded .iso with [MD5SUM Check]("https://help.ubuntu.com/community/HowToMD5SUM")? 

Did you Laptop come with any pre-installed OS? Newer Machines that come with Windows 8 pre-installed use UEFI and Secure Boot features that require certain manual intervention on our part to install ubuntu/linux.

Yes, I did a checksum check every time, I always do.

It won't reload Windows from the recovery disk because of the MBR. I am not sure where to proceed from here.

---

### Post by e-Tiggy on 2013-05-09
With computers nothing is over until it's over. :)
If I were you I would try to chroot into the system from the live usb environment and reset grub.
Boot up the usb or the dvd and select "try ubuntu", this can take a few seconds to load up, so wait until you're at the desktop and all. Launch the "Disks" app and look for your main drive's device path. [Here]("http://i.stack.imgur.com/1DMJB.png") is an example where the last drive is selected, in your case you probably want the first hard disk on the list in the left panel. In this case the device path is /dev/sdc and the parttiions follow as /dev/sdc1, /dev/sdc2 and so on. I'm not sure the what partitions the standard ubuntu install creates but you probably gonna have one called swap and another big one - you gonna need the later's path (click on it and you will see it at the bottom next to the "Device" word).
Now launch the terminal app and type the following, hit enter at the end of each line. **Replace the [COLOR="#FF0000"]red[/COLOR] part** with the path you found in the previous step.

```
sudo mount [COLOR="#FF0000"]/dev/sda1[/COLOR] /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev /mnt/dev
sudo mount --bind /usr /mnt/usr
sudo chroot /mnt 
```

In case you get an error something like this: 
```
/bin/bash not fund.
``` 
then type these:

```
sudo mount --bind /bin /mnt/bin
sudo mount --bind /lib /mnt/lib
sudo chroot /mnt 
```

Ok, you are almost done. Type the following, again **replace the [COLOR="#FF0000"]red[/COLOR] part** with the path you found in the Disks app, but this time without the number at the end, we are addressing the MBR of the disk, not the individual partitions on it.:

```
grub-install [COLOR="#FF0000"]/dev/sda[/COLOR]
update-grub2
```

If you got some error like "Can't open /usr/share/grub/grub-mkconfig_lib" then type the following:

```
sudo cp /usr/lib/grub/grub-mkconfig_lib /usr/share/grub/
update-grub2
```

In case you got any other error type these: 

```
grub-mkconfig -o /boot/grub/grub.cfg
```

Now cross your fingers and reboot your laptop. 
If you gut stucked at any point report here back, a lot of us are quite bored at work and are eager to help :)

---

### Post by fantab on 2013-05-09
If you can tell us what you want then perhaps we can help you accordingly. 
Did you download 32bit Ubuntu or 64bit? I don't think 32bit can use UEFI. 
Do you want to Dual boot Windows and Ubuntu? What version of Windows did your laptop come with? If you plan to dual boot then we have get that Windows going first.
Do you just want ubuntu? This could be easy.

Why do you think your MBR is corrupt? By the way if you have Windows8 pre-installed then the good chances are that you don't have MBR. That is why you have to answer those questions I asked? Without you telling us we won't know what exactly is going on.

Perhaps you need a [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair").... It would help us if you can post the output of Boot Info Script, which can be used from Boot Repair.

---

### Post by AmpersUK on 2013-05-09
I found the following.

sudo dd if=/dev/zero of=/dev/hda1 bs=512 count=1

Not 100% sure but it seems to be loading OK. Am encrypting my data so it will take a few hours. If I don't come back tonight, the above code will have worked.

---

### Post by e-Tiggy on 2013-05-10
It seems like this worked for you with 12.04 last year, hope it solves your problems this time as well.

---

### Post by AmpersUK on 2013-05-10
Did it? Oh dear. My problem is I find it difficult to remember last month, last year is impossible. Although I ca  remember the fifties a uite well.

---

### Post by AmpersUK on 2013-05-10
Did it? Oh dear! Trouble is, I can't remember last month, let alone last hear :-( But, I do remem er the fifties and sixties quite well!

---

### Post by e-Tiggy on 2013-05-10
I myself am quite familiar with that feeling :)

---

### Post by JamesProg on 2013-06-23
> **fantab said:**
> Sounds to me like a bad burn. Burn again and use lower burn speed settings. If you have USB drive use it to burn your .iso so that you don't waste DVD's.

Complete nonsense. Here it is June 23, 2014 and I am having EXACTLY the same problem to the letter, not only that the grub-install, grub-mkconfig and others are missing from the installation. It was not a badly burned DVD the DVD was tested and is flawless.

---

