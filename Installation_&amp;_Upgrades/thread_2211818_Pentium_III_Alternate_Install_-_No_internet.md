---
title: "Pentium III Alternate Install - No internet"
date: 2014-03-17
forum: Installation &amp; Upgrades
---

### Post by Paul_van_Gulick on 2014-03-17
Hi.  I'm having the devil of a time with a pentium iii 512mB trying to install any of the Ubuntu releases.  I was successful with Ubuntu 5.10 except that it won't connect to the internet.  Unfortunately, I can only CD install, and I have a D-Link Airplus DWL-G520 atheros card, and the computer is PAE.  The closest I've come to success is with a 10.04.4 alternate install which at least got me a command line but  no GUI.  I can't get internet either in order to apt-get any kind of gui - or drivers for that matter.  While I can't boot from a USB, I could transfer a driver via USB.  So, I guess I need to know how to install the correct driver for the wireless in order to connect to the internet in order to achieve needed updates/installs.  Any ideas?  Thanks

---

### Post by slooksterpsv on 2014-03-17
You may want to look into Lubuntu with those kind of specs. Any Ubuntu version below (not including) 12.04 is no longer supported and has out of date software packages. Lubuntu will run on systems with as low memory. The wireless drivers may already be in the kernel depending on how old the wireless card is. If Lubuntu doesn't work, you could try a lighter distro such as VectorLinux, AntiX, umm... Puppy, hmmm... try Lubuntu first though.

---

### Post by Paul_van_Gulick on 2014-03-17
Actually, I've had decent luck booting from a CD with Lubuntu - but for some reason when I choose "install" instead instead of "boot", it skips the install and just boots from the CD anyway.  I've tried Lubuntus 10.04 and 12.04 and they both do this.

---

### Post by Paul_van_Gulick on 2014-03-17
VectorLinux? - hmm...  I'll give that a try - I see they have a lite version.  It's just that I really enjoy the whole Ubuntu experience.  I've got a proper install of 12.10 on a more modern desktop and am quite happy with it.

---

### Post by slooksterpsv on 2014-03-18
Try Lubuntu 13.10, I know it's newer than 12.04 but i don't think 12.04 got official LTS status (I could be wrong).

---

### Post by mörgæs on 2014-03-18
Correct, Lubuntu has until now only short term support. 14.04 is expected to be the first with long.

I wouldn't spend time on a Pentium 3, but if you are keen on it then a [minimal Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") is your best option, not the regular Lubuntu ISO.

---

### Post by sudodus on 2014-03-18
You can try to install minimal versions of the latest and greatest Ubuntu Trusty with the Debian based installer 9w. You get instructions and tips at this link, post #88 and forward

[http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586](http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586)

and you can download it at this link

[http://phillw.net/isos/linux-tools/9w/](http://phillw.net/isos/linux-tools/9w/)

---

### Post by Paul_van_Gulick on 2014-03-18
Thanks :-)  I'm only fussing with this pentium because it's proven to be instructive even if not yet successful.  I'm working on the vectorlinux barebones install at the moment and we'll see how that goes.  Later, I'll certainly try a minimal Trusty too.  The problem that poses is that while I have a CD and also a DVD, I've only been able to boot from the CD which limits me to a 700MB iso.  If I can work out how to boot from the DVD that should make it possible to boot with the 9w and go from there.

---

### Post by whatthefunk on 2014-03-18
Two problems.  First, on older computers, the GPU usually cant handle graphic installers so Id throw out anything that uses one.  Second, with 512 mb the only Ubuntu family distro possible is Lubntu, and that would probably struggle.  Id go with Crunchbang.  It uses a command line install, is super light, and uses Debian repos so you have wide variety of software to choose from.

---

### Post by mörgæs on 2014-03-19
> **Paul_van_Gulick said:**
> Later, I'll certainly try a minimal Trusty too.  The problem that poses is that while I have a CD and also a DVD, I've only been able to boot from the CD which limits me to a 700MB iso.

If you read the link I provided you will see that there's no such limit if you use the minimal ISO (if it allows you to make a wired internet connection, that is). The CD is only around 30 MB.

---

### Post by sudodus on 2014-03-19
> **Paul_van_Gulick said:**
> Thanks :-)  I'm only fussing with this pentium because it's proven to be instructive even if not yet successful.  I'm working on the vectorlinux barebones install at the moment and we'll see how that goes.  Later, I'll certainly try a minimal Trusty too.  The problem that poses is that while I have a CD and also a DVD, I've only been able to boot from the CD which limits me to a 700MB iso.  If I can work out how to boot from the DVD that should make it possible to boot with the 9w and go from there.

There are [COLOR=#006400]three CD size 9w iso files[/COLOR] and [COLOR=#0000ff]one DVD sized multi-install 9w iso file[/COLOR]. So I suggest that you select one of the CD size iso files.

```

[COLOR=#006400]506M TrustyB1npae-text.iso
630M TrustyB1npae-LubuCore.iso
676M LubuSaucy-pae2pm-4GB.iso[/COLOR]
[COLOR=#0000ff]1,4G 9w_multi-install_trusty-n-saucy.iso[/COLOR]
```

---

