---
title: "Nvidia 185.19 Beta Is Out"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-04-06
[http://www.nvnews.net/vbulletin/showthread.php?p=1976912](http://www.nvnews.net/vbulletin/showthread.php?p=1976912)

Seems to be goodness :popcorn:

---

### Post by BGFG on 2009-04-06
Any point to me installing these bad boys with on-board graphics ? using 180.44 currently. there's only so much that on-board can do :)

---

### Post by Nullack on 2009-04-06
If your using VDPAU there is a key feature relating to memory management between the GPU and the system RAM that youll love

---

### Post by BGFG on 2009-04-06
Thanks a lot Nullack. One MORE thing for me to download tonight....:P

---

### Post by el-mar01 on 2009-04-07
Is there any PPA's or .deb packages out ??

---

### Post by mgsfan on 2009-04-07
this is what I get while trying to install

Adding Module to DKMS build system
driver version= 

Error! Invalid number of arguments passed.
Usage: add -m <module> -v <module-version>
Doing initial module build

Error! Invalid number of parameters passed.
Usage: build -m <module> -v <module-version>
Installing initial module

Error! Invalid number of parameters passed.
Usage: install -m <module> -v <module-version>
Done.


deb [http://ppa.launchpad.net/brandonsnider/ppa/ubuntu](http://ppa.launchpad.net/brandonsnider/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/brandonsnider/ppa/ubuntu](http://ppa.launchpad.net/brandonsnider/ppa/ubuntu) jaunty main

[https://launchpad.net/~brandonsnider/+archive/ppa](https://launchpad.net/~brandonsnider/+archive/ppa)

---

### Post by Serbitar on 2009-04-07
try 
$ sudo apt-get remove nvidia-180-*
$ sudo apt-get install nvidia-185-*

edit: does not seem to fix dkms . . .

---

### Post by Polygon on 2009-04-07
if you are installing it from nvidia's website, you do not need dkms...dkms is only used by the version that gets installed by ubuntu. 

If you are installing it from nvidia's website, make sure you uninstall any previous version using restricted drivers manager, and then 

ctrl+alt+f1
login
sudo /etc/init.d/gdm stop
cd <directory where the new driver install file is>
chmod +x ./NVIDIA-<whatever>
sudo ./NVIDIA-<whatever>
sudo reboot

and it should all be well.

---

### Post by ruik on 2009-04-07
> **el-mar01 said:**
> Is there any PPA's or .deb packages out ??

[https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

---

### Post by el-mar01 on 2009-04-07
> **ruik said:**
> [https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

Thanks a lot m8.

---

### Post by pferraro on 2009-04-07
Damn - this 185 series is turning out to be a gem.  My gtkperf scores are about half (i.e. twice as fast) of what they were with 180.44.

---

### Post by BGFG on 2009-04-07
@Nullack, thanks man. Desktop in general is much more responsive, and I almost did not bother to upgrade because 180.44 was already running so perfectly.

@everyone else, I understand why some like the ppa's but the manual install is really easy :)

Notes: I use 64 bit | I downloaded the pkg1 | Remove existing 180.** drivers through System>>Admin>>Hardware Drivers first.

[LIST=1]
[*]Grab whichever you need - [ftp://download.nvidia.com/XFree86/Linux-x86_64/185.13/](ftp://download.nvidia.com/XFree86/Linux-x86_64/185.13/)
[*]download to desktop
[*]ctrl+alt+f1
[*]sudo /etc/init.d/ gdm stop
[*]cd Desktop
[*]sudo sh ./NVIDIA-Linux-x86_64-185.13-pkg1.run
[*]Follow instructions
[*]sudo /etc/init.d/ gdm start
[*]Done :)
[/LIST]

My desktop is ridiculously sharp!

---

### Post by dasunst3r on 2009-04-07
Does anybody happen to know how to take advantage of VDPAU in VLC?

---

### Post by jfernyhough on 2009-04-07
> **BGFG said:**
> @everyone else, I understand why some like the ppa's but the manual install is really easy :)The key reason to installing from a PPA is DKMS compatibility.

---

### Post by FuturePilot on 2009-04-07
> **jfernyhough said:**
> The key reason to installing from a PPA is DKMS compatibility.

And the ability to easily revert back to the 180 driver if needed. Mucking around with the Nvidia installer and the Ubuntu packages has a high probability that something will get messed up.

---

### Post by simtaalo on 2009-04-07
185.19 is running beautifully on my system, nvidia drivers just get better and better :)

just played warsow to check frame-rate and i'm getting over a 100.

anyone else suggest good ways to check performance?

---

### Post by olskar on 2009-04-07
> **dasunst3r said:**
> Does anybody happen to know how to take advantage of VDPAU in VLC?

[http://forum.videolan.org/viewtopic.php?f=13&t=53928&p=176923](http://forum.videolan.org/viewtopic.php?f=13&t=53928&p=176923) :)

---

### Post by crjackson on 2009-04-07
Wow, this is great. I'll be upgrading several systems this weekend.

---

### Post by t.rei on 2009-04-07
Any chance for randr1.2+ ?

---

### Post by BGFG on 2009-04-07
> **jfernyhough said:**
> The key reason to installing from a PPA is DKMS compatibility.

> **FuturePilot said:**
> And the ability to easily revert back to the 180 driver if needed. Mucking around with the Nvidia installer and the Ubuntu packages has a high probability that something will get messed up.

Hope you all don't think i was presuming to tell people more experienced than myself how to install drivers :)
Was mainly for those happening across the thread wanting to try the exciting way..and a bit new to the beta thing...

---

### Post by FuturePilot on 2009-04-07
> **BGFG said:**
> Hope you all don't think i was presuming to tell people more experienced than myself how to install drivers :)
Was mainly for those happening across the thread wanting to try the exciting way..and a bit new to the beta thing...

Of course not :) That's just why I try not to step out of the Ubuntu repos when possible especially with things like drivers. Just a personal preference really. :)

---

### Post by sadicote on 2009-04-07
For bog's sake, where on earth are you all downloading the actual package from? [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) is not yielding anything later than 180.44! Also,I have a GeForce 6100/x32bit system, will it handle it?

Sorry,got it. Please ignore.

---

### Post by rudenko_ruslan on 2009-04-07
> **sadicote said:**
> For bog's sake, where on earth are you all downloading the actual package from?
[ftp://download.nvidia.com/XFree86/Linux-x86/185.19/](ftp://download.nvidia.com/XFree86/Linux-x86/185.19/)

---

### Post by crjackson on 2009-04-07
> **rudenko_ruslan said:**
> [ftp://download.nvidia.com/XFree86/Linux-x86/185.19/](ftp://download.nvidia.com/XFree86/Linux-x86/185.19/)

I wish someone could tell me what the difference between pkg0 and pkg1 is.

---

### Post by FuturePilot on 2009-04-07
> **crjackson said:**
> I wish someone could tell me what the difference between pkg0 and pkg1 is.

From the readme
> The package suffix ('-pkg#') is used to distinguish between packages
containing the same driver, but with different precompiled kernel interfaces.
The file with the highest package number is suitable for most installations.


---

### Post by cl333r on 2009-04-07
> **crjackson said:**
> I wish someone could tell me what the difference between pkg0 and pkg1 is.

[http://www.nvnews.net/vbulletin/showthread.php?t=127577](http://www.nvnews.net/vbulletin/showthread.php?t=127577)

---

### Post by BGFG on 2009-04-07
I actually installed the .13 absentmindedly :) won't bother to upgrade till they get to the .40's or something. dammit guys, I need a dedicated card. I feel like i'm missing out...

---

### Post by crjackson on 2009-04-07
> The package suffix ('-pkg#') is used to distinguish between packages containing the same driver, but with different precompiled kernel interfaces.

Yeah, I read that but the problem is I only speak english. I don't know what the whole precompiled kernel interfaces thing actually means for me. How is one supposed to know which package has the "precompiled kernel interface" that one needs?

I do understand that the higher number is probably what I want, but I'm just curious because package 1 is much larger than package 0.  Who uses package 0?

---

### Post by mamamia88 on 2009-04-07
can you revert back to older driver if it doesn't work out?

---

### Post by Nullack on 2009-04-07
Ofcourse. Log out, stop the GDM, sudo SH NV(tab) to complete the filename then simply add --uninstall to go through the uninstall process. then edit your xorg.conf to suit.

---

### Post by el-mar01 on 2009-04-08
Don't install the driver manually !! If you get a critical kernel security update it will stuff up your graphics driver .. always install from a PPA or .deb to ensure you get smooth kernel updates.

As far as the 185.19 driver goes it is a really good release .. you will see Firefox scroll a lot smoother than in previous driver releases.

---

### Post by BGFG on 2009-04-08
> **Nullack said:**
> Ofcourse. Log out, stop the GDM, sudo SH NV(tab) to complete the filename then simply add --uninstall to go through the uninstall process. then edit your xorg.conf to suit.

and suffix -k to build the kernel module as i recently learned. before that i was re-doing the entire install with any upgrade of the kernel.

---

### Post by sadicote on 2009-04-08
> **BGFG said:**
> @Nullack, thanks man. Desktop in general is much more responsive, and I almost did not bother to upgrade because 180.44 was already running so perfectly.

@everyone else, I understand why some like the ppa's but the manual install is really easy :)

Notes: I use 64 bit | I downloaded the pkg1 | Remove existing 180.** drivers through System>>Admin>>Hardware Drivers first.

[LIST=1]
[*]Grab whichever you need - [ftp://download.nvidia.com/XFree86/Linux-x86_64/185.13/](ftp://download.nvidia.com/XFree86/Linux-x86_64/185.13/)
[*]download to desktop
[*]ctrl+alt+f1
[*]sudo /etc/init.d/ gdm stop
[*]cd Desktop
[*]sudo sh ./NVIDIA-Linux-x86_64-185.13-pkg1.run
[*]Follow instructions
[*]sudo /etc/init.d/ gdm start
[*]Done :)
[/LIST]

My desktop is ridiculously sharp!

Would it be possible to the same in a terminal from the GUI? I would like to be able to copy-paste the commands, and frankly, i am not sure of myself in the ctrl+alt+f1 terminal.

---

### Post by el-mar01 on 2009-04-08
> **sadicote said:**
> Would it be possible to the same in a terminal from the GUI?

Yes .. add [this ]("https://launchpad.net/~thefirstm/+archive/ppa") PPA to your software sources list and then do reload in Synaptic then if you already have a previous NVIDIA driver then 185.19 should come up as an update.

---

### Post by BGFG on 2009-04-08
> **el-mar01 said:**
> Yes .. add [this ]("https://launchpad.net/~thefirstm/+archive/ppa") PPA to your software sources list and then do reload in Synaptic then if you already have a previous NVIDIA driver then 185.19 should come up as an update.

This is the better option if you are uncomfortable with the CLI, other benefits are also pointed out earlier in the thread. 

The commands i pointed out can't be cut and pasted since GDM must be stopped in order to successfully install in this fashion. The first time i did it this way I used a pen and paper :)

---

### Post by xebian on 2009-04-08
> **sadicote said:**
> Would it be possible to the same in a terminal from the GUI? I would like to be able to copy-paste the commands, and frankly, i am not sure of myself in the ctrl+alt+f1 terminal.

The answer is no.  Th NV installer will not let you if the X server is up and running.  That's why it's necessary to stop the gdm or kdm for kde.

---

### Post by meborc on 2009-04-08
> **BGFG said:**
> This is the better option if you are uncomfortable with the CLI, other benefits are also pointed out earlier in the thread. 

The commands i pointed out can't be cut and pasted since GDM must be stopped in order to successfully install in this fashion. The first time i did it this way I used a pen and paper :)

well... one could copy the commands to a text file... open it up in tty1 and then switch between tty2 to type them in :)

---

### Post by sadicote on 2009-04-08
Thanks guys, yu de men! I have just added the apt lines and am about to get the public key. Will let you how it goes. From what you have said about it, i am sure i will get dizzy from the ride.:guitar:

1 hour later: WHeeeeeeeee...!

---

### Post by wfp on 2009-04-08
Thanks for the beta information it's amazing how much better these drivers are getting from using 173 to 185. I just have the basic Nvidia 6150SE, but there has been a huge difference for me.

---

### Post by sandy8925 on 2009-04-18
Yeah the newer nvidia drivers sure rock! I installed 180.11 from the repos and then tried installing 180.29 after following proper instructions. My system is way smoother now. Scrolling,selecting text and playing videos are some of the areas where I noticed visible improvement. I just wish my games would work faster with Wine.

---

### Post by sandy8925 on 2009-04-18
I'm having some trouble installing the 185.19 drivers.\

I already ahd the 180.29 drivers.I stopped compiz and gdm,changed to runlevel 3 and uninstalled the 180.29 drivers using: sudo ./NV......run --uninstall

Then I rebooted went into safe graphics mode and changed to runlevel 3 and installed the new drivers.

After rebooting it gives me an error saying module type1 was not found. I had the same problem with 180.44 installation too. Can someone please help ? Removing the Load "type1" line in xorg.conf gives even more errors.

---

### Post by cecilpierce on 2009-04-18
Does the 185.19 work with the 2.6.30 kernel?

---

### Post by jfernyhough on 2009-04-18
> **cecilpierce said:**
> Does the 185.19 work with the 2.6.30 kernel?If it is patched. 185.50 works with .30 without patching.

---

### Post by cecilpierce on 2009-04-18
Thanks for the info but I can't find the .50 d/l ?

---

### Post by cecilpierce on 2009-04-18
I meant the 185.30, sorry

---

