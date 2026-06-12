---
title: "Graphic tablet driver (wp8060)"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by cereyanakapilma on 2012-10-20
Hi
I use this files [https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages](https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages) for my graphic tablet which is wp8060. It works in ubuntu 10.10 but now I use ubuntu 12.04. it doesn't work in ubuntu 12.04.
[https://bugs.launchpad.net/wizardpen/+bug/1029951](https://bugs.launchpad.net/wizardpen/+bug/1029951) in this page someone have same problem and they were solved it. But I can't understand.
Could you help me?

---

### Post by Favux on 2012-10-20
Hi

Is that a UC-Logic Tablet WP8060U?  Enter **lsusb** in a terminal and post the output.  You should see 5543:0005 in the tablet line.

Also **xinput list** in a terminal should contain the name the kernel is reporting.  Please post that too.

---

### Post by cereyanakapilma on 2012-10-20
> **Favux said:**
> Hi

Is that a UC-Logic Tablet WP8060U?  Enter **lsusb** in a terminal and post the output.  You should see 5543:0005 in the tablet line.

Also **xinput list** in a terminal should contain the name the kernel is reporting.  Please post that too.

```
onuruluturhan@onuruluturhan:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. Bluetooth Controller
Bus 004 Device 002: ID 5543:0041 UC-Logic Technology Corp. Genius PenSketch 6x8 Tablet

```

```
onuruluturhan@onuruluturhan:~$ xinput list 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Video WebCam                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]

```

---

### Post by Favux on 2012-10-20
Alright.  What is suppose to happen is there should be a kernel driver for your tablet.  When the kernel driver works correctly then the evdev X driver should pick it up and the tablet should work.  The WizardPen driver is no longer developed.

The DIGI*mend* Project has information on the UC_Logic tablets.
DIGI*mend* Project site:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend)
DIGI*mend* Project mediawiki:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend)
DIGI*mend* Project Tablet Support status:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

I do not see your model tablet on the *Tablet Support status* page.  I assume that means it does not yet have a correctly working kernel driver.  The fact that the evdev driver doesn't pick it up at all tends to confirm that.  If evdev picked it up, even in a non-working state, we should see it in **xinput list** but we don't.

A quick look does not seem to show diagnostic data for your tablet has been submitted.  It needs to be for Nick to fix the kernel driver.  You could help with the driver development by posting your tablets diagnostic information to the DIGImend-user mailing-list:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Collecting_tablet_diagnostics](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Collecting_tablet_diagnostics)

I think that just leaves us the WizardPen driver.  Fortunately I just posted instructions on compiling it for someone else.  Take a look at:  [http://ubuntuforums.org/showpost.php?p=12307583&postcount=27](http://ubuntuforums.org/showpost.php?p=12307583&postcount=27)

Just ignore the instructions on changing the 70-wizardpen.conf and adding a 52-tablet.conf.  Instead if it compiles and installs post the output of **xinput list** after a restart.

---

### Post by cereyanakapilma on 2012-10-21
I tried  but wizardpen don't work.
[http://sourceforge.net/projects/digimend/files/kernel-patches/digimend-kernel-patches-6.tar.gz/download](http://sourceforge.net/projects/digimend/files/kernel-patches/digimend-kernel-patches-6.tar.gz/download)
I want to try this files but I can't understand how to install this files.

---

### Post by Favux on 2012-10-21
> I tried but wizardpen don't work.
Right.  It is not compiled against Precise's 3.2 kernel.  That's why it does not work.  The instructions show you how to compile it against the 3.2 kernel.
> I want to try this files but I can't understand how to install this files. 
What is there in the [instructions for the tar.gz file]("http://ubuntuforums.org/showpost.php?p=12307583&postcount=27") that you do not understand?  The instructions are set up so that you copy and paste each command in a terminal, entering each one after you paste it.  That is so you do not need to understand them completely.

---

### Post by cereyanakapilma on 2012-10-21
> **Favux said:**
> Right.  It is not compiled against Precise's 3.2 kernel.  That's why it does not work.  The instructions show you how to compile it against the 3.2 kernel.

What is there in the [instructions for the tar.gz file]("http://ubuntuforums.org/showpost.php?p=12307583&postcount=27") that you do not understand?  The instructions are set up so that you copy and paste each command in a terminal, entering each one after you paste it.  That is so you do not need to understand them completely.

Ok but [http://sourceforge.net/projects/digimend/files/kernel-patches/digimend-kernel-patches-6.tar.gz/download](http://sourceforge.net/projects/digimend/files/kernel-patches/digimend-kernel-patches-6.tar.gz/download)

Can I use this file? If I can, How can I do this?

---

### Post by Favux on 2012-10-21
Oh, I'm sorry.  I missed that you were linking to the DIGImend patch set 6.  Unfortunately no.  Your tablet model 0041 is not in that patch set.  So it does not add support to it.  That's why I suggested you submit the diagnostics for your tablet.  So kernel support for it can be made.

---

### Post by cereyanakapilma on 2012-10-21
> **Favux said:**
> Oh, I'm sorry.  I missed that you were linking to the DIGImend patch set 6.  Unfortunately no.  Your tablet model 0041 is not in that patch set.  So it does not add support to it.  That's why I suggested you submit the diagnostics for your tablet.  So kernel support for it can be made.

thanks for help
I wrote message to developer of DIGImend

Regards;

---

