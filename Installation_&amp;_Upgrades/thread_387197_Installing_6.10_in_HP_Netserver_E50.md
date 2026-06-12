---
title: "Installing 6.10 in HP Netserver E50"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by Sozinho on 2007-03-18
Greetings!
I tried to install Ubuntu 6.10 using an old HP Netserver model E50. The CPU is an INTEL PII 333 MHz. 128 MB RAM. CD-ROM 52X. HD SCSI 9.8 GB. Adaptec 2940i (Aic 7880). But everytime the computer hangs. So I search for help in the web. Used many parameters as I can, like acpi=off, apm=on, noapic, nolapic, etc, following the recomendations that I found in many posts. Nothing work!
The last lines in the screen are always the same:

Registering unionfs1.1.4
loop: loaded (max 8 devices)
squashfs: version 3.0 (2006/03/15) Phillip Lougher
target 0:0:0: FAST-20 WIDE SCSI 40.0 MB/s ST (59 ns, offset 8 )
SCSI device sda: 17773524 512-byte hdwr sectors (9100 MB)
sda: write Protect is off
SCSI device sda: drive cache: write through
SCSI device sda: 17773524 512-byte hdwr sectors (9100 MB)
sda: write Protect is off
SCSI device sda: drive cache: write through
sda: sda1
sd 0:0:0:0: Attached SCSI disk sda

and the computers hangs at that point.
I want to use this computer in order to learn about Ubuntu. do you have any idea what do I have to do?

Thanks in advance.

P.D. Any idea, please? I REALLY need help.

---

### Post by digitalhillbilly on 2007-03-29
Hey Sozinho... Any luck yet? I'm having similar problems here with a HP Omnibook 4100 (PII 266, 96M ram & 4Gb hd). I've tried all the different boot options you listed found from various sites but it's this -> [http://linuxondesktop.blogspot.com/2007/02/installing-ubuntu-6.html](http://linuxondesktop.blogspot.com/2007/02/installing-ubuntu-6.html) <- method that got me the furthest. Method #2.

I can now boot into X and the ubuntu splash screen appears but it hangs a few moments after the window manager starts loading.  I don't know if it's just RAM thats holding me up because the errors I get are generally consistant but on occasion the thing 'll barf up something different. 

Hope you've had better luck than me. If not, check the link above.

---

### Post by Gold3n on 2007-06-11
Any update to these ones guys? I did a search and was happy to see the thread cause this is what I plan to do tonight, but I was quickly sad by the lack of follow up.

Hope you were successful.

---

### Post by Gold3n on 2007-06-13
Well even though I am just replying to myself, I'll let it be known that I had a flawless install of Ubuntu onto my Netserver E60 HP machine.

The only possible issue is that it won't boot directly to the OS. So I have to leave the LiveCD in and tell it to boot from first hard drive. Then it works just fine. 

This maybe due to my OS drive being and IDE "extra" drive and the factor ones (which has Windblows 2003 Ent) are SCSI. I changed the boot order and it just doesn't like it I guess.

Either way it runs and everything seems to be working. I started a Samba install last night and was able to pick i up on my XP machines, I just don't have the user accounts functioning that well just yet.

Good luck to everyone else.

---

