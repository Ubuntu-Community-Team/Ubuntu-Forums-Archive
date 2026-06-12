---
title: "Impossible to upgrade/install Lucid"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by benjamin_linux on 2010-04-08
Hi there, 

I tried to install a couple of times, with different isos, different cd's at different speeds and i always get stuck at the progress bar, i have to manually reboot.

And if i upgrade from Karmik, everything goes just fine but when i reboot after finishing the upgrade it happens the same thing, it crashes before loading anything and don't even have access to a terminal.

I have a Sempron with an Nvidia card that works great with every Ubuntu version i tried, i did a memtest and everything works ok.

I've read but haven't found anyone with this problem at all.

Thanks!

---

### Post by stilling on 2010-04-08
i get tha same think i resolved it by removing my wirelees network card that is in my desktop pc maybe you have something that ubuntu don`t like`s

---

### Post by _DoMeN_ on 2010-04-08
I just gave up triing to install 10.04 a few minutes ago...

I have the same issue with the difference that I wasn't able to even upgrade... It crushed while upgrading and now I'm getting kernel panic.

I tried to install 32bit version of today's beta 2 desktop image with Wubi, with boot from cd (tried to install and use life cd), beta 1 image with boot from cd (install and life cd) and also 64bit version with boot from cd(install and life cd) but nothing worked.

I have Intel core 2 2176MHz and Nvidia 8600 gt card that also worked fine with every ubuntu version till now.

Perhaps it's the Nvidia graphic card problem but I somehow doubt that.

If someone knows how I could get some log info or something like that please tell so I can at least file a bug report.

Thanks,
Domen

---

### Post by _DoMeN_ on 2010-04-08
I have an integrated network card (no wireless) so I can't test you theory. Do you know of any way of getting a report what went wrong with the installation? The loading screen is nice but doesn't provide any info when something goes wrong...

---

### Post by benjamin_linux on 2010-04-08
If it's hardware related i'm done because i'm on a laptop, but i don't think so because it crashes before even loading the installer.

And i still doesn't know if it might be Nvidia relatev, given this Plymouth/Neauveu/Propietary Nvidia thing.

---

### Post by ajgreeny on 2010-04-08
Have you checked the iso file you used to burn the CD?  If it is corrupt in some way you will never get a reliable install to work.  I am not sure how to check in windows, if that is what you will now need to use, but in any linux distro it is merely a case of running ```
md5sum /path/to/filename.iso
```and comparing the output with the published md5sum that you can find on the download site.

---

### Post by _DoMeN_ on 2010-04-08
It froze the same way here. I pressed a button on start of loading so I was able to select different options from menu but couldn't find the option for failsafe graphics card drivers or whatever it was called in 9.10... Did you trie to do that aswell or did it freeze even before that?

I have a PC and the only card not integrated is my graphics card and I don't have a spair one so I'm in the same mess as you are...

---

### Post by _DoMeN_ on 2010-04-08
I doubt that that's the case because I was able to install the same image in virtual machine on the same PC without any problem...

---

### Post by benjamin_linux on 2010-04-08
Same here. Checked md5 with both isos i downloaded, virtually checked for trouble and burned at lowest speed.

---

### Post by norbs on 2010-04-09
hi there, I had this problem last night.
Today I managed to set up lucid this way.

When the first screen appears I pressed a button on my keyboard, than the usual installation menu appears. There I press F6 than I select the option before free software (I've forgot what was it, though...).

This way the install goes without trouble. 

But after I start up my system, trying to boot from HDD, the splash screen freezes again.

Any ideas for this one?

---

### Post by norbs on 2010-04-09
> **norbs said:**
>  (I've forgot what was it, though...).


Ok, I've found out you have to select 'nomodeset' after hitting F6.

[http://ubuntuforums.org/showpost.php?p=9094227&postcount=11]("http://ubuntuforums.org/showpost.php?p=9094227&postcount=11")

Now I'll try to boot in :lolflag:

---

### Post by norbs on 2010-04-09
Success!

Following drs305's guides I've managed to boot in to lucid.

Here's how I did it:

When restarting my PC I press down on shift button (tried with left shift), and than GRUB appears. 
I pressed "e" than added to the line in which says something about "linux" and "quiet splash" "nomodeset" (like "quiet splash nomodeset").
Than I've booted the system (by pressing the key "X").

The system booted, and I've made the required updates (it was a partial upgrade), and installed restricted drivers for my video card.

Now it boots normally. 

Thanks for: [http://ubuntuforums.org/showpost.php?p=9094227&postcount=11](http://ubuntuforums.org/showpost.php?p=9094227&postcount=11)

---

### Post by _DoMeN_ on 2010-04-09
This worked for me as well. Thanks norbs.

Benjamin I hope this helps you too.

regards,
Domen

---

### Post by mifi on 2010-04-09
The 10.04 beta2 AMD64 does not boot. I did the above and set the nomodeset boot option and as a result the splash screen does remain course (where previously the resolution changed). The boot option is set ok.

After some activity on the CD, everything stops.

I have managed to get an error like (from the top of my head):
(initramfs) no file system found (the actual message is longer but I cannot remember what it was).

BTW, the 10.04 beta 1 AMD64 CD booted fine on the same system. The image on the HD is booting fine as well, no problems there.

Is it possible there is something wrong with the 10.04 beta 2 AMD64 live CD?

ASUS P6T mobo, Core i7 920, 6GB, nVidea 9800.

EDIT: to my surprise the 10.04 beta2 CD does boot this morning. I pressed ESC in the splash screen to have a watch the booting process. It stops twice for a while but then continues. I hope I do not have hardwrae problems, like temperatures....  anyways, never mind for now.

m

---

### Post by benjamin_linux on 2010-04-10
Thanks for the solution!

Anyway, i'm not at home this weekend and yesterday i tried only to install and it stucked around 40% (now, a problem on the cd), so i'll upgrade my karmik on monday with nomodeset on my first boot.

If it doesn't work, i'll let you know, but let's hope... :)

Thanks!

---

### Post by scifiskywatcher on 2010-04-10
I had the same problem and fixed it by unplugging second monitor. started the installation process all over again and it worked. Just to make sure it was the dual monitors I plugged the second one back in and same freeze. I don't know if this will help you but there may be others with the same problem where this will help.

Also I have to use the F6 option and use the command "pci=nomsi" due to my SATA controller not finding my DVD.

---

### Post by mifi on 2010-04-11
I went into the BIOS and changed the SATA controller setting to AHCI instead of IDE.
Seems to work now (even with a second monitor on the nVidea card).

m

---

### Post by benjamin_linux on 2010-04-12
Well, i've been trying all day and now i'm unable to upgrade, it saids it can't because i have broken packages (which i don't, i made a Karmik clean install and updated afterwards -just in case i checked, and i have not even one) and later it saids

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

Bad luck.

Edit: Bug 561705, in deed bad luck.

---

### Post by benjamin_linux on 2010-04-13
Writing from Lucid :D

Thanks for the workaround!

Now i have two questions, if someone can answer me:

1. I've installed nVidia propietary drivers but Plymouth still looks ugly, do i have to change the nomodeset again, something else...?

2. When i boot my laptop makes TOO MUCH NOISE. Someone else with this problem?

---

