---
title: "[SOLVED] no boot kernel 2.6.27-2-generic"
date: 2008-08-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lonniehenry on 2008-08-30
I upgraded to the new kernel from 2.6.26 and now the bootup stops at acpi:allow wakeups from S4.  I have tried no splash - freezes at kernal alive screen, no quiet gets me to the line about wakeups and freezes.  Any idea what to try next. I am using 64 bit intrepid alpha 4 -new install on separate partition about a week ago and updated since. Thanks in advance for suggestions

---

### Post by Slug71 on 2008-08-30
Can you get into last working boot or what ever it is?

---

### Post by lonniehenry on 2008-08-30
I booted back to the 2.6.26-5-generic kernel with no problem.

---

### Post by Slug71 on 2008-08-30
Ok, go here [http://kernel.ubuntu.com/pub/next/2.6.27-rc3/intrepid/](http://kernel.ubuntu.com/pub/next/2.6.27-rc3/intrepid/)

install these in this order i think.
linux-image-2.6.27-1-generic_2.6.27-1.1_amd64.deb
linux-headers-2.6.27-1-generic_2.6.27-1.1_amd64.deb

then in the parent directory these in this order
linux-headers-2.6.27-1_2.6.27-1.1_all.deb
linux-libc-dev_2.6.27-1.1_amd64.deb

click on those links and use open with and the default that it want to use and click ok another window will popup and run stuff and just click install.

---

### Post by Slug71 on 2008-08-30
restart, hit update manager and 2.6.27-2 should come in with no probs.

Thats exactly how i upgraded with Intrepid 64.

---

### Post by lonniehenry on 2008-08-30
slug71, I installed the 2.6.27-1-generic as you described and restarted.  It hangs in the boot process in the same place with the same last line as 2.6.27-2-generic kernel. Sure is a puzzle.

---

### Post by Slug71 on 2008-08-30
Sure is a puzzle! Thats what Intrepid did to me with 32bit when i first tried to move to Intrepid which is why i have 64 but never had probs since. I have no idea then, maybe wait till Alpha 5 comes out.

---

### Post by lonniehenry on 2008-08-30
Thanks for helping in the attempt.
L.

---

### Post by ronacc on 2008-08-30
have you tried adding noacpi to the boot line ?

---

### Post by lonniehenry on 2008-08-30
That helped.  I actually used acpi=off and deleted quiet and it loaded.  Now I have the Nvidia low res problem, but I'm calling it a night and will work on it tomorrow. Thanks for your help.

---

### Post by Slug71 on 2008-08-30
> **lonniehenry said:**
> Thanks for helping in the attempt.
L.

No prob, was just gonna say to try acpi-off but i see i got beaten to it.

---

### Post by Slug71 on 2008-08-30
Hit update manager tomorrow and 2.6.27-2 should come in, do a restart and repeat with update manager and some nvidia updates should come in.

Hopefully that should help you.

Not sure if its 173 or 177 that comes in with those updates but if its 173 then enter this

sudo dpkg -i /var/cache/apt/archives/nvidia-177-kernel-source_177.70-0ubuntu1_amd64.deb

If it is 177 though then just try giving your machine a few restarts since that did the trick for someone in a another thread.

---

### Post by lonniehenry on 2008-08-31
I changed the boot by deleting quiet and adding nolapic to the bootmenu.  That allowed it to boot to 2.6.27-2-generic.  Wireless Broadcom and graphics (Nvidia 173) works.
Thanks for all the help.

---

### Post by Nullack on 2008-08-31
Have you followed through and reported a bug?

It isnt about fixing it for you and then forgetting about it - participating and contribution is encouraged.

---

### Post by andyrogers2008 on 2008-08-31
I have had this same problem which I reported in another thread, and have tried altering the boot settings to acpi=off and it worked, but like reported screen has changed to low res, and my wireless broadcom does not work.

My laptop is a HP Dv6285eu, amd Turion 64x2 .

I have already raised this as a bugreport at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262788](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262788) .

Andy

---

### Post by Nullack on 2008-08-31
Andy thanks for the bug. It needs some further info so it can be worked on and I have pointed to some URLs with the details for you.

---

### Post by andyrogers2008 on 2008-08-31
Nullack, thanks for the information.  Iam fairly new to this bug reporting so all help is really appreciated.

Ill have a look at your URL's and get the relevant information where needed.

Thanks

Andy

---

### Post by andyrogers2008 on 2008-08-31
Nullack, I have provided some further information on the bug now, could you just double check this now and let me know if this is sufficient.  I have changed it back to new for the time being.

Thanks

Andy

---

### Post by Nullack on 2008-08-31
Thats a good report now Andy, thanks. Hopefully the issue will be resolved by the kernel team shortly.

---

### Post by lonniehenry on 2008-09-01
Earlier I had solved my problem by deleting quiet and adding nolapic to the bootmenu. That allowed it to boot to 2.6.27-2-generic. Wireless Broadcom and graphics (Nvidia 173) works. This however caused the system monitor to only see one of my cpus.  I then tried other boot options and found that deleting quiet and adding noapictimer solved the problem with no loss of nvidia driver or b43legasy wireless for broadcom and system monitor to see both cpus in a 64 bit intrepid.  (nolapic_timer in 32 bit systems.)
It might give some solution for some systems.

---

### Post by andyrogers2008 on 2008-09-01
thankyou so much lonniehenry, adding noapictimer instead of acpi=off has got my computer booting and everything working with no issues with the kernel.

Bug report now updated to reflect this.

Andy

---

### Post by lonniehenry on 2008-09-01
Glad I could help.  Thanks for filing the bug report.

---

### Post by Martiini on 2008-09-03
2.6.27-2-generic bootup time 3:20 from "Starting up" to working desktop  (HP dv6500 series) (AMD Turion tl-58 )
never had much trouble with kernels < 2.6.25.
it seems to stop @ "Waiting for resume device"

ive attached a bootchart

---

### Post by waspbr on 2008-09-03
it doesn't want to boot in my HP tx1320  either, without the acpi=off  the boot sequence doesn't even start, with the acpi=off it gets stuck with a dark screen with a blinking hifen (top left) just after the boot up progress bar and before the gdm (which I haven't seen yet)

it also didn't load in my desktop either... that's one unfriendly kernel

---

### Post by lonniehenry on 2008-09-03
waspbr,  are you 32 bit or 64 bit?   Try booting with quiet deleted and noapic_timer added if you are in 32 bit.  Try booting with quiet deleted and noapictimer added if you are in 64 bit.  Seemed to work for my 64 bit version for both the 2.6.27.1 and 2.6.27.2 kernels.

---

### Post by waspbr on 2008-09-04
it's a 64 bit laptop so I tried the noapictimer time command, apparently my X, it cannot seem to find my nvidia modules.

---

### Post by ronacc on 2008-09-04
try the fix suggested by nanog on the first page of this thread
[http://ubuntuforums.org/showthread.php?t=909240&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=909240&highlight=nvidia) .

---

### Post by andyrogers2008 on 2008-09-09
There are a couple of test Kernels @ [http://people.ubuntu.com/~smb/bug254668/](http://people.ubuntu.com/~smb/bug254668/) if people want to try them for 2.6.27-3 .

I have tried the amd64 one and mine is now booting as normal, but just hae the problem of the Nvidia display driver not installing because no source is installed.

Goods news then.

Andy

---

### Post by BC7333 on 2008-09-09
> **andyrogers2008 said:**
> There are a couple of test Kernels @ [http://people.ubuntu.com/~smb/bug254668/](http://people.ubuntu.com/~smb/bug254668/) if people want to try them for 2.6.27-3 .

I have tried the amd64 one and mine is now booting as normal, but just hae the problem of the Nvidia display driver not installing because no source is installed.

Goods news then.

Andy

I am now on the 386 generic, got a blank screen while using it now using recovery mode and seems ok so far.  Considering I could not get -2 to even boot, an improvement I 'guess'...

---

### Post by BC7333 on 2008-09-10
> **BC7333 said:**
> I am now on the 386 generic, got a blank screen while using it now using recovery mode and seems ok so far.  Considering I could not get -2 to even boot, an improvement I 'guess'...

The same items that ail in 2.6.27-1 still exist in 27-3

Screen blanking, can fiddle and get into terminal but cant start X

Random freezes

So no perceptible improvement here with 27-3 over 27/1

---

### Post by andyrogers2008 on 2008-09-10
I have downloaded the latest 2.6.27-3 kernels which are pending to be uploaded to the repositeries and for me this bug has now been fixed thanks.

[https://launchpad.net/ubuntu/intrepid/+queue](https://launchpad.net/ubuntu/intrepid/+queue)

Andy

---

### Post by spikenick on 2008-10-23
I have a hp pavillion and the only ways to get this to boot are to press the power button, or to add the acpi=off option too boot. The first is a horrible workaround and the later is not acceptable on a laptop, power config changes, video, and wireless. I am using 2.6.27-7 and am STILL having this problem during the RC, any insight would be helpful.

---

