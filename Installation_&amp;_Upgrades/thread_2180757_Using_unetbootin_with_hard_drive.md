---
title: "Using unetbootin with hard drive"
date: 2013-10-14
forum: Installation &amp; Upgrades
---

### Post by rogersma on 2013-10-14
I've got an Asus Eee 1001 px currently running Ubuntu 13.04. It has just 1GB RAM, so many things run slowly.  I've investigated putting a smaller distro such as Puppy/Puppeee on it, but quickly ran into a problem -- I can create the bootable USB, no problem, but cannot find a way to get the machine to actually recognize and boot from the USB (the BIOS doesn't seem to know about it).  I have tested the bootable USB on another machine and it works.

I've heard of two possible solutions -- (1) get Plop and mess with the BIOS, which I'm not really comfortable doing; sounds to me like one small mistake and I'm without a working laptop.  (2) I've also heard that I can use Unetbootin to add a distro to my hard drive.  This sounds more promising for my limited OS skills, but I have seen very little information on doing it this way; every web discussion seems to begin and end with a USB stick/SD card.

I'd appreciate any advice/opinions on which of these solutions is easier and safer.  In the worst case I'll put up with the existing performance issues, but it is awfully enticing to think of having a complete OS sitting in ~60MB RAM.

Thanks for reading.

---

### Post by sudodus on 2013-10-15
I think you should press the ***Escape key*** while booting. Browse the internet for ***eeepc boot from usb*** to get detailed advice.

It is possible to run Puppy and also Lubuntu or Xubuntu in eeePCs. Ubuntu's standard desktop environment may need too much horsepower to run well.

---

### Post by rogersma on 2013-10-16
I have done those things -- that is how I know that the BIOS does not recognize USB devices as possible boot devices.  Because I browsed the exact discussions you mention, I know that others have had the same problem.  However, the usual advice is to use Plop, which as I said in my original post, I am not comfortable doing.

Thus to repeat my original question: is it feasible and safe to use unetbootin on the hard drive to install a different version of Linux alongside Ubuntu?  Or am I better off trying Plop?  Or am I better off living with a slow laptop until I can buy a bigger/better laptop?

---

### Post by sudodus on 2013-10-16
I have installed Lubuntu into eeePCs, but there are different models. It is possible that your particular model won't accept booting from USB, but I would really try a lot before giving up.

I'm not sure but I don't think you can install with Unetbootin on the same hard disk as the the target. If you have two hard disks, you can install from the first disk (the source) to the second disk (the target).

Is it possible to take the hard disk drive out from your eeePC? In that case you can install your Ubuntu flavour operating system, when it is connected to another computer. This is possible because Ubuntu is ***portable*** between computers as long as you avoid installing proprietary drivers and UEFI.

Do you want to keep Windows, or do you intend to use the whole drive for Ubuntu (Lubuntu or Xubuntu)?

---

### Post by rogersma on 2013-10-16
Thanks for responding so quickly.  I bought this particular Asus 1001px from Linucity with Ubuntu installed (back when it was 11.something), so fortunately I have no Windows to worry about -- pure Linux through and through.

Most discussions mention turning off the Boot Booster in BIOS, but mine doesn't have it.  I have tried turning off the boot-from-HDD option, but then I get a message that it can't find a valid boot device.  I get the same message with either USB stick or SD card plugged in.

I like your suggestion to boot from my desktop, as I've been able to boot different distros via USB on it -- would that just be an ethernet connection?  I'll google for discussions on that method.

---

### Post by sudodus on 2013-10-16
Netboot is one possibility, but that was not what I was suggesting. I suggested that you disconnect and remove (lift out physically) the internal hard drive from your eeePC, and connect it ***internally*** or ***externally*** via a USB or eSATA box or a 'USB to IDE & SATA cable' ***to another computer***, for example your desktop computer.

In that computer you do what you would do to install your Ubuntu based system, but select the disk that belongs to the eeePC.

Since you won't need to worry about dual booting, the most straight-forward installation might be to use the [One Button Installer]("https://wiki.ubuntu.com/phillw/OBI"). It will extract an installed system from a compressed tarball. But it will also work well with Unetbootin or cloning with dd. [See this link]("https://help.ubuntu.com/community/Installation/FromUSBStick").

And finally you put your disk back into the eeePC.

-o-

Another alternative is to have your USB drive (or flash card) inserted, reboot and go into the BIOS. There you ***might*** be able to see it as a hard disk drive (actually it is a *mass storage device* configured in the same way a hard disk drive). In that case you can put it at the top of the boot order list to make the computer boot from it.

---

### Post by rogersma on 2013-10-24
> **sudodus said:**
> Another alternative is to have your USB drive (or flash card) inserted, reboot and go into the BIOS. There you ***might*** be able to see it as a hard disk drive (actually it is a *mass storage device* configured in the same way a hard disk drive). In that case you can put it at the top of the boot order list to make the computer boot from it.

This finally was the right answer!  The BIOS does not see the USB as part of the possible boot order, but in a different menu I was able to find the USB as a selection option for a disk drive.  Once I selected it, then I was able to include it in the boot order and go.  Thanks for your responses and patience!

---

### Post by sudodus on 2013-10-24
You are welcome :-)

Finally, when you have finished the installation and it works, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED!

---

