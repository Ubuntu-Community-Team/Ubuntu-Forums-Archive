---
title: "Ubuntu 14.04 WUBI installation help."
date: 2015-06-23
forum: Installation &amp; Upgrades
---

### Post by Stilian_Zagorov on 2015-06-23
[B]Sorry for bad image quality. My phone broke, so I had to use an old one.


[/B]Yesterday I downloaded the automatic Ubuntu install tool in my C drive and ran Wubi. It worked great, I didnt get any errors. I just waited for 10 - 15 minutes for it to install and do its stuff. Then I booted into Ubuntu from the boot screens (I am getting two screens for some reason). Then I got two errors. First.

[B]Serious errors were found while checking the disk drive for /.
[I]Press I to ignore, S to skip mounting or M for manual recovery.
[/I]
 [/B]That is all. I googled it, but everyone said that their error was ending with a name, not just a blank /. 
The second error, (this one dissapears after a few seconds, so it might not be a problem.)

[B]The disk drive for  /tmp is not ready yet or not present.
[/B][B][I]Continue to wait, or Press S to skip mounting or M for manual recovery.

[/I][/B]Then when I boot into whatever I am booting into, I get what I think is a text based OS.
I just want to get Ubuntu to be Ubuntu, with a GUI and I dont want to have to go through the text thing every time I turn my laptop on. 

Thanks in advance.

---

### Post by Bucky Ball on 2015-06-23
Welcome. Unfortunately Wubi is no longer supported by Canonical, hasn't been for some time, and you will get little help on these forums. I suggest you do a dual-boot install with Ubuntu and Windows on separate partitions. 

WUBI is not a Ubuntu install, it is a WUBI install and I have changed the thread title to reflect this. Be aware of this fact when you are trawling for a fix. What works on a full install is not necessarily going to work, or even have anything to do, with a WUBI install. :)

Wubi is on the shelf and unlikely to come off it. There is no-one working on it. 

See here for staff recommendations:

Wubi recommendations:
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

---

### Post by Stilian_Zagorov on 2015-06-23
Why is it so hard? I just want to use ubuntu on my old laptop. I dont have a CD tray. Could you help me? Where can i find a nice tutorial?

---

### Post by Bucky Ball on 2015-06-23
Tutorials about Wubi? I haven't looked for years but there's probably plenty out there. But as it is incompatible with modern Win releases ... (BTW, did you read the staff recommendations?) It's actually not hard to do it the right way, but you are trying to do it with an unsupported, obsolete piece of software inside an operating system that has nothing to do with Linux.

If you want to try Ubuntu on your computer, download the 14.04 ISO image (best release to start your journey and supported until 2019) from [here]("http://www.ubuntu.com/download/desktop") and create a bootable USB installer, boot it and select 'Try Ubuntu'. You can try Ubuntu from the stick and it will not change anything on your hard drive. If you want to install Ubuntu on your hard drive, then do that, not WUBI, and we can help you with that. :)
 
Whichever way you go, you need to use [Unetbootin]("http://unetbootin.sourceforge.net/") or [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") (there are others) to create the USB. There are lots of how-tos around.

I haven't installed from disk in a few years and in fact just bought a netbook that doesn't have an optical disk drive either. Currently running Xubuntu 14.04 just fine. 

PS: Having said this, you never know your luck. Someone who is still actually using Wubi (and there weren't a lot when it was supported) may jump in and try to keep it alive, but I'd cut my loses, save some time, and do it the right way in 2015. The WUBI horse no longer has a pulse and doesn't appear to be breathing. :)

---

### Post by coffeecat on 2015-06-23
@Stilian_Zagorov, the advice given will vary depending on what hardware you are running, and which version of Windows, assuming you want to be able to boot into both Windows and Ubuntu. Please tell us what make and model of computer you are running, and which version of Windows.

As to your question: "why is it so hard?" It doesn't have to be, but you are wanting to install a new operating system on a computer which was almost certainly designed for Windows only, and it seems you want to keep Windows. This is never going to be a trivial task. As far as wubi was concerned, it was never intended to be a long-term way of installing Ubuntu, merely for a try-out. It was never particularly reliable, and as Bucky Ball said, it is no longer maintained. As for why the wubi.exe file is included in the 14.04 ISO, I have no idea and really wish it wasn't. It causes unrealisable expectations in those new to Ubuntu, and we here on the forum are often left to pick up the pieces. Fortunately, there are many helpful people here, and I'm sure they will be able to get you up and running.

---

### Post by grahammechanical on 2015-06-23
Readily available.

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

[http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install](http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install)

By the way, you have told us nothing about your computer. We do not even know the version of Windows that is on it. And it does make a difference if it is Windows 7 or Windows 8.

Regards.

---

### Post by hakuna_matata on 2015-06-24
> **Stilian_Zagorov said:**
> 
[B]Serious errors were found while checking the disk drive for /.
[I]Press I to ignore, S to skip mounting or M for manual recovery.
[/I]
 [/B]That is all. I googled it, but everyone said that their error was ending with a name, not just a blank /. 

Hmm. Are you sure that there is no matching result? I googled it, too and my first result for "**Serious errors were found while checking the disk drive for /."** was [URL="http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted."]http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted
[/URL]
But nevertheless, if possible, try a dual-boot install without Wubi.

---

