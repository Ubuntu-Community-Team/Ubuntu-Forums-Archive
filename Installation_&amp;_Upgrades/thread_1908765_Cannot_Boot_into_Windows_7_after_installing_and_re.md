---
title: "Cannot Boot into Windows 7 after installing and removing Ubuntu"
date: 2012-01-14
forum: Installation &amp; Upgrades
---

### Post by emerson1234567890 on 2012-01-14
I'll start from the beginning...

At first I installed ubuntu11.10 via wubi in windows and it failed. (See [Here]("http://ubuntuforums.org/showthread.php?t=1902287"))

Then I tried installing 11.04, 10.10 and 10.04 with wubi again.  Only 10.04 worked.

Next, I don't feel so good about ubuntu being an OS inside Windows but not being an independent OS

So I uninstalled wubi and made a ubuntu 10.04 Live USB stick and installed ubuntu as a dual boot again.

The first boot after installation worked great, so I decided to use Windows for a while.

After I finished using windows after the second-boot after installing Ubuntu, I booted ubuntu again.

And now it says something.  I think it was "Missing Operating System".  It shows GRUB rescue.

So I booted into the live USB stick and removed Ubuntu (The 2 partitions.  One I deleted and the other one I can't delete it.)

And when I booted up my computer again it shows "Partition not found" and it shows GRUB rescue again!

I cannot Boot in either Ubuntu (because I removed it) or Windows 7!

Now when I want to use my computer I have to boot from the live USB stick.

I am typing this in the live session of the live USB stick

What should I do??

I really need an answer because I need to use Windows 7.

Help will be appreciated.

---

### Post by BC59 on 2012-01-14
Install Ubuntu again in the partitions you deleted. Grub will then recognize Ubuntu and Windows.

---

### Post by bcbc on 2012-01-14
You can install lilo (ignore warnings that relate to a different usage of lilo)
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Or if you prefer, you can boot a Win 7 repair CD and install the windows bootloader:
```
bootrec /fixmbr
```

Both have the same affect (replacing the grub2 bootloader, that's pointing at nothing, with a windows style bootloader).

If you are unsure, run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results.

---

### Post by ottosykora on 2012-01-14
the last time I had some mess with booting w7 after I spoiled something during linux install, i used the boot repair disk:

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)


it fixed the w7 mbr itself in seconds, no need for grubr repair or reinstall (your one is missing as you removed the partition where most of the grub code di live in)

---

### Post by emerson1234567890 on 2012-01-14
Thank you everyone!!  Everything has came back to normal.  

[IMG]https://5009935135978500308-a-1802744773732722657-s-sites.googlegroups.com/site/geomazegame/normalwindows7.PNG?attachauth=ANoY7cpjalICZtzGoILnt5TmRXViYHXv8325RvZI_4DU7w2IXPWdkM2nPdDikDqUu8S0gUvc3VdJ4AGQCPdoJObGMZxcjZMYKZNADfrnaVWERkAZQiZnDX52wetS6ob3VsTPezRBpOSsCkpf1Z4AXjCFV2A_jaGSvO49HXpCdrNWIHH7VUq4BuCuIe-G7_N3JpMARYugbnDqtlzhDPoFvK6f_07QxVqybw%3D%3D&attredirects=0[/IMG]

One last question:  Can I safely remove the ubuntu partition?  I cannot remove the old ubuntu partition before but now I can.  I wonder if I remove it will show the GRUB rescue.

---

### Post by bcbc on 2012-01-14
That depends. How did you fix it?

If you fixed it by installing lilo or the windows boot loader, then, yes, you can remove the ubuntu partition. If you fixed it by reinstalling Ubuntu, then, no, you cannot.

---

### Post by emerson1234567890 on 2012-01-14
I fixed using Boot-repair to repair Windows Boot Manager

And I decided not to use Ubuntu as a dual-boot.

I just created a Ubuntu VM decided to use just the VM.

Thanks!

PS I removed the Ubuntu Partition:p:p:):)

---

### Post by ottosykora on 2012-01-15
yes , I was also surprised how fine it works, on the Boot-repair disk there is a generic mbr apparently supplied by syslinux and it works well and without any big interaction to fix it, respectively to replace grub in the mbr.

you can mark as solved the thread

---

