---
title: "Installation hanging"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by sobewebmaster on 2006-11-22
Ok... This is the setup of the machine:
Motherboard      AOpen AX6B Plus
Processor  	 Intel Celeron 366MHz  	
Memory (RAM)  	 336MB SDRAM
Graphics 	STB Velocity 128 4MB PCI vid card
Harddrive(s) 	SCSI IBM 9GB
Monitor(s) 	Packard Bell 14" CRT
Soundcard 	ISA Creative Labs Sound Blaster 8-bit

Windows XP Professional was the last OS on the machine. And WinXP Pro will install with NO issues. However, I throw in the Ubuntu CD, it posts, states SCSI Bios installed, and then loads the Ubuntu CD. This is a burnt CD image burnt with MagicISO. Anyway, I click Start or Install Ubuntu from the menu, and it says OK for the 1st thing it shows at the bottom, then it gets to Loading Root or something like that and hangs.

Now, I read some posts earlier about burn speeds of 4x and such. I burnt @ 32x..... Could that be the issue?

Keep in mind I am a noob in the world of Linux. I was told Ubuntu would be a good place to start learning.

---

### Post by Bartender on 2006-11-22
Yeah, the general rule of thumb is to burn as slowly as you can.  Even at 2X, that little laser is busy.  680 MB is a LOT of little pits to burn.  As the speeds go up, the chances of error increase.

Check the download's md5 against the checksum on the download website to make sure the download is OK.  If it is, burn it slow, use good quality media, and use the "Check CD for Errors" function.

---

### Post by PurplePenguin on 2006-11-22
Do you have problems loading other live cds?  Some motherboards from big manufacturers have certain settings (that can't be changed!) that aren't very friendly to some live cds.

The most likely problem is an error with the CD, as Bartender mentioned.

Don't get frustrated, though.  Ubuntu is a great place to start learning!  You will come up against some small obstacles every now and then, though.

---

### Post by sobewebmaster on 2006-11-22
Oh no worries. I have heard good things about Ubuntu. When I have time I'll burn @ 2x later and let you guys know how it goes :)

I wanted to get a feel for it. As I know many people run game servers off of Linux running Wine to emulate Windows programs to run the dedis. And I wanted to see how much better a Linux game server would be compared to Windows.

---

### Post by futz on 2006-11-22
As I said in another thread:

I wouldn't worry too too much about the burn speed thing. Bad burns are not super common these days, as long as your burner is good and your blank media is of decent quality. Burning CD-R's at 2X? That's just crazy! :rolleyes: What kind of primitive, savage equipment are you guys running? If you want to be extra careful, burn at a nice slow 24X for an extra safe, quality burn.

> What might help (has helped me) on a funky install is installer boot options like noprobe and/or nousb. There are other options too, like noapic and a bunch of others I can't remember.

Try noprobe for that Detecting Hardware problem. Might not work, but it can't hurt to try it. All it costs is time.

I had one box where I couldn't install Dapper at all without the nousb option. With the option the install behaved perfectly. Only thing is, you can't use a usb keyboard during the install with that option. Just temporarily plug in a spare PS2 keyboard for the install. Once you've finished installing, unplug it and use your usb one again.

---

### Post by sobewebmaster on 2006-11-23
Well, I press install, left for town, was back about 30min. later and it was still on that same 2nd process about mounting file system or whatever.

And it always stays there.

---

### Post by sobewebmaster on 2006-11-23
Ok, I burned @ 2x, then it STILL stopped at the "Mounting File System". Afterwards, I saw an "Alternate Disk", I downloaded, burned, and it booted up on the pc. I choose US language, USA as country, and select keyboard layout, then it gets to Detecting CD-ROM and goes through that just fine, but after that.... The blue screen stays with nothing else moving..

This is starting to get a bit irritating <_< lol. Any other solutions?

The one thing I think, is that it is not detecting the single IBM Serial SCSI hard drive. But, I'm not familiar with this, so I won't say for certain.

---

### Post by sobewebmaster on 2006-11-24
Anyone have any ideas on why it hangs?

---

### Post by PSyMastR on 2006-11-25
I get the same problem too...

---

