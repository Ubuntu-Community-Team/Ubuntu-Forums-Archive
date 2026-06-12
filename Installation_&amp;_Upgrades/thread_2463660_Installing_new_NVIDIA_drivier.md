---
title: "Installing new NVIDIA drivier"
date: 2021-06-16
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2021-06-16
NVIDIA has released a new driver that we work with GeForce 310 graphics adapters.  I downloaded the .run file, did the chmod +x and ran the ,.run file as suso su.

I get the following error:You appear to be running an X server; please exit X before installing.  When I do a google search on that phrase, it get numerous hits, some pf which contradict each other.  So, would someone please give me step-by-step instructions for 21.04.

I also tried adding the driver through [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/) .  The only packages listed for NVIDIA 340 are transitional.  I installed several of thse, but clearly I don't know what I am doing.

Current video driver is X.Org X server -- Nouveau display driver .  However, this does not help performance.

All this applies to a DELL Vostro 3500 laptop
.
Thank you

John

---

### Post by MAFoElffen on 2021-06-16
Okay...

From #5 on, in this post should get you going to run that NVidia script: [**Installing NVidia Binary Drivers**]("https://ubuntuforums.org/showthread.php?t=1743535&page=10&p=10909540#post10909540")

---

### Post by cigtoxdoc on 2021-06-16
Thank you for your help.  i followed your instructions, but somewhere i messed-up big time.  I cannot log into Ubuntu.  I have tried recovery mode, etc.  Fortunately, I have other PC's and the same pc with the problem ubuntu has Win XP Pro on it so i can get to all my files on the ubuntu side.

BTW, Ubutnu comes up in the video mode and asked me to log in.  When I do, it says something like opps, you have a problem

So, how do I get back to a working Ubuntu on my DELL Vostro 3500?

Thank you,
John

---

### Post by MAFoElffen on 2021-06-16
Well, the binary driver was probably the incorrect driver. So now the Linux Graphics Layer is "confused" because it has that incorrect driver installed... Not a problem. Some more work... but everything is still there. Be patient and take a breath.

On the Sticky you were in, the one in my Signature line, go post#3. At the Table Of contents, select the option to "Temporally Boot into a TTY Terminal." From there, navigate to where your nvidia install script "is". Use the up arrow, repeatedly, until you get to the command you used to install the script... It should still be in the CLI History.

Edit the command to use "--uninstall" as an option. It will uninstall. Reboot and you will be back to where you were. 

Once you do that... Tell me how it went. I will "help you" find a good driver for your card.

---

### Post by cigtoxdoc on 2021-06-16
Things did not work so well.  Fortunately, had everything backed up on SpiderOak so i was able to get important file sent out.  I used the Yannbuntu boot repair CD to get the PC to boot, so I think I have the right kernel running.  However, I did get the Oh No scree again after logging in.  So, I need help moving on from that.  The message your referred me to was from 2011, so i didn't go there as i am running 21.04.

I tried installing the nvidia driver again.  Installation went much further than it has before.  Listed below are error messages:

BUILD_EXTMOD=/var/lib/dkms/nvidia/340.107/build/uvm...(bad exit status: 2)
ERROR (dkms apport) : binary package for nvidia:340.107 not found
Error! Bad return status for module build on kernel :
5.11.0-18-generic (x86_64)
Consult /var/lib/dkms/nvidia/340.07/build/make.log for more information

When i retried the installation and chose not to have dkms support, I am told that the rivafb driver conflicts with the NVDIA driver, please reconfigure your kernel and *disable* rivafb support, then try installing the NVIDIA kernel module again.

Looks like this job is for a super expert om drivers and kernels.

What should I try next?

Thank you for your help.

John

---

### Post by MAFoElffen on 2021-06-16
LOL. I sent you there (to that last post), to boot temporarily to a TTY Text mode... because those instructions for that are still the same...  And to back out of what that NVidia Installation script installed, you need to kill the Graphics Layers (shut it down), so that you can go back to that script, and instead of executing it to "install", if you used the same command and then give it a space, then "--uninstall", then it will uninstall all the pieces it installed and revert whatever it "chanced." Their scripts change, and evolve, so without seeing the specific script you installed from, I could not tell you what exactly "it" did.

Did you do that?

*** As someone else, put it so nicely:
> First, make sure you have uninstalled all drivers so you don&#8217;t get any conflicts.

---

### Post by MAFoElffen on 2021-06-16
The **only** recent/latest NVidia Linux driver that I see that supports your GeForce MX330 is 440.64.

---

### Post by cigtoxdoc on 2021-06-16
Thank you.  I have GeForce 310.  Driver is 340.07,

In any case, how do I get back to a running pc with the nouveau driver?

John

---

### Post by MAFoElffen on 2021-06-16
After you uninstall the script you installed... Rebooted. 

Then:
```
sudo lashw -C video
```
Post the results...

---

### Post by oldfred on 2021-06-17
Drivers do not auto delete previous installs.
So if you install a different driver, you must purge old driver first.
We typically do not suggest to download the .run file from nVidia as you then have to reinstall with every kernel update. If you install from Ubuntu repository, it automatically is added to newer kernel.

Uninstall the .run nVidia driver.
[https://askubuntu.com/questions/219942/how-to-uninstall-manually-installed-nvidia-drivers](https://askubuntu.com/questions/219942/how-to-uninstall-manually-installed-nvidia-drivers)

Until correct nVidia driver is installed, you often need nomodeset boot parameter. Ubuntu installer now offers Safe Graphic boot & install of proprietary driver, so nomodeset not required with latest versions.

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 

#To see video:
lspci -vnn | grep VGA -A 12
sudo lshw -c display 
sudo lshw | grep -A 11 display
#What is installed
dkms status

# Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
With 18.04, the only way I can get to this now is with Software Updater & Settings.
ubuntu-drivers devices

If newer driver required, latest are quickly added to ppa.
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
# make sure system is up to date
sudo apt-get update
sudo apt-get upgrade

sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update

# If later you do not want ppa, how to uninstall ppa
sudo add-apt-repository --remove ppa:graphics-drivers/ppa

# should show newest versions available in addition
ubuntu-drivers devices
You then can manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by deadflowr on 2021-06-17
The 340 driver is now considered unsupported and won't run on Ubuntu 21.04 with the current 5.11 kernel series it uses.
See : [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/+bug/1916640]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/+bug/1916640")
(The Ubuntu developers themselves have opted to stop patching it (as they patched it for kernels 5.5 to 5.9) and have scripted the package to just point to the open source the nouveau driver instead)

But luckily someone has created a ppa with the driver patched here: [https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy]("https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy")

Also, I don't think you ever installed the run file driver since the installation failed.

---

### Post by MAFoElffen on 2021-06-17
If he would do
```
sudo lshw -C video
```
It would verify the video he has...

What I was going to suggest to him, was that he used the video-team PPA, as you both said, even after he bad mouthed it in his first post, saying he did want to use it. He made a decision on what he wanted to use. After it failed, now he knows. I've used that PPA for "years" with very, very few problems.

He said the notebook he has. He said he has GeForce MX330. He cannot use "the latest and greatest." Why? Because for the graphics he says he has, NVidia support for Linux drivers dropped out for that GPU with 440.56. So can can use any driver in the PPA, up to and including 440.100.

---

### Post by MAFoElffen on 2021-06-17
Deleted...

---

### Post by deadflowr on 2021-06-17
>  He said he has GeForce MX330.
The OP has never said that.

---

### Post by cigtoxdoc on 2021-06-17
Thank you.  I have GeForce 310.  Driver is 340.07,

In any case, how do I get back to a running pc with the nouveau driver?

John

---

### Post by cigtoxdoc on 2021-06-17
I solved problem by reinstalling 21.04.  I have all my data files in separate partitions.  Also, everything was backed up on spider Oak.  john

---

### Post by ubfan1 on 2021-06-17
Just uninstall the Nvidia driver (and any associated packages if they still are installed), then use the nomodeset option on your kernel boot line (at grub first time, or edit the /etc/default/grub file to add it at the "quiet splash" words on the ...commandline.

---

