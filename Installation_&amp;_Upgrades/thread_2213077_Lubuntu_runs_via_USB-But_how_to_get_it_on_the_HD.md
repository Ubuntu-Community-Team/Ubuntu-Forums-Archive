---
title: "Lubuntu runs via USB-But how to get it on the HD?"
date: 2014-03-24
forum: Installation &amp; Upgrades
---

### Post by jjs2 on 2014-03-24
Hi i've got an oldie Dell D600 here and booted from USB using Lubuntu 13.10. All runs fine.
But i can't find a simple guide, how to install it on the HD. THe only guides i find is how to make a bootable usb, well i've got that.
It seems i succeeded to get the grub on the HD, but i'm not sure.

Can anyone tell mee please how to install it on the HD?  Thanks a lot!

nb i used the dd_saucy-a2-installed-system_4GB.img and converted it to dd_saucy-a2-installed-system_4GB.iso and made a bootable usb from it which works fine.
Now the install to HD is what is not succeeding, any help would be appreciated ! Thanks !

---

### Post by monkeybrain20122 on 2014-03-24
[https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu](https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu)

BTW, not sure which genuis told you to use dd to make a live usb. It can be dangerous if you are not careful and when you want to recover it later you have to use dd again (reformatting doesn't work) You could have used unetbootin.

---

### Post by buzzingrobot on 2014-03-24
You should have seen a very obvious choice between "Try Lubuntu" and "Install Lubuntu".

"dd_saucy-a2-installed-system_4GB.img" is not a standard name for the Lubuntu install ISO.  Download the appropriate image from the Lubuntu.net site, burn it to the USB, and give it a go.

---

### Post by jjs2 on 2014-03-25
Hi Thank you both for your answers.
I used this install because it has the no PAE option in it. So after some reading, it seemed the best option to use it. As i hoped to install it on an Pentium M machine. Well it runs smoothly. The harddisk is allready formatted, so it's ready to receive Lubuntu. I choose Lubuntu because it is light. But does the normal Lubuntu installation also run witn no PAE. (allthough i'm not 100% sure if the machine needs it, because there seems to be Pentium M with and without PAE). But i could give it a try.

---

### Post by mörgæs on 2014-03-25
Your approach is fine. The ISO you tried is probably the one described in these guides:
[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)
and installing with dd is the correct way to go. Please ignore the less helpful comments above. 

If you want to know whether or not your Pentium is able to run a standard ISO please post the output from
```
sudo lshw -C cpu
```

More about PAE:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by jjs2 on 2014-03-25
Thanks Morgaes !

it says±
Intel Pentium)R' M processor 1400MHz
then a bunch of non worthy to mention things
size 1400MHz
capacity 1700MHz
width±32 bits
clock 133 MHz
Capabilities± fpu fpu?exception wp pae vme de pse tsc msr mce cx8 sep mtr r pge mca cmov clflush dts acpi acpi mmx fxsr sse sse2 tm pbe bts est tm2 cpufreq

so i think this processor is capable of PAE, am i correct?

if so i would mean i could simply install ubuntu or Lubuntu like it is and do not need fake pae or a raring version right?

Thanks for your help!

---

### Post by mörgæs on 2014-03-25
The PAE flag you see might be fake. All CPU's have PAE, but a few of them do not show the flag by default, so they need a little help, hence the fake flag.

The output wasn't detailed enough. Please try **lscpu** and post everything (with cut and paste).

---

### Post by jjs2 on 2014-03-25
In the meanwhile i tried a lubuntu-13.10-alternate-i386.iso, so now i had the confirmation that it needs PAE.

so now i tried the lscpu command ( i cant copy/paste) because it is not my main pc
but here it is:
Architecture:    i686
CPU op-mode(s): 32-bit
Byte order: Little Endian
CPU(s): 1
On-Line CPU(s) list: 0
Thread(s) per core: 1
Core(s) per socket: 1
Socket(s): 1
Vendor ID: GenuineIntel
CPU family: 6
Model: 9
Stepping: 5
CPU MHz: 1400.00
BogoMIPS: 2790.95


that's it

Thanks!

---

### Post by jjs2 on 2014-03-25
i'm following the steps on the bottom of the page you wrote at [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by mörgæs on 2014-03-25
You have a 6.9.5 Pentium M, so the normal ISO's do not install. 
Your options are the two links from post 5.

---

### Post by sudodus on 2014-03-25
Hi jjs2,

I made and uploaded **dd_saucy-a2-installed-system_4GB.img.gz**

You can use that file directly to create a system on a hard disk drive, if you use the tool ***mkusb*** (using the version of Lubuntu, that is running now). If the files are in the current directory use this command (and let mkusb select which drive to use)

```
sudo ./mkusb dd_saucy-a2-installed-system_4GB.img.gz
```

You can use the description in these links

[https://help.ubuntu.com/community/InstalledSystemFakePAE](https://help.ubuntu.com/community/InstalledSystemFakePAE)
[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

After that you would like to use the whole drive or at least more than 4 GB. Grow the root partition, and create a swap partition if you like (using gparted) according to this link

[http://phillw.net/isos/linux-tools/9w/GrowIt.pdf](http://phillw.net/isos/linux-tools/9w/GrowIt.pdf)

But this method uses the whole drive (it overwrites the partition table and does not allow dual booting. If you want dual booting, try one of these methods instead

[https://help.ubuntu.com/community/grub-n-iso](https://help.ubuntu.com/community/grub-n-iso)
[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

If you want to find out if you CPU has a PAE flag, you can try the following command

```
cpuid|grep ^00000001
```

and compare it to the table of CPUs according to this link
[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

You can also try ***Trusty***, the version being developed right now, that will be released in April as Lubuntu 14.04 LTS. This version can use the boot option **forcepae** to make Pentium M CPUs boot and run.

Let us know what you want, and you can get more details how to get it :-)

---

### Post by jjs2 on 2014-03-25
Thanks Sudodus, that was the one i downloaded first, going to try again. And if it fails again i will switch to Debian as a colleauge told me that it should install without the PAE hasle.
But i could wait on Trusty, or is there maybe a beta version?

---

### Post by jjs2 on 2014-03-25
whaaaaaaaah it really pisses me off. I don't get it........:(((((
It looks like the only thing talked about on those pages is how to make your bootable usb pffffffffffffffff
it is allready running
I'm using you dd img and transferred it to the usb, the pc is up and running from the usb, there is no other systme installed on it so no dual boot is needed

i think i'm going to quit it and reinstall Windows XP, support or no support it will run, maybe not so fast but with less hasle.
Thanks for all your help guys.
But it is to much of a hasle.....

---

### Post by mörgæs on 2014-03-25
> **jjs2 said:**
> i'm following the steps on the bottom of the page you wrote at [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

Which steps exactly?

---

### Post by sudodus on 2014-03-26
> **jjs2 said:**
> whaaaaaaaah it really pisses me off. I don't get it........:(((((
It looks like the only thing talked about on those pages is how to make your bootable usb pffffffffffffffff
it is allready running
I'm using you dd img and transferred it to the usb, the pc is up and running from the usb, there is no other systme installed on it so no dual boot is needed

i think i'm going to quit it and reinstall Windows XP, support or no support it will run, maybe not so fast but with less hasle.
Thanks for all your help guys.
But it is to much of a hasle.....

If you are running ***mkusb***, you can 'toggle USB-only' with **[COLOR=#0000ff]u[/COLOR]** and get options to install into an internal HDD.

```
Do you want to clone dd-LubuSaucy-pae2pm-4GB.img.xz to a mass storage device (typically USB drive)? (y/n)
y
[COLOR=#0000cd]***  WARNING: the device will be completely overwritten      ***
     Use the info in the xterm window (less /tmp/help-mkusb.txt)
***  quit with (q)                                           ***
[/COLOR]***  Unmount the device if mounted  ****************************
 
Model: ATA SAMSUNG HD322HJ (scsi)    Disk /dev/sda: 320GB    
Model: ATA OCZ-AGILITY3 (scsi)    Disk /dev/sdb: 60.0GB    
Model: ATA WDC WD1003FBYZ-0 (scsi)    Disk /dev/sdc: 1000GB    
Live drive: /dev/sdb
 
No USB target device available. Toggle USB-only?
Go ahead with (g) or quit with (q). Toggle USB-only with (u).
u
[COLOR=#0000cd]---> 1: install to ATA SAMSUNG HD322HJ (scsi) Disk /dev/sda: 320GB
[/COLOR]#       could not unmount /dev/sdc because file system on device is busy
Go ahead with (g) or quit with (q). Toggle USB-only with (u).

```

---

### Post by jjs2 on 2014-03-26
Thanks Sudosus,

so let me get this clear.

1. I boot from the USB stick Lubuntu.
2. Then from within Lubuntu which is loaded and running then i start mkusb, and toggle USB only with u and then i can install it to the internal HDD? (note there is no other system on that pc)

Just like that?

@Morgaes i mean the steps 1 till 7. Thanks.

I even tried Debian, it installs right away, but after reboot i'm only seeing a dos box and no Gnome or KDE or whatever.....

Maybe if the 2 steps or sufficient after strating Lubuntu from USB stick, i might give it another try tonight, Thanks !

---

### Post by sudodus on 2014-03-26
> **jjs2 said:**
> Thanks Sudosus,

so let me get this clear.

1. I boot from the USB stick Lubuntu.
2. Then from within Lubuntu which is loaded and running then i start mkusb, and toggle USB only with u and then i can install it to the internal HDD? (note there is no other system on that pc)

Just like that?


You need to download ***mkusb***, for example from this link

[http://phillw.net/isos/linux-tools/mkusb/](http://phillw.net/isos/linux-tools/mkusb/)

***mkusb*** is a simple shell-script and needs no installation, but you can install it into for example **/sbin** or make your own bin directory and put it there (**/home/$USER/bin**). Then use it without any path

```
sudo mkusb file.img.gz
```

But to use it only a single time, you can simply have mkusb in the current directory, where you have also the compressed image file.

```
sudo ./mkusb file.img.gz
```
or
```
sudo ./mkusb file.img.xz
```

and when asked, toggle USB-only and select the correct target drive (in this case an internal drive)

---

### Post by jjs2 on 2014-03-26
Thank you very much Sudosus for explaining!
I will test it tonight!

---

### Post by sudodus on 2014-03-26
Good luck :-)

---

### Post by jjs2 on 2014-03-26
I wrote the dd-saucy version to the usb stick again and started the laptop again and booted from the stick
Luckely the piece of debian(without a gui) was still on it, so now i directly saw the icon upperleft "Install Lubuntu 13.10" so i thought click it.
And it worked the system is no up and running fine, so i did not have to use the mkusb application.

_**I would like to thank you very much for your efforts Sudodus !!!**_

Also thank you Morgaes!

What would people do without you 2, thanks again !

---

### Post by sudodus on 2014-03-26
I'm glad you made it and have a running installed system now. Congratulations :KS

You can come back (with a new thread) if you need help with the system in the future ... and finally, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by mörgæs on 2014-03-26
You don't have to thank us. Just write some helpful posts here when you feel like it. 

Welcome to the free world :-)

---

### Post by jjs2 on 2014-03-26
Thanks anyway ! :)

---

