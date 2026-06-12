---
title: "Dell Optiplex 320 and Ubuntu 7.10 Not Booting"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by tlongren on 2007-10-24
I believe this is related to [bug # 138305]("https://bugs.launchpad.net/ubuntu/+bug/138305").  Specifically, it's a problem with kernel version 2.6.22, because when I boot to 2.6.20, the machine comes up flawlessly.

I had Feisty on this Optiplex.  Was ready to do a fresh install of Gutsy.  Tried booting from the gutsy CD and got an error similar to this:
> PCI: Cannot allocate resource region 1 of device

At that point, I wasn't aware of the hpet=disable kernel option, so I just decided to boot back into Feisty and do an upgrade.  Upgrade went well, no problems.  That is, until I rebooted.

The system never came up after the upgrade, I now get this error message when attempting to boot:
> PCI: MSI quirk detected.  MSI deactivated.
It just hangs after that.

If I pass the hpet=disable kernel option when booting, it fails with this error:
> [33.068047] PCI: MSI quirk detected.  MSI deactivated.
[33.450583] Clocksource tsc unstable (delta = -296844835502 ns)
[33.466526] Time: hpet clocksource has been installed.
It also hangs at that point, never moves beyond that.

Does anybody have any suggestions for me?  I can't really provide a whole lot more information as I can't get my system to boot.  Has anyone gotten Gutsy to work on an Optiplex 320?

One more thing, I'm using Grub2 (1.95) and booting to kernel version 2.6.22-14-generic.  Again, booting to kernel 2.6.20-16-generic works just fine.

Thanks Everyone!!

---

### Post by Nolroz on 2007-10-25
I've had the same problem attempting to upgrade my optiplex. I have tried both the live disk and the alternate install cd and have had the same result:

cannot allocate resources region 1 device 0000:00:14.0

The optiplex just doesn't like to work with Linux does it??

---

### Post by stevanbt on 2007-10-25
Hi,
I'm having similar trouble with my Optiplex 320.  However, I have managed to sort of upgrade to Gutsy (more by luck by the sounds of it).  

When running 7.04 I had trouble with "PCI Cannot allocate resource" message, but I got round this by using LILO instead of Grub.  The Gutsy upgrade has worked, except for the fact that I'm still on kernel 2.6.20-15 - it will not boot using 2.6.22.

Steve.

---

### Post by jablko on 2007-10-26
Same problem here:

Optiplex 320 running 7.04 with LILO, upgraded to 7.10 using Update Manager hangs at:

PCI: MSI quirk detected. MSI deactivated.

Booting with the old kernel (LinuxOLD) works.

---

### Post by azcoffeehabit on 2007-10-27
see this bug:

[https://bugs.launchpad.net/bugs/138305](https://bugs.launchpad.net/bugs/138305)

It was assigned to a member of the kernel team!

\\:D/

---

### Post by NatMusak on 2007-10-27
> **stevanbt said:**
> Hi,
I'm having similar trouble with my Optiplex 320.  However, I have managed to sort of upgrade to Gutsy (more by luck by the sounds of it).  

When running 7.04 I had trouble with "PCI Cannot allocate resource" message, but I got round this by using LILO instead of Grub.  The Gutsy upgrade has worked, except for the fact that I'm still on kernel 2.6.20-15 - it will not boot using 2.6.22.

Steve.

First post here.  Hope to get some help and looking forward to using Ubuntu. :)

Alright, now Steve...how exactly do you "use" LILO instead of the default Grub?  Do you install it?  Download it from somewhere?  Is it a command prompt command?

I ask because I've tried in vane to install Ubuntu 7.10 on my Optiplex 320. Everything works out well (and fast thanks to a recent RAM 1GB upgrade from 256MB) but when it restarts after installation, Grub loads for 2 seconds and then a black screen with a blinking white cursor is all I see.  I use the guided installation which uses the entire 80GB.  I can give more details if necessary.

If anyone else has an answer, one that could be understood by someone fairly unfamiliar with Linux (though I am a Mac user), I'd really appreciate it.  Sorry if this has been answered somewhere else. I've done a search in this forum and looked up LILO articles but none of it's...computing.

---

### Post by Nolroz on 2007-10-28
yeah, thats an issue with all of the optiplex 320s, you either have to use grub2 (which I havent gotten to work) or lilo

both grub 2 and lilo are alternate boot loaders.  

because nobody has come up with a solution for 7.10 yet, I would consider using 7.04 until they come up with a fix, or a work around.  after the fix comes out, you can upgrade from 7.04 to 7.10 with the built in upgrade utility.

to get lilo working with 7.04, download the alternate install cd, its just as easy to use as the live install cd, but less pretty.  
get the thing started on installing ubuntu, and at some point (I usually wait until after I have allocated drive space)  hit the back button in the install window.  this will take you to a screen with all sorts of options for what to install or do next.  
scroll down and find install lilo, hit that, and you should be good to go from there.  that was the only real issue I have had with the optiplex, although, I must admit, it took me a good week or two to come up with that easy solution.

Let us know if you hear anything about 7.10 or if this doesn't work

---

### Post by NatMusak on 2007-10-30
Nolroz,

Thanks for listing the steps necessary to run Ubuntu.  I'll try this as soon as I get some free time.  While I'm a Mac user at heart, this Dell was free (I don't think it's worth much more than that) and if I can run Linux on it I won't have to deal with Windoz...as much. :D

***UPDATE***

Tried your plan, but I took a chance by using the alternate 7.10 install disc rather than the alternate 7.04 disc...and it worked!  So that saved me from having to upgrade.  It's so fast and customizable, though the flashy effects can't be turned on thanks to the limited graphics on the 320.  While I still prefer Mac OS X Tiger (soon to be upgraded to Leopard) over all other systems, Ubuntu sure as hell has Windoz beat in all its sad incarnations and if I had a better PC, Ubuntu would be an even closer second to the Mac for me. :D

---

### Post by Nolroz on 2007-11-01
good to know that you got it working with the alternate cd.  I tried that first off thinking that was the solution, but I was unable to make it work with mine.  perhaps Ill download it again and give it another whirl.

---

### Post by Nolroz on 2007-11-03
Well, I don't know what was changed in the past few days, but I downloaded a fresh copy of the 7.10 alt install disk (this time I went with 64bit for the heck of it) and lo and behold, it works!

now off to get my wireless working....

---

### Post by jofre on 2007-11-07
Hi everyone, 

I have the same problem. Nolroz,  when you mean no problem, that's using LILO or the default installation with Grub?

Thanks,
Jofre

---

### Post by sfabel on 2008-01-08
Hi,

installed Feisty with grub2 to be able to boot at all. Unknowingly, I rejoiced when 7.10 came out and immediately upgraded. Thankfully I did not remove my old (feisty) kernel, as gutsy now won't boot at all - *unless I choose the old feisty kernel*.

It seems to not detect the SATA drives as it can't find a hard disk to boot into.

I am also getting the above mentioned "MSI quirk" messages. No boot parameter so far has changed any behavior.

If there's anybody out there who could tell me if this is a bug or a missing feature in the new kernel (the latter being less of a problem, since I could always recompile with the option enabled, right?) - PLEASE, let me know. This is really annoying.

Here are the kernel versions.

Feisty (booting using grub2):  2.6.20-16-generic
Gutsy (not booting at all):   2.6.22-14-generic

Now, I don't know if there is an effort made to fix this problem in gutsy or whether I should just re-install feisty.

Any info would be greatly appreciated.

Cheers,
Stephan

---

### Post by jablko on 2008-01-09
I tried tackling this problem again in the new year and found a workaround.

As before, we have a Dell Optiplex 320 on which we installed Feisty and later upgraded to Gutsy when Gutsy was released. We use the lilo bootloader because I failed to get either grub or grub2 working on this machine.

The "Linux" image, vmlinuz-2.6.22-14-generic from Gutsy, fails to boot. Boot hangs immediately after:

```

PCI: MSI quirk detected. MSI deactivated.

```

The "LinuxOLD" image, vmlinuz-2.6.20-16-generic from Feisty, boots successfully.

However I am now able to successfully boot the "Linux" image, vmlinuz-2.6.22-14-generic from Gutsy using the "acpi=off" boot option.

I added "acpi=off" to the "append=" lines in my lilo.conf:

```

--- lilo.conf   2008/01/09 20:33:24     1.1
+++ lilo.conf   2008/01/09 20:49:21
@@ -109,7 +109,7 @@
        read-only
 #      restricted
 #      alias=1
-       append="root=/dev/mapper/juno-root  "
+       append="root=/dev/mapper/juno-root acpi=off"
        initrd=/initrd.img
 
 image=/vmlinuz.old
@@ -118,7 +118,7 @@
        optional
 #      restricted
 #      alias=2
-       append="root=/dev/mapper/juno-root  "
+       append="root=/dev/mapper/juno-root acpi=off"
        initrd=/initrd.img.old

```

---

### Post by Nolroz on 2008-01-11
I tried picking this problem up again in the new year as well, only to find that my ubuntu installation went belly up for some reason.  not discouraged, I decided to reinstall 7.10 from scratch, off of the alternate install disk like I did last time, but I get stuck on

[ 42.485593] PCI: Cannot allocate resource region 1 of device 0000: 00: 14.0 

or something like that.

I think I need to do the 

apci=off boot option or whatever, but I don't know how to add the option to the install.

---

### Post by pablosanchezuy on 2008-01-11
I battled for two days with an optiplex 320, i gave up. 

I read several posts from ubuntuforums and elsewhere and no (simple) fix available.

Greatest and latest don't go in that pc.

Tried slackware 12, kernel 2.6.21 and worked like a charm . I don't like their installer,
but i needed a file server up and running.

Pablo .

---

### Post by drlock on 2008-01-22
There are at least two separate issues with booting the Optiplex 320:
[LIST=1]
[*]**Hangs on loading the kernel.** You need to install LILO or Grub2. Plain old GRUB doesn't work on the 320.  I recommend Grub2. There are some good directions here: [http://ubuntuforums.org/showthread.php?t=409345&page=2](http://ubuntuforums.org/showthread.php?t=409345&page=2) (See post #20)
[*]**Hangs during boot with message about MSI.** Even using GRUB2, the 320 can't boot the 2.6.22 kernel, although it can boot older kernels.  I was able to correct this by disabling acpi.  In /boot/grub/grub.cfg add "acpi=off" to the linux line.
[/LIST]

```

menuentry "Debian GNU/Linux, linux 2.6.22-14-generic" {
        linux   (hd0,2)/boot/vmlinuz-2.6.22-14-generic root=/dev/sda2 ro **acpi=off**
        initrd  (hd0,2)/boot/initrd.img-2.6.22-14-generic
}

```

Hope that helps.

---

### Post by daehenoc on 2008-03-05
I successfully installed Gutsy an a Dell Optiplex 320, you have to use the alternate installer CD, as well as follow the instructions I have just put at the bottom of this page:
[https://wiki.ubuntu.com/DellOptiplex320](https://wiki.ubuntu.com/DellOptiplex320)

You will wind up with a computer that uses the Lilo boot loader, and you have to have a copy of the Ubuntu alternate install disc, but you get a working system!

---

