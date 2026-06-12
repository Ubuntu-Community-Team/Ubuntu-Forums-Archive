---
title: "linux-headers 2.6.22-14"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by TheLions on 2008-02-04
had anyone installed this? 
any side effects?

---

### Post by Pumalite on 2008-02-04
None. Do it if you want to compile graphic driver and the like. You can do this too:
sudo aptitude install build-essential
Or:
sudo apt-get install linux-headers-`uname -r`

---

### Post by TheLions on 2008-02-04
ok I installed this and:
1) I had lost sound
2) Windows loader had been removed from /boot/grub/menu.lst

1)recompiling alsa should fix this
2) i saved menu.lst before installation

(hope this will help some one):)

---

### Post by eznet on 2008-02-04
Checking to see I understand... bear with me :)

The update to 2.6.22-14 trashed alsa and removed your Windows label from your menu.lst file?

No other noticed side effects on your machine?

Also, what graphics card are you using?  The post [here]("http://ubuntuforums.org/showthread.php?p=4262751") kinda freaks me out as I just got my nVidia SLI config working smoothly :)
-Matt

---

### Post by Scavok on 2008-02-04
> **TheLions said:**
> had anyone installed this? 
any side effects?
YES! My PC won't boot (old BIOS with 137GB limit):

[http://ubuntuforums.org/showthread.php?t=687622](http://ubuntuforums.org/showthread.php?t=687622)

:mad:

---

### Post by freddyp on 2008-02-04
Just updated on my Lifebook and no problems found so far but I'm not dual booting either!

---

### Post by WenSes on 2008-02-05
I got problems!! 

It trashed my graphic drivers! I have a ATI Radeon 9550,and my sistem it's Ubuntu 64 (I have an AMD 64 Machine). I installed this upgrade... Now my graphic card's privative driver it's not working!!! I'm using the vesa drivers to be able to use Ubuntu... and each time I try to activate the privative drivers (fglrx) it doesn't works! Help me please! I want my nice effects and my 3d acceleration back!

---

### Post by MattBlack on 2008-02-05
Got a Lenovo 3000 N200 Laptop.

Upgrade to 2.6.22-14 has killed my wireless networking.
No Interface detected.

Dual boot still OK.

I'll Let you know what i find out.....

---

### Post by frodon on 2008-02-05
> **WenSes said:**
> I got problems!! 

It trashed my graphic drivers! I have a ATI Radeon 9550,and my sistem it's Ubuntu 64 (I have an AMD 64 Machine). I installed this upgrade... Now my graphic card's privative driver it's not working!!! I'm using the vesa drivers to be able to use Ubuntu... and each time I try to activate the privative drivers (fglrx) it doesn't works! Help me please! I want my nice effects and my 3d acceleration back!Let me guess you did not use the drivers from the repositories ?
> **MattBlack said:**
> Got a Lenovo 3000 N200 Laptop.

Upgrade to 2.6.22-14 has killed my wireless networking.
No Interface detected.Were you using ndiswrapper to get your wireless working ?

---

### Post by WenSes on 2008-02-05
Frodon:

I was using the closed driver that was offered by Ubuntu when I installed it. I didn't download anything extra .

---

### Post by MattBlack on 2008-02-05
> **frodon said:**
> 
Were you using ndiswrapper to get your wireless working ?

Hi 

Feel really silly...

done a dmesg and found 

[   15.420000] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b013)
[   15.420000] usbcore: registered new interface driver uvcvideo
[   15.420000] USB Video Class driver (v0.1.0)
[   15.424000] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.1.0
[   15.424000] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   15.424000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   15.424000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   15.424000] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
**[   15.540000] iwl4965: Radio disabled by HW RF Kill switch**

therefore noticed i accidentally switched it off in the hardware switch. Switched it back on and all OK.

Thanks for the responce - sorry for any inconvienience.

Matt

---

### Post by frodon on 2008-02-05
No problem, i'm glad all is back to normal for you :)

Upgrades brakes things in really few cases, the most common is users who don't use graphic drivers from the repositories and who don't know that they have to install drivers again after each kernel update. That's why i always advice to use graphic drivers from the repositories and thus never bother with this.

---

### Post by WenSes on 2008-02-05
This means that what I should do is install my graphic drivers again? mmm If it's like that, (sorry still a novice in this) how can I do that? When I installed the drivers that were closed, ubuntu itself told me that were closed dirvers not in use and in that oportunity I just ordered to activate them and the de driver downloading and installing were automatic... 

Now I'm suuposed to search at the repositories? How I should search? by fglrx? (my card it's and ATI Radeon 9550)

---

### Post by frodon on 2008-02-05
Then you did use the ubuntu system to install drivers so this is an unexpected problem, if you check again the restricted driver manager, does it tell you that your graphic driver is intalled ?

---

### Post by perixx on 2008-02-05
Hi WenSes...

Though I'm using FEISTY, not Gutsy - I've been going through great woes lately due to using different graphic card brands - I've ironed them out finally, by reinstalling several packages; perhaps some of this also helps you - I can't guarantee, though, as I don't know the behaviour of COMPIZ in Gutsy...
If you find those packages in Synaptic and choose to reinstall them, you should at least do no harm to your system !

[http://ubuntuforums.org/showpost.php?p=4266586&postcount=7]("http://ubuntuforums.org/showpost.php?p=4266586&postcount=7")

Good luck!

perixx

---

### Post by WenSes on 2008-02-05
If I go to system menu - restricted drivers manager (I'm using Ubuntu in spanish version, since I'm Chilean, I don't know if the names will be the right ones) and I check in there, it says that I have closed drivers that are not in use. If I activate them, system tells me to restart in order to make them work... however, when I restart and Ubuntu begins to load, a message appears saying that Ubuntu it's going to work in low resolution mode and start to work using vesa drivers...

My Ubuntu it's the 64 version by the way. I changed to the fglrx open version and it works but the results are really poor performance and no 3d acceleration. 

Can you help me with this info? Do you need more info?

---

### Post by WenSes on 2008-02-05
Thxs perixx for your replay, however if I reinstall all those packages again, I would downgrade the linux headers that I just updated...

I may use that solution if I got no other, but I think that idea will be helpful, thxs!

---

### Post by TheLions on 2008-02-05
> **eznet said:**
> Checking to see I understand... bear with me :)

The update to 2.6.22-14 trashed alsa and removed your Windows label from your menu.lst file?

No other noticed side effects on your machine?

Also, what graphics card are you using?  The post [here]("http://ubuntuforums.org/showthread.php?p=4262751") kinda freaks me out as I just got my nVidia SLI config working smoothly :)
-Matt

i got Gainward 7600GT
and no side other effects.(lucky for me)

---

### Post by WenSes on 2008-02-05
hey, there's anybody that got the same problem than me or similar? or even better, somebody with any solution to this problem?

800x600 w/o 3d it's a terrible res to work!

---

### Post by TheLions on 2008-02-05
> **WenSes said:**
> hey, there's anybody that got the same problem than me or similar? or even better, somebody with any solution to this problem?

800x600 w/o 3d it's a terrible res to work!

can you give us some info about your hardware?

---

### Post by WenSes on 2008-02-05
My hardware:

Process: AMD Athlon 64 +3200 skt 754
Ram: 1 Gb Ram (2x512 Kingston standard)
HD: 200 Gb Barracuda HD Seagate, only disc
Graphic Card: ATI radeon 9550 with 256 Ram
Mother Board: MSI K8T Neo-V
2 optical drives and diskette reader...

I don't know what else would be important... thxs for your assitence

---

### Post by Handssolow on 2008-02-05
Oh dear, it's not gone well.

Yet again an update puts 386 at the top of Grub rather that Generic which I need for my dual core Athlon. It doesn't really matter at this stage.
Several of the latest kernels don't boot with the error message stopped where it can't find Root File System. Currently I've finally been able to boot with 2.6.17-10-386 but only with a low resolution.

Any suggestions?

---

### Post by aysiu on 2008-02-05
Am I the only one who's had no problems with this kernel update?

---

### Post by WenSes on 2008-02-05
It seems that we will have to install Ubuntu from the disk and not allow it to update... I'm stuck with this and frankly don't have an idea how to solve it

---

### Post by frodon on 2008-02-05
I had none too aysiu, would i say as usual :)

---

### Post by WenSes on 2008-02-05
At least somebody knows how to downgrade this linux-headers? some way to take away this upgrade?

---

### Post by mmichalik on 2008-02-05
I updated one white box desktop computer, one Lenovo 3000 N100 laptop and two Compaq Presario laptops (both of which used the ndiswrapper for the broadcom wireless card) and have had no side effects.  Everything works now, just as before.

---

### Post by marmux on 2008-02-05
I did have problems.
My computer doesn't boot anymore. Grub seems to find the kernel correctly, the boot process begins but it hangs almost immediately, then after a while it defaults to something like 

```

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) 
Type help for a list of available commands
(initramfs)

```

(i don't remember exactly, but this is pretty much it).
I am totally stuck. Any ideas?

---

### Post by allig8r on 2008-02-05
I am also having problems. Similar to the previous post, grub finds the kernel, boot process begins but then it hard reboots. No idea...

I guess I should mention I had similar behavior when I first installed gutsy, but fixed it by using the nosplash option, but right now it doesn't work with or without splash.

---

### Post by mmichalik on 2008-02-05
Marmux, I've had similar issues like that in the past and I was able to type "reboot" (without the quotes) and press enter and the system would, from then on, boot up normally.

I hope that it does the same for you.

---

### Post by Handssolow on 2008-02-05
Made some progress, now up to 2.6.20-16-generic but I'm now sidetracked sorting out a Nvidia driver/screen resolution issue.

(pressing escape after the bios screen takes me into the Grub menu where I can select which kernel to boot into. Selecting 2.6.22-14-generic and pressing e takes me to another menu but my initramfs selection then b doesn't deliver a successful boot).

Like other attempting to boot with 2.6.22-14-generic delivers a BusyBox message about initramfs

Whilst still having problems with 32 bit OS on my IDE drive, I've been able to update my 64 bit on a Sata to 2.6.22-14-generic

---

### Post by sunstriker on 2008-02-05
No side effects beside I had to reload my Atheros modules (using macbook pro 2,4ghz), but I have to do that after every kernel update..

---

### Post by marmux on 2008-02-05
I just made it work.
I had to change the boot commands in the grub menu. Apparently, the update changed the UUID's of my partitions, which is total nonsense.
Editing the grub kernel command from "root=UUID=[the old UUID]" to "root=/dev/sda8" made the job.
Therefore, I take back what I said in my previous post: GRUB was NOT finding the root partition, because the UUID has changed. Oddly, it was not complaining about it, therefore I thought the error was somewhere else.
Anyway: isn't the UUID partition identification there exactly in order to avoid such problems? what's the point in changing it?

---

### Post by Scavok on 2008-02-05
My understanding is that one of the reasons for choosing Ubuntu (or its derivatives) is: it will satisfactorily run on "older" PCs. E.g., non-profit organization, PC recyclers, etc. use older PC hardware and open-source software. (In my particular case I have a PC that was built Oct. 31, 2001. It has the BIOS limitation of 137GB & 210GB of used space on the hard drive. So the kernel update rendered it useless.) The point is: kernel updates had better take issues like this into account if Ubuntu desires to tout "works on old PCs." Otherwise there are going to be a lot of non-profit organizations and individuals affected.

And WHY OH WHY doesn't the LiveCD installation follow the advice contained here for making a dedicated GRUB partition? :mad:

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)

Or even a separate /boot partition? :mad:

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

---

### Post by Cam1223 on 2008-02-05
what exactly was this upgrade supposed to do because my computer won't boot now. I tried changing the huis to /dev/hda3 which is where my root is. It starts booting and then hangs. Also before I upgraded I noticed it removed some of my programs (WTF why??) but I dont know any better and one of thoes upgrades had never broken my system before....until now. I had a bad feeling about this one.

---

### Post by pmorton on 2008-02-05
> **TheLions said:**
> had anyone installed this? 
any side effects?

Yes. It broke the NVIDIA proprietary 169.09 driver on 7.10.  The new 171.05 driver is no better. No help from Alberto Milone's usually reliable Envy ([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)). 
<<sudo dpkg-reconfigure xserver-xorg>> at console (thanks WenSes) gets the open driver working and that'll do me - it gets tiresome recompiling the proprietary kernel module with each kernel upgrade, especially if it all then breaks.

---

### Post by NJC on 2008-02-05
> **aysiu said:**
> Am I the only one who's had no problems with this kernel update?
 
No problems for me, either.

---

### Post by DarkSim on 2008-02-05
I got an Error 16: Inconsistent filesystem structure at Grub and the graphics are in low-res mode if I log into the other set of headers (2.6.20-15 or something like that)

I hope I can sort out this mess.

---

### Post by Cam1223 on 2008-02-05
well I sort of fixed it. The upgrade changed uuids and removed parts of kde like kdm so I just reinstalled thoes.

---

### Post by allig8r on 2008-02-05
Well after rebooting many many times and trying a lot of options/configurations, it seems to now be booting up consistently in the original configuration after the upgrade. I am mystified, but as long as it's working...

---

### Post by Pumalite on 2008-02-05
I'm updated in 64 and 32 bit in 5 computers with different hardware and I've had no problems.

---

### Post by Bart123 on 2008-02-05
Hi all.
After auto upgrading via update manager to new headers, grub doesn't boot, prompting Error 15, no file found. Tried already changing the:root		(hd2,0) to any of the 4 hd installed. Also redirecting    kernel		/boot/vmlinuz-2.6.22-14-rt root=/dev/sdc1 from previous uuid.
here are menu.lst and fstab, help will be much appreciated..


=================

title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=462c9b13-b170-43ee-b322-d55c925d0f30 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=462c9b13-b170-43ee-b322-d55c925d0f30 ro single
initrd		/boot/initrd.img-2.6.22-14-rt

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=462c9b13-b170-43ee-b322-d55c925d0f30 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=462c9b13-b170-43ee-b322-d55c925d0f30 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet
=========================

fstab:
==================
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=462c9b13-b170-43ee-b322-d55c925d0f30 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc5
UUID=999a6eed-a6d0-427b-908c-728814da8cfa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
===========
Tnx!

---

### Post by Pumalite on 2008-02-05
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by Bartje on 2008-02-05
Again, and again, and again.... no sound anymore after upgrade :

[http://ubuntuforums.org/showthread.php?t=688620]("http://ubuntuforums.org/showthread.php?t=688620")

---

### Post by jrharvey on 2008-02-05
My sound no longer works!!!!!!!!!!!!!!! Whats the deal ????/

---

### Post by WenSes on 2008-02-05
Hello everyone, 

I'm sorry to repeat the question, but does anybody knows how uninstall this update? this because it seems that I'm the only ATI user with problems and appears that there's no solution to it...

---

### Post by ger_macaco on 2008-02-05
Running Kubuntu Gutsy 64bit (AMD64 X2). Onboard NVIDIA graphic card.

X keeps crashing after a random amount of time. This is happening since last kernel update.

Any ideas?

---

### Post by DarkSim on 2008-02-05
I still haven't figured out whats going on. I ran G-Parted live cd and it didnt find anything wrong. I also manually did ran fsck and it didn'find anything. Anybody have an idea?

---

### Post by frodon on 2008-02-05
> **Bartje said:**
> Again, and again, and again.... no sound anymore after upgrade :

[http://ubuntuforums.org/showthread.php?t=688620]("http://ubuntuforums.org/showthread.php?t=688620")Again and again and again ...  [SIZE="5"]**_[COLOR="Red"]any driver you compile will have to be recompiled again after each kernel upgrade [/COLOR]_**[/SIZE], i'm sorry you were not aware of this but you should expect this after each update.
So if you compiled your sound drivers or graphic drivers they won't work till you re-install them again after the upgrade this is 100% sure.

I upgraded 2 computers today without any problem.

---

### Post by WenSes on 2008-02-05
Hello, everyone... It seems (not sure yet) that I solve my problem... 
I run a line in terminal: 

sudo dpkg-reconfigure xserver-xorg

the I follow the instructions on the screen to configure this and now It seems to work (at least I ran "glxgears" and the gears actually appears... also I recovered my screen res and 1024x768 and the effects from compiz seems to be back to normal...

to be really honest this was only luck... so I hope this serves to others...

thxs to everyone that was interested in helping.. I'll report if I find anything else

---

### Post by frodon on 2008-02-05
Sorry WenSes, i missed some of your posts, this command is indeed something to try with any xserver configuration issue as it reconfigure correctly your xorg.conf, i feel stupid to not have adviced you that first.

---

### Post by WenSes on 2008-02-05
no prob, now I have learned... thxs anyway... :)

---

### Post by coachwhip on 2008-02-05
Well i was pretty sure i'd updated (couldn't fully remember from last night).

uname -r gives 2.6.22-14-generic and so far everything works.

Nvidia card is working, so is the broadcom wireless with ndiswrapper.

Mike

---

### Post by Castaa on 2008-02-05
I upgraded to 2.6.22-14 and my video is now hosed.  My desktop resolution is like 640x480 and it's drawing a fraction of the bottom of my screen at the top.  My video card is a Geforce 6800GT.

I did not change my graphic drivers from any other than the default ones Ubuntu installs.  How do I roll back? :(

---

### Post by frodon on 2008-02-05
Just several post before :
```
sudo dpkg-reconfigure xserver-xorg
```Didn't you read the post of WenSes sharing how he solved his problem ?

---

### Post by Handssolow on 2008-02-05
frodon

What is the cause of my 32 bit kernel upgrade dropping me to Busybox and  a line about initramfs? I've currently reverted to booting 2.6.20-16-generic with the nv driver but rather that sort out a non functioning nvidia driver, I want to be using 2.6.22-14-generic first.

Incidentally since my last post I've updated the bios of my Asrock 939Dual-VSTA partly because I occasionally had problems with the bios recognising my Sata drive. My 32 bit Ubuntu is on the IDE master. I've updated the kernels on my 64 bit OS and my wife's PC (single cpu Athlon) without a hitch.

---

### Post by Tosa on 2008-02-05
I think that I have a panic here...

I've just updated, well I tried to update.At the and of it Adept informed me that there were same errors, but I couldn't see what.

This is what I get when I run *apt-get -f install*:

```
Setting up linux-image-2.6.22-14-generic (2.6.22-14.51) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I haven't rebooted, but what now?

---

### Post by Handssolow on 2008-02-05
Attempting to boot up 2.6.22-14-generic I get the following messages-

New kernel Recovery waiting for root file system
After a minute or two it reports-
Done
check root=bootarg cat /proc/cmdline
or missing modules,devices:cat /proc/modules ls /dev
Alert! /dev/disk/by-uuid/242e7752-e68e-45b4-a5b4-581e3762ca00 does not exist

then Busybox appears

The uuid is my IDE drive that I'm currently using with 2.6.20-16-generic

How do I go about repairing these errors?

---

### Post by alexandreracine on 2008-02-06
> **TheLions said:**
> had anyone installed this? 
any side effects?

Yep, my menu in grub went -> RESET.

No more Windows, no more customise menu (there is bug with the 64bit and network cards and I have to put 3GB of memory or else it crash.)


So... what happened to GRUB? It is not suppose to just add the new entry?

---

### Post by OnSite511 on 2008-02-06
my situation is a bit different...the update seems to have disabled or turned off my USB ports. I had to dig around in the box 'o old computer crap to harvest a ps2 mouse. How would I go about checking what may be failing.

---

### Post by frodon on 2008-02-06
> **alexandreracine said:**
> So... what happened to GRUB? It is not suppose to just add the new entry?No it is not, it rebuilds your menu.lst file so if you tweaked some entries or added some extra options you are more likely to have to do that again.

For those who have the busybox problem boot a live CD then mount your ubuntu partition and open your menu.list file then check that the UUID are good and partition number too.

@Handssolow, i feel that your problem is a wrong UUID or partition number in your menu.lst file, should be easy to fix with a live CD.

Will try to digg a little on this busy box issue that some of you are issuing.

EDIT:

For those with the busybox issue and only those with busy box issue you can try the following. Boot a live CD then mount your ubuntu partition and edit your /boot/grub/menu.lst and at the end of your kernel entry add "all_generic_ide". I can't guaranty you it will work but it is something to try.
If you don't want to boot the liveCD you can try this temporarily press Escap when GRUB appear then press E to edit the wanted kenel and E again to edit the kernel line and at the end of the line add *all_generic_ide* then press Escap again and B to boot your kernel thus you can see quickly if it improve things.

---

### Post by DarkSim on 2008-02-06
Yay! I got mine sorted out. Turns out i reinstalled the headers and added the i386 set along with it. I also did the same with restricted modules to get the nvidia drivers working. Compiz is working and my games are all working too. I was so close to nuking the installation and starting over. You have no idea how happy this makes me.

---

### Post by frodon on 2008-02-06
Thanks DarkSim for sharing your experience, i think that anyone with problems should try to re-install the kernel headers and restricted modules first.

---

### Post by rbrechei on 2008-02-06
Hi,

I installed them this morning and it looks like my volume rendering application doesn't work anymore. It compiles fine but when I run it, I get the dump shown below. I have no idea what's the problem but I'm going to try to reinstall my nvidia drivers. Last week there was no problem with this. Today is the first time I ran the program with the new linux headers installed.

*** glibc detected *** ./mvr: malloc(): memory corruption: 0x0818ef10 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6900636]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x90)[0xb6901fc0]
/usr/sbin/../lib/libstdc++.so.6(_Znwj+0x27)[0xb6aca6a7]
./mvr(_ZN16vtkSceneAssembly3NewEv+0x30)[0x808dc6a]
./mvr(_ZN14QMainWindowMVR4InitEv+0xa99)[0x80ad0d5]
./mvr(main+0xb8)[0x80ef6ae]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb68ac050]
./mvr(_ZN18vtkInteractorStyle9StopStateEv+0x8d)[0x8070531]
======= Memory map: ========
08048000-08115000 r-xp 00000000 fe:00 276720     /home/rbrecheisen/usb/data/projects/phd/dev/mvr/mvr
08115000-08116000 rw-p 000cc000 fe:00 276720     /home/rbrecheisen/usb/data/projects/phd/dev/mvr/mvr
08116000-082a2000 rw-p 08116000 00:00 0          [heap]
b4900000-b4921000 rw-p b4900000 00:00 0 
b4921000-b4a00000 ---p b4921000 00:00 0 
b4ac7000-b4b52000 r--p 00000000 08:02 12010829   /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b4b52000-b4b58000 r--s 00000000 08:02 20070853   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b4b58000-b4b5b000 r--s 00000000 08:02 20070840   /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b4b5b000-b4b5f000 r--s 00000000 08:02 20070839   /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b4b5f000-b4b60000 r--s 00000000 08:02 20070837   /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b4b60000-b4b61000 r--s 00000000 08:02 20070824   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b4b61000-b4b64000 r--s 00000000 08:02 20070823   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b4b64000-b4b65000 r--s 00000000 08:02 20070822   /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b4b65000-b4b68000 r--s 00000000 08:02 20070762   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b4b68000-b4b6a000 r--s 00000000 08:02 20070738   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b4b6a000-b4b72000 r--s 00000000 08:02 20070735   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b4b72000-b4b78000 r--s 00000000 08:02 20070725   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b4b78000-b4b79000 r--s 00000000 08:02 20070723   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b4b79000-b4b90000 r--s 00000000 08:02 20070705   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b4b90000-b4b92000 r--s 00000000 08:02 20070702   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b4b92000-b4b98000 r--s 00000000 08:02 20070701   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b4b98000-b4b9c000 r--s 00000000 08:02 20070700   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b4b9c000-b4b9e000 r--s 00000000 08:02 20070630   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b4b9e000-b4b9f000 r--s 00000000 08:02 20071084   /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b4b9f000-b4ba0000 r--s 00000000 08:02 20071083   /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b4ba0000-b4ba1000 r--s 00000000 08:02 20071082   /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b4ba1000-b4ba4000 r--s 00000000 08:02 20071081   /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b4ba4000-b4ba7000 r--s 00000000 08:02 20071080   /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b4ba7000-b4bae000 r--s 00000000 08:02 20071079   /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b4bae000-b4bb0000 r--s 00000000 08:02 20071078   /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b4bb0000-b4bb1000 r--s 00000000 08:02 20071077   /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b4bb1000-b4bb2000 r--s 00000000 08:02 20071076   /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b4bb2000-b4bb3000 r--s 00000000 08:02 20071075   /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b4bb3000-b4bb8000 r--s 00000000 08:02 20071074   /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b4bb8000-b4bbd000 r--s 00000000 08:02 20071073   /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b4bbd000-b4bbf000 r--s 00000000 08:02 20071072   /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b4bbf000-b4bc2000 r--s 00000000 08:02 20071071   /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b4bc2000-b4bc3000 r--s 00000000 08:02 20071070   /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b4bc3000-b4bc4000 r--s 00000000 08:02 20071069   /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b4bc4000-b4bc5000 r--s 00000000 08:02 20071068   /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b4bc5000-b4bc9000 r--s 00000000 08:02 20071046   /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b4bc9000-b4bcf000 r--s 00000000 08:02 20071045   /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b4bcf000-b4bd0000 r--s 00000000 08:02 20071031   /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b4bd0000-b4bd4000 r--s 00000000 08:02 20071030   /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b4bd4000-b4bd8000 r--s 00000000 08:02 20071027   /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b4bd8000-b4bdc000 r--s 00000000 08:02 20070863   /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b4bdc000-b4be1000 r--s 00000000 08:02 20070482   /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b4be1000-b4be3000 r-xp 00000000 08:02 11848045   /usr/lib/gconv/UTF-16.so
b4be3000-b4be5000 rw-p 00001000 08:02 11848045   /usr/lib/gconv/UTF-16.so
b4be5000-b4c24000 r--p 00000000 08:02 11879601   /usr/lib/locale/en_US.utf8/LC_CTYPE
b4c24000-b4c25000 r--p 00000000 08:02 11879606   /usr/lib/locale/en_US.utf8/LC_NUMERIC
b4c25000-b4c26000 r--p 00000000 08:02 11879609   /usr/lib/locale/en_US.utf8/LC_TIME
b4c26000-b4d06000 r--p 00000000 08:02 11879600   /usr/lib/locale/en_US.utf8/LC_COLLATE
b4d06000-b4d07000 r--p 00000000 08:02 11879604   /usr/lib/locale/en_US.utf8/LC_MONETARY
b4d07000-b4d66000 rw-p b4d07000 00:00 0 
b4d66000-b4d67000 r-xp 00000000 08:02 12191146   /usr/lib/tls/libnvidia-tls.so.100.14.19
b4d67000-b4d68000 rw-p 00000000 08:02 12191146   /usr/lib/tls/libnvidia-tls.so.100.14.19
b4d68000-b56c4000 r-xp 00000000 08:02 11830968   /usr/lib/libGLcore.so.100.14.19
b56c4000-b56fc000 rwxp 0095c000 08:02 11830968   /usr/lib/libGLcore.so.100.14.19
b56fc000-b5700000 rwxp b56fc000 00:00 0 
b5700000-b5715000 r-xp 00000000 08:02 11830595   /usr/lib/libXmu.so.6.2.0
b5715000-b5716000 rw-p 00015000 08:02 11830595   /usr/lib/libXmu.so.6.2.0
b5716000-b571a000 r-xp 00000000 08:02 11830579   /usr/lib/libXdmcp.so.6.0.0
b571a000-b571b000 rw-p 00003000 08:02 11830579   /usr/lib/libXdmcp.so.6.0.0
b571b000-b571c000 rw-p b571b000 00:00 0 
b571c000-b571e000 r-xp 00000000 08:02 11830568   /usr/lib/libXau.so.6.0.0
b571e000-b571f000 rw-p 00001000 08:02 11830568   /usr/lib/libXau.so.6.0.0
b571f000-b5723000 r-xp 00000000 08:02 11830585   /usr/lib/libXfixes.so.3.1.0
b5723000-b5724000 rw-p 00003000 08:02 11830585   /usr/lib/libXfixes.so.3.1.0
b5724000-b57e0000 r-xp 00000000 08:02 5587004    /usr/lib/libglib-2.0.so.0.1400.1
b57e0000-b57e1000 rw-p 000bc000 08:02 5587004    /usr/lib/libglib-2.0.so.0.1400.1
b57e1000-b57e8000 r-xp 00000000 08:02 11191259   /lib/tls/i686/cmov/librt-2.6.1.so
b57e8000-b57ea000 rw-p 00006000 08:02 11191259   /lib/tls/i686/cmov/librt-2.6.1.so
b57ea000-b57ee000 r-xp 00000000 08:02 5587116    /usr/lib/libgthread-2.0.so.0.1400.1
b57ee000-b57ef000 rw-p 00003000 08:02 5587116    /usr/lib/libgthread-2.0.so.0.1400.1
b57ef000-b57f0000 rw-p b57ef000 00:00 0 
b57f0000-b5805000 r-xp 00000000 08:02 11831180   /usr/lib/libaudio.so.2.4
b5805000-b5806000 rw-p 00014000 08:02 11831180   /usr/lib/libaudio.so.2.4
b5806000-b582d000 r-xp 00000000 08:02 11831396   /usr/lib/libvtksys.so.5.0.3
b582d000-b582e000 rw-p 00027000 08:02 11831396   /usr/lib/libvtksys.so.5.0.3
b582e000-b587b000 r-xp 00000000 08:02 11830609   /usr/lib/libXt.so.6.0.0
b587b000-b587f000 rw-p 0004c000 08:02 11830609   /usr/lib/libXt.so.6.0.0
b587f000-b5889000 r-xp 00000000 08:02 11831395   /usr/lib/libvtkftgl.so.5.0.3
b5889000-b588a000 rw-p 0000a000 08:02 11831395   /usr/lib/libvtkftgl.so.5.0.3
b588a000-b58a8000 r-xp 00000000 08:02 11830770   /usr/lib/libexpat.so.1.0.0
b58a8000-b58aa000 rw-p 0001e000 08:02 11830770   /usr/lib/libexpat.so.1.0.0
b58aa000-b58ab000 rw-p b58aa000 00:00 0 
b58ab000-b58fd000 r-xp 00000000 08:02 5587430    /usr/lib/libtiff.so.4.2.1
b58fd000-b58ff000 rw-p 00052000 08:02 5587430    /usr/lib/libtiff.so.4.2.1
b58ff000-b591e000 r-xp 00000000 08:02 5587198    /usr/lib/libjpeg.so.62.0.0
b591e000-b591f000 rw-p 0001e000 08:02 5587198    /usr/lib/libjpeg.so.62.0.0
b591f000-b593d000 r-xp 00000000 08:02 11831382   /usr/lib/libvtkDICOMParser.so.5.0.3
b593d000-b593e000 rw-p 0001d000 08:02 11831382   /usr/lib/libvtkDICOMParser.so.5.0.3
b593e000-b5c7c000 r-xp 00000000 08:02 11831388   /usr/lib/libvtkImaging.so.5.0.3
b5c7c000-b5c89000 rw-p 0033e000 08:02 11831388   /usr/lib/libvtkImaging.so.5.0.3
b5c89000-b5d0b000 r-xp 00000000 08:02 11830535   /usr/lib/libGLU.so.1.3.070001
b5d0b000-b5d0c000 rw-p 00081000 08:02 11830535   /usr/lib/libGLU.so.1.3.070001
b5d0c000-b5f49000 r-xp 00000000 08:02 11831383   /usr/lib/libvtkFiltering.so.5.0.3
b5f49000-b5f60000 rw-p 0023d000 08:02 11831383   /usr/lib/libvtkFiltering.so.5.0.3
b5f60000-b5f61000 rw-p b5Aborted (core dumped)

---

### Post by quibbler on 2008-02-06
I installed linux-headers 2.6.22-14 and then rebooted.
I got error 22 (no such partition). HD 1,0
I could boot to my Windows partition HD 0,0
Booted with Super Grub CD and this told me my partition
was HD 1,4
I edited grub menu and it booted fine. Once in I edited
menu.lst changing HD 1,0 to HD 1,4
Everything seems to work fine now.

My problem is solved, but could someone please explain to
me the what and why this happened.

Regards quibbler

---

### Post by frodon on 2008-02-06
You should fill a bug report thus developers would be aware of this side effect and maybe correct this for future updates.

[https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

---

### Post by Handssolow on 2008-02-06
Thanks for your support frodon.

I'm still mystified and have made little progress.
I can see nothing abnormal in my menu.lst. To check, I copied my UUIDs into an Open Office document to see if any UUID was different and they are all the same. Rather than a live CD I can use my 64 bit OS on a Sata drive to look at my none functioning 32 bit 2.6.22-14-generic etc. on my IDE drive. 

Last night from a working 32 bit 2.6.20-generic, I re-installed what I think are the latest kernel's header and restricted modules with Synaptic but I'm still dropped to Busybox. Please confirm what packages in Synaptic that are required for the kernel upgrade?

Because I had a dual boot system I also ran
sudo grub-install /dev/hda --recheck

This did actually update my  /boot/grub/device.map so it now shows my floppy and the sata drive.

(fd0)	/dev/fd0
(hd0)	/dev/hda
(hd1)	/dev/sda

Using the temporary edit feature in Grub, I changing the UUID so root= /dev/hda but no success.

What next?

---

### Post by Tosa on 2008-02-06
To add to my previous post (#57):

I haven't rebooted yet, so I still have a functioning machine, but for how long? I still get the same error messages when I run *apt-get -f install*.

All packages are marked as installed in Adept, but in details I found these problems:

in linux-image-2.6.22-14 generic[INDENT]conflict: hotplug<0.0.20040105-1

[/INDENT]in linux-sound-base[INDENT]conflict: alsa-base<=1.0.-7
[/INDENT]I have no clue what to do now...

Any Help?

---

### Post by Castaa on 2008-02-06
> **frodon said:**
> Just several post before :
```
sudo dpkg-reconfigure xserver-xorg
```Didn't you read the post of WenSes sharing how he solved his problem ?

sudo dpkg-reconfigure xserver-xorg

This did allow me to get back to the Ubuntu desktop.  But it isn't allowing me to use the nv or nvidia graphic driver.  If set it to nvidia the 'Screens and Graphics' app silently exits and VESA config remains.

The xserver command line utility did auto detect my Gefore 6800GT but once in the GUI it's back to VESA.  The new kernel doesn't like the standard nvidia driver.  I haven't touch the nvidia driver. It's the one installed on the 7.10 install CD.

Thanks for any help.

---

### Post by frodon on 2008-02-06
You tried to re-install linux-headers and restricted modules as well ?

@Tosa, alsa-base should be 1.0.14 in gutsy, did you compiled alsa or locked any alsa package. Check what alsa-base version you have installed.

@Handssolow, boot your live CD and run a "ls -l  /dev/disk/by-uuid/" i have already seen some weird cases where UUID of a disk change even if it is not supposed to happen. so check that the uuid of you root partition as not changed, in all the case this uuid must be the one used in the menu.lst file.

---

### Post by Frem on 2008-02-06
I'm having problems similar to WenSes. Intel Pentium M 1.6 GHz, ATi Xpress 200m.

I got on IRC and asked for help, and everyone kept telling me "you need to RECOMPILE your DRIVERS. you need to USE GENERIC DRIVERS." (One chap in particular persisted in using that capitalization.) This was extremely frustrating as I didn't compile them to start with and I was using the generic drivers, and noone could accept this.

If I boot into single user mode using the second opion on grub and run "startx", I get X. I can run it using the fglrx, ati, and vesa drivers in xorg.conf
If I boot normally, the entire system jams up when the login screen should start, no matter what graphics driver I use.

Both modes are using the same kernel. Any ideas on how to fix this?

edit: I should probably mention that I've already run "sudo dpkg-reconfigure xserver-xorg", and it didn't make any differance.

---

### Post by Castaa on 2008-02-06
> **Frem said:**
> I'm having problems similar to WenSes. Intel Pentium M 1.6 GHz, ATi Xpress 200m.

I got on IRC and asked for help, and everyone kept telling me "you need to RECOMPILE your DRIVERS. you need to USE GENERIC DRIVERS." (One chap in particular persisted in using that capitalization.) This was extremely frustrating as I didn't compile them to start with and I was using the generic drivers, and noone could accept this.

If I boot into single user mode using the second opion on grub and run "startx", I get X. I can run it using the fglrx, ati, and vesa drivers in xorg.conf
If I boot normally, the entire system jams up when the login screen should start, no matter what graphics driver I use.

Both modes are using the same kernel. Any ideas on how to fix this?

edit: I should probably mention that I've already run "sudo dpkg-reconfigure xserver-xorg", and it didn't make any differance.


I'm in a same boat as you.  I upgrade.  I've been using the standard nvidia video driver.  I ran sudo dpkg-reconfigure xserver-xorg and reconfigured.  The nvidia driver simply does not appear to work for me.  I'm not sure what my differences are.  I did find that the nv driver at least gives me a non-accelerated video support at resolutions beyond 800x600 that VESA gave me.  But I'm still far from where I was before the update.  The nvidia driver just crashes the moment I try to test it if the config menu in Gnome.

---

### Post by confused57 on 2008-02-06
> **Castaa said:**
> I'm in a same boat as you.  I upgrade.  I've been using the standard nvidia video driver.  I ran sudo dpkg-reconfigure xserver-xorg and reconfigured.  The nvidia driver simply does not appear to work for me.  I'm not sure what my differences are.  I did find that the nv driver at least gives me a non-accelerated video support at resolutions beyond 800x600 that VESA gave me.  But I'm still far from where I was before the update.  The nvidia driver just crashes the moment I try to test it if the config menu in Gnome.
It's a longshot, but try reinstalling your linux-restricted modules in Synaptic Package Manager...type "linux-restricted" in the SPM Search bar, reinstall Restricted linux modules for generic kernels.

---

### Post by mtngun on 2008-02-07
The header update seriously screwed up my PC.

I've tried most of the suggestions and a few other things.

I can no longer boot into Windows XP, but Ubuntu will boot -- usually, not always.

However, Ubuntu doesn't run right.   For example, Wine won't run at all.   I uninstalled and then reinstalled Wine but it didn't help.   Attempting to start Wine will lock up the PC.  Wine was running fine before the header update.

A few files seem to be corrupted on both partitions.  While attempting to backup my personal files today, I kept getting hangs, seemingly due to trouble reading or writing files.   It acts like a dying hard drive -- except everything was fine prior to the update.  I suspect the update scrambled the hard drive.

Perhaps there is a simple fix, but come tomorrow I'll be looking at reformatting and reinstalling.   I've already lost most of day's work because of this blasted update.  :confused:

---

### Post by Frem on 2008-02-07
So, yeah. With the VESA drivers, I can make Ubuntu jump back and forth rapidly between command line and failed X session. Work for about 2 minutes before freezing during which rapid typing revealed no errors in the X logs in /var/log/. Not entirely sure what to do about it, something keeps trying to restart the X server.

Is there any way to disable the stupid "bulletproof X" feature that Gutsy introduced? I need to have X not restart as soon as an error message comes up because I need to read the error!

Alternatively, is there a way to rollback to linux-image-2.6.22-13-generic?

---

### Post by frodon on 2008-02-07
Everyone here you should really fill bug reports otherwise developers might not be aware of your multiple problems :
[https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

---

### Post by Handssolow on 2008-02-07
Little progress to report and I'm still mystified.
This morning I couldn't boot either from my Sata's 64 bit or IDE's 32bit getting grub error18 and 21 respectively. So I removed the IDE drive to work just on the Sata which I moved from a Sata2 socket to a Sata1 and after a few changes to the bios eventually getting 64bit 2.6.22-14-generic fired up after a few reboots and xserver configurations. I also ran "sudo grub-install /dev/hda --recheck" to remove references to my IDE drive to keep things separate.

Next working with only the IDE's 32bit in the machine, I used  Supergrub on a CD to repair Grub and I'm back to where I was yesterday, able to boot with kernel 2.6.20-16-generic but 2.6.22.14-generic drops me as before to Busybox's line about initramfs.

Is there an issue about the 2.6.22-14  kernel affecting dual boot setups? Also just suppose I had an intermittent fault with my Sata drive (as slave) or even removed it, would these events cause my system to hang when attempting to boot from my IDE's 32bit OS? Is the OS looking for a missing slave drive?

I reinstalled the new headers and restricted modules - yet again and it made no difference.

Help and advice will be much appreciated.

(I'll have to look around for my Launchpad password)

---

### Post by Tosa on 2008-02-07
> **frodon said:**
> 
@Tosa, alsa-base should be 1.0.14 in gutsy, did you compiled alsa or locked any alsa package. Check what alsa-base version you have installed.

Thanks for answering frodon.

Yes, when I check in Adept it says alsa-base is 1.0.14... And no, I haven't compiled nor blocked anything (I'm just an average Win user :)).

What really troubles me is the output of apt-get -f install:

```
Setting up linux-image-2.6.22-14-generic (2.6.22-14.51) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Although I don't know what it actually means, I've got a feeling that I won't be able to boot.

---

### Post by frodon on 2008-02-07
Initramfs is the tools which handle your boot image so if it fails your kernel will indeed not boot except if you are lucky.
getopt packages seems not found so you should try to re-install the util-linux package which contain getopt :
```
sudo apt-get install util-linux
```Then update your system (if it works) :
```
sudo apt-get dist-upgrade && sudo apt-get update
```The if this fail you will surely be asked to run the following command :
```
sudo dpkg --configure -a
```

---

### Post by Tosa on 2008-02-08
Thanks frodon.

I'm back home and I ran
*sudo apt-get install util-linux* because apt said that command *reinstall* didn't exist.

This is the output:

```
Selecting previously deselected package util-linux.
(Reading database ... 92342 files and directories currently installed.)
Unpacking util-linux (from .../util-linux_2.13-8ubuntu1_amd64.deb) ...
Setting up util-linux (2.13-8ubuntu1) ...

Setting up linux-image-2.6.22-14-generic (2.6.22-14.51) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled
(2.6.22-14.47 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

This seems to be OK now, at least I guess so.

I'll continue with the rest of your suggestions now, and i hope I'd dare to reboot.:)

---

### Post by frodon on 2008-02-08
Don't forget to re-install your kernel headers and restricted package as last step, i cross my fingers.

PS: i should have made a typo in my command but apt-get install should do the same job anyway.

---

### Post by Tosa on 2008-02-08
I ran sudo apt-get dist-upgrade && sudo apt-get update and only 2 files were to  be updated, firefox and nspluginwrapper. I'm done, I guess.
I'll check /boot/grub/menu.lst, though just in case my drives got mixed up...

---

### Post by Tosa on 2008-02-08
> **frodon said:**
> Don't forget to re-install your kernel headers and restricted package as last step, i cross my fingers.

PS: i should have made a typo in my command but apt-get install should do the same job anyway.

:p

Of course I forgot to do that.
OK I've just reinstalled all header and restricted modules packages.

Now, be brave, be brave...
I've got to reboot don't I?

---

### Post by Tosa on 2008-02-08
[B]Frodon je t'adore! Mon PC marche!

[/B]OK, I've calmed down. I've rebooted and it obviously works.

Thanks a million!

---

### Post by Handssolow on 2008-02-08
I require help with 2.6.22-14-generic, I apologise for this but I started a new thread earlier after I discovered that I was missing the file /lib/firmware/2.6.22-14-generic and I haven't rebooted my PC whilst waiting for advice.
This morning  as an experiment I ran- 
"sudo apt-get remove linux-image-2.6.22-14-generic"
" sudo update-grub"
 "sudo apt-get install linux-image-2.6.22-14-generic" this showed the following-
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic 
find: /lib/firmware/2.6.22-14-generic: No such file or directory 
find: /lib/firmware/2.6.22-14-generic: No such file or directory

 I have got  /lib/firmware/2.6.22-14-386 but I need generic.

What should I do next? How do I generate file /lib/firmware/2.6.22-14-generic?

---

### Post by frodon on 2008-02-08
> **Tosa said:**
> [B]Frodon je t'adore! Mon PC marche!

[/B]OK, I've calmed down. I've rebooted and it obviously works.

Thanks a million!

Woohoo !

I'm really glad to hear this, i think you should be good for long know with upgrade problems, i nerver really understood where this util-linux package mess come from.

Hope this can help some other users too.

---

### Post by frodon on 2008-02-08
@Handssolow try to install the headers and restricted modules, you might just miss a package related to this kernel.

---

### Post by Handssolow on 2008-02-08
First the good news frodon. I found I was missing  two linux-restricted packages.  Considering I run generic I'm a bit surprised that these were missing at the time of the kernal upgrade also that I hadn't noticed them missing, anyway I installed these two-
Non free Linux 2.6.22 on x86/x86_64
Restricted Linux mudules for generic.

After installing with Synaptic and sudo update-initramfs -u -v -k 2.6.22-14-generic I saw no error messages and /lib/firmware/2.6.22-14-generic has appeared. I was hopeful.

No, when I attempt to boot from Grub anything that has 2.6.22-14 generic or 386, boot stops to look for a root file system.

I'm back on 2.6.20-16-generic as I type.

---

### Post by frodon on 2008-02-08
I would reinstall both kernel in this case and let the automatic initramfs configuration do the job, check the terminal for errors. Maybe you just forgot to run a depmod before your sudo update-initramfs -u -v -k 2.6.22-14-generic.

---

### Post by Handssolow on 2008-02-08
Thanks frodon. Maybe I don't know how to use the depmod command, I don't.
I've used Synaptic to re-install  both three linux-headers 2.6.22-14 packages.
I would like you to confirm  the depmod command line I should use for 2.6.22-14, obviously I don't want to affect the 2.6.20-16-generic kernel I'm using at the moment.

---

### Post by Handssolow on 2008-02-10
Bump.

Including the command  depmod 2.6.22-14-generic did not help me to run  to run 2.6.22-14-generic. I've found nothing abnormal and but I'm not able to use any  2.6.22-14 kernel so I am posting using 2.6.20-16-generic instead. My system cannot be that corrupted.

I suspect something abnormal happened with my original  linux-headers update 5 days ago. I think it is probably related to me having a dual boot system, 32 bit Ubuntu IDE and 64 bit Ubuntu on a Sata. Each have Grub files and I used bios to alter the boot order. I wonder if  part of my faulty 32 bit upgrade was caused by me having a Sata with another Grub file. Perhaps one pointer here, when I had both drives connected during the upgrade at some point with my faulty OS I accessed Grub on my Sata and edited the UUID from my Sata's using e then altered  it to that of my IDE drive and it then accessed my IDE drive, though I don't remember what happened next. Currently I have the Sata drive disconnected to work just on my faulty 32bit OS.

If I choose any  2.6.22-14 kernel I've left with-
Begin : waiting for root file system
check root=bootarg cat/proc.cmdline
or missing modules,devices: cat/proc/modules ls/dec
Alert /dev/disk/by-UUID/242e7752-e68e-45b4-a5b4-a581e3762ca00 does not exist. Dropping to a shell.

Busy Box etc.
(initramfs)_

Any suggestions?

---

### Post by Pumalite on 2008-02-10
> **Handssolow said:**
> Bump.

Including the command  depmod 2.6.22-14-generic did not help me to run  to run 2.6.22-14-generic. I've found nothing abnormal and but I'm not able to use any  2.6.22-14 kernel so I am posting using 2.6.20-16-generic instead. My system cannot be that corrupted.

I suspect something abnormal happened with my original  linux-headers update 5 days ago. I think it is probably related to me having a dual boot system, 32 bit Ubuntu IDE and 64 bit Ubuntu on a Sata. Each have Grub files and I used bios to alter the boot order. I wonder if  part of my faulty 32 bit upgrade was caused by me having a Sata with another Grub file. Perhaps one pointer here, when I had both drives connected during the upgrade at some point with my faulty OS I accessed Grub on my Sata and edited the UUID from my Sata's using e then altered  it to that of my IDE drive and it then accessed my IDE drive, though I don't remember what happened next. Currently I have the Sata drive disconnected to work just on my faulty 32bit OS.

If I choose any  2.6.22-14 kernel I've left with-
Begin : waiting for root file system
check root=bootarg cat/proc.cmdline
or missing modules,devices: cat/proc/modules ls/dec
Alert /dev/disk/by-UUID/242e7752-e68e-45b4-a5b4-a581e3762ca00 does not exist. Dropping to a shell.

Busy Box etc.
(initramfs)_

Any suggestions?

Your upgrade of kernel might have changed your IUUD and or partitions.
Run:
blkid
cat /etc/fstab
cat /boot/grub/menu.lst
And checke them and change them if necessary.

---

### Post by Handssolow on 2008-02-10
Thanks Pumalite for your help. I've only my IDE drive, cdrom and floppy. Here are some results-
$ blkid
/dev/hda1: UUID="242e7752-e68e-45b4-a5b4-581e3762ca00" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: UUID="233aebef-8b77-4da5-86c1-94b228ebc45e" TYPE="swap"

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=242e7752-e68e-45b4-a5b4-581e3762ca00 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=233aebef-8b77-4da5-86c1-94b228ebc45e none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

Here are a few entries from ~$ cat /boot/grub/menu.lst

# kopt=root=UUID=242e7752-e68e-45b4-a5b4-581e3762ca00 ro

# groot=(hd0,0)

(The following selection doesn't boot and drops me to "Begin:waiting for root file system)
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=242e7752-e68e-45b4-a5b4-581e3762ca00 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

(The following is my current selection that I've booted from-)
title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=242e7752-e68e-45b4-a5b4-581e3762ca00 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet

Is there anything abnormal to be seen here?

---

### Post by Pumalite on 2008-02-10
Check sudo fdisk -lu for partition problems.
Get Super Grub and see if you can boot your 14-generic: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by confused57 on 2008-02-10
> **Handssolow said:**
> Thanks Pumalite for your help. I've only my IDE drive, cdrom and floppy. Here are some results-
$ blkid
/dev/hda1: UUID="242e7752-e68e-45b4-a5b4-581e3762ca00" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: UUID="233aebef-8b77-4da5-86c1-94b228ebc45e" TYPE="swap"

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=242e7752-e68e-45b4-a5b4-581e3762ca00 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=233aebef-8b77-4da5-86c1-94b228ebc45e none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

Here are a few entries from ~$ cat /boot/grub/menu.lst

# kopt=root=UUID=242e7752-e68e-45b4-a5b4-581e3762ca00 ro

# groot=(hd0,0)

(The following selection doesn't boot and drops me to "Begin:waiting for root file system)
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=242e7752-e68e-45b4-a5b4-581e3762ca00 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

(The following is my current selection that I've booted from-)
title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=242e7752-e68e-45b4-a5b4-581e3762ca00 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet

Is there anything abnormal to be seen here?
This may not work, but when you boot your pc, highlight the 2.6.22-14 entry in your grub boot menu, press "e", then highlight the kernel line, press "e" again, then add "all_generic_ide"(without quotes) to the end of the kernel line, press "enter", then "b" to boot.

I was lucky & had no problem upgrading the kernel, but found the above info in a bug report...if by chance it happens to work, it might give some insight to the problem.

---

### Post by Handssolow on 2008-02-10
Here's the result of sudo fdisk -lu whilst I find my Supergrub CD and instructions.

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcc3ccc3c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    76967414    38483676   83  Linux
/dev/hda2        76967415    80292869     1662727+   5  Extended
/dev/hda5        76967478    80292869     1662696   82  Linux swap / Solari

---

### Post by Handssolow on 2008-02-10
I regret to say that neither adding all_generic_ide nor my use of the Super grub CD has helped. Initially I did think I was onto something when using the SuperGrub CD and had selected GNU/Linux seeing the line containing "sda1" as here-
Select a /etc/fstab file
1 hda1 sda1 (hda0,0) hd)s1 ext2fs Ubuntu 7.10\n\l

But I think this is normal and not a reflection of me having had a Sata drive connected at the time of my linux-headers 2.6.22-14 upgrade. I'm still thinking that I should have removed my Sata drive before upgrading the kernel on my 32 bit Ubuntu's IDE drive, I will next time.

---

### Post by alexandreracine on 2008-02-11
[QUOTE=frodon;4278721]No it is not, it rebuilds your menu.lst file so if you tweaked some entries or added some extra options you are more likely to have to do that again.

Yeah, but I had Vista in my menu before I changed stuff, and it is still not there. (Don't worry I had a backup!) I'll fill a bug report.

---

### Post by Handssolow on 2008-02-11
It's frustrating, I've been unable to find anything wrong with my files including Grub etc to explain why I'm not able to boot up kernel 2.6.22-14 in any flavour. My use of the Supergrub CD and some exploration of  Busybox didn't yield any pointers.  I have gone now for complete removal of 2.6.22-14 using Synaptic and now Grub's menu.lst no longer shows the latest kernel. I'm posting this from  the lower life form that is 2.6.20-16-generic.

Next I'd like to reinstall (yet again) the latest kernel but this time using the terminal, what packages do I need to installed for kernel 2.6.22.14. As  I have an AMD Athlon 64 x2 cpu running 32 bit Ubuntu OS I use generic and  I assume to be on the safe side I should have 386 too. 

What packages and therefore what command lines in the Terminal should I employ to install  the 2.6.22-14 kernel considering too that I've a Geforce 6600gt Nvidia based card?

---

### Post by Pumalite on 2008-02-11
If you want to reinstall; download an iso frrom here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
I don't know about your computer, but find out if you can run 64 bit. You might like it better.
Follow this guideline:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by Handssolow on 2008-02-11
Thanks Pumalit.

I've got 64 bit working on a Sata ( currently disconnected) but Skype Beta with webcam support isn't yet available for64 bit Linux. We use 32 bit Skype Beta to chat to our son and family in the USA. I'm not at this stage wanting a fresh install of 32 bit to overcome my 2.6.22-14 kernel problem. What do need to do to install the latest kernel?

---

### Post by Pumalite on 2008-02-11
Just updating gets you the latest kernel. (for your system)

---

### Post by Creap on 2008-02-12
I don't actually experience any problems that I've noticed yet, but whenever I install any new updates the installers (Synaptic, apt-get or the autoupdater) give me errors and tells me to reinstall. This is what I get, reconstructed with a reinstall of the kernel:

```
sudo apt-get install --reinstall linux-image-2.6.22-14-generic 
--snip--
Ställer in linux-image-2.6.22-14-386 (2.6.22-14.51) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-386
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: fel vid hantering av linux-image-2.6.22-14-386 (--configure):
 underprocess post-installation script gav felkod 2
Ställer in linux-image-2.6.22-14-generic (2.6.22-14.51) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: fel vid hantering av linux-image-2.6.22-14-generic (--configure):
 underprocess post-installation script gav felkod 2
Ställer in linux-image-2.6.22-14-rt (2.6.22-14.51) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: fel vid hantering av linux-image-2.6.22-14-rt (--configure):
 underprocess post-installation script gav felkod 2
Fel uppstod vid hantering:
 linux-image-2.6.22-14-386
 linux-image-2.6.22-14-generic
 linux-image-2.6.22-14-rt
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
What's wrong here?

---

### Post by Handssolow on 2008-02-13
Well after several days of working at it,  I'm no further forward getting 2.6.22-14-generic to run on my PC. It stops every time at "waiting for a root file system". Eventually I've had enough,  press escape to select 2.6.20-16-generic in Grub which then boots up no problem

Back to 2.6.22-14,  neither reinstalling linux-headers 2.6.22-14-generic, linux- image 2.6.22-14-generic, nor updates of initramfs 2.6.22-14-generic or my experiments in Grub resolve this issue. Equally I've found no bios changes or Grub edits which work. I'm mystified, I have no idea.

I had a moment of optimism yesterday when a sudo apt-update and sudo apt-upgrade showed there was a linux-image2.6.22-14 update. Nothing doing, I sill get waiting for a root file system. Changing Grubs UUID to the older /dev/hda or /devhda0 or /dev/hda1 makes no difference.

Any suggestions apart from a fresh install?

---

### Post by sleepingdragon on 2008-02-13
My KDE desktop went haywire. Lost my taskbar and vmware-server went to 100%. Had to dump my .kde folder and uninstall vmware to regain my desktop. On top of all this, I lost access to my MP3 players; they were totally ignored. I had to install pysdm to get them working again, that was quite a surprise. 

I see that a lot of people had problems with either ALSA or the graphics, I can't say that I experienced either problem. I'm on an nVidia 6200 with a generic C-media 5.1 surround sound card.

---

### Post by DaytonaJohn on 2008-02-13
I have had a problem with the last several linux-headers/linux-image updates. Every time I install a linux-image update, it incorrectly modifies my menu.1st file, changing the root device from hd(0,1) to hd(0,2), and making my system unbootable. I am using a dual boot system with Windows on partition 0, ubuntu on partition 1 and swap on partition 2. In the past I have fixed this by booting the ubuntu CD and editing menu.1st. With the most recent update, I corrected menu.1st before the reboot. Here is what fdisk says about my disk:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3830    30764443+   7  HPFS/NTFS
/dev/sda2            3831        6635    22531162+  83  Linux
/dev/sda3            6636        7296     5309482+  82  Linux swap / Solaris

    I suspect that the routine that updates menu.1st is incorrectly identifying my swap partition as my bootable linux partition.

---

### Post by DaytonaJohn on 2008-02-13
Oops. After a bit more research I discovered the "# groot=(hd0,2)" line in menu.1st. I modified that to (hd0,1). I believe this will fix my problem. Anyone else having a similar problem: the #groot= line sets the default partition where /boot is located.

---

### Post by Handssolow on 2008-02-13
Looking at the history file in Synaptic I successfully downloaded and installed linux-headers and image 2.6.22-14.46 on 19th December 2007. It was the upgrade to 2.6.22-14.47 on 5th February 2008 that screwed things up resulting in me having to drop back to 2.6.20-16-generic.

I've only my IDE drive currently connected with it's 32bit Ubuntu but I still wonder if the presence  of my Sata drive with 64 bit Ubuntu (dual boot using bios drive priority) on the 5th February 2008 affected the kernel upgrade.

Anyone else booting with kernel 2.6.22-14.47 and a mixed Sata and  IDE setup?

---

### Post by Shazaam on 2008-02-13
handssolow...
According to Synaptic I am running .47 and there is an update to .52 available. Have you tried updating to 2.6.22-14.52 generic? So far I haven't updated to .52 yet because of the problems people are having. And mine is a clean install of Gutsy not an upgrade. Gutsy is on a SATA and XP is on an IDE drive.

---

### Post by eznet on 2008-02-13
Been busy lately and haven't been able to check back in or upgrade... I use this system a lot and so wanted to wait until I could fix what might brake... This thread has really grown in the last week... Looks like there have been a lot of people having problems and a fortunate lot who hasn't... 

I am happy to report that I completed all available upgrades without incident (thus far, at least)...

```
Linux eznet-1 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz

GeForce 8500 GT(SLI)
GeForce 8500 GT(SLI)
```

---

### Post by frodon on 2008-02-14
That's not true really few people had issues with this update, it's just that this forum is big and persons who post are in 90% of the cases persons who have had problem because we are a support forum.

You can update without risk and if you are really unlucky which i hope you're not then we will help you.

---

### Post by Pumalite on 2008-02-14
> **Shazaam said:**
> handssolow...
According to Synaptic I am running .47 and there is an update to .52 available. Have you tried updating to 2.6.22-14.52 generic? So far I haven't updated to .52 yet because of the problems people are having. And mine is a clean install of Gutsy not an upgrade. Gutsy is on a SATA and XP is on an IDE drive.

Just upgraded to 2.6.22-14.52 generic in 5 different hardwares without any problem.

---

### Post by Handssolow on 2008-02-14
Final thoughts before I'm off-line until the end of the month. 
I've still no idea why I can no longer use 2.6.22-14 since the update on 5th February. My system isn't that corrupted because I can use 2.6.20-16 but something happened during the upgrade of the linux headers and image rather than it just being a fault with the new kernel.  I have also reported on another thread an error during update-initramfs -c  -k 2.6.22-14-generic which I later resolved.  I  subsequently found a similar incident report after a web search.

update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
find: /lib/firmware/2.6.22-14-generic: No such file or directory

---

### Post by Mach1US on 2008-02-15
I have upgraded last week to  kernel 2.6.22-14-generic which came in with some other updates through update manager.
Since the upgrade i am unable to boot 2.6.22-14 but i still have 2.6.20-16 in my splash boot menu which i'm using now.
When i chose 2.6.22-14 it starts normally i get the Ubuntu logo but after about 5 or 10 seconds the orange bar stops progressing and after another 30 seconds screen turns black with blinking " _ " symbol and at that point it does not react to anything.
Do i need to reinstall everything all over again?

---

### Post by Pumalite on 2008-02-15
After the upgrade of every kernel you have to reinstall your video driver if you download them from Nvidia and installed them in a virtual terminal.

---

### Post by Mach1US on 2008-02-15
I actually have intel's  integrated 915 chipset, no special drivers have been installed.
All i have done was fixed the resolution which wasn't configured properly during initial install.
my xorg.conf
```
Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```  
Should use xorg.conf.failsafe or something in in that sort to get it back ?

---

### Post by Pumalite on 2008-02-15
Do you have an xorg.conf.back or .old?

---

### Post by Mach1US on 2008-02-15
I have tried all my backup xorg files and still is stopping in the same exact place ?
i also tried sudo dpkg-reconfigure -phigh xserver-xorg but didn't help at all.
Any other ideas?

---

### Post by Handssolow on 2008-02-26
Back on line after a break I'm still looking for ideas why I'm unable to run with the 2.6.22-14-generic kernel. Nothing I've read on the Forum or done in the last few hours has helped. I can only run Gutsy using the 2.6.20-16-generic kernel but anything higher drops me back during boot up  looking for a root file system and then a BusyBox line about initramfs. I'm not talking about an xserver-xorg/ linux restricted module driver/ re-configuration with every kernel upgrade issue here.

The good news is that on my dual boot system,  I've still got 64 bit Ubuntu on my Sata running 2.6.22-14-generic and no problem with my wife's PC, the bad news is that 32 bit Ubuntu on my IDE drive will still only run 2.6.20-16-generic.

I've re-installed the 2.6.22-14-generic headers and also tried what happens when I remove the 386 kernel header and image packages which I assume I don't need but got nowhere further than back to having to run 2.6.20-16-generic. There are no errors in Grub's menu.lst that I've identified.

Any help or inspiration will be appreciated.

---

### Post by Mach1US on 2008-02-26
Just to let you know i haven't been able to fix it too, doing fresh upgrades of .22-14 on top of my old kernel yielded same effect .
I finally cut my losses after hours of fruitless work  and did fresh install, realizing that at that point time-cost benefit ratio got too ridiculous .
I have to admit that matured version of Gutsy is way better than the one i installed day after release.
I like experimenting and i always was early adapter but i think i'll wait with all next big roll outs.
Still if any body has any ideas regarding this problem any help would be appreciated.

---

### Post by prostar on 2008-02-28
I've also had boot up/stalling issues since the kernel upgrades.  Mine are not 100% though.  If I try 2-3 times I can get it to go.  So far it "seems" like if I disable the splash screen, it goes okay.  I am on gutsy AMD 64bit with NVidia built in.  This is really annoying and it hurts the "Wife Acceptance Factor"...

---

### Post by prostar on 2008-03-07
I discovered that the grub boot line option  "vga=xxx" that I added for the previous boot up issues was causing my problem.  With out it all has been fine for a week.

---

