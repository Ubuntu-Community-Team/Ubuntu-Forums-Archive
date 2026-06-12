---
title: "trying to upgrade Inspiron 700m to Xubuntu 14.04 - impossible???"
date: 2015-07-30
forum: Installation &amp; Upgrades
---

### Post by Buntu Bunny on 2015-07-30
My old Dell Inspiron 700m sports Xubuntu 12.04.Today I tried to upgrade to 14.04 but got a message that I must first enable PAE. 

I attempted a DVD install, following the directions at help.ubuntu.com/community/PAE, but apparently PAE is not installed. 

Next I followed the directions on help.ubuntu.com/community/PAE/PentiumM for upgrading, but still had problems.

```
buntubunny@buntubunny-Inspiron-700m:~$ apt-get install linux-image-generic-pae
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
buntubunny@buntubunny-Inspiron-700m:~$ uname -a
Linux leigh-Inspiron-700m 3.2.0-88-generic #126-Ubuntu SMP Mon Jul 6 21:35:35 UTC 2015 i686 i686 i386 GNU/Linux
```

To install PAE (according to that help page) I need 3.11 or above, so am I to understand that my 3.2 is outdated?

IOW am I attempting the impossible?

---

### Post by dino99 on 2015-07-30
PAE is not something you can install, its a builtin hardware feature: so if your mobo has PAE capabilities, then it is listed as explained by:
 [http://askubuntu.com/questions/179958/how-do-i-find-out-my-motherboard-model](http://askubuntu.com/questions/179958/how-do-i-find-out-my-motherboard-model)
and you need to enable that option into the bios (ram settings)

otherwise you will need to use this howto: [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)  as the recent have removed support for non pae mobo ( linus decision)

---

### Post by tgalati4 on 2015-07-30
While booted into any linux distro, open a terminal:

```
grep pae /proc/cpuinfo
```


It might look like:

> 
tgalati4@Mint17 ~ $ grep pae /proc/cpuinfo
flags		: fpu vme de pse tsc msr **pae** mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
flags		: fpu vme de pse tsc msr **pae** mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm


---

### Post by Buntu Bunny on 2015-07-30
> **dino99 said:**
> ... otherwise you will need to use this howto: [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)  as the recent kernels have removed support for non pae mobo ( linus decision)

That's the howto I used, as mentioned in my original post. 

> **tgalati4 said:**
> While booted into any linux distro, open a terminal:

```
grep pae /proc/cpuinfo
```

No output. :confused:

---

### Post by Dennis N on 2015-07-30
> **Buntu Bunny said:**
> 
grep pae /proc/cpuinfo
No output. :confused:
Part of the command is missing. Instead, try: **cat /proc/cpuinfo** or **cat /proc/cpuinfo | grep pae**
The first is the full information on your cpu, the second only gives lines containing 'pae'


In the output, 'pae' is going to be mentioned in the line starting 'flags'.

---

### Post by Buntu Bunny on 2015-07-30
> **Dennis N said:**
> Part of the command is missing. Instead, try: **cat /proc/cpuinfo** 

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Pentium(R) M processor 1.70GHz
stepping	: 6
microcode	: 0x17
cpu MHz		: 600.000
cache size	: 2048 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2
bogomips	: 1196.09
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:

```

Nothing about pae under 'flags' as in tgalati4's example. Am I correct to suspect that this is a no-go for this little old computer?

---

### Post by sudodus on 2015-07-30
I think the command and the result are correct.

According to [http://www.cnet.com/products/dell-inspiron-700m/specs/](http://www.cnet.com/products/dell-inspiron-700m/specs/)

> Processor / Chipset

    CPU
    Intel Pentium M 725 / 1.6 GHz
    Cache
    L2 - 2 MB
    Data Bus Speed
    400 MHz
    Chipset Type
    Intel 855GME
    Features
    Enhanced SpeedStep technology



it is a typical Pentium M processor with PAE capability but no PAE flag. ***You can use the boot option forcepae in Trusty (14.04 LTS) and newer***, or you can use 12.04 LTS. The 3.2 kernel has a non-pae version. If you use version 12.04.2 or later, you need fake-pae. See the following links

[Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

or maybe kansasnoob's [Precise Gnome Classic Tweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks), that you get easily (with fake-pae installed) as a tarball to be installed by the [One Button Installer](https://help.ubuntu.com/community/OBI).

---

### Post by Dennis N on 2015-07-30
> **Buntu Bunny said:**
> Nothing about pae under 'flags' as in tgalati4's example. Am I correct to suspect that this is a no-go for this little old computer?

No, It should work. Looks like that model  processor (Pentium M  1.70 gHz) is one of the earliest Pentium Ms, and does not display its capabilities when queried (but it still has pae capabilities):

From Wikipedia:

> The Banias family processors internally support PAE but do not show the PAE support flag in their CPUID information; this causes some operating systems (primarily Linux distributions) to refuse to boot on such processors since PAE support is required in their kernels

[https://en.wikipedia.org/wiki/Pentium_M](https://en.wikipedia.org/wiki/Pentium_M)

Once the OS is installed, from what I have read it should be fine. I'm not up on this issue as I've never run into it. I would think the guides should get it done?

---

### Post by sudodus on 2015-07-30
A friend of mine has an IBM Thinkpad with exactly the same processor. I have an IBM Thinkpad with a very similar processor. Both computers work well for us with Lubuntu and Xubuntu.

I installed the following system for my friend:

***Xubuntu 14.04.1 LTS*** and into that [B][I]Lubuntu Core
[/I][/B]
```
sudo apt-get install lubuntu-core
```

That way you can get an ultra-light LXDE desktop environment that can run video better than Xubuntu. But for other purposes you can take advantage of the more polished and advanced interface of Xubuntu (with XFCE).

---

### Post by Buntu Bunny on 2015-07-30
> **sudodus said:**
> I think the command and the result are correct.

According to [http://www.cnet.com/products/dell-inspiron-700m/specs/](http://www.cnet.com/products/dell-inspiron-700m/specs/) it is a typical Pentium M processor with PAE capability but no PAE flag. ***You can use the boot option forcepae in Trusty (14.04 LTS) and newer***, or you can use 12.04 LTS. The 3.2 kernel has a non-pae version. If you use version 12.04.2 or later, you need fake-pae. See the following links <snip>

sudodus, thanks. I tried the forcepae but got an error message. I didn't write it down so I don't recall what it was, but it seems I need to go a different route. I will take a look at the links you provide and see if there is something I can do.

This was a freebie computer that I've used for learning and experimenting. It hasn't failed me in the learning department, as this thread shows. It does well with Xubuntu 12.04, so if that's the best it'll be able to do, I'll still get a few more years out of it until support ends.

> **Dennis N said:**
> No, It should work. Looks like that model  processor (Pentium M  1.70 gHz) is one of the earliest Pentium Ms, and does not display its capabilities when queried (but it still has pae capabilities):

From Wikipedia: [https://en.wikipedia.org/wiki/Pentium_M](https://en.wikipedia.org/wiki/Pentium_M)

Once the OS is installed, from what I have read it should be fine. I'm not up on this issue as I've never run into it. I would think the guides should get it done?

Well, that's curious and feeling a bit above my head. I followed [community help for PAE and PentiumM]("help.ubuntu.com/community/PAE/PentiumM"), but without success. Unless I overlooked something. 

So, I need to keep trying but need to do a little more study and digging first.

---

### Post by Buntu Bunny on 2015-07-30
> **sudodus said:**
> A friend of mine has an IBM Thinkpad with exactly the same processor. I have an IBM Thinkpad with a very similar processor. Both computers work well for us with Lubuntu and Xubuntu.

I installed the following system for my friend:

***Xubuntu 14.04.1 LTS*** and into that [B][I]Lubuntu Core
[/I][/B]
```
sudo apt-get install lubuntu-core
```

That way you can get an ultra-light LXDE desktop environment that can run video better than Xubuntu. But for other purposes you can take advantage of the more polished and advanced interface of Xubuntu (with XFCE).

sudodus, I missed this. I must have been typing my other reply when this was posted. 

Are you saying you installed Lubuntu Core first, and then Xubuntu 14.04? Or was it the other way around? If so I'll need to figure out how to get 14.04 on there first. For that I need to take a closer look at the [Lubuntu-fake-PAE link]("https://help.ubuntu.com/community/Lubuntu-fake-PAE") you mentioned. It looks like it might have some help for me.

---

### Post by sudodus on 2015-07-30
I suggest that you try again with the boot option **forcepae**.

The error message can be about something else, for example the graphics or wifi. If the graphics causes problems, you can try to boot with the boot option **nomodeset** (you can have many boot options, just write them after each other on the 'linux line').

---

### Post by Buntu Bunny on 2015-07-30
> **sudodus said:**
> I suggest that you try again with the boot option **forcepae**.

Will do. I won't be able to get to it until tomorrow, but will report back then.

---

### Post by Buntu Bunny on 2015-07-30
> **sudodus said:**
> I suggest that you try again with the boot option **forcepae**.

I tried this again. I guess because I had added forcepae -- forcepae previously, I got the keyboard and man, then it skipped the menu screen and went directly to the following message:

> WARNING: PAE disabled. Use parameter 'forcepae' to enable at your own risk! This kernel requires the following features not present on the CPU: pae
Unable to boot - please use a kernel appropriate for your CPU.

Then there's a blinking cursor that doesn't appear to respond to the keyboard including any of the Alt+SysRq+ combinations. I'm not sure what else to do besides a hard reboot.

I seem to be stuck here at the moment.

---

### Post by sudodus on 2015-07-31
It seems that you have not managed to activate the boot option forcepae.

What you write indicates that you have done things correctly, but the boot option is not recognized anyway :confused:

from [https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M):
> Lubuntu 14.04 LTS 'Trusty' can use the boot option forcepae and can be installed using the standard installers.

After selecting language you arrive at the main menu of the installer. Click on F6

At the boot menu screen the options are

    Try Lubuntu without installing (in the desktop installer but not in the alternate installer]
    Install
    ... 

[COLOR="#006400"]**With the Install choice high-lighted press F6**[/COLOR]. (This option needs less RAM than installing from 'Try Lubuntu')

A menu with a number of options appears. The option 'forcepae' is not there, so press Escape to close the list.

Now a string of options is visible, often with 'quiet' or 'quiet splash --' at the end. Add 'forcepae' to the string before and after the two dashes.

... quiet splash forcepae -- forcepae

Press return, and the installation begins.


0. how much RAM is there in the computer? Lubuntu needs 512 MB, Xubuntu needs 1 GB.
1. maybe you made some minor error when you were typing
2. maybe you entered it in the wrong place
3. maybe the motherboard is made to not allow a pae kernel (is checking somehow).
4. maybe the CPU is not exactly like the very similar one of my friend (that it simply lacks PAE capability - but I don't think so)

Does this happen when you boot a live session (or is it an installed system)? The instructions assume you boot a live session, and are in the 'syslinux menu', click F6 and then escape to edit at the end of the 'linux line'.

Which version of Xubuntu are you trying to boot (14.04.1, 14.04.2)?

How did you create the boot media?

Did you check with md5sum that the download was good?

Did you check that the DVD is good, that it can boot another computer?

Did you check that the DVD drive is good, that is can boot another DVD disk? Maybe it is only a CD drive, and needs a CD disk (700 MB), or can burn only CD disks?

Maybe the computer can boot from a USB pendrive. My IBM Thinkpad of similar age boots happily from USB, and it makes things easier. See this link

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

-o-

But it might be easier with a work-around: to install a community re-spin based on Ubuntu 12.04 LTS, that has a non-pae kernel and promises support until April 2017: for example ***Bento, Bodhi, LXLE***, maybe ***ToriOS***, which is still in the beta stage (working fairly well, but not yet released officially).

Other alternatives are ***Wary Puppy*** and ***TahrPup***, two nice ultra-light Puppy Linux flavours.

---

### Post by Buntu Bunny on 2015-07-31
sudodus, thanks. Not being the geeky sort, I'm willing to try things but never know if I'm doing it right until it works, LOL. Your suggestions for troubleshooting are helpful.

Of your points 0 - 4, I believe RAM is 1.2 GB. I double checked to make sure I was doing things correctly, but who knows? The one thing I'm not sure of is which install option was highlighted when I attempted to forcepae. The instructions I first used weren't as specific as the ones you pointed me toward. 

Of the rest I can tell you that I'm trying to boot Xubuntu 14.04.2 from a live DVD created in Xburn, that it was a torrent download, checksums matched. I checked the DVD as you suggested, and it booted just fine on another computer. I can boot this troublesome little Dell to the previously installed Xubuntu 12.04 with no problem. 

I guess the question now is, what do I want to do? This laptop is an extra and the upgrade was simply to try Trusty Tahr. I may give one of your other suggestions a try.

Thanks to everyone who helped with this problem, and especially to sudodus. Thanks for hanging in there with me, it is much appreciated.

---

### Post by sudodus on 2015-07-31
You are welcome :-)

1.2 GB RAM is enough for Xubuntu.

The DVD disk is good.

What about the DVD drive (the optical-mechanical device)? Will it boot from a Xubuntu 12.04 LTS or Xubuntu 12.04.1 LTS disk?

-o-

Anyway, whatever you decide to do with this old Dell, please let us know the details about your final result! (And of course, ask more questions, if you need.)

---

### Post by Buntu Bunny on 2015-07-31
> **sudodus said:**
> What about the DVD drive (the optical-mechanical device)? Will it boot from a Xubuntu 12.04 LTS or Xubuntu 12.04.1 LTS disk?

No! I tried to boot from my original Xubuntu 12.04 LTS installation DVD, but it booted directly to my login screen. That surprised me because before I tried forcepae, it would try to boot to the Xubuntu 14.04 DVD. I must have really messed things up. This is why I'd rather experiment on a non-essential computer than my main machine, LOL

EDIT: It occurred to me to try to boot from the UbuntuMATE 14.04.02 LTS DVD I used to intall UbuntuMATE on my ThinkPad T43. That one got to the same warning, "Unable to boot - please use a kernel appropriate for your CPU".  So I remain at square one.

> **sudodus said:**
> Anyway, whatever you decide to do with this old Dell, please let us know the details about your final result! (And of course, ask more questions, if you need.)

Will do, thanks!

---

### Post by sudodus on 2015-07-31
Yesterday and today I have been making a tarball and a compressed image file of ToriOS beta.

The tarball is more flexible - you can make dual boot systems in the same drive if you wish, but installing a compressed image file is easier.

Download the image file [dd_ToriOS-LubuCore-pae-OEM_precise_7.8GB.img.xz](http://phillw.net/isos/linux-tools/compressed-images/dd_ToriOS-LubuCore-pae-OEM_precise_7.8GB.img.xz)

Install [mkusb](https://help.ubuntu.com/community/mkusb), which can also make USB boot drives from ISO files. View or download the [quick start manual](http://phillw.net/isos/linux-tools/mkusb/mkUSB-quick-start-manual.pdf)

Run the following command or do it 'completely' GUI-style and follow the instructions in the zenity windows.

Change directory to where you downloaded the compressed image file, maybe **~/Downloads**

```
sudo -H mkusb dd_ToriOS-LubuCore-pae-OEM_precise_7.8GB.img.xz
```

After the installation has finished, you can reboot the computer. I did the corresponding thing (it took around 4 minutes) in my IBM Thinkpad with a Pentium M, that lacks a PAE flag. This particular ToriOS system comes with fake-pae and the 3.2.0-88-generic-pae kernel. See the attached file and good luck :-)

---

### Post by Buntu Bunny on 2015-07-31
Great, this sounds hopeful! I don't need a dual boot so the image file will be fine. I've downloaded it and the quick start manual. I will be out of town until later next week, so you'll hear how I got on after that. I see on your screenshot that pae is now flagged, so I'm very much hoping to report the same success then.

---

