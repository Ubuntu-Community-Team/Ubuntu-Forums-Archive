---
title: "New Grub Dilemmma..."
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by dvice on 2008-01-19
I've gotten down with Grub before but, this is a new one on me... 

Situation: I have a somewhat dated bios with a 160 GB HD that requires a seperate "/boot" partition or I encounter "Grub Error 18" 

So, on this disk I have a "/boot" partition, a second partition with "64Studio" installed, a third partition where I have installled "Ubuntu Studio", a forth partition (for storage or whatever) and a swap partition, as you can see from attached images.


Problem.  The kernel (or kernel images)  for "64Studio" ( /dev/hda6) resides in the "/boot" partition (/dev/hda1) and it boots fine. but, the kernel image for "Ubuntu studio" is on "/dev/hda7" and will not boot though I added Ubunto Studio to  "menu.lst"  as you can see from attached image.

I need the kernel for Ubuntu to reside in the "boot" partition, I believe.   I tried (very carefully) to get it configured that way during install but, it didn't work .

My thought was (and I was about to attemp) to copy the kernel  for Ubuntu studio to the "/boot" partition and and/or maybe create symbolic links (if needed) but, before I do - any help, thoughts, advice would appreciated.

---

### Post by luvr on 2008-01-19
> **dvice said:**
> My thought was (and I was about to attemp) to copy the kernel  for Ubuntu studio to the "/boot" partition
Yes, that's basically the way to make it work. You should, however, copy not only the kernel, but also the initial RAM disk (*"initrd-something"*). Then there's also the system map (*"System.map-something"*) and probably also the kernel config file, though I'm not entirely sure that you will need them.

There's no need for any symbolic links; just make sure that your menu.lst specifies the correct location for the files (i.e., the boot partition).

I used to do it this way. Actually, I created *"/grub/Slackware,"* *"/grub/SuSE,"* etc., directories on my boot partition *(those were the pre-Ubuntu days...),* and copied the files there. The only catch is, when you upgrade (or recompile) your kernel, you will have to copy it manually to the boot partition (and edit your menu.lst).

These days, I still use a small boot partition at the beginning of the disk, and I **could** copy my kernels there (the partition is some 100MB, so it can store a few kernels), but there's no longer any need to do so.

Such a separate boot partition (on which I install a custom GRUB version that I compile from source) still does come in quite handy, since I can reorganise my harddisk (e.g., remove, replace, reinstall, add, etc., any Linux distribution, or even any other Operating System) whenever I want to; as long as I leave my boot partition intact, I can be sure that I won't mess up my GRUB boot loader. (Except, of course, that any Windows reinstall will overwrite the *Master Boot Record*--but that's pretty easy to overcome once you figure it out.)

---

### Post by logos34 on 2008-01-19
dvice,

you might want to take a look [at this]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition").
(--> update-grub script -- scroll down to section 'The main disadvantage of having to use a separate /boot partition')

---

### Post by dvice on 2008-01-20
Thanks for the help!

This problem isn't one that you might encounter often but, you never know, I did, so, heres what I did to get it working.

The best working solution I found was to simply copy the kernel and initrd and nothing else to my "/boot" partition and then add the entry to "menu.lst" and reboot and it worked!


Because of the Bios limitation with the large hard disk, a "Grub" partition wouldn't work and the "boot" partition was needed to get the first OS booted which, in this case, is Debian based "64Studio"  Booting into that first, I was able to mount the partition with "Ubuntu Studio" installed and then  "sudo nautilus" and copy and paste the  kernel and initrd images into my "boot" partition, add the entry to "menu.lst"  and reboot into Ubuntu Studio.

It may not be the best solution but, it works. 

If I need to update or try another kernel I will just do as I did above and deal with it.

This 'old' PIII 1G with a 160GB HD, Pioneer DVD burner, M-Audiophile 2496 can still crank out the tunes so, I won't give up on it as long as it still beeps and whirs.

---

### Post by luvr on 2008-01-20
> **logos34 said:**
> 'The main disadvantage of having to use a separate /boot partition'
The document that you reference talks about the difficulty of *sharing* a single boot partition among multiple Linux systems that you install on a single computer.

For instance, suppose that you use **/dev/hda1** as your boot partition. Now, you want to install a second Linux system onto your computer. If you specify your *existing* boot partition, **/dev/hda1,** as the *"/boot"* location for your new Linux system, then your existing GRUB will get overwritten.

To overcome this problem, I **never** specify a separate mount point for a boot partition when I install a new Linux system; I just let its */boot* directory become an integral part of my new root volume. In addition, I let the new system install GRUB onto the *boot block of the new root partition,* **not** on the Master Boot Record. There are three advantages to this method:
[LIST]
[*]My existing boot partition remains untouched by the new install.
[*]My existing Master Boot Record remains untouched by the new install.
[*]The new Linux root partition becomes *bootable,* so I can simply boot it through *chainloading* from my existing GRUB--which still sits on my Master Boot Record.
[/LIST]
Now, when I reboot my computer, I arrive at my familiar GRUB boot screen. To boot the newly installed Linux system, I can call up a GRUB command line, and type something like the following commands:
```
root (hdx,y)
makeactive
chainloader (hdx,y)0+1
boot
```
(where *"(hdx,y)"* represents the root partition of the new Linux system--substitute *"x"* and *"y"* with the appropriate disk and partition numbers, respectively). That will bring me to the GRUB boot menu that sits on my new root partition.

The main **disadvantage** is, that I will have to **manually** add entry for the new Linux system to my GRUB configuration file, if I want to make it easily accessible. Also, whenever I install a new kernel, I will have to manually edit my main GRUB configuration file, to create an entry for the new kernel. Even so, if I goof up and introduce an error my GRUB configuration file, I can still manually enter the commands to force a chainload.

There's one problem that **dvice** will run into, though: Even if he makes his new root partition bootable, the (ancient) BIOS of his computer will not want to boot it through chainloading. He will have to copy the kernel (and associated files) to his boot partition and update the GRUB configuration file in order to boot the Linux system.

---

### Post by luvr on 2008-01-20
> **dvice said:**
> The best working solution I found was to simply copy the kernel and initrd and nothing else to my "/boot" partition and then add the entry to "menu.lst" and reboot and it worked!
That is, indeed, the best solution, in my opinion.

> Because of the Bios limitation with the large hard disk, a "Grub" partition wouldn't work and the "boot" partition was needed to get the first OS booted 
I'm not sure what you mean with a "GRUB" partition as opposed to a "boot" partition. You are right that, due to the BIOS limitation, you need the "boot" partition, but since GRUB is your boot loader, that partition will also be your "GRUB" partition. Or am I misunderstanding you here?

> It may not be the best solution but, it works.
Again, I believe it actually **is** the best solution, given the BIOS limitation that you have to live with.

> This 'old' PIII 1G with a 160GB HD, Pioneer DVD burner, M-Audiophile 2496 can still crank out the tunes so, I won't give up on it as long as it still beeps and whirs.
I must say your screenshot looks great. I like Kraftwerk, too... :-)
You did notice that there are updates available for your system, didn't you? :wink:

---

### Post by logos34 on 2008-01-20
> **luvr said:**
> The document that you reference talks about the difficulty of *sharing* a single boot partition among multiple Linux systems that you install on a single computer.

For instance, suppose that you use **/dev/hda1** as your boot partition. Now, you want to install a second Linux system onto your computer. If you specify your *existing* boot partition, **/dev/hda1,** as the *"/boot"* location for your new Linux system, then your existing GRUB will get overwritten.

To overcome this problem, I **never** specify a separate mount point for a boot partition when I install a new Linux system; I just let its */boot* directory become an integral part of my new root volume. In addition, I let the new system install GRUB onto the *boot block of the new root partition,* **not** on the Master Boot Record. There are three advantages to this method:
[LIST]
[*]My existing boot partition remains untouched by the new install.
[*]My existing Master Boot Record remains untouched by the new install.
[*]The new Linux root partition becomes *bootable,* so I can simply boot it through *chainloading* from my existing GRUB--which still sits on my Master Boot Record.
[/LIST]
Now, when I reboot my computer, I arrive at my familiar GRUB boot screen. To boot the newly installed Linux system, I can call up a GRUB command line, and type something like the following commands:
```
root (hdx,y)
makeactive
chainloader (hdx,y)0+1
boot
```
(where *"(hdx,y)"* represents the root partition of the new Linux system--substitute *"x"* and *"y"* with the appropriate disk and partition numbers, respectively). That will bring me to the GRUB boot menu that sits on my new root partition.

I misread -- I was thinking dvice was going to combine everything in one /boot rather than just copy the kernel and initrd.

I personally use a dedicated Grub partition, with configfile menu.lst stanzas for other linux distros. (Of course, I can do so because I don't have a Bios limitation).

> The main **disadvantage** is, that I will have to **manually** add entry for the new Linux system to my GRUB configuration file, if I want to make it easily accessible. Also, whenever I install a new kernel, I will have to manually edit my main GRUB configuration file, to create an entry for the new kernel. Even so, if I goof up and introduce an error my GRUB configuration file, I can still manually enter the commands to force a chainload.

Why not just point the entry to the[ symlinks]("http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink")?
> 
There's one problem that **dvice** will run into, though: Even if he makes his new root partition bootable, the (ancient) BIOS of his computer will not want to boot it through chainloading. He will have to copy the kernel (and associated files) to his boot partition and update the GRUB configuration file in order to boot the Linux system.
yes.

---

### Post by luvr on 2008-01-21
> **logos34 said:**
> Why not just point the entry to the[ symlinks]("http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink")?
Hmmm... Interesting idea. Guess I never really considered that option.
I'll sure give it a try!

---

