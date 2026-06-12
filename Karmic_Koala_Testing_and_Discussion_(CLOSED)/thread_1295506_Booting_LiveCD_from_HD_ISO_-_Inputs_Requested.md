---
title: "Booting LiveCD from HD ISO - Inputs Requested"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by drs305 on 2009-10-19
I'd still like confirmations.

Edit: Go to Post 11 for the final menu entries.

> 
menuentry "ISO" {
loopback loop /boot/iso/ubuntu-9.10-beta-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-9.10-beta-desktop-amd64.iso
initrd (loop)/casper/initrd.lz
} 



One of Grub 2's touted features is being able to boot Live ISOs from a hard drive. I've had success and frustration and would like other user's experiences.

The success:
Placed the Karmic 64-bit ISO in /boot/iso and added the following entry into grub.cfg (via my custom menu file):
> 
menuentry "ISO" {
 loopback loop /boot/iso/ubuntu-9.10-beta-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-9.10-beta-desktop-amd64.iso 
 initrd (loop)/casper/initrd.lz
}


It works great.

On my laptop, I've tried the same thing and have had absolutely no success. It always drops to Busybox with an 20iso-scan script error saying it can't find sr0. Same CD file structure, same everything as far as I can tell (filenames, etc excepted of course).

I've tried iso-scan, isofrom and several others on the linux line but they all drop to Busybox.

If anyone has had success mounting the 32-bit Ubuntu 9.04 Beta LiveCD ISO, would you please post your menuentry?

Also if you have had success (or not) with the above 64-bit entry or one of your own (please post successes).

Thanks.

---

### Post by VMC on 2009-10-19
I think one of the problems is the initrd. Gparted didn't work because of it. There was a work around, but it was a hideous hack job. Maybe the newest version will work.

 As far as using any Ubuntu livecd , I haven't tried yet. 

Have you tried replacing your:

loopback loop /boot/iso/ubuntu-9.10-beta-desktop-amd64.iso

with something on this line(change hd numbers to your reference):

loopback loop (hd0,1)/boot/iso/ubuntu-9.10-beta-desktop-amd64.iso

Here's a [tip]("http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/") on how I got PartedMagic to boot upsing grub2.

Edit: Another guy's USB [Multiboot]("http://www.panticz.de/MultiBootUSB") - He's has Ubuntu karmic booting.

---

### Post by JustRon on 2009-10-19
When the boot fails and you are dropped at the Busybox could you save the casper.log file and show the output?

So far I had no problems booting LiveCD Isos (tested Ubuntu 9.10 and karmic on several PCs and laptops) from my USB flash drive.

---

### Post by VMC on 2009-10-19
> **JustRon said:**
> When the boot fails and you are dropped at the Busybox could you save the casper.log file and show the output?

So far I had no problems booting LiveCD Isos (tested Ubuntu 9.10 and karmic on several PCs and laptops) from my USB flash drive.

I have one for you to try. [Lubuntu]("http://linux.softpedia.com/progDownload/Lubuntu-Download-50492.html"). I figured out how to loop-back and get it started, but it had some rather bazaar errors that followed, and then an end-less loop.

---

### Post by drs305 on 2009-10-19
@ VMC 

I tried what you suggested last night, and every other variation I could think of. Adding paths, substracting paths, etc. But I think you are on the right track because the Busybox message always said it couldn't find the ISO and that is couldn't find sr0. From what I remember the path it was searching wasn't correct. So I think it's just a matter of getting the right path. 

**Added: **It may even have something to do with me having Ubuntu on sda1 on my desktop and sda2 on the laptop. The fact that it's not sda1 may not be accounted for.

JustRon,

I looked at the log last night but it was late. I'll fire up the laptop and get the log. From what I remember it always hung on line 45 of the iso-scan script, couldn't find the ISO, etc and then mentioned running a chkdsk on the Windows partition, etc.

I'll post it in a bit.

Thanks for the responses.

I've been running gparted and systemrescuecd from my hard drive for a few years and love the convenience. But those aren't ISOs I'm using. It will be nice to get this sorted out.

---

### Post by JustRon on 2009-10-19
> **VMC said:**
> I have one for you to try. [Lubuntu]("http://linux.softpedia.com/progDownload/Lubuntu-Download-50492.html").

I had no success booting it. After a while of loading I landed at the Busybox.

It seems that the live system doesn't support the iso-from parameter because there is no corresponding script under /scripts/casper-premount.

---

### Post by drs305 on 2009-10-19
> **JustRon said:**
> I had no success booting it. After a while of loading I landed at the Busybox.

It seems that the live system doesn't support the iso-from parameter because there is no corresponding script under /scripts/casper-premount.

I couldn't find much about this with an extensive search. I stumbled on iso-scan, iso-from, and IIRC there was one that was hdd something.

Anyway, attached is the casper.log, which mostly says it can't find the ISO.

---

### Post by VMC on 2009-10-19
> **JustRon said:**
> I had no success booting it. After a while of loading I landed at the Busybox.

It seems that the live system doesn't support the iso-from parameter because there is no corresponding script under /scripts/casper-premount.

I found the problem for both Lubuntu and gparted - Both end up with some mallock among other error messages. I said it was convoluted, so if you willing and the minds not weak here is the [discussion]("http://gparted-forum.surf4.info/viewtopic.php?pid=21218#p21218") and fix(hack). 

BTW, this was using gparted-live-0.4.5-3, I downloaded gparted-live-0.4.7-1 and the fix is still not there.

---

### Post by ranch hand on 2009-10-19
I have had no luck with this, so far.  All I am getting is the old song and dance "file not found - hit any key to continue".

And my keyboard doesn't even have and "any" key.  OH WHAT SHALL I DO.  Yes I have been reading other threads in the forums.

Does this need a /.iso/ instead of /iso/ in
                                 "linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-9.10-beta-desktop-amd64.iso"?
 
                            echo "Adding Karmic ISO" >&2
menuentry "ISO" {
loopback loop /boot/iso/ubuntu-9.10-beta-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-9.10-beta-desktop-amd64.iso 
initrd (loop)/casper/initrd.lz
}


 for 64bit
 

 from drs305
 

 What  I did - 1
 

 echo "Adding Karmic ISO" >&2
menuentry "ISO" {
loopback loop /boot/iso/karmic-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ karmic-desktop-amd64.iso 
initrd (loop)/casper/initrd.lz
}
 

 What  I did &#8211; 2
 

 echo "Adding Karmic ISO" >&2
menuentry "ISO" {
loopback loop (hd0,17)/boot/iso/karmic-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ karmic-desktop-amd64.iso 
initrd (loop)/casper/initrd.lz
}
 
After retrieving the beta .iso;
 
What  I did &#8211; 3
 

 echo "Adding Karmic ISO" >&2
menuentry "ISO" {
loopback loop /boot/iso/ubuntu-9.10-beta-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-9.10-beta-desktop-amd64.iso 
initrd (loop)/casper/initrd.lz
}
 

 What  I did &#8211; 4
 

 echo "Adding Karmic ISO" >&2
menuentry "ISO" {
loopback loop (hd0,17)/boot/iso/ubuntu-9.10-beta-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-9.10-beta-desktop-amd64.iso 
initrd (loop)/casper/initrd.lz
}

---

### Post by floborg on 2009-10-20
I've been using the following with "legacy" GRUB to boot Ubuntu ISOs for a while now:

```
title		Karmic Daily i386 (from ISO)
kernel		(hd0,2)/fromiso/vmlinuz iso-scan/filename=/fromiso/karmic-desktop-i386.iso boot=casper quiet splash
initrd		(hd0,2)/fromiso/initrd.lz
```

I think iso-scan only looks one directory deep into the filesystem.  Also, I extract the kernel and initramfs.  Not quite like booting from the ISO, but I don't think GRUB2 + iso-scan counts as actually booting from the ISO either.

---

### Post by drs305 on 2009-10-20
SUCCESS. :P


The 32-bit menuentry ran fine from my sda1-booted machine, but not on my sda2 laptop setup. 

To make a long story short, the line that has to be changed to reflect the proper drive is only the first "loopback loop" line, and you have to make sure of the initrd extension, because it may be "gz" or "lz" depending on which release you are using. If the ISO is contained somewhere on the system partition, it doesn't appear necessary to include the (hdX,X) entry.


[COLOR="DarkRed"]SUCCESSFUL MENUENTRY SAMPLE:[/COLOR]


> 
menuentry "ISO" {
loopback loop [COLOR="Blue"](hdX,Y)/path[/COLOR]/ubuntu-9.10-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=**/boot**/ubuntu-9.10-beta-desktop-amd64.iso **noprompt**
initrd (loop)/casper/initrd.**lz**
} 




NOTE 1: 
(hdX,Y) X is the drive/device; 0 is the first device. Y is the partition number; 1 is the first partition.

NOTE 2:
Make sure you have the proper extension for initrd. It was **.lz** for Karmic but **.gz** for my Jaunty ISO.
You can mount the iso and check the initrd file extension if you want for different releases/versions:
```
sudo mount -o loop /path/file.iso /path/mountpoint
ls /path/isofile/casper
```

NOTE 3:
I had to add **noprompt** to the end of the linux line to prevent a system hang when I tried to "Restart" from the LiveCD ISO. JustRon suggested "noprompt", which worked. See post #17 for the full details.

[B][COLOR="Red"]Please provide feedback on your results using the above menuentry. I'd like this solution confirmed by as many users and with the same or different ISOs as possible so we can be confident in passing on the information.

I'll delay marking this solved while awaiting further inputs.

Thanks for your assistance.[/COLOR][/B]

PS Floborg - Thanks for the input. If I'd seen this before I did more experimenting I might have come up with the (hd0,7) solution/format for Grub 2 a bit faster.

---

### Post by drs305 on 2009-10-20
EDIT: Update to Update. Solved. See post 17.

Update:

One drawback I'm still trying to resolve and need assistance with (in addition to feedback from the previous post) is that once I am finished with the LiveCD I cannot exit without rebooting. 

I've tried "Shutdown", "Restart", "sudo reboot" and all exit the LiveCD but return me to a blank but unresponsive screen. 

Hopefully there is another ooption that can be added to the linux line that will allow successful exit back to a running system.

---

### Post by ayates on 2009-10-20
Worked like a charm for me with today's karmic-desktop-i386.iso.

---

### Post by JustRon on 2009-10-20
> **drs305 said:**
> Hopefully there is another ooption that can be added to the linux line that will allow successful exit back to a running system.

I don't know if it helps you but with the "noprompt" boot option you can disable the "please remove the cd" prompt at the end.

---

### Post by drs305 on 2009-10-20
> **ayates said:**
> Worked like a charm for me with today's karmic-desktop-i386.iso.

@ ayates

Thank you for providing the input on the i386 ISO boot. We you able to successfully exit the LiveCD and return to a grub menu without the computer locking up? If so, what method did you use to exit the LiveCD? Thanks again.

@ JustRon,

I only remember getting that message once but I'll give it a shot the next time I try it.

---

### Post by ayates on 2009-10-20
I did a 'restart' from the upper right corner pull down, hit enter after the 'remove cd' message and it 
proceeded to a normal reboot.

---

### Post by drs305 on 2009-10-21
> **JustRon said:**
> I don't know if it helps you but with the "noprompt" boot option you can disable the "please remove the cd" prompt at the end.

Thanks JustRon - That did it!  :P

On both my 32-bit and 64-bit ISOs, when I tried to restart the screen would blank and nothing would happen. Was not asked to remove the CD. I even tried pressing ENTER from time to time to see if it was waiting for "remove CD and hit ENTER". Didn't work and I was forced to power off the computer and reboot.

Adding "noprompt" to the end of the linux line solved it for me, so now I have no issues remaining.

I'm going back and adding a "noprompt" note to the menu samples.

---

