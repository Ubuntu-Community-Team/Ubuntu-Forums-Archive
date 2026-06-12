---
title: "An Ubuntu provided pre-install script for Nvidia driver"
date: 2016-10-13
forum: Installation &amp; Upgrades
---

### Post by johnmne on 2016-10-13
Upon installation of the graphic driver "NVIDIA-Linux-x86_64-367.44.run", I received the message:
"The distribution-provided pre-install script failed! Are you sure you want to continue?"
I clicked "Abort installation" and now I'm trying to install the pre-install script.

Nvidia's support told me that the message means that I should use the scripts that Ubuntu provides for Nvidia drivers, which suppose to uninstall any Nvidia driver that is already installed.

The installation of the Nvidia driver is performed as follows:
    ```

apt-get install dkms
service lightdm stop
cd /graphic_Driver_Dir
sh ./"NVIDIA-Linux-x86_64-367.44.run" --dkms
```

I'm using Ubuntu 16.04.

I prefer to avoid Ubuntu's provided drivers because that I tried to install drivers from the following PPA:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Which worked well at first, but it failed when the kernel upgraded - see message from 'dmesg':
"NMI watchdog: BUG: soft lockup - CPU#2 stuck for 23s! [nvidia-persiste ..."

How do I install Ubuntu's provided pre-install script for Nvidia driver?

---

### Post by oldfred on 2016-10-13
We typically do not suggest running the .run files from nVidia.
You have to rerun the dkms on every kernel update.
Where versions of nVidia installed from repository just work.
And if you have a very new nVidia card, and need a driver newer than in default repository, there is a ppa with all the new versions pre-configured.

       #What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 
      
 # Shows standard repository versions, which is the same as System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 

 Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
      
 # should show newest versions available in addition
ubuntu-drivers devices 
    
If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
This may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 

sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall 
Or you manually choose any in list.
      sudo apt-get install nvidia-XXX

---

### Post by Bucky Ball on 2016-10-13
Is it available in Additional Drivers? Do an update and have a look. Make sure the Canonical Partners repository is enabled.

You are sure that is the driver for your GPU? You don't mention what you've got.

---

### Post by johnmne on 2016-10-15
@**oldfred**:

The 3 commands:
```
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia
```

Return empty string (no error and no output).

```
$ ubuntu-drivers devices
== cpu-microcode.py ==
driver   : intel-microcode - distro non-free
```

I don't understand why did you suggest that I'll install drivers from the following PPA:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
??
As I wrote in my first post - I already tried that and had troubles when the kernel upgraded..
I'm afraid to use it again (I don't want to re-install my system all over again..).

I have GTX 1060.

**Edit:**

Why do I have to "rerun the dkms on every kernel update" ??
The idea of dkms, as far as I understand, is to automatically perform installation of the driver so that the user won't have to "suffer" through every kernel update.

---

### Post by johnmne on 2016-10-15
@**Bucky Ball**:

I'd rather to avoid any non-default repos.. Last one made me troubles.. (as I wrote in my first post)

I have GTX 1060.

What about "nvidia-current"? Would it work well?

---

### Post by oldfred on 2016-10-15
Your GTX1060 is about as new as they come.
So you do need the very newest driver.
What version did you install from ppa?
This says only 367 or 370 for your model.
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

 Ubuntu 16.04 LTS installation problem with GA-Z170X-UD5 TH & GTX 1080
[http://ubuntuforums.org/showthread.php?t=2327648](http://ubuntuforums.org/showthread.php?t=2327648)

---

### Post by Bucky Ball on 2016-10-15
> **johnmne said:**
> @**Bucky Ball**:

I'd rather to avoid any non-default repos.. Last one made me troubles.. (as I wrote in my first post)

I have GTX 1060.

What about "nvidia-current"? Would it work well?

Not sure what you mean by 'non-default repos'. You mean you only want open-source? Canonical Partners repo has been set by default on my last two installs. 

Anyway, what you're suggesting to do is exactly the same as what I suggested, just a different way of doing it. That command will install the driver in Additional Drivers and if you enable Canonical Partners, do an update and look in Additional Drivers the driver for that card should be there, the 367 from memory.

---

### Post by johnmne on 2016-10-19
@**oldfred**:

Yep, the GTX 1060 is quite new.
This is my first good graphic card after many years that I was with a cheap & low specs card..

I installed the version 367 from the [PPA]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa"), as follows:
```
apt-get purge $(dpkg -l | awk '$2~/nvidia/ {print $2}')
add-apt-repository ppa:graphics-drivers/ppa
apt-get update
apt-get install nvidia-367
```

I'm afraid that the problem of "CPU#2 stuck for 23s" will happen again if I install from that PPA...
Should I attempt installing "nvidia-370" ?? The PPA says it is a "Current official release".
What's the difference between "Current official release" and "Current long-lived branch release" ? 
Both seem relevant to the common user.

According to the thread:
[http://ubuntuforums.org/showthread.php?t=2327648](http://ubuntuforums.org/showthread.php?t=2327648)
Then the user "[**[COLOR=#000000]paul263[/COLOR]**]("https://ubuntuforums.org/member.php?u=2034875")" did exactly everything that I did in the first place, but for me - when the kernel upgraded then problems started (the "CPU stuck"...).

Can you speculate the time that it will take for GNU/Ubuntu to develop a default graphic card for the GTX 1000+ series?

---

### Post by johnmne on 2016-10-19
@**Bucky Ball**:

By "non-default repo" I mean that it is _not_ enabled by default.
(I have, by default, that repo listed in "Other Software" tab at the "Software & Updates" window, but it's disabled. )

The 367 version caused me the trouble of "CPU stuck ..." when the kernel upgraded.. 
(the first 2 weeks - before the kernel upgrade - were OK.)

---

### Post by oldfred on 2016-10-19
Ubuntu/Linux has nothing to do with proprietary drivers other than offering them. If issues with drivers then you need to talk to nVidia.
The Linux programmers creating open source drivers get little help from the vendors. It is now a little better, but they are usually several years behind and some features just are not included.

Some have posted that having UEFI Secure Boot on creates issues. They have implemented some security features into drivers now in addition and that can cause more conflicts.

---

### Post by johnmne on 2016-10-25
@**Bucky Ball**:

Let's assume that I enable the repository "Canonical Partners" and install the driver as follows:
```
sudo apt-get install nvidia-current
```

How do I un-install the "nvidia-current" driver and revert to Ubuntu's default graphic driver in case that troubles start?
(Via console/text, not GUI)

Last time, when I tried to un-install the driver as follows:
```
sudo apt-get purge $(dpkg -l | awk '$2~/nvidia/ {print $2}')
```
It didn't help and I was left without a GUI..

---

### Post by deadflowr on 2016-10-25
If you install nvidia-current, then purge nvidia-current.
What you also need to check, though, is if you ran the nvidia-xconfig command, or selected save X configuration in nvidia settings you will need to remove the xorg.conf file.
Easy enough with:
```
sudo rm -rf /etc/X11/xorg.conf
```
point of notice, make sure that the whole string is connected. rm -rf can be powerful and if you somehow have the first / seperate from the whole entry, like */ etc/X11/xorg.con*f, it'll wipe/mess up the whole root file system.
Just a caution.

---

### Post by Bucky Ball on 2016-10-25
> **johnmne said:**
> @**Bucky Ball**:

Let's assume that I enable the repository "Canonical Partners" and install the driver as follows:
```
sudo apt-get install nvidia-current
```

How do I un-install the "nvidia-current" driver and revert to Ubuntu's default graphic driver in case that troubles start?
(Via console/text, not GUI)

Purge nvidia-current, as suggested above. Not sure why you were adding the arguments to remove. (If you were using a GUI and installed nvidia-current you will probably find it in 'Additional Drivers' and can disable it there.)

---

