---
title: "fail: try install ubuntu on old non pae laptop"
date: 2014-09-01
forum: Installation &amp; Upgrades
---

### Post by tomas19 on 2014-09-01
By this post Im wondering despites of coming through many topics along the linux internet community if everyone will suggest solvint solution for making my old ibm x31 laptop working.

1. As it seems it has cpu not supporting pae.

2. Ram 512 ram

I do not mind so much. Im not picky when it comes down to os. Im having simple demmands.

I want use my ibm for internet. Email music and writtings. Word. Thats all.

I transform from xp. I stay curious how it would be this possible acomplished. 

Since now i ve tried:

Lubuntu with forcepae
Pepermint 5
Bodhi
Slax

All got stuck. Some of them soon or later. Most far i got by trying lubuntu by forcepae. To loading scren. Than it stucked on screen with blue lubuntu wallpape lr got frozen.

Please could you adviced me how to proceed in that case?

Thank you very much

ps. i did not also formated yet my ibm

---

### Post by tomas19 on 2014-09-01
By this post Im wondering despites of coming
through many topics along the linux internet
community if everyone will suggest solvint
solution for making my old ibm x31 laptop
working.
1. As it seems it has cpu not supporting pae.
2. Ram 512 ram
I do not mind so much. Im not picky when it
comes down to os. Im having simple
demmands.
I want use my ibm for internet. Email music
and writtings. Word. Thats all.
I transform from xp. I stay curious how it
would be this possible acomplished .
Since now i ve tried :
Lubuntu with forcepae
Pepermint 5
Bodhi
Slax
All got stuck. Some of them soon or later .
Most far i got by trying lubuntu by forcepae .
To loading scren. Than it stucked on screen
with blue lubuntu wallpape lr got frozen.
Please could you adviced me how to proceed
in that case ?
Thank you very much
ps. i did not also formated yet my ibm

---

### Post by mörgæs on 2014-09-01
Threads merged. Please stop double-posting.

---

### Post by mastablasta on 2014-09-01
try LXLE as well. also Chrunchbang if you have the time.

when you boot lubuntu and get that what you call "wallpaper" hit Esc see what is happening behind the curtain. it could be that computer is still working. live OS (try it option) requires all system to be loaded into ram and that might take some time on older machines.

also what GPU does the computer have (it would be good if you could post some specs. on WinXP you can use S*peccy t*o get the info)? you might need to use some additional boot parameter like nomodeset or force vesa : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by sudodus on 2014-09-01
Hi Thomas,

I have an IBM Thinkpad T42 with pae capability but without pae flag. It works with 12.04 LTS using non-pae kernels and also with pae kernels and fakepae. It also works with 14.04.1 LTS using forcepae and with [Phill W's non-pae kernel]("http://ubuntuforums.org/showthread.php?t=2216356"). I have no problems with the graphics and no problems with the network.

But I think your computer is older. Maybe you will have better luck with a system built on 12.04 LTS. I don't know which version of ***Bodhi*** you tried, but I would try an old one based on 12.04 LTS or ***LXLE*** based on 12.04 LTS or ***Precise Gnome Classic Tweaks***. If you are not afraid of another kind of installer, you can try the One Button Installer, which can download and install such systems quite easily. All these distros and tweaks promise support until April 2017. Because your computer is old, it is likely that an older version of the software will work better than 14.04.1 LTS.

See these links if you can boot from a USB pendrive[URL="http://ubuntuforums.org/showthread.php?t=2172971"]

One Button Installer, 'OBI'[/URL]
[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

or if need to boot from a CD

[OBI-9w installer]("https://help.ubuntu.com/community/9w#Ubuntu_14.04_LTS_text_non-pae_.27Trusty-npae124-text.iso.27_and_.27obi_Trusty-npae124-text-9w.iso.27")

You can find some more details in order to understand the problem and test your computer's CPU in this link

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

---

### Post by grahammechanical on 2014-09-01
May I offer an opinion? You may also be having video driver problems because the video adapter is so old that it is not supported by the proprietary video driver. When you install do not tick the box marked "install third party software." Then the install will use an open source video driver.

If you get a working desktop then you can search for Restricted Extras in the software centre and get those audio and video codecs but without a proprietary video driver.

Regards.

---

### Post by tomas19 on 2014-09-02
first of all. thank you for any responds of trying get it solved. for your time. but guys be aware that im not guru when it comes down to hardware, software and linux at all. codes etc.

please keep that in mind when you writting answers and giving advices.

by this i would  like u kindly ask for detailed step by step how to get it work out. 

which system i supposed to. use in order to make my laptop function:

ibm thinkpad x31
intel pentium m processor
1.3ghz

installed memory: 1024mb

thank you for any advice

---

### Post by mastablasta on 2014-09-02
try LXLE with no PAE kernel. 
AntiX (debian/mepis based) also comes with no-PAE kernel version. and is aimed at older PC.: [http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)
might not look so pretty but you can always add LXDE to it or XFCE later on.

you can try both in live session.

You CPU does not support PAE so you need the kernel (core of the OS) that works with such CPU. 
suggestions above include - using distributions that support such CPU or to replace the default kernel with kernel that supports the CPU (a bit more hardcore solution).

at the same time when choosing a distribution take care to use light desktop environment (such as the one found in LUbuntu or Xubuntu) or install windows manager only. since you GPU is likely not strong and support the heavy 3D desktops (found in Ubuntu and Kubuntu).

 good luck.

---

### Post by tomas19 on 2014-09-02
i am totqly beginner in order to provide quality answer i must be able give quality question.

what am i doindg till now is just randomly trying downloading several linux os. kubuntu, bodhi, ubuntu etc. by creatint boot flash with usb installer universal and then boot them in my laptop. and always end by failing.

what am i doing wrong, what must be done better?

---

### Post by tomas19 on 2014-09-02
please could be possible for you provide me correct link where to get it?

thank you so much

---

### Post by mörgæs on 2014-09-02
It could be a problem of not enough memory. All the distros suggested above are GUI distros, and though they are light in relation to modern standards they might be too heavy for an x31.

I suggest that you begin with a command-line system for example the [minimal 12.04 without PAE]("http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/mini.iso"). How does it work?

---

### Post by mastablasta on 2014-09-02
> **tomas19 said:**
> please could be possible for you provide me correct link where to get it?



I've put the link already in the post.
but ok here it is again AntiX this time with direct link - [http://sourceforge.net/projects/antix-linux/files/Final/MX-14.2/](http://sourceforge.net/projects/antix-linux/files/Final/MX-14.2/) select the non-pae image to download.

as for LXLE you need to check which version has non pae.

> **mörgæs said:**
> It could be a problem of not enough memory. All the distros suggested above are GUI distros, and though they are light in relation to modern standards they might be too heavy for an x31.

 I suggest that you begin with a command-line system for example the [minimal 12.04 without PAE]("http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/mini.iso"). How does it work?


they said they have 1 GB ram so it should be enough to run it live and descent at that.

@ tomas19 if you go this route with minimal iso - you can't use that to boot a live session. you an only use it to install. make sure you have wired internet connection and then here is a tutorial on how to do a minimal install: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

mostly you will be clicking "next" button a lot of times...

---

### Post by mörgæs on 2014-09-02
I see both a 512 MB post and a 1 GB one. In any case it's worth a shot to try something non-graphical.

---

### Post by tomas19 on 2014-09-02
ok. i got antix u described by using universal usb installer i created bo ot usb flash. bootnul and it wen to black screen by using escape went to command prompt by loading system. saying to use login root and pswd root and following instruction. that moment im stuck. how can i go furtheclr?

btw. im apr leciate a lot your help guys qeish just get it into success just only because of your time. thx

---

### Post by tomas19 on 2014-09-02
same is happening like in others case. wallpape lr show but then it got frozen.

im adding video:

[https://db.tt/OQG1ga7j](https://db.tt/OQG1ga7j)

---

### Post by tomas19 on 2014-09-02
maybe hdd is,just full. it s mystery to me thats would not be posadible get system working. i dont getting it.

---

### Post by mörgæs on 2014-09-02
Please give priority to spelling and punctuation. Makes your posts easier to read and might attract more answers.

---

### Post by tomas19 on 2014-09-02
ok. Im sorry. ao what Have been I doing. I gave an attempt what mastablasta gave like an advice:

downloaded antix version mx14 non. pae

I created in windowsxp pc boot flash by using utility usb universal installer

booted usb in my ibm thinkpad x31

i tried rubg antix while it got bo lot to install screen with using video mode safe.

endup in black screen shown in my videofootage posted above.

kindly asking advice what suppoesed to be next step?

thank you very much

---

### Post by sudodus on 2014-09-03
Hi again,

[See also my previous post (post #5)]

0. Have you got 512 MB RAM or 1 GB RAM?

It makes a big difference also in what distros to suggest. I'm assuming 1 GB RAM in the following, so if you have only 512 MB, please tell us, and you will get modified advice!

1. I suggest that you try another tool to create USB drives, Unetbootin. It works also from Windows. See these links

[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")

[https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_a_bootable_Ubuntu_USB_flash_drive_from_Windows](https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_a_bootable_Ubuntu_USB_flash_drive_from_Windows)

2. Which distro was running in the uploaded video clip? AntiX?

In that video clip your computer runs much longer than what is possible, if you have problems with PAE. So there are other problems, maybe

- the graphics driver
- the wifi driver
- lack of RAM
- (maybe something else ...)

3. Try the different linux distros ***live*** (if possible). Do not install until you find something that works.

Have you tried the current Lubuntu (version 14.04.1 LTS, 32-bits), lubuntu-14.04.1-desktop-i386.iso with the boot options **forcepae** and **nomodeset**?

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

4. If still problems, try a non-pae version of LXLE, for example the version 'LXLE 12.04.4 32bit Revisited' (that I have modified with isohybrid) at

[http://phillw.net/isos/linux-tools/hybrid-isos/](http://phillw.net/isos/linux-tools/hybrid-isos/)

I have tested it, and it works for me (in my IBM Thinkpad with a Pentium M CPU).

---

### Post by tomas19 on 2014-09-03
as I ve already announced im not advanced about hardware. but by my view i think my laptop is equiped 1gb ram. that what bios says on following screenshot:

[https://db.tt/1Saxj4LP](https://db.tt/1Saxj4LP)

---

### Post by tomas19 on 2014-09-03
ok lets do it step by step. what am i going to do now then?

1. i m gonna get lubuntu- 14 .04. 1 -
desktop- i386. iso

2. make usb boot flash on desktop xp pc

3. boot it in ibm thinkpad and start by forcepae and nomodeset. ill bring result soon.

thank you very much.

---

### Post by sudodus on 2014-09-03
Good luck :-)

---

### Post by tomas19 on 2014-09-03
thank you. but i need something more. good luck its not enough:

[https://db.tt/3zVgZAge](https://db.tt/3zVgZAge)
[https://db.tt/OQG1ga7j](https://db.tt/OQG1ga7j)

---

### Post by sudodus on 2014-09-03
1. The other distro - AntiX - did you log in as root? (as suggested in the second video clip) Did that work?

2. So the startup of Lubuntu stopped. If you want to try more with Lubuntu, try the other boot options too (several at the same time, and you need **forcepae**).

3. If still no go, you can try the boot option **text** (together with forcepae). If this works (but not without it, I think it is the graphics driver that is causing problems.

4. While in text mode, and you have old intel graphics, you can try modifying to UXA acceleration according to this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics)

Edit (or create) **/etc/X11/xorg.conf** as follows: (there should be ***a tab*** before each line except the first and the last). 

Section "Device"
        Identifier "Intel Graphics"
        Driver "intel"
        Option "AccelMethod" "uxa"
EndSectionRestart X (reboot, restart your display manager, whatever).

So edit as superuser (with sudo) with the following command and enter the lines above and save the file.

```
sudo nano /etc/X11/xorg.conf
```

5. If still problems, try a non-pae version of ***LXLE***, for example the  version 'LXLE 12.04.4 32bit Revisited' (that I have modified with  isohybrid) at

[http://phillw.net/isos/linux-tools/hybrid-isos/](http://phillw.net/isos/linux-tools/hybrid-isos/)

I have tested it, and it works for me (in my IBM Thinkpad with a Pentium M CPU).

---

### Post by tomas19 on 2014-09-03
can you explain bit further step with text? I must say im having no clue how to make this happened ? what does it mean while in text? in boot screen?

---

### Post by sudodus on 2014-09-04
When you boot with the boot option **text**, you will not get a graphical desktop environment, but only a text screen. It may be similar to the boot screen, but (if it works) the system is ready for log in (or if you have auto login) ***ready for command lines in the bash shell***. In other words, the linux engine is running, but not the graphical desktop environment.

This way you can run commands to ***test and to tweak*** your system. I hope we can find what is wrong and tweak the system so that also the graphical desktop environment will work.

---

### Post by tomas19 on 2014-09-04
ok. let me try it out. I created also bootable flash usb with your LXLE 12 .04 .4.iso. but it goes into very colored distored screen while loading live os and endup there:

[https://db.tt/YDKeF0Hb](https://db.tt/YDKeF0Hb)

im.starting doubt about any solution... cannot be true. must be. mysterious to me.

---

### Post by sudodus on 2014-09-04
If LXLE fails too, try ***Knoppix***. It is known to be very good at recognizing old hardware.

[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

---

### Post by stillblue2 on 2014-09-04
Something I use now to install on non switchable PAE is MultiSystem [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

It allows for you to install the iso(s) to a flash drive and it gets around the PAE issue by using GRUB to launch the ISO and bypassing the PAE test. It's highly unlikely that your CPU doesn't support PAE, it's just getting it activated. With your ram Lubuntu or Xfce are the lightweights but you might try Mint as well since it comes with some extra drivers that are proprietary.

---

### Post by sudodus on 2014-09-04
> **stillblue2 said:**
> Something I use now to install on non switchable PAE is MultiSystem [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

It allows for you to install the iso(s) to a flash drive and it gets around the PAE issue by using GRUB to launch the ISO and bypassing the PAE test. It's highly unlikely that your CPU doesn't support PAE, it's just getting it activated. With your ram Lubuntu or Xfce are the lightweights but you might try Mint as well since it comes with some extra drivers that are proprietary.

This information about PAE is correct, but the OP has another problem now, I think concerning the graphics driver.

+1: Maybe the tip about ***Linux Mint*** will be successful.

---

### Post by tomas19 on 2014-09-07
believe or not after many non succesful attempts at least get my laptop into qork able mode it get happened now with knoppix. must say its not best interface i ve ever seen but i dont mind actually as long i will be able use word, spotify and email.

my questions and remarks.

im not specialists as same as many of u here guys and my gratefulness for you keep helping solve it. without it it couldnt be possible. thank you.

i want still try mint. just curious.



Q: now im booting from usb knoppix. it works. in case of using this os without having usb sticked inside all the time, how can i install it on laptop hdd ?

thank you.

---

### Post by sudodus on 2014-09-07
See this link [http://smtp.knoppix.net/wiki/Category:Hard_drive_Installation](http://smtp.knoppix.net/wiki/Category:Hard_drive_Installation)

Look for the paragraph ***"Poor man's install"*** which has a good description of how Knoppix is installed. It is *not* installed like for example Ubuntu.

---

