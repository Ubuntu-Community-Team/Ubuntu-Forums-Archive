---
title: "Installing Hardy under MS Virtual PC 2007"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by Hymyly on 2008-04-27
Hi, I'm trying to install Ubuntu 8.04 (i386 desktop) from scratch on Microsoft Virtual PC 2007 (version 6.0.156.0 under Windows XP SP2). I have 7.10 working flawlessly under the same configuration, requiring only the "i8042.noloop"-workaround.

Now it fails miserably, and I after reading several forums (...fora?) and blogs I am still stumped. The Bootloader menu appears normally. The 30-second-countdown runs about three times faster than it should, but other than that everything seems fine. However, when trying to boot I get "isapnp: checksum for device 1 is not valid (0x89)" shortly followed by VPC reporting that "An unrecoverable processor error has encountered. The virtual machine will reset now."

Has anyone had any similar experiences when installing? Can anyone decipher the error message?

I also added "console=ttyS0", removed "quiet splash", and redirected all the output to a file. I can upload this if anyone is interested.

And please please please do not reply with "Why use Virtual PC? What's wrong with using the Live CD directly?" I have my reasons for doing this.

Sincerely, Hymyly.

PS. The CD-image is not corrupted. I have tested it against the official checksum.

---

### Post by Hymyly on 2008-04-27
Oh, and I have disabled the "Use hardware acceleration"-option since it has been known to cause problems.

I'm also uploading the kernel output. It would be very helpful if someone who has encountered the same or similar problem could share their experience. I'm not expecting a solution right away, but anything that can help me figure it out myself. For example, does anyone know what the "isapnp" error message means? Which device is malfunctioning?

---

### Post by rpalmer2181 on 2008-04-28
Supposedly addding:

noapic nolapic vga=791

to the end of the boot options clears the problem for some users. It doesn't work for me but it's something you can try.

---

### Post by HESH234 on 2008-05-02
[QUOTE=Hymyly]Hi, I'm trying to install Ubuntu 8.04 (i386 desktop) from scratch on Microsoft Virtual PC 2007...
"An unrecoverable processor error has encountered. The virtual machine will reset now."...[/QUOTE]


I am getting the same error message.


[QUOTE=rpalmer2181]
Supposedly addding:

noapic nolapic vga=791

to the end of the boot options clears the problem for some users. It doesn't work for me but it's something you can try. 
[/QUOTE]

I have tried this and not having any luck.

I've had a good look in the internet and scouted around the ubuntu forums before posting this and I cant see that anyone has a solution.

Im running XP Pro (at work) with VPC2007. I've tried from the iso and from bootable cd but neither works.

I also went to download virtual box but currently the site have susspended downloads to "comply with US export regulations", or something.

Can someone please post if they have found a fix for this problem. :(

Thanks
PJ

---

### Post by Hymyly on 2008-05-02
I did manage to get the live CD to boot by using a combination of noacpi, nolacpi, xforcevesa, vga=791, and no-hlt. I cannot remember which I did use use in the end though. Unfortunately, the machine cannot boot after install. It seems the installed kernel generates the same error as the kernel on the disc. (Which one should expect, really...)

I have however dug further into the cryptic error message from VPC, and it turns out that this message is displayed when the processor triple-faults. I know that the linux kernel triple-faults on purpose if it fails to halt the computer by normal means, but I don't think it would triple-fault on purpose during startup, so I'm guessing that linux uses a processor instruction which VPC does not support. Maybe recompiling the kernel with different options would do the trick...

My next step is probably going to be booting from the 7.10 live CD and downgrading the kernel, but there really is no point since I already have 7.10 running in another virtual machine. If anyone else has anything to share, please post it. Happy hacking.

---

### Post by Hymyly on 2008-05-02
> **Hymyly said:**
> I did manage to get the live CD to boot by using a combination of noacpi, nolacpi, xforcevesa, vga=791, and no-hlt.

Sorry, typo. I meant noapic and nolapic of course, but now that I  mention it, I'm gonna try noacpi as well. :)

---

