---
title: "Install UBUNTU on ASUS X90S"
date: 2016-12-01
forum: Installation &amp; Upgrades
---

### Post by laurent-guenery on 2016-12-01
Hello
When I try to Install UBUNTU (or XUBUNTU) on an ASUS laptop X90X, the installation stops, the screen become dark, and the cursor blink in the upper left corner 
This computer has an Intel DUO CORE 2, a NVIDIA GT 220M 1Go, 4 Go RAM. I try to change Bios options, already the same problem.
I try to install XUBUNTU 16.04.1 LTS et UBUNTU 16.04.1.
Solution to my problem ?
many thanks
Laurent

---

### Post by oldfred on 2016-12-01
Becuase you have nVidia you may need nomodeset.

Full Ubuntu with Unity probably will not run on that system. My old laptop with core2 duo chip did not have enough video capability. With your nVidia you may just have enough, but Xubuntu or Lubuntu will be much better.

Press any key while tiny accessiblity icons are at bottom of screen, then f6.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by laurent-guenery on 2016-12-02
Hello Olfred
I try to install XUBUNTU.
In nomodset the result is the same if I use try Ubuntu, or install Ubuntu.
The windows 10 on this machine in not an UEFI installation.
the F6 memu options has the same resut
laurent

---

### Post by oldfred on 2016-12-02
Are you getting the accessibility screen for the first few seconds right after BIOS.
That is the screen with two tiny icons at bottom (or person pressing keyboard for accessibility).

---

### Post by laurent-guenery on 2016-12-03
Yes
after bios start the message appears : ISO LINUX 6.0.3 ......, and after the screen with the 2 tiny icons at bottom of the screen, if I press enter immediately I accede to the menu, the problem appears just after the selection of the linux installation 
Laurent

---

### Post by oldfred on 2016-12-03
And at menu are you pressing f6 and adding nomodeset before booting into live mode?

Or does you system let you set in BIOS which video you are using when booting?
The nomodeset is for nVidia driver, if used. But Intel should just work.

---

### Post by laurent-guenery on 2016-12-05
Hello
 I had try to install with the nomodset mode.
It is not possible to disconnected the nvidia video board, from the Bios setings
Laurent

---

### Post by oldfred on 2016-12-05
Some newer Asus have also needed this boot parameter, in addition to nomodeset.

  pci=nomsi

---

### Post by laurent-guenery on 2016-12-06
How used this ?
Laurent

---

### Post by oldfred on 2016-12-06
It is another boot parameter. Often better to replace quiet splash so you can see boot process and perhaps see other errors. You should only need the nomodeset to install & first boot. If other boot parameters are required you may have to make them permanent by editing /etc/default/grub, but that is only after install and test of what parameters are required.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by laurent-guenery on 2016-12-07
The install procedure not start. The install crashes after validation of the "install Xubuntu" in the install menu.
I can't see any error messages, only a black screen with a blink cursor on the upper left corner 
I try to install Ubuntu, same problem, I try to execute Gparted, same problem
If I try to evaluate Xubuntu without install, same problem
Laurent

---

### Post by oldfred on 2016-12-07
Black screen is almost always the video driver issue that nomodeset resolves.

Without knowing if booting with nVidia or internal video, difficult to know what to suggest. There may be other BIOS settings that need to be changed. Do you have latest BIOS from Asus? It may not have been updated for years, but could still be newer and include some fixes.

Some have needed nomodeset, but also use f-key to increase brightness of screen as it just was dark.

       [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by laurent-guenery on 2016-12-08
nomodset give the same result

---

### Post by oldfred on 2016-12-08
Not sure what else to suggest.

Do you get the tiny icons, person & keyboard or accessibility at bottom of screen for just a few sec after BIOS?
This shows that screen:
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076)

Are you replacing quiet splash so you can see if process starts?

---

### Post by ubfan1 on 2016-12-08
Lets do a reset, OldFred's suggestions should have fixed any video issues, so maybe it's something else, like bad installation media.
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
  For other releases' hashes, like lubuntu, see:
  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (perhaps another live-media menu choice) on your PC?

Doing the above can save you a lot of time struggling with a bad install media or hardware problems.

---

### Post by oldfred on 2016-12-08
+1 on ubfan1's suggestions.

---

### Post by laurent-guenery on 2016-12-09
Hello
I try to install Xubuntu with the nomoset option + one of other of the F6 memu option activated, same problem, BUT I have try the Install with all options of the F6 menu activated in the same time, the installation starts ! and Xubuntu runs correctly.
Can you tell me what are the actions of each F6 menu option ?
A combination of many F6 options solves the problem.
Now I must find how to adjust the screen resolution.
Laurent

---

### Post by oldfred on 2016-12-09
Normally you then install the video driver once booted into your install.
But with the install you have grub menu and must edit it with nomodeset as posted before.

You then may also need other boot parameter(s). I doubt you need all of them, but many systems need both nomodeset & another one. You may have to experiment to discover which one(s) you need.

You should be able to fix video issues, by using System Settings, Software & Updates icon, and Additional drivers tab. Only if a very brand new system may you need newer drivers than the newest available in the Ubuntu repository.

---

