---
title: "No Grub, after post - Not Booting"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by everythingsround on 2010-10-26
Both on a 10.04 and a newly installed 10.10:

After BIOS post, I get no grub and just a blinking index in the upper left. I've left it for hours, never boots.

How can I resolve this without getting any Grub boot options?  Any help would be greatly appreciated, and I am more than happy to elaborate any bit of my situation to help.  Thanks

---

### Post by drs305 on 2010-10-26
> **everythingsround said:**
> Both on a 10.04 and a newly installed 10.10:

After BIOS post, I get no grub and just a blinking index in the upper left. I've left it for hours, never boots.

How can I resolve this without getting any Grub boot options?  Any help would be greatly appreciated, and I am more tan happy to elaborate any bit of my situation to help.  Thanks

Normally Grub2 is going to present some type of message, which may mean G2 has already passed control over to the kernel.

Try holding the SHIFT key down during the initial stages of boot to see if the Grub menu displays. If it does, highlight the first Grub menu item, press "e" to enter the EDIT mode, and then cursor to the end of the "linux" line.

Replace "quiet splash" with "nomodeset"  (no quotes). If your system is hanging because of a video problem this may help it boot. If you know of any other special kernel options that you know of, such as "noapic" etc , this is the place where you would enter them as well.

If you get your system to boot with 'nomodeset', install your video drivers.

If it doesn't boot, try the LiveCD and run the boot info script found here:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

It will create a file called RESULTS.txt which will provide us with your system's boot information. Post the contents of this file here so helpers can take a look at it.

---

### Post by everythingsround on 2010-10-26
Wow, wonderful information there...

Never knew holding Shift will force Grub to show up, Thanks!
[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net) is a great resource too!

I'll have to have a look at what's going on with Grub as it only has 'Grub.' with one dot and never posts the grub options so I could go in and change it.

Would you recommend booting a live cd and editing something, or giving the bootinfoscript a go?  Thanks again.

-Michael

---

### Post by drs305 on 2010-10-26
> **everythingsround said:**
> 
I'll have to have a look at what's going on with Grub as it only has 'Grub.' with one dot and never posts the grub options so I could go in and change it.

If you mean you have a "grub" prompt, you can take a look at this thread on how to try to boot:
[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")
It discusses how to boot from the grub prompt.

If you would rather just try to reinstall Grub2:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD ]("http://ubuntuforums.org/showthread.php?t=1581099")

Otherwise, if you would like some recommendations based more on specifics than speculation, boot the LiveCD and post the RESULTS.txt would probably be a good idea. When you paste the contents, press the # icon in the post's menubar to generate 'code' tags, then paste between them.

---

### Post by mr clark25 on 2010-10-26
you might try re-installing grub. the link in my signature should make this easier. (it is a script that automates the process)

EDIT: looks like drs305 beat me to it. my script does almost exactly what is mentioned there. (from the live cd)

---

### Post by everythingsround on 2010-10-26
> **drs305 said:**
> 
Otherwise, if you would like some recommendations based more on specifics than speculation

...attached...

---

