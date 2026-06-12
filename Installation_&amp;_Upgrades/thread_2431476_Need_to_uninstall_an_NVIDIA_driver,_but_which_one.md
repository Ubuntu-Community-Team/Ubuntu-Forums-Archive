---
title: "Need to uninstall an NVIDIA driver, but which one?"
date: 2019-11-17
forum: Installation &amp; Upgrades
---

### Post by orthoducks on 2019-11-17
I have a problem with my system (Ubuntu 18.04) that I think is caused by  a "stuck" NVIDIA driver. No matter what graphics adapter I plug in,  Software & Updates says that a "manually installed" video driver is  in use and doesn't give me an option to change it.

I know how to uninstall a driver, but which one do I need to uninstall? "A manually installed driver" tells me nothing.

(Just to be clear, the driver, whatever it is, is not manually installed. I don't even know how to do that.)

---

### Post by mörgæs on 2019-11-17
Please post the output from ```
sudo lshw -C video
``` in CODE tags.

---

### Post by orthoducks on 2019-11-17
lshw says this:

```
sudo lshw -C video
[sudo] password for ...
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: GF110 [GeForce GTX 580]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:fa000000-faffffff memory:d8000000-dfffffff memory:d6000000-d7ffffff ioport:dc00(size=128) memory:c0000-dffff
```
The card currently installed is indeed a GeForce GTX 580. When I try to run nvidia-smi, however, it says:

```
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.
```

---

### Post by orthoducks on 2019-11-18
mörgæs, as I understand it, lshw displays information about the system's *hardware* configuration. It says "GeForce GTX 580" because a GeForce GTX 580 is installed, which has nothing to do with what driver is installed. If that's correct, it doesn't tell me what I need to know.

---

### Post by ubfan1 on 2019-11-18
The video driver should be listed on the "configuration" line, which it isn't, not even an integrated driver like i915. please post the output of lsmod | sort to see what modules are actually loaded.

---

### Post by CatKiller on 2019-11-18
> **orthoducks said:**
> No matter what graphics adapter I plug in,  Software & Updates says that a "manually installed" video driver is  in use and doesn't give me an option to change it.

I suspect that you think that tool is more clever than it actually is. It can't identify a driver in use, and it can't offer you one, so it just assumes that you must have installed your own somehow.

Of course, if you *have* used the .run file to install stuff you should use the same file to remove them again. That script is for package maintainers rather than end users, but it bites ex-Windows users hard because they don't yet understand package management.

Open source drivers won't show up in that tool because you don't need to do anything with them; they're just there as part of the kernel, or the graphics stack, or the networking stack, or whatever.

Proprietary drivers can't show up there unless you enable the *restricted* repository and run an *apt update* (or equivalent) to refresh the list of available packages.

Swapping out graphics cards willy-nilly is prone to failure. Proprietary drivers won't play nice if you're actually trying to use an open source driver, and no single version of the proprietary driver will cover all cards. Support for Turing didn't get added till the 410 branch, for example, but support for the 580 that you're trying to use got dropped after the 390 branch. Branches earlier than 390 are still available through the repositories as Legacy branches.

As noted, you don't currently have a driver that's being used. If you've actually done things to install drivers, rather than just looking in that tool but not doing anything, you should let us know what those things are so that we don't inadvertently give you bad advice. Otherwise, you'll want to enable the restricted repository, run an update, and then install a graphics driver no later than the 390 branch for that card, or likely a different branch if you put in a different card.

---

### Post by oldfred on 2019-11-18
We typically do not suggest running the .run files from nVidia.
As then you have to rerun the dkms on every kernel update.
Where versions of nVidia installed from repository just work.
And if you have a very new nVidia card, and need a driver newer than in default repository, there is a ppa with all the new versions pre-configured.
Uninstall the .run nVidia driver.
[https://askubuntu.com/questions/219942/how-to-uninstall-manually-installed-nvidia-drivers](https://askubuntu.com/questions/219942/how-to-uninstall-manually-installed-nvidia-drivers)

Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)
When I plug your version in, I get the 390.xx is correct driver.

I would run the purge commands, as they should not do anything if not installed.

If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by orthoducks on 2019-11-20
Fred, I looked at all of the references under "If wrong nVidia driver..." but I didn't find the answer to my question: How can I tell which NVIDIA driver is installed so that I can remove it? Am I missing something? (The other links don't appear to be relevant to the question.)

---

### Post by oldfred on 2019-11-20
Did you download a .run file directly from nVidia?
Then you have to uninstall that.

All others just run the uninstall commands if you installed from Ubuntu repository or the ppa.
First link above:
#What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 
   # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab, if ppa should then show the XXX for recommended version.
ubuntu-drivers devices 

If you have installed any version, you must purge first, old will  conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
   sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX                 

And if very new card, you want to add the ppa which has the very newest drivers. Standard Ubuntu repository normally has a working version, unless new card and installing old version of Ubuntu.


You can see what is the recommend version of driver:
Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

If very new driver required, info on ppa:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

# make sure system is up to date
sudo apt-get update
sudo apt-get upgrade

sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update

# If later you do not want ppa, how to uninstall ppa
sudo add-apt-repository --remove ppa:graphics-drivers/ppa

---

### Post by orthoducks on 2019-11-24
Fred: I ran the commands you suggested. dkms listed one driver as "installed," so I think that's the druver I need to remove.

There's just one remaining problem: how to determine the name of the package I need to purge. I looked at a great number of sites that describe these commands at varying levels of technicality, and I have at my fingertips everything I might conceivably want to know about how to *use* them, but I couldn't find a word about how to *interpret* their output.

dkms said:

    nvidia, 435.21, 5.0.0-32-generic, x86_64: installed

On e line from dpkg said (with some spaces deleted to shorten the line):

    ic  nvidia-

I recognize "435.21" as a driver version number, and actually as one of the ones I have installed.

Seventeen lines contain "435" in the second and third columns, so I assume all of these have something to do with the installed driver. But none of their descriptions says unequivocally that "this is the NVIDIA 435.21 driver." That's suspicious, because there is a package with the straightforward, unequivocal description "NVIDIA binary driver - version 340.107."

But two of the packages are named "NVIDIA driver metapackage," and "NVIDIA driver support binaries." Am I required to delete one of those? Or both?

Then there are the other 15 "435" packages, with descriptions that refer to "Shared files used by libraries," "Video decoding runtime libraries," "compute utilities," and other stuff. Can I leave these in place (the preferred choice if it's safe) or must I delete them too?

I want to add a few words about what I'm doing, because your answers have included a lot of stuff that isn't useful to me and I don't want you to waste your time writing more. I'm using this computer to test video cards for functionality. Essentially I install a card, boot Linux, and install and test the driver; then I do the same for Windows; then I go on to the next card.

None of the cards I'm installing are very new. When I have problems (much more often in Windows than Linux), it is because a card is too old and is no longer supported.

I have never in my life installed a Linux graphics card driver with a .run file. I normally use the "Software and Updates" utility's "Additional Drivers" pane. When it doesn't work I sometimes try to get a driver from NVIDIA's web site and install it manually, but that rarely if ever helps. I consider it a curiosity rather than a useful tool.

---

### Post by oldfred on 2019-11-24
This should purge everything. Then you install the correct one.

If you have installed any version, you must purge first, old will   conflict with new as new install does not overwrite old version. (post #9) And looking at nVidia site for your model, you should not even have that new of a driver. It should be in the 390.xx series.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

---

### Post by mc4man on 2019-11-25
The way the current drivers are packaged to completely remove I'd go
sudo apt purge nvidia*
sudo apt autoremove

(some may want to 1st simulate the autoremove if not inclined to read output before hitting y or enter..
sudo apt -s autoremove

---

### Post by orthoducks on 2019-12-04
I couldn't wait any longer to resolve this, so I blew away all of the NVIDIA drivers and started over. I had to get my system back in usable condition.

That is not an optimal solution. I know the problem will come up again -- in fact, as I write this, it already has come up once -- and I want a solution that does not force me to wipe the slate clean every time.

The remaining bit of this puzzle should not be hard for an experienced person to fill in: how to translate the stuff that dkms displays into package names?

It seems to me that we've all spent too much time on this problem to abandon it one step short of the solution!

---

### Post by mörgæs on 2019-12-06
Since you are in the process of radical solutions: Have you considered a clean install of 19.10 using only the default drivers?

---

