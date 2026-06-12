---
title: "blank screen during install on Toshiba laptop - Intel graphics"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by bizna on 2010-01-29
The grub screen displays correctly, and that's the last thing you see... After selecting the Install option (or the liveCD option), you get to a blank black screen, even though the disk IS reading.

Even safe graphics mode doesn't show a thing.

**Model**: Toshiba L500-1xc 64bit
**Graphics card**: Intel® HM55 Express Chipset with Intel® Graphics Media Accelerator HD
[U]
[A link to specs sheet]("http://uk.computers.toshiba-europe.com/innovation/product/Satellite-L500-1XC/1081193/toshibaShop/false/")[/U].

Just to be on the safe side, I also tried a 32bit install CD that I have, and the result was the same.

Does anybody have any clue, as for the possible reason? Is there any additional option I can give during boot, that will do the trick?

Thanks!
Dotan

---

### Post by bizna on 2010-01-31
bumping...

---

### Post by bizna on 2010-02-01
After trying the alternate install, the problem is still there.

GRUB displays perfectly, and at the moment the screen needs to out of the textual display, the screen comes to black again.

'Safe mode' doesn't do any trick.

Tried adding the following to the boot in GRUB, and they did nothing:
acpi= off noapic nolapic vga=771

(actually, vga=771 is deprecated, but the gfxpayload didn't help either)

Keeping on trying...

---

### Post by mattfudd on 2010-02-03
I am seeing the exact same issue with my ASUS NOTEBOOK U50. Were you able to figure anything out on this?

---

### Post by bizna on 2010-02-04
Sadly enough: no.

The [beta release notes]("http://www.ubuntu.com/testing/karmic/beta") state something about adding i915.modeset=0 to the boot parameters. No love here.

The parameter nomodeset allows the splash screen, but then again the black screen appears. ([solution from here]("https://bugs.launchpad.net/ubuntu/+source/xubuntu-artwork/+bug/431812"))

I've currently reverted to working with the pre-installed Win7, until such time will come that I will have more time to fiddle with that.

Dotan

---

### Post by bizna on 2010-02-06
So, what do we have until now?

- The new **Intel HM55 graphics adapter is not compatible with Linux** in general, and of course it is incompatible with Ubuntu 9.10 in specific. Apparently, even rescue CDs such as GPartED fail to load the graphics interface.

- The suggested solutions all deal with the 'splash' option in the GRUB and boot stage, and they don't deal with the problem in the Xorg stage (or GDM for that matter). Add the word **nomodeset** to your boot line in GRUB, and you'll be able to at least load your shiny-but-useless Toshiba laptop in safe mode.

- In Ubuntu, it might have to do with the new **EDID** that is supposed to detect screen modes, but fails miserably in this case. A suggested solution can be found here, by [creating a new xorg.xonf file]("http://www.grenage.com/xorg.html"). This is a tedious procedure, that I didn't find the time to go through.

So, for now there's no use in opening a bug in Ubuntu, since it's not an Ubuntu-specific issue, but a general Linux one.

Dotan

---

### Post by oniltonmaciel on 2010-02-08
I think I've got the same problem.
But since I can't boot live cd I can't make sure if my graphic card is the same.
My laptop is Toshiba Satellite A 505 S6005

Do you know a way I could check this?

By the way, I think we should fill a bug report at launchpad anyway. The bug could be closed but the right person could get the problem/bug upstream? What would be very nice.

If my graphic card is the same as yours you (and your thread) are the only concrete things I have found so far, so please don't give up yet.

---

### Post by bizna on 2010-02-08
oniltonmaciel,

You also have the Mobile Intel® HM55 Express Chipset. The _[Toshiba a505 s6005 spec sheet]("http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2515202&rpn=PSAT6U&modelFilter=A505-S6005&selCategory=3&selFamily=1073768663")_ can be found here.

Launchpad you say? Launchpad it is! Bug opened: _[black screen on Intel HM55 - during boot and Xorg]("https://bugs.launchpad.net/ubuntu/+bug/518938")_

Let's see if any solution comes...

Dotan

---

### Post by oniltonmaciel on 2010-02-10
It seems we've got some activity back there. You should check launchpad as soon as possible. :)

---

### Post by bizna on 2010-02-11
Thanks to Geir Ove Myhr from LaunchPad, the issue is now solved.

[This is the relevant post, with the solution]("https://bugs.launchpad.net/ubuntu/+bug/518938/comments/4").

Installing the newest Kernel did the trick for me.

Good luck, and thanks for the feedback!

Dotan

---

### Post by oniltonmaciel on 2010-02-11
Terrific!

But how exactly you did that?

You installed karmic with the alternate cd using nomodeset?

Then you booted in safe mode and than installed the new kernel?

---

### Post by oniltonmaciel on 2010-02-11
I really need to know if you were using karmic or lucid alpha 2

---

### Post by bizna on 2010-02-11
Installed 9.10 Karmic, using the alternate installer. This is a text-only installer, so that it had no trouble in installing.

After doing that, during the 1st boot, you need to co to the safe mode, and press 'e'. This will enable you to edit the boot parameters, and add the 'nomodeset' to the end of the line that ends with 'single'. Then you press Ctrl+x and the system boots into a single user text mode.

In there, you can select to work with network (if you have wired network), and do whatever you like.

If you have no wired network, then you'll need to download the .DEB files using your win7 OS, and then mount that location after you load Linux.

Good luck!
Dotan

---

### Post by oniltonmaciel on 2010-02-11
It didn't work for me. The greatest thing i've got was a shell without using safe mode, but then it tries to use graphics and then I get the blank screen again.  

Maybe a did something different.

Which kernel (version) did you use? What version did you use AMD 64 or x86?

I don't really know if my laptop supports x86. 

Ah and my system keeps complaining about some usb related stuff did that happen to you?

Thanks in advanced

---

### Post by ericboesch on 2010-02-12
I followed Geir and Dotan's suggestions and they worked for me (big thanks to everyone for the fast, courteous and helpful replies!). I used the alternate 9.10 amd64 installer, followed the suggestions to use nomodeset in recovery mode, installed kernel 2.6.33-rc7, shut the system down, rebooted in the new kernel, and have had no graphics problems since.

---

### Post by bizna on 2010-02-13
> **oniltonmaciel said:**
> It didn't work for me.
...
Which kernel (version) did you use? What version did you use AMD 64 or x86?

Ah and my system keeps complaining about some usb related stuff did that happen to you?


My machine is a 64bit laptop, so these are the files that I've downloaded:
[linux-headers-2.6.33-020633rc7-generic_2.6.33-020633rc7_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc7/linux-headers-2.6.33-020633rc7-generic_2.6.33-020633rc7_amd64.deb")
[linux-headers-2.6.33-020633rc7_2.6.33-020633rc7_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc7/linux-headers-2.6.33-020633rc7_2.6.33-020633rc7_all.deb")
[linux-image-2.6.33-020633rc7-generic_2.6.33-020633rc7_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc7/linux-image-2.6.33-020633rc7-generic_2.6.33-020633rc7_amd64.deb")

After downloading, I just did a:
dpkg -i *.deb

And rebooted.

Regarding the USB, I didn't even get to that part, since currently the main issue is the unidentified wlan (Wifi wireless connection), that I don't have the time to attend.

Dotan

---

### Post by jdthomp on 2010-02-15
Thanks for bringing up this issue, Dotan.  I had the same problem (Gateway NV79 series, same graphics card) and was able to fix it via this thread.

For what it's worth to those who still have problems (warning: I am not a Linux expert by any stretch of the imagination):

I installed Ubuntu 9.10 using the Alternate CD.  And although I noted something about GRUB being installed toward the end of the installation I could never reach a GRUB menu on start up (note that I let the Ubuntu installation blissfully obliterate my Windows 7 partition; also note that when I say 'I could never reach a grub menu on start up', I mean the only thing I did was push the power button and look at my blank screen with an even more blank stare).  Instead, I booted using Super Grub Disc, did a search for available operating systems,  selected ubuntu single-user option,  edited this boot option by placing 'nomodeset' at the end of the line ending in 'single', and then booted using <ctrl>+x.  From there I successfully updated the kernel.  Hopefully this is helpful to some of you; I know how frustrating it can be to solve problems of this nature.

Jason

---

### Post by DeeMenace on 2010-02-16
I have a gateway nv59 and this thread has helped me a great deal. although i didn't use the alternate cd(to my knowledge) I just downloaded the 64bit version from the main ubuntu download page.I was able to boot from the cd and get into safe graphical mode. Once I got ubuntu installed, I then followed the instructions to updgrade the kernel. I used the rc8 version of the kernel though since it was newer. 


Everything works as far as 3d desktop, wobbly windows , desktop cube etc... but if i use a screen saver that is like a slide show the entire computer locks up. If i try to play a game that has a slide show type loading screen the entire computer locks up. 

Should I downgrade to rc7 or is everyone else having the same problem as me?

---

### Post by bizna on 2010-02-16
> **DeeMenace said:**
> 
Should I downgrade to rc7 or is everyone else having the same problem as me?

You can install it side-by-side. It will have its own option in GRUB, once you install it.

And try to have a look at the logs. All of them. Maybe you'll find a hint.

Dotan

---

### Post by DeeMenace on 2010-02-17
I tried rc7 it does the same thing as rc8..... I hope something that fixes this comes out soon cause then this laptop will be great running ubuntu :)  

p.s. Ubuntu is still faster than windows 7 on this laptop.

---

### Post by Chris_cur on 2010-02-18
Matt Fudd, did this thread help you? I have the same laptop and the same issue. 

I have been running 9.04 successfully since November, and I haven't really tried to mess with 9.10 again since my success with 9.04.

Has any one had any luck with upgrading from 9.04 to 9.10 when they were having this problem after a clean install or an install attempt?

---

### Post by magdasadrian on 2010-03-29
I have a Toshiba A505 S6005, I've upgraded the kernel to .33 RC7, the problem is that the luminosity of the display is really low, I can't see almost anything on the screen. Did anyone had this problem before?

Edit: If I start the GUI from SAFE MODE using vesa in xorg.conf, the display is ok. Seems that upgrading the kernel didn't help. Any idea how to force xorg to use the existing config file?

Thanks,
Adrian

---

### Post by theviking10 on 2010-04-05
Hello, I am also experiencing trouble installing Ubuntu onto my Toshiba A505 and I believe what is described in this thread would solve my problem. 

However, I am very nervous about installing a new kernel onto my machine, especially since the entire process will be text based (like yours, my video card is unsupported on the current kernel). 

I am fairly new to Linux (user for two months, before I bought this new laptop) and I do not know if I could safely integrate the new kernel.

Is there some way to get the newest kernel on a regular installation? (i.e., on an install disc) If this is not available  on Ubuntu, could it be done an some other distro? I am very willing to reformat my entire hard drive. I am running Windows 7 currently, and would much like to be rid of it.

---

### Post by bizna on 2010-04-05
> **theviking10 said:**
> 
I am fairly new to Linux (user for two months, before I bought this new laptop)...

Having the same laptop, and several years of experience, I say: keep the Windows 7.

I have an experience of several years, and still I've decided to keep Windows 7 as the main operating system. There are enough good reasons for that, and some of them are being detailed in this thread.

You should, in my opinion, keep your Windows 7, at least such a time comes that you can safely say that you master the command line, and know how to edit the GRUB menu file.

There's a lot of Free and Open Source Software (FOSS), that you can use both on GNU/Linux and Windows. The basics are:
**Firefox **for surfing the net
**Thunderbird **for Email (with the **Lightning **add-on for calendar support)
**OpenOffice **for editing office documents
**Songbird **for playing music files
**VLC **for movies and/or music files
**Vuze **for torrents
**Pidgin **for almost any IM protocol out there
You can also install **Skype **and **DropBox**

Once you decide that you can safely migrate from Windows to Linux, you can just copy the profile folders, and you're home safe.

Good luck!
Dotan

---

### Post by theviking10 on 2010-04-07
Thank you! And it looks like Fedora 13 will be released in just over a month, and that it will use the 2.6.33 kernel. (I have used Fedora before, and feel comfortable with it).

Hopefully Ubuntu 10.10 will have adequate kernel support, as I do prefer Ubuntu to Fedora. However I will be able to (safely) use Linux this summer, just on a different distro.

Thank you for your help!

---

### Post by jalvarez on 2010-04-18
Thanks to bizna for documenting his procedure to install Ubuntu 9.10 on a Toshiba L500. It worked quite well with my HP Pavillion dv4 2160us using an i5 processor. After the kernel update to 2.6.33, the video adapter is now working properly.

Many notebooks with the i3/i5/i7 processors use the HM55 chipset for their main video output. The enhanced Nvidia or ATI adapters are more costly so the HM55 is more common for base configurations. This procedure should be documented in the wiki while the changes appear on the Ubuntu distribution. Not having a good workaround for the HM55 chipset is probably making many laptop users shy away from Ubuntu.

BTW - There are updates to the 2.6.33 kernel after rc7 and some 2.6.34 builds available at:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/")
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

As far as wifi support, it is still somewhat weak in Ubuntu 9.10. These sites offer guidelines and compatibility info for some (usually older) wifi adapters:

[http://wireless.kernel.org/en/users/Devices](http://wireless.kernel.org/en/users/Devices)
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/)

---

### Post by greybeard62 on 2010-12-11
I note this thread is marked solved however it should be noted the problem still exists in 10.04 and 10.10.  Applying the recommendations in the bug fix did not correct the issue.  My issue is exactly the same as reported here.  Lenovo U160 ideapad,  with new i5-470um processor and the Mobile Intel HM55 Express chipset.  I was able to install using nomodeset, then boot into black screen.  Tried all recommended fixes, no joy.  Support for this chipset is still missing apparently.  I did subscribe to bug.

---

### Post by bizna on 2010-12-12
greybeard62,

Though I hardly go into my Ubuntu, I know that the regular stock Kernel works perfectly well.

I believe I still have the 10.04. But even if I don't, then I remember that I had it when I deleted the non-standard Kernel that I had to install in the beginning.

Perhaps there's a new problem with the i5, as there was with the i3 at the time.

Good luck!

Dotan

---

### Post by mmortall on 2011-08-07
I have same issue on Asus K52Jc. Use Ubuntu 11.04 64-bit. 

When this bug will be fixed?

---

### Post by mmortall on 2011-08-07
Sorry, It was on my side. *.iso file was bad.

---

### Post by jcer93705 on 2011-09-11
> **mmortall said:**
> Sorry, It was on my side. *.iso file was bad.

So you got Intel Graphics HM55 Express graphic working? Does the latest ubuntu version work without modification?

---

