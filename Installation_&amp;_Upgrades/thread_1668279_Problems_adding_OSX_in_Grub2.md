---
title: "Problems adding OSX in Grub2"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by JohnFante on 2011-01-16
I have a triple boot setup (Windows 7, Ubuntu 10.10 and OSX - latest iATKOS s3) on a RocketRaid3560 hardware raidcard (to raid0 arrays :-)). Windows 7 and Ubuntu (my primary OS) is on the same array (dev/sda) and OSX on the other (dev/sdb). Two separate discs for each.

I can boot Windows 7 and Ubuntu using grub2 as the bootloader (on MBR). And when I set OSX as boot partition on the raidcard it loads nicely (and really fast!).

I would like to use Grub2 as my bootmanager that loads Windows, Ubuntu and Chameleon -> OSX. OSX (which the Grub2 automatically adds) comes up in Grub2 but gives me an loading error when I use it. Something like: No such device: 7e329388d2db2214. As far as I can see this is a normal Grub2 problem.

Instead I have tried to make a custom entry in grub. I searched a bit and found an entry that should work. but not on mine. The entry is: 

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "MacOS X, chameleon, multi" {
         insmod hfsplus
         set root=(hd1,gpt2)
         multiboot /boot
}

menuentry "MacOS X, chameleon" {
         insmod hfsplus
         search --file --set=root /boot
         multiboot /boot
}
```

When I select it in grub I get the following errors:

The first entry:
error: couldn't open file.

The second entry:
error: no such device: /boot.
error: couldn't open file.

Any suggestions?

---

### Post by JohnFante on 2011-01-17
Bump :-)

---

### Post by TechnoMonkey76 on 2011-01-17
I would forget the second entry for OS X that you're using. ;)

Also, your first one likely can't open the file because you're trying to either use a partition that is not GPT or because it is GPT but you aren't inserting the "insmod part_gpt" line.

Typically, if you tri-boot with WINDOWS, get rid of "gpt" before the partition number.  However, Windows is on an entirely separate drive from OS X for you.  Therefore, you may have a GPT formatted drive indeed for OS X.

Personally, IIRC, I used:
```
insmod hfsplus
set root=(hdX,Y)
multiboot /boot
```

If you really use a GUID partition table (GPT) as opposed to MBR (which is required with Windows on the same drive), you'd need to do this:
```
insmod hfsplus
insmod part_gpt
set root=(hdX,gptY)
multiboot /boot
```

Note the insmod part_gpt must be included if it is a GUID partition table, and if it's not, you don't use GPT anywhere!

Please try this.

---

### Post by JohnFante on 2011-01-18
Thank you for the reply :-)

I changed my custom grub entry to:

```
menuentry "MacOS X, chameleon, multi" {
         insmod hfsplus
	 insmod part_gpt
         set root=(hd1,gpt2)
         multiboot /boot
}

```

That didn't help. I still get "error: couldn't open file."

My second drive (array) have a GUID partition table. I have attached scrren-dumps of my two drives so that you can see the structure. Sorry for the danish language!

Thank you again for your help!

---

### Post by TechnoMonkey76 on 2011-01-18
> **JohnFante said:**
> Thank you for the reply :-)

I changed my custom grub entry to:

```
menuentry "MacOS X, chameleon, multi" {
         insmod hfsplus
	 insmod part_gpt
         set root=(hd1,gpt2)
         multiboot /boot
}

```

That didn't help. I still get "error: couldn't open file."

My second drive (array) have a GUID partition table. I have attached scrren-dumps of my two drives so that you can see the structure. Sorry for the danish language!

Thank you again for your help!

Sorry for the relatively late reply.

I am not completely sure, but are you sure Chameleon installed correctly?  If you aren't using Chameleon, I'd try it; that entry has worked with Chameleon for me when I had a GPT hard drive, and the non-GPT one worked with me for my current config.  Double-check that the file "boot" is on the root of your HFS+ partition, then if it is, boot using something else and try to use Chameleon instead if you aren't already using it.

---

### Post by TechnoMonkey76 on 2011-01-18
> **JohnFante said:**
> Thank you for the reply :-)

I changed my custom grub entry to:

```
menuentry "MacOS X, chameleon, multi" {
         insmod hfsplus
	 insmod part_gpt
         set root=(hd1,gpt2)
         multiboot /boot
}

```

That didn't help. I still get "error: couldn't open file."

My second drive (array) have a GUID partition table. I have attached scrren-dumps of my two drives so that you can see the structure. Sorry for the danish language!

Thank you again for your help!

Sorry for the relatively late reply.

I am not completely sure, but are you sure Chameleon installed correctly?  If you aren't using Chameleon, I'd try it; that entry has worked with Chameleon for me when I had a GPT hard drive, and the non-GPT one worked with me for my current config.  Double-check that the file "boot" is on the root of your HFS+ partition, then if it is, boot using something else and try to use Chameleon instead if you aren't already using it.

EDIT: Whoops, how do I delete my double-post?

---

### Post by JohnFante on 2011-01-20
I have reinstalled my iATKOS S3v2 install with the default bootloader (AsereBLN which is a fork of chamerelon r2, rc4)  and everything works fine on the Mac side. 

Unfortunately grub2 still will not load. Still "error: couldn't open file.".

The same error as when I used the latest Chameleon r2 rc5.

Maybe grub2 just doesn't like my RaidCard.

Thanks for the help thou. Hopefully some day I will solve the problem. Hope it is soon. OSx runs very nicely n my setup ...

---

### Post by JohnFante on 2011-01-29
I changed my OSX install to the latest iBoot+MultiBeast setup. Works very nice and way better than iATKOS.

Unfortunately I still have the same boot grub problem.

Besides that Chameleon (the OSX bootloader) dos not see my Win7, Ubuntu 10.10 setup so the finger keeps pointing to the RaidCard.

Btw. I have put the card up for sale on ebay. Works very well but I am not getting 24 HD's anytime soon ;-)

---

### Post by HarmCla on 2011-07-21
Hello,

I know I am a little late with this, but I believe I found the answer to your problem :)
I have a GPT, non-RAID partitioned disk, and I have this entry for putting my Chameleon RC4 bootloader inside my GRUB2 menu:

```

menuentry "Chameleon" --class osx --class darwin --class os {
    insmod part_gpt
    insmod hfsplus
    set root='(/dev/sdb,gpt5)'
    [COLOR=Red]search --no-floppy --fs-uuid --set=root c7ed1e3b4e6c827b[/COLOR]
    multiboot /boot
}
```
I took most of the lines from the automatic generated Mac entries when doing *sudo update-grub*,
and I added the *multiboot /boot* line that TechnoMonkey76 gave.
**Notice that the extra red line is essential, because it solves the *error: couldn't open file* problem (for me).** :)

---

