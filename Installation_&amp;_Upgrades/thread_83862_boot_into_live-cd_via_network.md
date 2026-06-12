---
title: "boot into live-cd via network"
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by the-65 on 2005-10-29
Hi everyone,

is there any way to boot into the live-cd via network boot ?

I have ubuntu running on my hp tc1100 tablet pc, which don't has a cd or floppy drive. I want to boot into the live cd to test if everything works fine with breezy badger. It was some work to get everything i need running with linux, so i want to be sure it still works with the new release. Otherwise, i'll have to ask my boss for holidays :)

I already got the net-boot installation running, but i don't want to boot into installation mode but into the live-cd and use an iso-file on my server as a replacement for the missing cd drive.

Any ideas ?

tia
the-65

---

### Post by UbuWu on 2005-10-30
I don't think that is possible. You could try this: [https://wiki.ubuntu.com/ThinClientHowto](https://wiki.ubuntu.com/ThinClientHowto) to try out breezy, but I don't think it will give an accurate experience of what will work with a full install and what not.

---

### Post by the-65 on 2005-10-31
Tnx for your help, but i suppose you'r right and it won't help much.
But i solved my problem by using an empty partition on my tablet pc, where i did a fresh install of breezy badger. All the important things worked like a snap, i only had to add two modules to /etc/modules. So i upgraded my installation and everything worked fine.

tnx again

The

---

### Post by mendieta on 2005-10-31
[QUOTE=the-65]
But i solved my problem by using an empty partition on my tablet pc, where i did a fresh install of breezy badger. 
[/QUOTE]

So, how did you do that ? I am very interested, I have a computer with only one optical drive, running another distro, and the is not working apparently. I have been trying to the Kubuntu Live CD from a partition, following these instructions:

[http://wiki.lunar-linux.org/index.php/Installation:No_CD](http://wiki.lunar-linux.org/index.php/Installation:No_CD)
Section: Booting the ISO from a hard disk partition

It reads:

> 
Your best bet is to free some space at the end of your disk. Make sure this is larger than the lunar iso (somewhere around 350mb). Create a partition and copy the contents of the iso to that partition: 

```

cat lunar-1.5.1-i686.iso > /dev/hda15

```

Once done, you should edit your bootloader (be it windows or grub or lilo) and make it boot the boot sector of the iso. Here's the lilo entry you would need: 

```

other = /dev/hda15
    label = lunar-1.5.1

```

That's it! reboot and select the iso entry, and you're ready to go! The lunar installer should start and everything should work just as good as from a CD! 


But even if I make the parition holding the iso bootable, I have no luck booting from there with Lilo

Any help would be greatly appreciated.

---

### Post by mendieta on 2005-11-23
I am just reposting to see if anyone can help. I saw this question asked several times, and no clear answer. See my post above, but in short: **is it possible to download a CD image and run it (BOOT it) from the hard drive** without using a CD drive ?

Many thanks in advance. Cheers!

---

### Post by yesplease on 2005-11-24
@mendieta: Perhaps this helps

HOWTO: Install Ubuntu Linux without burning a cd - 04-22-2005

[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

or the guide it refers to. Havent tried it myself.

---

### Post by mendieta on 2005-11-24
[QUOTE=yesplease]@mendieta: Perhaps this helps

HOWTO: Install Ubuntu Linux without burning a cd - 04-22-2005

[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

or the guide it refers to. Havent tried it myself.[/QUOTE]

Thanks yesplease!

It's a bit off, and it assumes you have Windows (not my case). With some work I might be able to make it work for me (I am running Mandriva). But what I really want is to boot the bootable iso directly, and run the live CD from HD. At least to test if my DVD drive is really dead.

I'll keep looking around (or just buy a new drive whenever I have the buck)

Thanks again, cheers!
-- mendieta

---

