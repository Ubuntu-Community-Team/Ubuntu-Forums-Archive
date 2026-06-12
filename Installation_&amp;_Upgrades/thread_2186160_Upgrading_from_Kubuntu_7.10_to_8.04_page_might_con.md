---
title: "Upgrading from Kubuntu 7.10 to 8.04 page might contain error"
date: 2013-11-06
forum: Installation &amp; Upgrades
---

### Post by amitst on 2013-11-06
I am trying to upgrade Kubuntu 7.10 to Kubuntu 8.04 on my legacy hardware.

I am referring to the link [https://help.ubuntu.com/community/EOLUpgrades/Gutsy](https://help.ubuntu.com/community/EOLUpgrades/Gutsy) for the same (let me know if there is any better way to get Kubuntu to the latest version).

I noticed that the following line on the above page contains (perl syntax) error.
```

sudo perl -p -i.ORIG -e 's#^(/dev/)hda(\d+)#$1sda$2 /etc/fstab

```

I feel the above line should be,
```

sudo perl -p -i.ORIG -e 's#^(/dev/)hda(\d+)#$1sda$2#g' /etc/fstab

```

Please let me know if my suggested change is correct.

---

### Post by sudodus on 2013-11-06
Both those versions are way past end of life. It will be hard to find repositories with packages for the upgrade. And there will be no security updates.

I suggest that you back up your personal files and maybe bookmarks of the web browser, and make a fresh installation of a current version. The current long time support version is 12.04 LTS (actually the point release 12.04.3 LTS). The newest version is 13.10, but it has only 6 months support, so I would recommend 12.04.3 LTS, which is well debugged and polished.

If standard Ubuntu with Unity needs too much horsepower, try Xubuntu 12.04 with LTS until April 2015. The next LTS version will be 14.04 to be released in April 2014, and you  can expect that it will be possible to upgrade directly from one LTS  system to the next one in July or August, at the first point release (so  from an updated/dist-upgraded 12.04 to 14.04.1).

---

### Post by amitst on 2013-11-06
Thanks. I was trying to do a 12.04 LTS installation (Ubuntu 12.04 an also Xuuntu 12.04) through a USB flash drive. However, it the USB won't boot (it is known to boot properly on my newer system).

Sorry to trail away from the main topic, but the USB port is I think of type USB1. In the BIOS I see "USB FDD" and "USB ZIP" options for booting. However, I tried both with no luck.

I will try to burn a Xubuntu 12.04 DVD and try again.

---

### Post by mastablasta on 2013-11-06
if you have a floppy you can use plop boot manager to boot from USB (i do that on ancient laptop).

2 things i want to mention here 

first is you never mentioned your systems specs so we could give you better advice what to use. Kubuntu changed a lot since 7.10 and it now uses KDE4, but partial "classic" look&feel can still be obtained. but anyway for lower specs Kubuntu has low fat package which will turn off desktop effects and reduce system resoruces usage. you would be at about 200 MB ram with those.

second if you decide to go with Kubuntu i suggest the lastest 13.10 (supported for 9 months) and then upgrade to 14.04 LTS (supported 3 years i believe). the reason for that is that 13.10 is polished release in Kubuntu (they really didn't add that many new features) and  it uses latest KDE version which has a better system resource optimisation and uses less resources and is faster than the one in 12.04. ofcourse another neat option is to install 12.04 (supported for 5 years) and then just add PPA for newer KDE. KDE as desktop is now mostly getting bugs solved and improvement in system resources usage. so it's quite good and stable. at the same time they are developing version 5 which is not ready for use yet as i read.

---

### Post by amitst on 2013-11-07
I don't have a floppy but my old system has DVD writer. I can boot using a DVD/CD.

Here are the specs:
```

Processor: AMD Athlon XP 2000+ 1.67GHz, 
224MB RAM
Display adaptor: NVIDIA GeForce2 Integrated GPU

```

Another thing I noticed was, when I inserted Ubuntu 12.04 LTS DVD and booted through it, my monitor started showing something like "out of sync frequency, please change resolution" message. I tried with Mageia 3 Live DVD as well. Got the same message. I have Xubuntu 12.04 LTS CD, which boots fine. However, it seems it has errors while writing. So after couple of installation wizard screens the UI crashes and I start seeing shutdown messages in the console.

Any idea why frequency out of sync message might be coming?

---

### Post by amitst on 2013-11-07
I burned another DVD (Xubuntu 12.04) thinking the CD might have errors. However in both cases I observed the following (painstakingly slow performance),
- It took around 10 minutes to reach the "Do you want to try Xubuntu or install Xubuntu" message
- After clicking "Install Xubuntu" it took another 5 minutes to get the next screen "Install below third party software check box, free disk check, internet connectivity check"
- After selecting 3rd party software install and clicking continue, it took another 5-10 minutes and then UI disappeared
- I started seeing the following console message:
```

* Stopping enable remaining boot-time encrypted block device.... rest of the message went past the screen
                                                                                [OK]

```

I waited for 5-10 more minutes but nothing happened. The installation is stopping exactly at this point every time.

Any pointers?

---

### Post by mörgæs on 2013-11-07
You don't have enough RAM for installing. You could try to find some used sticks, but frankly I don't think it's worth the effort. CPU and graphics card are too weak.

Best is to find some used hardware, say 4-6 years of age. Should not cost you much.

---

### Post by amitst on 2013-11-07
I am able to move ahead after referring to this thread: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I selected nomodeset option by pressing F6 (removed quiet splash and also inserted xdriver=vesa) and went ahead. However, after a while, I am hitting a blank screen. :(

---

### Post by overdrank on 2013-11-07
> **amitst said:**
> I am able to move ahead after referring to this thread: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I selected nomodeset option by pressing F6 (removed quiet splash and also inserted xdriver=vesa) and went ahead. However, after a while, I am hitting a blank screen. :(

[_Recommended Minimum System Requirements_]("https://help.ubuntu.com/community/Installation/SystemRequirements")
> 512 MiB RAM (system memory)

---

### Post by amitst on 2013-11-07
Thanks mörgæs. Yes, I think, this is a good time to stop trying.

---

### Post by mastablasta on 2013-11-07
there is not enough RAM for Kubuntu (as others already said) but there are a few linux distributons (some Ubuntu based) that will work on your mashcine. i have something similar with slightly weaker CPU.

Some good and relatively easy options that are Ubuntu based are:
Lubuntu
LXLE
Bodhi Linux
Peppermint OS
Puppy Linux Precise (though not really ubuntu based, the precise version is made to use Ubuntu repositoies).

Chrunchbang - this one is Debain ("ubutnu's father") based but is still relatively easy to install. It runs a nice script after basic install so oyu can just add what you want and say no to the rest.

there are a few more dedicated to older hardware:
Slitaz Linux
Tiny Core linux
DSL  (damn small linux) - this one evenuses very old kernel


i would start with lubuntu but you won't be able to use graphics install. so just use mini.iso and then add lubuntu desktop package to it.

on a similar setup to yours i use Chrunchbang (but an older version that came with xfce). it takes about 80 MB ram on boot. i can write, watch you tube videos, play a few older games... nothing much. it acts as a netbook. it's fast enough for what it does.

---

### Post by sudodus on 2013-11-07
224MB RAM is enough for the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"), that you might try, if you like to test what is possible with this computer. But if you want a computer that can manage modern web pages with reasonable speed, use the tips by ***mörgæs*** in post #7.

---

### Post by leeper69 on 2013-11-07
Hi I have an old laptop that wont work with Ubuntu 12.4 but it will run just fine with puppy precise or macpup both of these use ubuntu precise repositories.  macpup is real nice check it out at distrowatch.com.

---

### Post by amitst on 2013-11-07
Thanks for the info. I am thinking of one last try before giving up. I am checking Lubuntu or Macpup.

For Lubuntu install from mini.iso will it need wired connection? I have a wireless USB stick. Will it be able to detect the internet and install lubuntu desktop package?

---

### Post by sudodus on 2013-11-08
> **amitst said:**
> 
For Lubuntu install from mini.iso will it need wired connection? I have a wireless USB stick. Will it be able to detect the internet and install lubuntu desktop package?

Yes the mini.iso will need internet, and it might be difficult to get a WIFI device to work. Such devices vary a lot, some work out of the box (Lubuntu finds and installs a suitable driver) some do not work at all with linux, and it is possible to install a linux driver for some WIFI devices (more or less manually).

If that is a problem, try the One Button Installer, which needs no internet during the installation. It works with 128 MB RAM. It might also work with the Lubuntu ***alternate*** iso file (that needs less RAM than the Lubuntu desktop iso file).

---

### Post by mastablasta on 2013-11-08
go with One button installer then if you don't have wired connection.

additionally just as info, the old KDE 3 is available as Trinity desktop. not sure how well it works. i know there is a distro that support it.

also i remembered there is another nice distro for older mashicnes called AntiX (it's debian based but with backports, so you get some more modern programes and drivers out of the box). it uses IceWM and looks a bit like windows 98 or 95. it can be modified easilly to make it look a bit better. anyway it's very low on resurces.

---

### Post by amitst on 2013-11-08
I am going to try Macpup first as I have downloaded the ISO. I will burn a DVD with it. My wireless connection is Tata Photon+. Kubuntu was able to detect it. So I hope any recent distro should recognize it as well.

In case you still feel one button installer is the way to go (and if Macpup live CD install will fail). Let me know.

---

### Post by amitst on 2013-11-08
Also note that I am unable to boot through the USB. I read that the one button installer gives difficulties using CD/DVD boot.

---

### Post by sudodus on 2013-11-08
The detection of hardware and selection of drivers is done by the kernel, which is the same in all Ubuntu flavours of the same version, for example Kubuntu, Lubuntu, Ubuntu, Xubuntu 13.10 or Kubuntu, Ubuntu, Xubuntu 12.04 LTS. (Lubuntu 12.04 has no LTS and is past end of life now).

So if Kubuntu 12.04 detects your wifi, you can also use Ubuntu and Xubuntu, and if Kubuntu 13.10 detects your wifi, you can also use Lubuntu, Ubuntu and Xubuntu (of the same version). But if Kubuntu 7.10 detects it, there is no guarantee, that 12.04 LTS or 13.10 will detect it.

Anyway, if you have an internet connection with decent speed (and price per downloaded MB), I suggest that you download several iso files and also the image file and some tarballs for the One Button Installer. Then you can test a lot of them and finally find what is the best alternative for you.

---

### Post by sudodus on 2013-11-08
> **amitst said:**
> Also note that I am unable to boot through the USB. I read that the one button installer gives difficulties using CD/DVD boot.

In such cases booting via Plop is an alternative, that I have tested with my oldest hardware.

---

### Post by mastablasta on 2013-11-08
plop boot manager can be installed on CD or DVD or even floppy.

---

### Post by amitst on 2013-11-08
I burned Macpup on a DVD and booted through it. It booted just fine. However, I am not able to connect to Internet using my wireless USB stick. It also seems to be needing the DVD every time to boot (I don't prefer this). This is similar to Damn Small Linux I had tried long back.

I am really short on time now and will have to move away from the old hardware for at least 3-4 months. The plop boot manager looks good and I will try it next time I can lay my hands on this old hardware. I hope I can put the plop boot manager along with one click install and various ISOs on a single CD/DVD.

The idea of replacing Win XP with Lubuntu with single click install is good. To attract more users to it, I suggest to have a short and long version of the documentation. Many users might turn away by looking at the extensive documentation which is vast and might confuse people.

Thanks for all the assistance provided

Meanwhile Ubuntu 13.10 (and also 13.04) detects my wireless USB stick (Kubuntu 7.10 is also able detect it most of the times). I checked the 12.04 liveCD on my new hardware. Through live CD at least I am having trouble connecting to the Internet (can't recall whether detection through hard disk was working for 12.04).

---

### Post by leeper69 on 2013-11-08
Hi macpup i386 uses a cd and will boot live from the cd then from the menu  go to setup and pick the universal installer to put it on your hard drive. after macpup has bwen copyed to the hard drive run first run setup from menu,setup,quicksetup first-run settings this will finish your setup and copy a srs file to your hard drive that will let you remove the cd so the drive can be used for music etc. tthe only problem I have with mac pup is it dosent come preconfigured with flash player and you need to manualy install it. puppy 5.7 comes with this file already enabled.

---

### Post by amitst on 2013-11-09
Thanks. I am able to connect to Internet with my wireless USB through Macpup. The following link helped.
[http://www.thinkdigit.com/forum/open-source/168799-tata-photon-puppy-linux.html](http://www.thinkdigit.com/forum/open-source/168799-tata-photon-puppy-linux.html)

I selected "Full install" (instead of recommended frugal install) as the same partition as Kubuntu 7.10 (edited /boot/grub/menu.lst to include Macpup entry as directed). However, it is not able to boot (throws up command prompt with errors). Thankfully I can still boot into Win XP and Kubuntu 7.10. Trying to figure out how to wipe out Win XP and install Macpup properly (first I want to overwrite Kubuntu 7.10 to check whether it is working properly through hard disk).

---

### Post by amitst on 2013-11-09
It seems grub is not able to load macpup properly even with Frugal (getting "Error2: invalid file or directory").

I reformatted an extended partition (earlier FAT32) with ext3 (/dev/sda7). I did a frugal install in this partition. I edited the /boot/grub/menu.lst (in /dev/sda3 which has Kubuntu 7.10) with the necessary entry displayed by macpup at the end of installation.

Somehow it is not able to boot into macpup.

---

### Post by amitst on 2013-11-09
Selecting frugal with same partition as Kubuntu 7.10 worked. Though during first shutdown, I saved the personal file to /dev/sda7 (which i had created for macpup). For now I will refrain from kill any other OS till I get used to macpup.

---

### Post by sudodus on 2013-11-09
> **amitst said:**
> ...
I am really short on time now and will have to move away from the old hardware for at least 3-4 months. The plop boot manager looks good and I will try it next time I can lay my hands on this old hardware. I hope I can put the plop boot manager along with one click install and various ISOs on a single CD/DVD.

The idea of replacing Win XP with Lubuntu with single click install is good. To attract more users to it, I suggest to have a short and long version of the documentation. Many users might turn away by looking at the extensive documentation which is vast and might confuse people.
...

Thanks for the feedback :-) 

There are different kinds and levels of documentation already, but I see your point, and I will try to make something shorter, that will not turn many users away.

By the way, right now I am developing the One Button Installer (OBI) according to feedback from other users. The default compression will be xz, ***mkusb*** will be the main tool to install the OBI and above all, giving the user a ***convenient way to download new tarballs*** via an entry in the main menu of the OBI.

When the usage is simplified, the instructions can be shorter and simpler too, or at least a short version can be enough for many users.

---

### Post by TenPlus1 on 2013-11-09
Bodhi Linux 2.4.0 is a great distro to try on your older hardware since it's made for low spec pc's and built using ubuntu 12.04 LTS repo's...

Grab the non-pae edition for your setup and burn .iso to a bootable CD: [http://www.bodhilinux.com/downloads_desktop.php](http://www.bodhilinux.com/downloads_desktop.php)

---

### Post by amitst on 2013-11-10
Thanks TenPlus1 for the advice. For now I have put Macpup on the old hardware and it seems to be working fine. Video player is running perfect. Firefox is taking couple of minutes to start. But overall the system seems to be usable.

I have moved away from the old hardware so can't try out anything further for now. 

I will give One button installer a try (also the plop boot manager) next time I come across any older hardware.

---

