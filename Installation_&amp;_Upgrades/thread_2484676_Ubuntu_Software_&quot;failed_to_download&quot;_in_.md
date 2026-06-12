---
title: "Ubuntu Software &quot;failed to download&quot; in Ubuntu 17.04"
date: 2023-03-06
forum: Installation &amp; Upgrades
---

### Post by nemo8269 on 2023-03-06
I installed Ubuntu v17.04 on my i386 (32 bit) laptop few days ago, but I can't install any software till now. Trying with the Ubuntu Software app and going on the Updates tab and clicking on the refresh button, after few seconds give me the message below:

> failed to download [https://extensions.gnome.org//extension-query/?shell_version=(null)&page=1&n_per_page=1000:](https://extensions.gnome.org//extension-query/?shell_version=(null)&page=1&n_per_page=1000:) SSL handshake failed

I installed this version of Ubuntu using an ISO for CD Live from the official website.
 How I can do to download software? I'm new to Ubuntu and I feel confused by all this

---

### Post by coffeecat on 2023-03-06
Ubuntu 17.04 was an interim release (not a long term release version), released in April 2017 and supported for nine months only. It has been end of life for over 5 years, and that is why you can't download any software. The repositories for that release are closed.

Normally, we would recommend that you download a newer and supported release such as 22.04, but your post reveals a problem: you are using 32-bit software. There are no currently supported releases of Ubuntu or any of the official flavours of Ubuntu for i386 hardware. (I think it's possible to install the 32-bit 18.04 release, but as that is due to go out of support very soon, that's a moot point. And, tbh, I'm not 100% sure about the situation for Ubuntu 18.04 rather than the 18.04 flavours which are definitely out of support.)

Your question really needs to be: what supported version of a Linux distro can you install on your hardware? Perhaps if you tell us more about your 32-bit laptop, and what you hope to achieve with Linux as a newcomer, forum members may be able to help.

As this thread is unlikely to be about support for Ubuntu per se, it probably needs moving to another sub-forum, so I'll monitor the thread and move it to an appropriate place when it's clear which way the conversation is heading.

Good luck, and welcome to the forum.

---

### Post by Impavidus on 2023-03-06
Ubuntu 17.04 is no longer supported. It was supported until October 2017, over 5 years ago. The repositories have been archived and are no longer maintained. If your computer is indeed 32 bit (double check that, most computers less than 15 years old are 64 bit), you have to use a different Linux distro, as Ubuntu stopped supporting 32 bit after 18.04, which has about one month of support left. I heard some people on the forum recommend Debian.

---

### Post by nemo8269 on 2023-03-06
Thank you very much for the clarification, honestly I yet read that Ubuntu abandoned development for 32-bit PCs, but I thought I would still find some necessary software. Now I would like to migrate to Debian, but I realized that on the current OS several of the applications already installed do not work well, and one of these is Startup Disk, with which I hoped to create a bootable USB. and also I don't found any burnin ROM app on Ubuntu.. I'm afraid I'll have to reinstall Windows first, and then switch to Debian from there. Is there anything else that saves me all this work? Thank you in advance for any help! You were all very kind and helpful, although I understand that maybe I'm "trapped"   ](*,):biggrin:

---

### Post by guiverc on 2023-03-06
Ubuntu still provides support for 32-bit ARM hardware (ie. *armhf *architecture).

Ubuntu provided support for *i386* or 32-bit x86 until *disco* or 19.04 reached EOL.

The only **still supported release of Ubuntu with *i386* support currently is Ubuntu 18.04 LTS**, which reaches the end of it's five years of *standard support* in April 2023.

The last *i386* QA testing I performed was in August 2020  (ie. if you look at [http://iso.qa.ubuntu.com/qatracker/milestones/415/builds](http://iso.qa.ubuntu.com/qatracker/milestones/415/builds) you'll note many *i386* ISOs which is what Debian & Ubuntu both refer to x86 32-bit), but this is the release which reaches **EOSS** (*end of standard support*) next month.

You can just install Debian directly over Ubuntu without issue,  I performed QA of both Debian & Ubuntu on numerous (~12) devices that were *i386* and only one (*of those ~12*) performed better on one OS than the other (*one performed faster with Lubuntu*/LXDE/LXQt *over Debian/LXDE or Debian/LXQt*).  Yes its easier to migrate from Debian to Ubuntu (*in my opinion*), but you can do it the reverse way too. 

*FYI: My 32-bit QA was mostly pentium M laptops, but also pentium 4 desktops, atom netbooks & more..*
EOSS for 18.04 is expected to be EOL for *i386*, with ESM options only for *amd64, ppc64el, s390x ....*

---

### Post by Impavidus on 2023-03-07
You don't need a special application to create a live usb. Any command line tool that can copy files will do: dd, cp, cat, whatever you like. See for example this page in the Debian installation guide: [https://www.debian.org/releases/stable/i386/ch04s03.en.html](https://www.debian.org/releases/stable/i386/ch04s03.en.html)

---

### Post by MAFoElffen on 2023-03-07
By another fine member of the community (sudodus): [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by BBQdave on 2023-03-07
> **nemo8269 said:**
> I installed Ubuntu v17.04 on my i386 (32 bit) laptop few days ago, but I can't install any software till now.

As said before, out of date.

Debian is your friend :) [https://cdimage.debian.org/cdimage/unofficial/non-free/cd-including-firmware/11.6.0+nonfree/i386/iso-cd/](https://cdimage.debian.org/cdimage/unofficial/non-free/cd-including-firmware/11.6.0+nonfree/i386/iso-cd/)

---

### Post by nemo8269 on 2023-03-07
Thank you ALL :guitar:
I found yesterday a voice into an app (I don't remeber something about disks partitions) to change my USB stick into "bootable" so I tried to mount the image of Debian on my HDD before, then just copied all files on the key and so, hopefully tried to restart my pc by it and did work now I'm on Debian!! I was trying for days all looked without a solution  I am very grateful to all of you for help and support! Thank you all very very much!!

---

### Post by coffeecat on 2023-03-09
@nemo8269, congratulations on installing Debian on that machine.

If you need help with that installation, you are very welcome to post here, but in our [Debian sub-forum]("https://ubuntuforums.org/forumdisplay.php?f=161"). That section is not very busy, as our main focus here at ubuntuforums is Ubuntu and its official flavours. Debian also has a forum [here]("https://forums.debian.net/"), which may be a better place to post for Debian questions, and which like us also has a beginners' section. And, of course, if you have another machine on which you install Ubuntu or a flavour and need help, please do not hesitate to post here on ubuntuforums.

Good luck!

---

### Post by nemo8269 on 2023-03-10
@coffeecat Very kind! Thanks for the suggestion surely I'll need it in the future since I am new to Debian, but also in general I know very little about Linux and I like this si whole new world for me so I'd like to deepen. Have a beautiful day!

---

### Post by him610 on 2023-03-13
++Debian
Ubuntu Forums also has a Debian sub-forum, [https://ubuntuforums.org/forumdisplay.php?f=161]("https://ubuntuforums.org/forumdisplay.php?f=161")

---

