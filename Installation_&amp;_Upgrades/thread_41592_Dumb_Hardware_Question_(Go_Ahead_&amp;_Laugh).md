---
title: "Dumb Hardware Question (Go Ahead &amp; Laugh)"
date: 2005-06-14
forum: Installation &amp; Upgrades
---

### Post by polo_step on 2005-06-14
OK, so I'm installing Live Ubuntu on a new OEM Linux box running bloodsucking Linspire, which I desire to replace ASAP.

I see a prompt for the video card driver/chipset, and I honestly have no idea what's in there and the case is (wait for it!) pop-riveted shut!  Apparently this is to keep people out until the warranty is over.

Is there a command-line basic Linux program that will give me a readout of what I have in there so that I may enter the correct info?

Thanks for any help with this!

---

### Post by GrumpySmurf on 2005-06-14
Hello.

Try running the following in a Terminal.  The output below is a sample from my Linux server.
```
$ /sbin/lspci | grep -i vga
0000:01:00.0 VGA compatible controller: nVidia Corporation NV15DDR [GeForce2 Ti] (rev a4)
```
You can also run just 'lspci' by itself without the | grep to see your PCI devices.

---

### Post by polo_step on 2005-06-14
[QUOTE=GrumpySmurf]
Try running the following in a Terminal.  The output below is a sample from my Linux server.
```
$ /sbin/lspci | grep -i vga
0000:01:00.0 VGA compatible controller: nVidia Corporation NV15DDR [GeForce2 Ti] (rev a4)
```
You can also run just 'lspci' by itself without the | grep to see your PCI devices.[/QUOTE]
I did, thanks.

I got that it was an unknown SiS card.  It might even be on the momboard for all I know. :neutral: 

I installed with the SiS video drivers selected.  It worked, but I'm not absolutely sure if it's 100% right or not.  Seems OK though. [shrug]

---

### Post by TeeJay on 2005-06-14
[QUOTE=polo_step]OK, so I'm installing Live Ubuntu on a new OEM Linux box running bloodsucking Linspire, which I desire to replace ASAP.

I see a prompt for the video card driver/chipset, and I honestly have no idea what's in there and the case is (wait for it!) pop-riveted shut!  Apparently this is to keep people out until the warranty is over.

Is there a command-line basic Linux program that will give me a readout of what I have in there so that I may enter the correct info?

Thanks for any help with this![/QUOTE]

The only "DUMB" question is the one you don't ask, If it is a onboard SIS card the Vesa video drivers should work about as well as the SIS ones.

---

### Post by az on 2005-06-14
1.  It would have been fun to know if you can dist-upgrade form Linspire 5-0 to Ubuntu!  (They say you can run linspire and use the debian repositories...)

2.  Did the ubuntu installer not detect your video card?  Sis is a common onboard video card.  You may even be able to get hardware acceleration working. (look up dri sourceforge and follow the link to winihoffer sis page)

3.  Linspire are not as bad as other proprietairy linux distributions who do not give anything back to the community.  There are only a few elements of linspire that they keep closed.  Linspire gives back fonts, icons, code and translations to the linux community.

---

### Post by polo_step on 2005-06-14
Interesting about the VESA drivers -- that was what was highlighted when I did the first live install, and I just punched it not knowing any better.

The results were the same as when I selected the SiS, so there y'go.

I have no idea which is better.  Maybe I should go for the autoselection.  I can't see anything like Device Manager to give me the status of the device and driver, though it might be there somewhere.

The funny part was the case being pop-riveted shut. ;-) 

That was hilarious, but less funny as I see I need more RAM in there above the meager 128M that came stock.  Running those "Live" distros will demonstrate that quite vividly.  Memory is dirt cheap here in California, but I'll have to get out the power drill and void the warranty to upgrade.

Ah!  Another question:  If after doing a real install of K/Ubuntu, I pull the original stick and pop in a 512M one, will Ubuntu automatically sense and auto-configure that new memory upon boot from the BIOS as in XP?

Linspire bugs me because they have a totally stripped installation and then tell you on the site to get a different distro if you don't want to pay a subscription fee for their proprietary CNR service to install the software that should have been there in the first place!  Amazing lack of insight about marketing concepts like "the network effect."  Well, I wish them all the success they deserve.  :-P

BTW, their forum is full of disaster reports in using the Debian repositories.

---

### Post by az on 2005-06-14
No!  Do not use debian repos.  Linspire is said to be compatible - not Ubuntu!

Live cds suck a lot of memory.

You will not need to do anything to get Ubuntu to see your memory.  If we were talking about more memory than a common computer can handle, you may need to install a different kernel (easy) but adding anouther 256 megs is not a problem.

---

### Post by mingus on 2005-06-14
[QUOTE=polo_step]will Ubuntu automatically sense and auto-configure that new memory upon boot from the BIOS as in XP?[/QUOTE]

Sure.

---

### Post by skoal on 2005-06-14
[QUOTE=polo_step][...]Memory is dirt cheap here in California, but I'll have to get out the power drill and void the warranty to upgrade.[/QUOTE]
Void warranty? Are you sure you didn't already do that by replacing the installed OS (linspire) with Ubuntu? At least for old Dell machines, you had to reinstall the Windows CD before you could even get hardware support.

\\//_

---

### Post by polo_step on 2005-06-14
[QUOTE=azz]No!  Do not use debian repos.  Linspire is said to be compatible - not Ubuntu![/QUOTE]
So, what's the hot setup for managing program installation/removal?

I'm completely new at this, sorry.

---

