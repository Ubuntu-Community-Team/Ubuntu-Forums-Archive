---
title: "NTLDR is missing + won't boot from CD"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by jon4thong on 2010-07-20
Hello All,

i am stunned... i don't remember what i did with this old lap top of my, i remember i installed linux on it, then reformatted the HD to NTFS trying to installed windows.  I believed it was successfully installed and never used it since.  just recently, i brought it out and want to install ubuntu.  now when i turn it on, it just give me NTLDR is missing error message.

i have tried putting the window XP cd in, using the ubuntu live cd, tried the "ultimate boot cd" trying to erase the whole drive and repartition.. and it all give me the same error message... NTLDR is missing.  can someone please help?  thanks a lot

---

### Post by whych on 2010-07-20
ntldr is required to boot windows. You can use the xp disk in recovery mode to recover this if you want windows back or you can just install linux.
If you search for 'restore ntldr' you will find many links to windows related sites with details on how to do this.
It sounds also that part of your problem is that you are not booting from any of the cd's/dvd's you are trying.
You need to set the bios to boot from cd.

---

### Post by jon4thong on 2010-07-20
Hello Whych,
 
Thank you for the reply.  I have already made sure the BIOS is set to boot from CD first.  and actually, after reformatting the HD, for the first few times, when i booted without the CD, it gave me the error message, no OS is found.  and this is where i am stuck, the laptop wont let me boot from the CD PERIOD! i have also tried to find the new version of BIOS hoping i can boot from the USB, but there is no newer version.... HELP!!!

---

### Post by pricetech on 2010-07-20
Check the CD and make sure it boots elsewhere.  If so, you probably have a buggy ODD in your laptop.

The message you're getting would indicate that you have a partition on the hard drive, formatted NTFS, but nothing on it.  NT4 and beyond behave that way.  Same thing would happen if you formatted a floppy NTFS and tried to boot to it.

I'd pull the Optical Drive out, clean the compartment where it goes along with the rest of the laptop, then try again.  Hopefully the drive isn't dead altogether.  Oh, and clean the inside of the ODD as well.  Compressed air works well for this.

---

### Post by efflandt on 2010-07-20
Sometimes even if you set BIOS to boot from CD/DVD first, it will not unless you press a specific key shown on the BIOS splash screen during boot.  That is protection against inadvertently getting infected with something on removable media.  The first and only virus I caught was a boot sector virus spread by floppy disks a long time ago (mid-90's).

For Dell computers the key you need to press is usually F12 to select an alternate boot device, or some use Esc.  But the boot splash screen should say.

---

### Post by jon4thong on 2010-07-23
thank you all
i doubled checked with the CD... works fine...
took out the ODD... cleaned it... 
same thing...
and i tried the booting option (for me, it was also F12) .... selected CD to boot... same error message... HELP!

---

