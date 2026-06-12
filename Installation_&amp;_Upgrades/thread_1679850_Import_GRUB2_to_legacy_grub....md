---
title: "Import GRUB2 to legacy grub..."
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2011-02-01
Anybody know how this is done? I know how to edit menu.lst, but I haven't been able to point GRUB to the new disk's GRUB2 correctly yet...

GRUB2 is on its own disk, with 10.04 and W7.

Help?

---

### Post by wilee-nilee on 2011-02-01
> **Moozillaaa said:**
> Anybody know how this is done? I know how to edit menu.lst, but I haven't been able to point GRUB to the new disk's GRUB2 correctly yet...

GRUB2 is on its own disk, with 10.04 and W7.

Help?

What is your set up, what is running grub-legacy. Run this command in Linux to identify all the OS, and name them.
sudo fdisk -lu

---

### Post by Moozillaaa on 2011-02-01
> **wilee-nilee said:**
> What is your set up, what is running grub-legacy. Run this command in Linux to identify all the OS, and name them.
sudo fdisk -lu

Hi wilee...

It's a home build that's running grub-legacy. BioStar TA-790GX 128M, AMD Ath II x2 6400+, 4 x 1G pc5300. The drive is a Maxtor DiamondMax 30G, slave, single IDE channel.

Does hardware really change how GRUB-legacy runs?

I'll get the disk partition list in a few here; I'm repairing the W7 btldr at the moment.

---

### Post by wilee-nilee on 2011-02-01
> **Moozillaaa said:**
> Hi wilee...

It's a home build that's running grub-legacy. BioStar TA-790GX 128M, AMD Ath II x2 6400+, 4 x 1G pc5300. The drive is a Maxtor DiamondMax 30G, slave, single IDE channel.

Does hardware really change how GRUB-legacy runs?

I'll get the disk partition list in a few here; I'm repairing the W7 btldr at the moment.

You say grub-legacy but don't identify the OS, 10.04 is grub2 unless you have downgraded to grub-legacy.

---

### Post by Moozillaaa on 2011-02-01
> **wilee-nilee said:**
> You say grub-legacy but don't identify the OS, 10.04 is grub2 unless you have downgraded to grub-legacy.

I misunderstood there... - you didn't mean what (hardware) GRUB-legacy is ON, you mean what's (OS's) ON GRUB-legacy???

Sorry - Hardy is on GRUB-legacy, and XP. Some other stuff is on extended partitions, but that doesn't matter? (PCLOS '07, FC8, SuSE 11.1)

I DO know how to edit Hardy menu.lst; just how to point Hardy GRUB-legacy to GRUB2 loader on another disk?

Thanks!

---

### Post by presence1960 on 2011-02-01
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by Moozillaaa on 2011-02-01
Run the script from a Live environment, or from Windows? Or from Linux?

This is really getting pretty involved here...

I just need to edit GRUB-legacy, to point it to GRUB 2, on a second disk. 

As the number of posts increases, the chance of desired solution decreases exponentially, with workaround suggestions increasing proportionately...

I just want to chainload GRUBS???

---

### Post by presence1960 on 2011-02-01
> **Moozillaaa said:**
> Run the script from a Live environment, or from Windows? Or from Linux?

This is really getting pretty involved here...

I just need to edit GRUB-legacy, to point it to GRUB 2, on a second disk. 

As the number of posts increases, the chance of desired solution decreases exponentially, with workaround suggestions increasing proportionately...

I just want to chainload GRUBS???

If you want a solution we need to see your set up and boot process.

Let's get a better look at your setup & boot process.**_ Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:_**

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command
Code:

sudo bash ~/Desktop/boot_info_script*.sh

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by oldfred on 2011-02-01
We really need boot script to be able to give good advice. Then we can be specific about drives & partitions as we will know what is where.

This was an old grub entry to boot another MBR. Note that if you boot sdc then that is hd0 and other drives become hd0, hd1 etc.

title       Ubuntu 9.10 Karmic 64 bit @ sdc
root        (hd2)
chainloader +1

But grub2 is so good at finding and setting up installs I stopped chainloading and just use grub2. if you have grub2 in another drives MBR just use BIOS to change & boot that drive.

---

### Post by Moozillaaa on 2011-02-01
Thanks!

Sometimes the easiest stuff gets the best of geniuses (and sometimes dummies like me too!)

Solution (trial from GRUB loader first):

At the GRUB-legacy menu, get to a command line, set root access, direct loader to the GRUB image (core.img), and boot

[FONT=courier new]root        (hdX,Y)[/FONT]
[FONT=courier new]kernel /boot/grub/core.img[/FONT]
[FONT=courier new]boot[/FONT]

TOO SIMPLE!!!

(and of course, load the legacy OS, and edit menu.lst with the new entry for GRUB2!)

---

### Post by Moozillaaa on 2011-02-01
Alas - for any who wishes still to help, all hope is not lost...

Once GRUB2 loads, W7 is prompt to load, once selected. 

10.10 however, has a pause, of about one minute. This I'm sure is a config setting of some sort.

Ideas???

---

### Post by Moozillaaa on 2011-02-01
Oh my - questions galore here...

With GRUB2 chainloaded from GRUB-legacy, will kernel updates of 10.04, loaded from GRUB2, affect booting??? :confused:

---

### Post by Moozillaaa on 2011-07-15
> Oh my - questions galore here...

With GRUB2 chainloaded from GRUB-legacy, will kernel updates of 10.04, loaded from GRUB2, affect booting??? :confused:

Oh my... YES THEY [B]WILL!!!

[/B]Now the GRUB2 menu/ GRUB2 loader, that's chainloaded from GRUB-GOOD (legacy) is all jammed up.

We need GRUB legacy back. GRUB2 is for Windows people, who won't learn, or try.

---

