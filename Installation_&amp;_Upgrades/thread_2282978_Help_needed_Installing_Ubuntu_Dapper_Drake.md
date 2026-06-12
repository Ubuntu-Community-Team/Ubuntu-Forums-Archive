---
title: "Help needed Installing Ubuntu Dapper Drake"
date: 2015-06-18
forum: Installation &amp; Upgrades
---

### Post by Ali_Ashal on 2015-06-18
I'm trying to install Ubuntu Dapper Drake and I'm a total newbie to these things. Firstly I have a reallyyyy old laptop on which I only have 20 GB HDD due to which I decided to replace windows with Ubuntu. Currently I have 3 partitions, 3GB (empty), 5GB (empty), 70MB (partitioned as linux-swap) and a 10 GB partition with 1 GB free (its having windows on it). I wan't to partition manually but I can't understand anything, can anyone please guide me through everything? Secondly I need help to getting WiFi running on this. P.S. My laptop is an Dell Inspiron 700m with RAM upgraded to 2 GB. Thanks in advance...

---

### Post by cmcanulty on 2015-06-18
first of all I would burn a dvd  with the latest version of xubuntu or lubuntu (15.04)and use the install DVD to do the partitioning.  Dapper Drake is very old and long out of support. I expect with your older computer try Lubuntu, it would run very well and fast with 2 GB Ram. I also suggest in the installer in the partition page choose something else and  use ext4 file system with 5-8 GB for / (this would be your boot files, operating system, and apps), 2GB for Linux swap and the rest for /Home (for your docs and most settings). By having a separate /Home partition your docs and most setting are not affected if your system gets corrupted or you just want to reinstall or do a clean upgrade. Post back as you try this if you need more info.

---

### Post by grahammechanical on 2015-06-18
Dapper Drake was before my time. So, I do not know if it was possible to install updates during the installation process as we do today. But anyway, you should not tick to install updates as part of the installation process because the Dapper Drake software repositories are closed and are no longer at the server addresses that the installer program has listed for them.

Therefore, you will get errors when it come to installing. And you will not be able to update or install software. And that includes proprietary video and WiFi drivers. If the live session is not recognising the wireless adapter then you will need a proprietary driver.

Because Dapper Drake is so old and Ubuntu has changed so much since then I think it will be very difficult explaining how to do things in Dapper Drake. Does anybody remember how to set up a wireless connection on those old version of Ubuntu?

Partitioning is much the same

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Regards.

---

### Post by kansasnoob on 2015-06-18
Dapper has been EOL for nearly six years:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

The specs for that laptop show it as having an Intel Pentium M 725 / 1.6 GHz CPU so I think you'll need either a current non-pae distro or Lubuntu fake pae:

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

If I were you I'd download the i386 desktop version of Lubuntu 14.04.1 (not 14.04.2 so you can avoid [HWE EOL]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")):

[http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/)

And then just use the forcepae boot option to either run the live DE or to install, and then edit grub on the installed system using Boot Repair:

[https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation](https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation)

Please feel free to ask more questions. **[COLOR="#FF0000"]Perhaps even start a new thread requesting help installing a non-pae Lubuntu Trusty[/COLOR]**.

---

### Post by ajgreeny on 2015-06-18
> **kansasnoob said:**
> Dapper has been EOL for nearly six years:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

The specs for that laptop show it as having an Intel Pentium M 725 / 1.6 GHz CPU so I think you'll need either a current non-pae distro or Lubuntu fake pae:

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

If I were you I'd download the i386 desktop version of Lubuntu 14.04.1 (not 14.04.2 so you can avoid [HWE EOL]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")):

[http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/)

And then just use the forcepae boot option to either run the live DE or to install, and then edit grub on the installed system using Boot Repair:

[https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation](https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation)

Please feel free to ask more questions. **[COLOR=#FF0000]Perhaps even start a new thread requesting help installing a non-pae Lubuntu Trusty[/COLOR]**.
^^^
+1

It will not be possible to install updates while you install the system as there are no more updates available for Dapper Drake, or not from the repository address that the installer would use anyway, and if you try I suspect that the whole installation will just grind to a halt.

Lubuntu 14.04.1 is very worthwhile looking at and I am pretty sure that using the forcepae boot option it should work fine, though I don't have any hardware old enough to test that theory.

---

### Post by Ali_Ashal on 2015-06-18
Thanks guys, I installed Xubuntu 12 and its running perfectly :)

---

### Post by mörgæs on 2015-06-18
Xubuntu 12.* is unsupported just like Dapper. Your options are 14.04.2 and 15.04.

---

### Post by Ali_Ashal on 2015-06-19
Will 14.04.2 run on my laptop? Its a Pentium M with 2 GB RAM and 20GB HDD :lolflag:

---

### Post by Ali_Ashal on 2015-06-19
BTW can I run Xubuntu 14.04.2? I like its GUI, Lubuntu doesn't look good.

---

### Post by cmcanulty on 2015-06-19
As I said originally try Xubuntu 14.04 it is long term support and would work for you, I even use it with 1GB ram on a few old laptops

---

### Post by v3.xx on 2015-06-19
> **Ali_Ashal said:**
> BTW can I run Xubuntu 14.04.2? I like its GUI, Lubuntu doesn't look good.

Lubuntu, like most linux distros and flavors, are 100% changeable.  Really no need to move on just because of looks.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=customize+lubuntu+desktop&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=customize+lubuntu+desktop&sa=Search&cof=FORID:9)

And considering your computer specs, I think you would be better off with Lu.

---

### Post by cmcanulty on 2015-06-19
I do too but he said he likes the looks of Xubuntu, Lubuntu will definitely be faster

---

### Post by kansasnoob on 2015-06-19
I'd think Xubuntu would work with [the forcepae trick]("https://help.ubuntu.com/community/Lubuntu-fake-PAE") just like Lubuntu, they both use the same Linux kernels. But I would use [the 14.04.1 version]("http://cdimage.ubuntu.com/xubuntu/releases/14.04/release/") to avoid [HWE EOL]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") in August 2016.

---

### Post by Ali_Ashal on 2015-06-19
Okay, I would try both by making a bootable thumbdrive. If Lubuntu is fast, I'm installing it.
Secondly, I'm a total noob for this linux thingy, is forcepae method complicated? I need a detailed tutorial on how to setup Ubuntu 14 on my laptop :(
BTW Thanks everyone, you guys rock ;)

---

### Post by kansasnoob on 2015-06-19
Details for using forcepae with the live image:

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

After installation to edit grub:

[https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation](https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation)

---

### Post by mörgæs on 2015-06-20
First let's be sure that PAE is in fact necessary. There could be more than one processor used for a 700m, so we need to look at this particular one.

Using any distro please run ```
sudo lshw -sanitize > lshw.txt
``` in a terminal and post lshw.txt in CODE tags.

---

### Post by Ali_Ashal on 2015-06-21
I have installed Lubuntu 14.04.1 using forcepae, but I haven't edited Grub using boot-repair as I don't know how to open it. Otherwise its running perfectly.
Can anyone tell me how to open boot-repair and edit Grub and what to edit there?

---

### Post by sudodus on 2015-06-21
Don't fix it if it is working ;-)

***Boot repair*** is not for editing grub, but rather for installing the grub bootloader in a correct way, but it seems you don't need that.

---

### Post by Bucky Ball on 2015-06-21
You don't need Boot Repair as your machine is running perfectly. All you need to do now is enjoy your new OS! :)

Please mark the thread as solved as it appears your original support request is solved. See the second link in my signature. This will _not_ close the thread to future discussion, but it will help future travelers. Have fun and post a new thread if you have any other support issues.

---

### Post by oldos2er on 2015-06-21
> **Ali_Ashal said:**
> I have installed Lubuntu 14.04.1 using forcepae, but I haven't edited Grub using boot-repair as I don't know how to open it. Otherwise its running perfectly.
Can anyone tell me how to open boot-repair and edit Grub and what to edit there?

As others have said, boot-repair is not a grub editor, but [grub-customizer]("https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer") is.

---

