---
title: "not booting"
date: 2022-05-21
forum: Installation &amp; Upgrades
---

### Post by thecubis on 2022-05-21
[COLOR=#DCDDDE][FONT=Whitney][/FONT][/COLOR][COLOR=#000000][FONT=arial black]Pls help i can not boot linux now beckuse it just reset it self but boot from the usb installer is fineAnd if it is in LEGACY support only it wont boot to linux "bootloader"The disk is not bootebole in LEGACYIt is a Hp elitebook 840 g2[/FONT][/COLOR]

---

### Post by sudodus on 2022-05-21
It helps us help you, if you tell us more about the situation with your computer:

- Is your computer booting in UEFI mode from a cloned Ubuntu USB drive?
- How do you want to boot (UEFI or BIOS alias legacy boot)?
- Is Ubuntu the only operating system or is there Windows too, or maybe some other Linux distro alongside Ubuntu?

What did you try before asking us?

- Did you check and repair the file system?
- Did you check and repair Ubuntu (the operating system files)?

Is there reason to suspect some hardware fault?

- Did you check the RAM (memory)?
- Did you check the main drive (HDD, SSD)?

---

### Post by thecubis on 2022-05-21
its booting in UEFI beckuse linux can not boot in legacy on the computer and it can be UEFI its not a problem and the linux install is frech it so frech so it is after the reboot from the install usb and the ran abd ssd is fine and ubuntu is the only os

---

### Post by sudodus on 2022-05-21
- Am I understanding correctly, that your HP Elitebook is working like it should in UEFI mode?

- Is it important to make it work in legacy mode too?

- How did you create the USB boot drive? Please describe the tool or method that you used.

- Which version and flavour of Ubuntu are you using (for example Ubuntu Desktop 22.04 LTS or Lubuntu 20.04 LTS)?

Maybe you can try another tool, for example a cloning tool, or [mkusb](https://help.ubuntu.com/community/mkusb), that can both clone and use other methods in order to create a USB boot drive with Ubuntu.

---

### Post by thecubis on 2022-05-21
it works in both mode but if it is in legacy mode and install linux in leagacy mode then the ssd is not bootibole if you switch to UEFI it just bots to the disk then resest imedelty and i use rufus to make the usb and it is ubuntu desktop 22.04 LTS

---

### Post by sudodus on 2022-05-21
What graphics chip/card is there? Elitebooks can have advanced graphics, for example nvidia, and some of those cards need the boot option nomodeset and later on a proprietary nvidia graphics driver. Please tell us the **brand name and model of the graphics chip/card**.

- It is normal that installed operating systems boot only in one boot mode, either UEFI or legacy mode.

- If you **clone** from Ubuntu iso files to USB pendrives, most computers will boot 'live' or 'persistent live' in both modes.

Rufus can clone, if you select 'dd-mode'. Otherwise it uses extracting methods, and some of them may only create booting in one of the modes in your HP.

Now that you have a working Ubuntu system, you can install and use mkusb. I am rather sure that *at least one of the alternatives from Rufus and mkusb can give you a drive that can make your computer boot also in legacy mode*. But I have no direct experience of your particular model (only of older HP computers), so I suggest that you try several different alternatives and takes notes, so that you need not repeat what you already tested.q

---

### Post by thecubis on 2022-05-21
its working fine when i boot from usb but not ssd hmm

---

### Post by sudodus on 2022-05-21
Could be problems with the graphics chip/card.

Try with the [boot option](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808) nomodeset.

What graphics chip/card is there? Elitebooks can have advanced graphics, for example nvidia, and some of those cards need the boot option nomodeset and later on a proprietary nvidia graphics driver. Please tell us the brand name and model of the graphics chip/card.

---

### Post by thecubis on 2022-05-21
it is a amd readion r7 m260x


hare is a vidio of the boot [https://drive.google.com/file/d/12nczQ4rOIavb7HZuBDeNq3yaONIx_SKx/view?usp=sharing](https://drive.google.com/file/d/12nczQ4rOIavb7HZuBDeNq3yaONIx_SKx/view?usp=sharing) and that pop in the end is thare beckuse it hard reset so that sound comes from the speker

---

### Post by sudodus on 2022-05-21
The current versions of Ubuntu should be able to manage Radeon graphics with the built-in Linux drivers.

So there might be another problem, but you can still try to manually and temporarily add the boot option nomodeset to the 'linux' line in the grub menu.

If that does not help, please scroll back and look at the questions I asked in previous posts - maybe one of them rings a bell - and we can continue from there.

Edit: It is getting late here, so I'll say 'see you tomorrow' :-)

---

### Post by thecubis on 2022-05-21
check the vidieo pls i can besecly do noting (see vidio)

---

### Post by oldfred on 2022-05-21
Hp has some unique setting. Check if your system has this UEFI setting.
HP Elitebook 840 G5 gpt issues - 
HP put a fail-safe gpt recovery into the UEFI Settings,  go into the UEFI Menu in Security -> Hard Drive Utilities -> Uncheck "Save/restore GPT System of Hard Drive"
[https://ubuntuforums.org/showthread.php?t=2436271](https://ubuntuforums.org/showthread.php?t=2436271)

Some HP have Optane or Intel RST, make sure drive(s) are in AHCI mode.

Many HP also need UEFI firmware update and SSD may need firmware update.

---

### Post by thecubis on 2022-05-21
this is a g2 not a g5

---

### Post by oldfred on 2022-05-21
Issues are often common across many models of the same brand of system.

---

### Post by thecubis on 2022-05-22
but that laptop has none of that fetures

---

### Post by tea for one on 2022-05-22
Boot into a live session.
Download boot-repair and [COLOR="#0000FF"]provide the link[/COLOR] to the report in this thread.
Details [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) - Please use 2nd Option.

---

