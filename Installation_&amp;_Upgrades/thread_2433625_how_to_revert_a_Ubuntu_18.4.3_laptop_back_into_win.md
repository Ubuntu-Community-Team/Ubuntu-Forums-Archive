---
title: "how to revert a Ubuntu 18.4.3 laptop back into windows 10 (no dual booting)"
date: 2019-12-22
forum: Installation &amp; Upgrades
---

### Post by nocruoro on 2019-12-22
HI Im tired of Ubuntu and it's complexity.

So i have a simple question. Is there a simple and safe way to **remove a ubuntu installation and turn it back into a windows 10 **It was a Windows 10 installation to begin with)


My preferred method of hoice will be a (Windows Disk Image ISO File) with a usb drive (my laptop has no CD drive)



How do i get this to work and what precautions do i need to take?

---

### Post by crip720 on 2019-12-22
If doing with ubuntu will need woeusb to make a bootable windows usb drive.  Can do it like this, [https://snapcraft.io/install/woe-usb/ubuntu](https://snapcraft.io/install/woe-usb/ubuntu), or like this [https://www.omgubuntu.co.uk/2017/06/create-bootable-windows-10-usb-ubuntu](https://www.omgubuntu.co.uk/2017/06/create-bootable-windows-10-usb-ubuntu).  Windows should wipe out ubuntu completely on format and install.  Most of us find ubuntu simpler to use, maybe you can explain what you find complex.

---

### Post by nocruoro on 2019-12-22
> **crip720 said:**
> If doing with ubuntu will need woeusb to make a bootable windows usb drive.  Can do it like this, [https://snapcraft.io/install/woe-usb/ubuntu](https://snapcraft.io/install/woe-usb/ubuntu), or like this [https://www.omgubuntu.co.uk/2017/06/create-bootable-windows-10-usb-ubuntu](https://www.omgubuntu.co.uk/2017/06/create-bootable-windows-10-usb-ubuntu).  Windows should wipe out ubuntu completely on format and install.  Most of us find ubuntu simpler to use, maybe you can explain what you find complex.

Problem 1: Ubuntu 18.4.3 Bionic Beaver 64 Bit version gets stuck on startup. I sometimes even have to depress to power button several times 

Problem 2: Lack of support for installing a windows program called **Lego Digital Designer **&#8203;and how to get it to work with Wine. Most of the docunents that do exist are outdated and the installer for handling the installer through Wine doesn't seem to work properly. I also have a thread here but no comments have been efficient help here.

Also Chrome and gets stuck on videos on you. You can hear the sound but the animation gets stuck including scrolling. Cache cleaning and reinstallation hasn't helped.

Thats why im tired of ubuntu's problems, hiccups and instability on my notebook.

---

### Post by crip720 on 2019-12-22
If you need that program, then I think your best bet would be to use windows.  Problem 1 should not be happening nor problem 3.  Without more information(new question), cannot help, but it also sounds like a computer hardware problem,with 1 and 3 together, than an Ubuntu problem.  It can be also a few other software problems including bad settings.

---

### Post by nocruoro on 2019-12-23
i still need a prooer guide to know how the windows installer works on a woeusb version

---

### Post by nocruoro on 2019-12-23
And what buttons do i need to bypass a standard the ubuntu bootup so the laptop can detect the installer usb inserted, and start the proceess of installing windows 10?

---

### Post by strangerthanbland on 2019-12-23
Problem 3: last I heard Chrome had some nasty video/audio bugs in the *stable* releases (version 78 or 79), the Beta version (80) so far seems to have no issues with video play back, also missing codecs can cause all manor of issues.

Problem 2: I'd first try the Play on Linux suite, in my experience it sets Wine up with the required configs and versions, and when that fails I usually resort to running Windows within a Virtual Machine, eg. Virtual Box

Problem 1: often boot hiccups can be bypassed by configuring Grub with `nomodeset`. Hint when ya see the Grub menu tap the `e` key to make temporary edits to configs, see the Q&A on [Ask Ubuntu]("https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu") for more details and how to make persistent Grub modifications.

Installing proprietary graphics drivers, via Driver Manager, may also help with Problems 1 & 3

There's a lot of hardware out there so initial setup of any OS can lead to frustrations; personally I find Linux based systems worth it, because there's usually permission to fix stuff instead of propitiatory software that has no such freedoms. If you've got more details as to what ya have tried so far with those three issues I'd be willing to read through and perhaps offer some assistance.


___


As for bypassing the Ubuntu bootup process `sudo systemctl reboot --firmware-setup` from an Ubuntu shell should restart into the BIOS menu, from there it depends on if you've got UEFI or Legacy boot enabled for selecting a USB connected drive to boot from.

Regardless of UEFI or Legacy boot, it basically boils down to setting the USB as a higher priority than the internal drive.


___


Oh and as far as precautions, be sure to backup anything important to an external drive that is formatted such that the new OS can read it (Fat32 or NTFS for Windows), also unmount **&** unplug the backup drive prior to installing any new OS. It might also be a good idea to make a Live Boot USB with the same version of Ubuntu that you're currently running, just in case the new OS barfs; few things are worse than having a device turn into a temporary paper-weight because there's no bootable OS available.

---

### Post by Impavidus on 2019-12-23
> **crip720 said:**
>  Most of us find ubuntu simpler to use, maybe you can explain what you find complex.

I don't fully agree with that. Although Ubuntu is not a system exclusively for geeks, it does require a bit more technical knowledge than Windows to use it effectively. Once you understand the basics, all of Ubuntu begins to make sense and it gets simple to use, I agree with that. For complex tasks, it's much simpler to use Ubuntu than Windows, once you know the basics. But if you just want a computer that works for basic applications, want to be able to download random stuff from the web and get it running on your computer, trust your anti-malware suit to protect you (most of the time) and don't care being locked-up in a Windows environment, then Windows is probably better.

I just wished those Windows people don't expect us free folk to join them in their prison. To me, open source means freedom from vendor lock-in. Like most people on Ubuntuforums, I prefer Ubuntu, but we must admit that Linux isn't for everyone. Although I think it is suited to more than the 2% or so of people who use it on their home computer.

> **nocruoro said:**
> And what buttons do i need to bypass a standard  the ubuntu bootup so the laptop can detect the installer usb inserted,  and start the proceess of installing windows 10?
It depends on your hardware. When you start your computer, usually the first thing you see for a few seconds is a screen with some logo of the hardware manufacturer and some text, before you see the grub menu or any Ubuntu logo. It should say which key to hit. Usually it's escape, F4, F12, delete or one of the other function keys. It should be the same as the one you used to boot the Ubuntu installer before you installed it.

---

### Post by crip720 on 2019-12-23
If you have grub page showing up on start, then the last line 'system setup'(?) should take you to bios setup, or google your computer for bios entry.  Set bios to boot from usb first.  The link for omgubuntu should give you all instructions to make usb installer,  if something you don't understand/not sure of, let us know.

---

### Post by yancek on 2019-12-23
You indicate you want to "go back" to windows so that implies you originally had windows 10 on the computer.  Did you format and overwrite the windows partitions when you installed Ubuntu?  If not, it is a simple process to change which system boots in the BIOS firmware.  If you no longer have the windows partitions, then the suggestions above should work.  Better yet, you might try the microsoft support site or a windows forum where people are more familiar with windows.

---

### Post by nocruoro on 2019-12-23
> **yancek said:**
> You indicate you want to "go back" to windows so that implies you originally had windows 10 on the computer. Did you format and overwrite the windows partitions when you installed Ubuntu? If not, it is a simple process to change which system boots in the BIOS firmware. If you no longer have the windows partitions, then the suggestions above should work. Better yet, you might try the microsoft support site or a windows forum where people are more familiar with windows.

I'm certain was completely overwritten. I rarely see the so called grub text before the logo for the login screen appears. Is there any tool that can diagnose what partitions are on a ubuntu pc before i consider doing the removal process?

> **Impavidus said:**
> 
It depends on your hardware. When you start your computer, usually the first thing you see for a few seconds is a screen with some logo of the hardware manufacturer and some text, before you see the grub menu or any Ubuntu logo. It should say which key to hit. Usually it's escape, F4, F12, delete or one of the other function keys. It should be the same as the one you used to boot the Ubuntu installer before you installed it.

Unfortunately  no such text "Press Button for ***" has ever appeared. It only shows a Acer logo screen then goes blank and loads ubuntu orange on purple background screen which loads the login screen.

---

### Post by SeijiSensei on 2019-12-23
Holding down Shift while booting should bring up the grub menu.

To view the structure of your hard drive, boot from an Ubuntu installation disk and pick Try Ubuntu. When it has finished booting, you can run the program gparted to see your drive.

---

### Post by crip720 on 2019-12-23
The disks program will show your partitions on the drive/s.  With Acer should be small text at the bottom, but will usually go to next screen too fast to read first time.  My Acer is F2 for bios and F12 to change boot order.  Button needs to be press during Acer logo screen being on, so have finger on button when starting.

---

### Post by yancek on 2019-12-23
If you have a GPT drive and only one drive the command below should output the partitions and type:

```
sudo gdisk -l /dev/sda
```

sudo fdisk -l and sudo parted -l should also output that information, the -l is a lower case Letter L in all commands.

---

### Post by nocruoro on 2019-12-25
> **SeijiSensei said:**
> Holding down Shift while booting should bring up the grub menu.

To view the structure of your hard drive, boot from an Ubuntu installation disk and pick Try Ubuntu. When it has finished booting, you can run the program gparted to see your drive.

My laptop has no CD-Drive only usb ports

---

### Post by yancek on 2019-12-25
> My laptop has no CD-Drive only usb ports 		

Not sure what that is in reference to?  If you still have the Ubuntu usb you used to install it, boot it with the Try Ubuntu option.  Have you done that and run the commands suggested?

---

### Post by nocruoro on 2019-12-26
> **yancek said:**
> Not sure what that is in reference to?  If you still have the Ubuntu usb you used to install it, boot it with the Try Ubuntu option.  Have you done that and run the commands suggested?

Haven't had enough time to do so, been busy with christmas cleaning and helping out at home

---

### Post by CelticWarrior on 2019-12-26
You're now at the point where you need to make a decision.

According to your other thread - [https://ubuntuforums.org/showthread.php?t=2430951&page=3&p=13919921#post13919921](https://ubuntuforums.org/showthread.php?t=2430951&page=3&p=13919921#post13919921) - and a reference here, your "problem" with Ubuntu is not being able to run the Lego software which is Windows native software. Having tried and initially failed with Wine you are now getting help from someone who seems to be pointing you in the right track. So, maybe, the reason for this thread is no longer valid. However, if all fails and you really need that software, you should consider running a Virtual Machine with Windows if the hardware is capable, or install Windows in dual-boot, like I already suggested in the other thread.

If, in the end, decide to install Windows instead of Ubuntu, not as a dual-boot, then you may. Boot Windows installation media and when it asks where to install make sure to select and delete the partitions already there. From that point on the Windows installer will do everything for you. Please also note that detailed instructions on how to install Windows are outside of the scope of this forum, for obvious reasons. That you have Ubuntu already installed is relevant for dual-booting but totally irrelevant if just installing one OS instead of the other.

---

### Post by nocruoro on 2019-12-29
[COLOR=#008000][SIZE=5]After much speculation i've decided it's safest to consult with my dad who knows a bit about re-installing operating systems.

[/SIZE][/COLOR][COLOR=#ff8c00][SIZE=5]this thread should be closed.[/SIZE][/COLOR][COLOR=#008000][SIZE=5][/SIZE][/COLOR]

---

