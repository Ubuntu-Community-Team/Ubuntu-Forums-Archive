---
title: "Cannot install on ASUS Eee PC Surf (2G)"
date: 2016-09-11
forum: Installation &amp; Upgrades
---

### Post by brool on 2016-09-11
Hi All;

I am new to Linux.
was trying to install "lubuntu-16.04.1-alternate-i386" on an old ASUS Eee PC that i have. everything went well until i reached the actual installation of the software stage. i got an Error that the system cannot be installed but w/o explanation as to why

This PC have 512Mhz memory with 2G HD
will highly appreciate your help in this matter

Regards

---

### Post by howefield on 2016-09-11
With no further information on the actual error it is difficult to offer anything, the minimum requirements for Lubuntu include having a 2 gigabyte hard drive, could well be insufficient space.

---

### Post by RobGoss on 2016-09-11
I think Howefield had pointed out what the problem maybe, it looks like you barely have enough hard disk space along with very little Ram, you might what to rethink what OS is right for that machine

I would suggest getting a machine with more hard disk space and Ram, in order to run Ubuntu on it. I'ts kind of border line here with those specs

---

### Post by mörgæs on 2016-09-11
From a live boot please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags. It will show us the hardware details.

---

### Post by sudodus on 2016-09-11
2 GB hard disk drive (or SSD) is not enough to install Lubuntu. The standard installer needs more than 4 GB, but an installed system can do with 4 GB. I think a fully installed Lubuntu will use about 2.6 GB in the root file system and with 512 MB RAM, you had better add a swap partition of maybe 1 GB. One alternative is to install Lubuntu into a fast USB pendrive, and boot your eeePC from there.

It is probably easiest to grab a compressed image file and flash it like operating systems for mobile phones, Raspberry Pi and similar devices.

See the following links

[Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Tested and debugged system to install [Ubuntu flavours of] Xenial 32-bit alias 16.04 LTS](https://ubuntuforums.org/showthread.php?t=1958073&page=19&p=13511300#post13511300)

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

You may want a minimal system, and only install the most important program packages. In that case it would do with a 2 GB drive, except that the compressed image file assumes that the drive size is at least 4 GB. So this is not a solution unless you use a separate USB pendrive or SD card.

***There are extremely light-weight linux distros too, for example Wary Puppy, TahrPup and Tiny Core.***

Download and try several linux distros. Try them live, and install what you like the best. It is possible to install a ***persistent live*** system. It needs less space than an installed system, because most of the programs are stored in a compressed file system. Puppy and I think also Tiny Core will run live-only or persistent live. Ubuntu can also be 'installed' persistent live.

See also this link

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

Another option is to try the One Button Installer, the OBI, and let it install this mini system from a tarball. It *should* work also with a 2 GB drive, but you must be very careful and avoid installing Lubuntu or even Lubuntu Core, because they need more drive space. Install only the most necessary program packages.

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

[OBI/Trusty-mini-txt](https://help.ubuntu.com/community/OBI/Trusty-mini-txt)

[OBI/Xenial-32-txt](https://help.ubuntu.com/community/OBI/Xenial-32-txt)

---

### Post by kalehrl on 2016-09-12
Try to install ubuntu mini-iso followed by lubuntu-core as described here:
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

### Post by sudodus on 2016-09-12
I checked, and the One Button Installer did not work directly :-(, because of a limit (that I set long ago and forgot about). The minimum drive size at the basic OBI level is 4 GB. But as usual in linux, there is a workaround :-)

You can use ***gparted*** [in the system with the OBI] according to the attached screenshot #1.

0 - Select the correct drive, where you want to install the system (in this case the 2 GB drive, 2 GB = 1.87 GiB (base 2)).
1 - You may want to select to see the Device information panel.
2 - Device -- Create partition table - the default, MSDOS partition table is OK.

Create a partition that uses the whole drive, select the **ext4** file system and create the label **obiroot**

3 - Click the tick to start the action.

After that the 2 GB drive will be ready for the advanced OBI level (select it in the starter menu 'select basic or advanced')

Start the OBI and use its menus:

- Download a tarball, and I suggest **X32-Txt-Startx-Intl_2016-06-29.tar.xz**
- Select this tarball
- Start the installer: 'Install tarball'

Check with the attached screenshot #2.

- with the label obiroot, the partition should be selected automatically.
- there is no swap partition, so go ahead.

I did this, and after the OBI had finished I moved the card to another computer and it booted and runs now. I quit from the menu to the bash shell, and checked the used and free space with the command

```
df -h
```

It reports that 1.3 GiB is used and 492 MB is free.

***Conclusion:*** It is possible to run this installed Xenial mini system in a 2 GB drive. And there is already a minimal graphical system with the window manager ***fluxbox***, that you can can start from the menu. If you right-click you can select the available application programs (not many are installed, but at least, you can run the terminal emulator ***xterm***).

But ***492 MB free space***, before you have started to install applications ***is not enough except for testing***. So I would really recommend that you either install a persistent live system or intstall your system into a fast USB 3 pendrive.

---

### Post by sudodus on 2016-09-12
> **kalehrl said:**
> Try to install ubuntu mini-iso followed by lubuntu-core as described here:
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

You can install ubuntu mini-iso, but there is not enough space for lubuntu-core in a 2 GB drive.

Only after getting the mini system up to date and cleaning (removing cruft after the update && upgrade), the used space has increased to 1.6 GIB.

After installing lubuntu-core with the light-weight Midori web browser (into a system with more drive space), and cleaning, the used space has increased to 2.5 MiB, which is way beyond the available size in this case, 2 GiB. After purging Midori, and cleaning, it still uses 2.5 GiB (only around 50 MiB was removed from the drive).

---

### Post by kalehrl on 2016-09-12
Maybe skip creating swap and install lubuntu-core with --no-install-recommends.

---

### Post by sudodus on 2016-09-12
There was no swap in my test. Yes, it might help with --no-install-recommends, but the drive would be almost full. The 2 GB limit is really too low for a modern full size linux operating system with a desktop environment.

---

### Post by kalehrl on 2016-09-12
I have Debian Jessie on an eee pc 4g installed using expert install, no swap and lxde-core with --no-install-recommends.
I moved some folders to tmpfs to reduce writes and I've got firefox installed.
The system takes just 699MB.
There was a nice thread on Debian forum about how to install Debian mini but it's gone now.

---

### Post by sudodus on 2016-09-12
That's nice *kalehrl* :-)

It seems Debian Jessie can be made much smaller than Ubuntu Xenial because what you describe is far less than what you get with the most basic Ubuntu Xenial mini installation. I did some work on Debian Wheezy some year ago (but I have very little experience with Jessie except from ToriOS). And Wheezy could make much smaller systems than Ubuntu Trusty. See this link,

[RAM and disk usage tests with Trusty non-pae and Debian Wheezy](https://help.ubuntu.com/community/9w/RAM_%26_disk_usage)

---

### Post by brool on 2016-09-18
Hi All;

thank you for your answers and support. and most of all your valuable time.
as i'm new to all of this i will read again the suggestions carefully and will follow your guides.

i need this laptop mainly for surfing at home and i prefer it over any tablet i have
i will consider the mini iso and will probably give it a try when i'll find the time again

regards;

---

