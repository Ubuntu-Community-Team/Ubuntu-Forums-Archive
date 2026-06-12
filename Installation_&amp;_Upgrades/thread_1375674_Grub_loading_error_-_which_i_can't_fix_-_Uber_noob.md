---
title: "Grub loading error - which i can't fix - Uber noob needs help!"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by enterprisemusic on 2010-01-08
Hi everyone - I have seen this problem on the forums before, but in all cases there have been other circumstances, such as dual boot with windows, and peoples live cds still working, but here goes...

I have recently made the transition from windomws to Ubuntu 9.10 Karmic Koala, and on install, seemed to have everything up and running as normal. But ran in to a wireless driver problem, which involved a re-instalation.

After the reinstallation I had the OS up an running fine with wireless, and then I come to open my lappy today (Dell Inspiron 1525, 1.86Ghz, 4GB, 80 GB HD) and it loads through Bios then enters a grub loading error to the prompt:

GRUB loading.
error: file not found
grub rescue>

I have seen this problem on forums all over, and have attempted many remedies, though my main problems are...

My laptop is a solo boot, one partition running Ubuntu 9.10
Both my 9.10 and 9.04 live cds will not work, even when boot from disc is selected in bios

Are there any specific commands I have to type in to the GRUB prompt to resolve this issue? 

I hate to sound like a dumb *** when it comes to this, I have been born and bread on Windows, just in recent months have I discovered the power and freedom of Ubuntu, as well as the amazing assistance everyone online provides, and I am trialing it out before forcing it upon all my staff around the country. Just hope this isn't a major issue.

Cheers guys, I hope you can help me.

---

### Post by darkod on 2010-01-08
I haven't tried it unless booted from the livecd, but you can try the same procedure at this grub rescue prompt.
First try
sudo fdisk -l

to list your partitions. Confirm which is your ubuntu root partition. On solo boot you would usually have /dev/sda1 as root, and logical /dev/sda5 as swap. If that's the case, try mounting root and reinstalling grub:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

As I said, I haven't tried it like this and have no idea if it will work. Alternatively, google for "reinstalling grub from grub rescue prompt" or similar.

---

### Post by llawwehttam on 2010-01-08
The grub prompt uses different commands to the terminal.

Your problem sounds quite serious as if you cannot boot from the live cd I am guessing that you cannot reinstall.

The most likely problem is that your hard drive is failing as a bad drive can cause the live cd to crash when booting if it tries to mount it.

Try booting with the hard drive unplugged and see if it boots. If so then it is the hard drive causing the problem. Other than that I have no idea.

---

### Post by enterprisemusic on 2010-01-08
I tried the sudo command, but as just mentioned, Grub uses a different command structure, and the error:

Unknown command 'sudo' comes up

As for removing the hard drive - will that not cause the computer to fail on load anyway, by removing the BIOS?

I am at a loss for this - and I would hate to have to go back to windows :(

---

### Post by llawwehttam on 2010-01-08
The BIOS is NOT on the hard drive. The BIOS is embedded in the motherboard and is what controls everything else ( such as the hard drives, cd drives etc).

In the GRUB prompt type 'help' to see a list of commands. I'm guessing you have GRUB2 which I have had little experience with. 

You could always try [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) as If your hard drive is not dying ( it sounds like it is) the the MBR could be broken.

---

### Post by drs305 on 2010-01-08
From the Grub 2 rescue prompt, type:
```

ls

```
Does it list your two partitions? Perhaps:  (hd0) (hd0,1) (hd0,5)

If so, type (change to match the values found above for your system partition):
```
ls (hd0,1)/
```
That normally would display the system folders, and at the end hopefully you will see "vmlinuz" and "initrd". You can also try "ls (hd0,1)/boot". 
If you can find the "vmlinuz" and "initrd" files,  you should be able to boot into Ubuntu, using the Command Line boot instructions found here: [https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode")

---

### Post by darkod on 2010-01-08
> **enterprisemusic said:**
> I tried the sudo command, but as just mentioned, Grub uses a different command structure, and the error:

Unknown command 'sudo' comes up

As for removing the hard drive - will that not cause the computer to fail on load anyway, by removing the BIOS?

I am at a loss for this - and I would hate to have to go back to windows :(

No, BIOS is on your motherboard. In theory, you can start a computer without hdd, and even run OS from usb stick these days, etc.
Just remember this: NEVER UNPLUG/REPLUG INTERNAL HDD WHILE PC IS RUNNING!!!! It's one of the ways to kill it. Unless specifically designed, you can't connect/disconnect hdds with the computer powered on.

---

### Post by llawwehttam on 2010-01-08
> **darkod said:**
> No, BIOS is on your motherboard. In theory, you can start a computer without hdd, and even run OS from usb stick these days, etc.
Just remember this: NEVER UNPLUG/REPLUG INTERNAL HDD WHILE PC IS RUNNING!!!! It's one of the ways to kill it. Unless specifically designed, you can't connect/disconnect hdds with the computer powered on.


For instance I run an entire FreeNAS without a boot hard drive. The OS boots from a 1GB usb which then mounts the storage hard drives.

I have hot swapped a hard drive before and it failed within 5 minutes so I learned my lesson there!

---

### Post by enterprisemusic on 2010-01-08
> **drs305 said:**
> From the Grub 2 rescue prompt, type:
```

ls

```Does it list your two partitions? Perhaps:  (hd0) (hd0,1) (hd0,5)

If so, type (change to match the values found above for your system partition):
```
ls (hd0,1)/
```That normally would display the system folders, and at the end hopefully you will see "vmlinuz" and "initrd". You can also try "ls (hd0,1)/boot". 
If you can find the "vmlinuz" and "initrd" files,  you should be able to boot into Ubuntu, using the Command Line boot instructions found here: [https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode)


I tried this, 1s comes up as an unknown command, as does help - so I am unable to determine system partitions or reboot to a specific partition using those commands. Though from what I reca.l they are (hd0, 1) and (hd0,5) respectively - which I believe is the common designations.

The 1s boot didn't work either :(

Sorry to sound like a bit of an amateur in regards to BIOS, I'm not that technically minded in some respects haha I have since removed my hdd and tried a reboot, ensuring cd/dvd drive gets priority boot, I have tried both my 9.10 and 9.04 live disks and neither work (of which both were working fine previously) and now it is coming up with the following:

No bootable devices--strike F1 to retry boot, F2 for setup utility, press F% to run onboard diagnostics.

I have run diagnostics, and everything is coming up as a pass - just the lack of an internal hdd - I'm at a brick wall again - any ideas?

---

### Post by presence1960 on 2010-01-08
> **enterprisemusic said:**
> I tried this, 1s comes up as an unknown command, as does help - so I am unable to determine system partitions or reboot to a specific partition using those commands. Though from what I reca.l they are (hd0, 1) and (hd0,5) respectively - which I believe is the common designations.

The 1s boot didn't work either :(

Sorry to sound like a bit of an amateur in regards to BIOS, I'm not that technically minded in some respects haha I have since removed my hdd and tried a reboot, ensuring cd/dvd drive gets priority boot, I have tried both my 9.10 and 9.04 live disks and neither work (of which both were working fine previously) and now it is coming up with the following:

No bootable devices--strike F1 to retry boot, F2 for setup utility, press F% to run onboard diagnostics.

I have run diagnostics, and everything is coming up as a pass - just the lack of an internal hdd - I'm at a brick wall again - any ideas?

The command is ```
ls
```
that is a lowercase L not  the number 1. Try it again!

---

### Post by enterprisemusic on 2010-01-08
DOH!!! Now we are getting somewhere...

the command ls (hd0,1)/ brought up my drive contents as follows:

./ ../ lost+found/ var/ etc/ media/ cdrom

neither of the folders you mentioned before, any ideas what to do next please. I really appreciate the help.

---

### Post by drs305 on 2010-01-08
> **enterprisemusic said:**
> DOH!!! Now we are getting somewhere...

the command ls (hd0,1)/ brought up my drive contents as follows:

./ ../ lost+found/ var/ etc/ media/ cdrom

neither of the folders you mentioned before, any ideas what to do next please. I really appreciate the help.

At the end of the folders list were there "vmlinuz" and "initrd"? They may look like just other folders. Anyway, try booting with these lines:  (X,Y) would be your system partition (sda1, etc)
If it's working, when you enter the linux and initrd lines there will be a pause and then an entry within [ ]. There are pix here:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode")

```

linux /vmlinuz root=/dev/sd**XY** ro
initrd /initrd.img

```
Then CTRL-X

---

### Post by enterprisemusic on 2010-01-08
No folders for either of them :(

And both linux and initrd come up as Unknown commands.

I did a little scooting about to find some more info, not to much luck, but I did find another command that works on the prompt

grub rescue>

when I type set it comes up with the following:

prefix=(hd0,1)/boot/grub
root=hd0,1

Now I'm no expert, but I'm guessing that os telling Grub where to find the boot files - and as previously with the ls command, there is no boot or grub folder on hd0,1? Is that correct?

Other than the 'set' and 'ls' commands everything else is coming up with unknown command - even help!? The only other command I have found that can generate a different response is 'insmod' - but as I have no address to reference to the install I am unable to tell this what to do.

Any ideas?

---

### Post by drs305 on 2010-01-08
enterprisemusic,

Read through the entire rescue mode section in the community doc. If the commands are not working, you may need to also run the "set prefix=" command detailed in the doc. 

There are several methods to try to boot from the rescue prompt. The first one uses less commands but the second one in the doc will give a better chance of finding the kernel.

---

