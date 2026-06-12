---
title: "SATA drive on ASRock 939S56-M motherboard"
date: 2005-10-27
forum: Installation &amp; Upgrades
---

### Post by Bastaard on 2005-10-27
*I already posted this on the Hardware forum but didn't get any help there so I thought maybe this would be the right forum for it...*

Hey guys,

I'm a linux n00b, but I got tired of Windows and wanted to try something new. After reading alot about different linux distributions I decided to install Kubuntu 5.04. I can't get it installed though because it can't find my harddrive. I thought maybe Kubuntu 5.10 would make a difference but it's all the same. The motherboard I'm using is the ASRock 939S56-M and the harddrive I'm using is the Samsung SP1213C (SpinPoint P80 120GB).

I read here that I'm not the only one with these kind of problems, and that Linux kernel 2.6.14-r2 might solve the trouble. Kubuntu 5.10 is based on 2.6.12 though (correct me if I'm wrong) so I wondered how long it will take for a (K)ubuntu release to include this or a newer kernel, and if it takes long, if there is any way to install Kb5.10 with the 2.6.15-r2 kernel. Apart from that, is there any other way of getting my SATA drive detected in the Kb5.10 install?

Thanks for the help!

---

### Post by misGnomer on 2005-10-28
Could you try downloading the Sis190/191 Linux driver from Sis and either recompiling the kernel or compiling the driver as a module?

You could also try compiling a new kernel from the latest sources since your SATA chipset seems to be getting into the mainline kernel right now. There are HOWTOs for Ubuntu users on how to do these things.

For some reason Ubuntu developers don't favour packaging the latest and greatest kernels for users as an "after-sales" service. Maybe it helps them keep the support variables manageable, but it'd be nice if someone built new kernels for Ubuntu even unofficially.  :-)

Can you set the SATA in your motherboard BIOS to operate in PATA "legacy" (?) mode (so it uses IDE drivers instead)?

I personally had some issues with SATA detection during booting under Hoary (using both built-in Via VT6420 and PCI-based Sil3112 SATA controllers) and chose to boot from an older PATA drive instead, although the SATA drive gets also detected later on.

If you're not keen on compiling anything, you could also try some other distro with a cutting-edge kernel (2.6.14-rc2 or above) to get Linux installed and running while waiting for Ubuntu to catch up. Livedistro.org is also useful in testing different distros and their hardware support. If you install your /home directory on a separate partition it'll be rather simple to do an "expert" installation of Ubuntu later on and keep the data and settings there.

PS. Apparently Asrock themselves couldn't care less about supporting Linux users. I *almost* bought a board from them recently... ;-)

---

### Post by Bastaard on 2005-10-29
Thanks for the reply!

Yeah, I tried changing all the possible bios setting for my SATA drive, without any success. And since the SATA drive is the only drive on the computer, I can't first install Ubuntu on another drive and then try to detect the SATA one.

Since I'm a linux-newbie and compiling and inserting drivers or even another kernel seems like quite a hassle, I'll just go try another distro. I'm thinking about trying SUSE 10, it uses the 2.6.13 kernel, I think no other distro uses one newer than that. If it doesn't work either, I'll go try compiling the seperate drivers for Ubuntu.

Thanks for your help, appreciated :)

---

### Post by Bastaard on 2005-10-29
Oh and are you sure I need the SiS 190/191 drivers? I searched it and it seems like it's the drivers for the SiS ethernet adaptor. Even though Ubuntu doesn't detect my ethernet adaptor either, my real problem is the HD detection because I need this for installing.

---

### Post by misGnomer on 2005-10-29
My bad! SiS965L is the chipset with SATA support...  ;-)

I found the kernel bug tracker for this issue:
[http://bugme.osdl.org/show_bug.cgi?id=4192](http://bugme.osdl.org/show_bug.cgi?id=4192)

There's also a SATA-specific mailing list (with nice web archives) somewhere under the Linux kernel mailing list hierarchy, but I couldn't find it just now.

Looks like Mandriva submitted a patch for it most recently so that might be included in their latest release (Mandriva 2006) which came out shortly afterwards. Despite being KDE-centric, Mandriva still ships with GNOME (2.10) as well. I don't know if they've released their ISOs out in the open yet, though. I suppose the easiest way to find out if that distro supports your SATA chipset is to test-run MCNLive (198MB livecd using the Xfce window manager) which is based on the latest Mandriva:

MCNLive ("Jordaan")
[http://distrowatch.com/?newsid=02980](http://distrowatch.com/?newsid=02980)

Another distro to try could be openSUSE and esp. their new cutting-edge 1-CD install ("SUPER") release:

[http://www.opensuse.org/1_CD_install](http://www.opensuse.org/1_CD_install)

Some people also managed to *tinker* the SiS965L SATA to work under Fedora Core 3, but I realize that's not what you're looking forward to.

Good luck!

---

### Post by misGnomer on 2005-10-29
Another thought.. when you tried booting Breezy in the PATA "legacy mode" (in the BIOS), did you also try the "noapic" and "acpi=off" boot parameters (separately and together)?

---

### Post by Bastaard on 2005-11-04
Thanks for the help Misgnomer! I'll try the stuff you told me and post my findings here. I didn't try those boot parameters because there is no PATA legacy mode or the like in my BIOS.

---

### Post by Bastaard on 2005-11-04
I just searched distrowatch.com for distributions that contain linux kernel 2.6.14-rc2 or newer and found out that the developing versions of Fedora Core and SUSE both use a newer version, Fedora Core using the stable 2.6.14, SUSE the unstable 2.6.14-rc5. I can't really find the installer for the latest developer Fedora Core though, the link on the website gives a 404: 

[http://download.fedora.redhat.com/pub/fedora/linux/core/test/3.92/x86_64/iso/](http://download.fedora.redhat.com/pub/fedora/linux/core/test/3.92/x86_64/iso/)

So I guess I'll try to install the latest SUSE developer version using the internet installation so I don't have to download 5 CD's--the SUPER version doesn't include a new kernel so I'll stick to the regular one.

edit: By the way, there's no downloadable ISO's for Mandriva 2006 yet

---

### Post by Bastaard on 2005-11-05
I just successfully installed the Suse bleeding edge distribution! It does detect my SATA and network adaptor properly, so now I'll just have to wait for the new Ubuntu to come out with this kernel or newer, or any stable major distribution, so I don't have to run a bleeding edge version. Thanks for the help!

---

