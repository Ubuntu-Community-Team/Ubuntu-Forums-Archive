---
title: "nividia driver wont install!"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by hessiess on 2007-05-18
i tryed to install the .run driver for my lappy card

got this error mesage

[IMG]http://home.wanadoo.nl/ebrahimismail/hessiess.jpg[/IMG]

what do i do? i still have no internet in linux

---

### Post by dannyboy79 on 2007-05-18
> **hessiess said:**
> i tryed to install the .run driver for my lappy card

got this error mesage


what do i do? i still have no internet in linux

if you're sure you have a nvidia card then just make sure you meet the nvidia driver's requirements. one of them is to have what the error is telling you installed. so the easiest way is to install the build-essential package using this command

sudo aptitude install build-essential

most all tools required for compiling stuff and development work will be installed when you do the above command. if you can't get your internet to work, you should use the search function within this forum and look for other internet problems threads. a good way to solve your issue, is to always be preparred  first. check out the output from this command and it'll tell you what pci chipset's your computer has.

lspci -v

or if you have a usb wireless adapter

lsusb -v

within the results from the above commands you should see the ethernet adapter for your computer and if you get help from some1 they'll most likely ask you for tyhis info. also, you can view the output from 

dmseg


to see if it says anuythign about wifi, wlan0, eth0, rausb0, or soemthing relateing to wireless or ethernet. if all else fails, then post another thread asking for internet help.

---

### Post by vtel57 on 2007-05-18
Make sure you have the following installed on your Ubuntu system before attempting to run the Nvidia compiler script:

1) GCC --> It's in the repos. Install using Synaptic.

2) kernel-headers --> install the corresponding kernel-headers package for the kernel you're booting to.

Run the Nvidia compiler script from Run Level 3 (no X running). If you have the above installed properly, the Nvidia compiler will create a kernel module for your current kernel and reconfigure your xorg.conf.

One thing to remember... you'll have to rerun the Nvidia script each time you do a kernel upgrade. The driver module it creates is ONLY for the particular kernel that it was running on at the time.

Luck! :)

---

### Post by hessiess on 2007-05-18
it ses that somthing isant instaled ant it tryes to download it , no internet. then outputs the above mesage

i alredy have a post for the internet problem, its a bt voyager network and linux seems to be unable to conect to it.

is it posable to download the files needed by the driver in windows and moove them to linux? i need to get this graphics driver working to make blender good

---

### Post by dannyboy79 on 2007-05-18
if you have the cdrom that you installed ubuntu from, you should be able to enable that within your sources.list and then it should retrieve the required stuff from the cd instead of trying to download the stuff. I didn't put 2 and 2 together when you said your internet didn't work and then I told you to download the build-essential package, sorry about that. so this is what you should try. go to system, admin, and I forget if it's package manager, or what, but somewhere you can open a gui which will allow you to add the cdrom as a repository. do this and hten try to do install using the same command again. if it doesn't work, than I am guessing that the build-essential is in the universe or multiverse repo whicih isn't on the cd. you could I suppose download everything on windows and transfer it over but that's a hell of a lot harder than just gettting your internet working in ubuntu. please post waht I asked for and I can maybe help depending on your ethernet card.

ps, if you have a post for the internet, you really shouldv'e linked to it so I could help you there.

---

### Post by vtel57 on 2007-05-18
The Nvidia compiler tries to access the Net to look for any pre-compiled modules for your system on the Nvidia site. Just skip this part of the install.

AH! Yes... I apologize. I see that you don't have Internet access at this time. Use dannyboy's method to install the required items.

---

### Post by dannyboy79 on 2007-05-18
> **vtel57 said:**
> The Nvidia compiler tries to access the Net to look for any pre-compiled modules for your system on the Nvidia site. Just skip this part of the install.

but he doesn't have access to the internet to download the required build packages and or kernel headers. do you think they are on tyhe cd as I have suggested?

---

### Post by hessiess on 2007-05-18
> **dannyboy79 said:**
> if you have the cdrom that you installed ubuntu from, you should be able to enable that within your sources.list and then it should retrieve the required stuff from the cd instead of trying to download the stuff. I didn't put 2 and 2 together when you said your internet didn't work and then I told you to download the build-essential package, sorry about that. so this is what you should try. go to system, admin, and I forget if it's package manager, or what, but somewhere you can open a gui which will allow you to add the cdrom as a repository. do this and hten try to do install using the same command again. if it doesn't work, than I am guessing that the build-essential is in the universe or multiverse repo whicih isn't on the cd. you could I suppose download everything on windows and transfer it over but that's a hell of a lot harder than just gettting your internet working in ubuntu. please post waht I asked for and I can maybe help depending on your ethernet card.

ps, if you have a post for the internet, you really shouldv'e linked to it so I could help you there.

il give that a go now, thx

[the network post]("http://ubuntuforums.org/showthread.php?t=434944&highlight=bt+voyager")

windows is extremly slow, linux is usless without the graphics driver, see my problem :lolflag:

---

### Post by vtel57 on 2007-05-18
> **dannyboy79 said:**
> but he doesn't have access to the internet to download the required build packages and or kernel headers. do you think they are on tyhe cd as I have suggested?

Hi Danny,

Yeah... I'm pretty sure that stuff is on the CD. It might be older versions, but they'll still work. :)

~Eric

---

### Post by hessiess on 2007-05-18
just saving page so i can try it;)

why dosent this stuff come pre installed?

---

### Post by vtel57 on 2007-05-18
Kernel-headers are not needed, usually. The everyday user wouldn't be compiling his own modules. Same for GCC. Both of those packages are used mainly for development. They're there if you need them, though. :)

---

### Post by hessiess on 2007-05-18
guss what, it didant work!

did add cdrom from the menu in the app. it monted the live cd red it and unmounted agen in under 10 seconds

surched threw the thingie and it sed that gcc is alredy installed.

im begining to thing that its inposable without a internet conection. but my only internet conection is via a wireless network that seems to be completly incompatable with linux! bt linux support is poor. 

im runing the driver by using sudo sh NVIDIA-Linux-x86-1.0-8756-pkg1.run

---

### Post by vtel57 on 2007-05-18
1) You don't need Internet access to run the Nvidia script.

2) Running it as sudo sh... is fine. If you weren't doing it right, you would have never gotten to the stage where you are in that picture above.

3) Do a search, using Synaptic (now that the CD is added to the repos), for the exact file that the compiler is asking you for in that picture above: libc or libc-devel.

Tell us what happens when you search for that...

---

### Post by hessiess on 2007-05-22
[witch one of these is it?]("http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=feisty&subword=1&exact=&arch=any&releases=all&case=insensitive&keywords=libc&searchon=names")

---

### Post by vtel57 on 2007-05-22
None that I could see. I didn't look through every page, though. What you need is gcc. That's just the way it looks in synaptic... **[COLOR="Red"]gcc[/COLOR]**.

---

### Post by hessiess on 2007-05-23
when i tryed to install the hedders and gcc it sed thay wore alredy instaled?

---

### Post by vtel57 on 2007-05-23
Run your Nvidia script again and let me know what happens, please.

---

### Post by hessiess on 2007-05-24
ok:)

---

### Post by p1977p on 2007-05-24
i tried installing the synaptic touchpad drivers for my AMD turion64 laptop running Xubuntu 64bit. it suggested installing the nvidia display driver (i have an onboard nvidia geforce card). however after reboot, X doesn't start. it reports something like :" couldn't find page; no driver installed" . booting in recovery mode doesn't help either.... i'm not an expert at command line recovery.  somebody please help!

---

### Post by hessiess on 2007-05-24
can you acsess the comand line?

log in with your normal user and do "sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf" it is case sensative, print it out if nesoserry. 

and if that dosant work   "dpkg-reconfigure xserver-xorg"

and set the driver to nv, leev the rest as defolt

then restart xserver "sudo /etc/init.d/gdm restart."

i lernt this the hard way my furst atemt at instaling the driver!!

vetl57. it still dos exactly the same thing.

---

### Post by vtel57 on 2007-05-24
Hi, Heissiess...

Well, that s*cks! :( I think you're going to have to snoop around on your own and see if you can determine why the installer doesn't like your gcc. Without me actually sitting in front of your computer, I've kinda' reached the end of my ideas here.

Have you, by any chance, attempted to install and use Automatix to install your video drivers? Automatix is a pretty handy application. You can install a lot of other goodies, too, not just the Nvidia stuff. 

Keep us posted on any progress, please.

Luck!

@p1977P... it would probably be a good idea for you to start your own thread on your situation. You'll get better response that way.

---

### Post by hessiess on 2007-05-24
it gives this error:

unable to determine the verson of the kernal scorces located in '/usr/src/linux-headers-2.6.20-15-generic'. plese make shore you have instaled the cernel scorce files for your kernel and that thay are propaly configured; on read hat linux systems, foe example. be sure you have the 'kernel-source' rpm installed. if you know the correct kernel scorce files are installed, you may specify the kernel scorce path with the '--kernel-scorce-path' command line option.

dos this healp?

---

### Post by vtel57 on 2007-05-24
Well, it tells me that you probably do not have the correct kernel source installed for the kernel you're booting to.

```
 $ uname -r
```

```
 $ ls -a /boot
```

```
 $ ls -a /usr/src
```

Please post the output of those commands here.

---

### Post by hessiess on 2007-05-25
here you go:)

```
cd 
a@a-laptop:~$ uname -r 
2.6.20-15-generic 


a@a-laptop:~$ ls -a /boot 
.                         initrd.img-2.6.20-15-generic 
..                        initrd.img-2.6.20-15-generic.bak 
abi-2.6.20-15-generic     memtest86+.bin 
config-2.6.20-15-generic  System.map-2.6.20-15-generic 
grub                      vmlinuz-2.6.20-15-generic 


a@a-laptop:~$ ls -a /usr/src 
.  ..  linux-headers-2.6.20-15  linux-headers-2.6.20-15-generic 
a@a-laptop:~$
```

---

### Post by vtel57 on 2007-05-25
Everything looks good there. Can you show me the output of this command:

```
$ gcc -v
```

---

### Post by hessiess on 2007-05-25
```
a@a-laptop:~$ gcc -v 
Using built-in specs. 
Target: i486-linux-gnu 
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu 
Thread model: posix 
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4) 
a@a-laptop:~$
```

---

### Post by vtel57 on 2007-05-25
Well, my friend... you have everything you need to get the Nvidia script to run correctly. You have the proper kernel headers, you have gcc installed, etc. I have **no** idea why you're having problems running that script. At this point, you're probably going to have to seek assistance from a more knowledgeable source. 

Sorry I couldn't get it squared away for you. :(

---

### Post by hessiess on 2007-05-25
would you know who to ask? 

thanks for your halp;)

---

### Post by dabl on 2007-05-25
You might want to give Envy a try -- no guarantees.  First look (with Synaptic) in the repositories.  If you don't see it, then download it and follow the instructions from this web site:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

HTH

---

### Post by vtel57 on 2007-05-25
I would recommend a search of these forums and Google, Hessiess. A quick Google search that I just did using "Installing Nvidia in Feisty" brought quite a few hits of other forum posts and tutorials.

I'm not familiar with Envy, but Automatix should install the Nvidia drivers for you relatively painlessly. Try it. :)

Luck!

---

### Post by hessiess on 2007-05-25
dos that recwire a internet conection in ubuntu? it still isant working

---

### Post by vtel57 on 2007-05-25
Umm... yes. Automatix definitely requires an internet connection. :(

---

### Post by hessiess on 2007-05-25
il try sertching for an anser.

is it posable to find out what the ristricted driver manager is trying to download, so i can get it in windows and transfur it.

sofar everything in ubuntu has been dificult, but i dont rilly care as i can see it has lots of potensal.

---

### Post by hessiess on 2007-05-25
i tryed using this furst before making this thred. metherd 1 ruind x, metherd 2 just dosent work
[URL="http://ubuntuforums.org/showthread.php?t=432056"]
http://ubuntuforums.org/showthread.php?t=432056[/URL]

---

### Post by vtel57 on 2007-05-25
You're just experiencing a small bump in the road in your Ubuntu experience. I had many (and worse) when I first started out. It gets easier as you go along (and learn more). 

I'm not sure what "restricted drivers" you're talking about. When you download the Nvidia compiler script from the Nvidia site (make sure you get the right one for your kernel type) and run it, that compiler uses gcc and the linux headers to custom create a driver module for your kernel.

---

### Post by tseliot on 2007-05-27
hessiess:
You shouldn't have used Nvidia's installer without an Internet connection.

type:
```
sudo name_of_the_nvidia_installer --uninstall
```

then try Method 1 offline of my guide:
[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

---

### Post by hessiess on 2007-05-27
the nivida installer wouldet run, cept saying somthing about the kernal scorce.

the furst thing i tryed was metherd 1 ofline in your guide. xserver wouldent load. il try doing that again, i was abit confused over witch of the 3 files i need to download

---

### Post by tseliot on 2007-05-28
> **hessiess said:**
> the nivida installer wouldet run, cept saying somthing about the kernal scorce.
this depends on the fact that your internet connection is not available.

> **hessiess said:**
> the furst thing i tryed was metherd 1 ofline in your guide. xserver wouldent load. il try doing that again, i was abit confused over witch of the 3 files i need to download

What's the model of your graphic card?

---

### Post by hessiess on 2007-05-28
nividia gforce go 7200

---

### Post by tseliot on 2007-05-28
> **hessiess said:**
> nividia gforce go 7200

You will have to install nvidia-glx-new i.e. driver 9755

---

### Post by hessiess on 2007-05-28
i tryed to install that driver but it sed somthing about dependency/ nivida-glx

installed that, then it sed that it's conflicting with nvidia-glx! what am i dooing wrong here?

---

### Post by hessiess on 2007-05-31
ok, i broke ubuntu again, but ive fixed it again.
 
purge removed nividia glx and now it ses (see atachment)

what do i need to do now?

---

### Post by tseliot on 2007-05-31
> **hessiess said:**
> ok, i broke ubuntu again, but ive fixed it again.
 
purge removed nividia glx and now it ses (see atachment)

what do i need to do now?

Close Synaptic and try doing it from the command line (so that you can copy and paste the output of the error here.

Open Terminal and type:
```
sudo apt-get --purge remove nvidia-glx
```

then:
```
sudo apt-get install nvidia-glx
```

---

### Post by hessiess on 2007-05-31
thx for your help:) i got it working:).

---

