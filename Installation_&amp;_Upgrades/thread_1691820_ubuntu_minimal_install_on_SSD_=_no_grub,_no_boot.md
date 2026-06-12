---
title: "ubuntu minimal install on SSD = no grub, no boot"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by leespa on 2011-02-20
**System:** i3-540, 4GB RAM, Asus P7H55-M mobo, Intel X25-V 40 GB SSD, GT 430 vid card

**Problem:** I have installed Ubuntu Minimal amd64 [10.10 + 10.04] multiples times without errors. 

After the install completes and asks for 1st boot, however, [B]I do not see anything other than a blinking cursor once BIOS finishes POSTing. 
**No GRUB2, no terminal, NOTHING.**

What I Have Tried / Done:[/B]
-- updated SSD firmware to latest without issue
-- had 'pre-partioned SSD to proper block size through one iteration' without issue; still no boot
-- booted into a LiveCD, mounted the SSD to see if files there; all looks good.
-- booted into a LiveCD, wrote a test file to the SSD using dd without issue
-- used the Manual -AND- Guided Using Whole Disk partioning options in the Minimal Installer
-- danced in a circle whilst booting. No effect.

**-- AND YES; the SSD is the first device in Boot Priority; have also tried AHCI + IDE mode for the device.**

**One Other WEIRD phenomenon:**
-- after 1st successful install it seemed the FlashCARD I used to install the Minimal with got trashed...I know this because when I selected it to boot off of it didn't work. **What did happen though is that it ignored the flashCARD and instead booted off of the SSD...leading me to a Ubuntu 10.10 tty / prompt like I expected to see:confused:** I haven't been able to reproduce this once moved past the first Minimal 10.10 install attempt. Every subsequent attempt since to boot straight off the SSD leads to the blinking cursor that'll sit there doing nothing for an hour.

**So Basically...** at this point I am wondering if there is some disconnect between the mobo and SSD with respect to booting. Grub2 is installed and seems to be intact, but nothing works.

Any ideas?

Thanks in Advance.

---

### Post by oldfred on 2011-02-20
Are you using manual install to specify where grub's bootloader is installed? You flash drive may be promoted by BIOS to sda and then grub installs to that?

To see where everything is at:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by wojox on 2011-02-20
After it reboots hold down the left shift key and bring up the grub prompt. You need to edit the boot kernel line with nomodeset

---

### Post by leespa on 2011-02-20
Thanks for the suggestions guys. I'll have a look. 

I got a similar feedback on xbmc forums. 

PS0: I did an 10.04 minimal install using same procedure but normal HDD and never had any issue...what you detailed makes sense though.

PS1: And yes; the Flashdrive is typically listed first...be a silly problem if that's what is happening. ;-)

PS2: And this would also explain the failed boot from Flash and then booted into the SSD type scenarios. Once the Flash was reformatted it no longer works.

---

### Post by leespa on 2011-02-20
Thanks folks. That was a quick fix.

It was indeed installing the GRUB bootloader to the Flashdrive.

sdd = flash
sde = SSD

I ran through the Expert Install and noticed a brief snippet during the GRUB installation '/dev/sdd'. Backed out; unplugged the Flashdrive; reran installation of the GRUB bootloader and instead saw '/dev/sde'.

It now boots from the SSD - plan to go back and redo the SSD partition alignment since this is now sorted.

Thanks a bunch! Enjoy your weekend.

---

### Post by weaktight on 2011-03-06
I'm having this same problem with Ubuntu Server.  I tried unplugging the USB before it installed GRUB and it said sda... but I'm still getting the blinking cursor on boot.  :(

---

### Post by weaktight on 2011-03-06
Scratch that.  Your fix works, thanks :)

(boot priority was wrong when I tried it initially)

---

### Post by leespa on 2011-03-07
Good to hear that it helped out.

---

