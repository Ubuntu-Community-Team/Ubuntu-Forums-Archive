---
title: "&quot;NTLDR is missing&quot; error when booting Ubuntu 12.04.2 LTS from USB"
date: 2013-05-25
forum: Installation &amp; Upgrades
---

### Post by maggiezzz on 2013-05-25
Hello! I am having an issue that I hope I can describe accurately. I have had Ubuntu 11.04 for many years (so my experience with upgrading/installing Ubuntu is quite limited), and am now trying to do a fresh install of 12.04.2 LTS (32 bit).       When I try to boot the installation from my USB drive, I get the error "NTLDR is missing. Press ctrl+alt+delete to restart" and am unable to proceed. From what I have just read, NTLDR is a loader for Windows NT, so I have no idea why I would be getting such an error while trying to install Ubuntu ... I've never had Windows NT on this laptop (was Vista before Ubuntu).      Here's what I did ....    -- Erased existing files on my 8bg USB drive  -- Downloaded source disc image "ubuntu-12.04.2-desktop-i386.iso" from Ubuntu   -- Used Startup Disk Creator to put the boot file on my USB drive, got a message that the installation was complete and I can now run Ubuntu by booting with USB device inserted   -- Restarted computer with USB inserted   -- Pushed ESC key on startup screen   -- Selected option to boot from USB device   -- Immediately got message "NTLDR is missing, press ctrl+alt+delete to restart" and could not continue with installation  .... Tried several times now to boot from USB - same issue...      Another piece of info that may be pertinent: I left Vista on another partition during the original Ubuntu installation, but was never able to boot it up (some error message that I cannot recall), and chose to ignore it because I didn't end up needing to use Vista anyway. Could Vista on my other partition be causing this error somehow? I was planning to get rid of the Vista partition on this new fresh install.    I would very much appreciate any info on how to get my fresh install of 12.04.2 LTS via USB to work. I am not sure how to proceed since I don't really understand the problem. I've poked around on the forums but was unable to locate a solution. Thanks in advance for your patience and advice!

---

### Post by maggiezzz on 2013-05-25
Hmm... the line breaks in my above post appear to be missing, and I can't seem to put them back in the Edit Post box. Sorry if that's hard to read....

---

### Post by sanderj on 2013-05-26
Your system is NOT booting from the USB stick. So correct that, or create a bootable Ubuntu CD/DVD; maybe that's easier.

---

### Post by Mark Phelps on 2013-05-26
I've generally found that the Universal USB installer made available at PenDriveLinux.com does a better job at creating bootable USB sticks with Linux distros.

The error message you're getting indicates the PC can't boot from the USB so it then goes to the hard drive to boot.

---

### Post by maggiezzz on 2013-05-26
Thanks for the replies. So I take it, something is wrong with my USB itself - somehow incapable of booting Ubuntu, even though the Startup Disc Creator said it was all good?? I will look into purchasing a new compatible USB drive, or some burnable DVD discs for booting, whichever is cheaper.... Thank you all! Much appreciated.

---

### Post by sanderj on 2013-05-26
> **maggiezzz said:**
> Thanks for the replies. 

Or you hardware does not know how to boot from a USB stick. Modern hardware can, but older hardware can be stubborn.

Easy check: put the USB stick in a modern computer and try to boot from it.

---

### Post by maggiezzz on 2013-05-26
> **sanderj said:**
> Easy check: put the USB stick in a modern computer and try to boot from it.    Well, what do ya know... Put USB in boyfriend's laptop and it booted up fine... so my laptop is just too old to boot from USB (2006ish)?  I tried to copy the .iso to my external hard drive and see how that would work for booting up ... Startup Disc Creator lets me select the hard drive, but then the "Make Startup Disc" button is greyed out! Does that leave me with buying DVDs to make a bootable disc?   Thanks again for everyone's help.

---

### Post by sanderj on 2013-05-27
There is still hope for the USB stick: go into the BIOS of the 2006ish computer, and see if you can find "boot order" and "boot from USB".

If not, create a bootable DVD/CD. Oh, and even then you have to tell your computer the boot order: CD should be before harddisk.

---

### Post by prodigy_ on 2013-05-27
Check boot order in BIOS or select boot device manually. Also make sure that your machine has the latest BIOS.

---

### Post by maggiezzz on 2013-05-27
Hi all. I have indeed been trying to get it to  "boot from USB," but it leads directly to the NTLDR error. On startup, I select: "Press ESC to change boot order." This takes me to "Boot Menu: 1. ATAPI CD/DVD ROM Drive; 2. Notebook Hard Drive; 3. USB Hard Drive." I select option #3 for USB hard drive and am immediately taken to the NTLDR error and forced to restart! (However, it boots fine from my USB on boyfriend's newer laptop.) Sooo.. Then I went into SETUP and found that I have BIOS version F.13. I am currently attempting to locate and download the newest version of BIOS for my laptop and will report back to see if that helps at all. :)

---

### Post by maggiezzz on 2013-05-27
I forgot to mention: in BIOS, I also checked the Boot Options under System Configuration, and found that USB Hard Drive is indeed listed and is NOT disabled, i.e. it should be enabled (there is no exclamation mark next to it on the list). Just to see what would happen, I moved USB Hard Drive up the boot list a bit and tried again to boot from it, but still no luck. So, yep, trying to update BIOS as the next step. Although HP doesn't seem to have a BIOS update for my old ass 2006ish laptop... I will see what I can find..... Thanks again.

---

### Post by maggiezzz on 2013-05-27
And the saga continues....!  The HP website does not have a BIOS update available for my system. In order to retrieve my software updates, I have to select my OS (Windows Vista, Vista 64-bit, or XP)... Since Ubuntu obviously isn't listed, the website tells me: "If your operating system is not listed, HP does not have software or driver downloads available for this product in that operating system." Should I try the Vista option, since that's why my computer had installed when purchased? Or might it just be safer/easier to go by a blank DVD for booting....?

---

### Post by prodigy_ on 2013-05-27
> **maggiezzz said:**
> In order to retrieve my software updates, I have to select my OS (Windows Vista, Vista 64-bit, or XP)
Yeah. In order to update my 6510b to F.20 I had to install XP temporarily. :) And, mind you, it was hell even after that because you can't install F.20 on just any previous BIOS. I had F.0E initially, I think, and I had to do 3 intermediate upgrades with a lot of trial-and-error along the way.

But that solved USB boot issues for me.

---

### Post by sanderj on 2013-05-28
> **maggiezzz said:**
> Or might it just be safer/easier to go by a blank DVD for booting....?

Yes.

---

