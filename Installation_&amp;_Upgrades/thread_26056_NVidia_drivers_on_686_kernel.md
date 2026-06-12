---
title: "NVidia drivers on 686 kernel?"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by ChrisTheGeek on 2005-04-11
I've done a fresh Hoary install but I can't get the NVidia drivers working.  As per ubuntuguide I've tried the following lines:

sudo apt-get install nvidia-glx nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable

The final command does not produce any errors and appears to work but doesn't actually install the drivers (I have rebooted).  modprobe reports that there is no such thing as a nvidia module.

I've had the NVidia drivers working just fine under Warty so I'm sure it's just a configuration option somewhere.  I did install the 2.10-5-686 kernel using symantic before attempting to install the drivers:

- Do the default NVidia drivers support the 686 specific kernel?
- If not, how can I get rid of the 686 kernel and swap back to the default 386 kernel? 
- Is there some way to log/trace why the 'nvidia-glx-config enable' line didn't succeed?
- Are there some manual steps I can do that will achieve the same effect?

I have a Dell Inspiron 8100 (laptop). Any help is much appreciated.

---

### Post by skoal on 2005-04-11
[QUOTE=ChrisTheGeek]- Do the default NVidia drivers support the 686 specific kernel?[/QUOTE]

Yes. I'm using them (7174) in Hoary now.  I upgraded the same way you did with Synaptic and don't have that problem.  You must have missed a step somewhere,  or...maybe it matters when you update your nvidia packages, before or after the 686 upgrage?  I believe I did my 686 upgrade *after* the nvidia update and it pulled over the modules for me (if memory serves me correctly).

---

### Post by armar on 2005-04-11
I'm running the 686-smp kernel--had the same problem. I just downloaded the drivers from NVidia and installed it that way. No problems since.

---

### Post by farnsworth on 2005-04-11
The nvidia packages DONT support the 686 kernel: but you can install the nvidia-kernel-common pkg with linux-restricted-modules-2.6.10-386.  After doing this I still had to run the binary installer from nvidia.com, nvidia-glx-config enable,  and remove /etc/rc2.d/S20nvidia-glx and /etc/rc6.d/K20nvidia-glx.  If you don't delete those scripts your xserver will work great... until you reboot.

---

### Post by farnsworth on 2005-04-11
Oh, forgot to ask.  Did you install from the iso or upgrade from warty?

---

### Post by Whiffle on 2005-04-11
Im running the 686 kernel w/ nvidia drivers on hoary.  Work great, didn't have to do anything special either.  

I have:
 linux-restricted-modules -2.6.2.6.10.5-1
nvidia-kernel-common
nvidia-glx

I don't remember what order I installed them in.

---

### Post by ChrisTheGeek on 2005-04-12
Farnsworth, I did originally try upgrading from Warty but for some reason it hosed my system completely (couldn't even get a command prompt up!)  It's really frustrating because I had that system setup with the 686 kernel and NVidia working fine.  I feel the need to point out here that I'm not a total linux noob so I feel suitably foolish that the update failed so spectacularly despite following the instructions!

I'm reluctant to install the drivers from NVidia binaries since they then wouldn't be under apt control - I'm really eager to make my next apt-get dist-upgrade work without fluffing up the system (is this a legitimate concern or am I being over-paranoid?)

Does anybody know how I can swap back to using the 386 kernel and uninstall the 686 one?  If I choose to load the 386 kernel in Grub will symantic then allow me to remove the 686 kernel safely?  Due to the somewhat serious consequences I'm reluctant to try this without some idea of whether it will work  :|

Thanks!

---

### Post by farnsworth on 2005-04-12
I wouldn't think there'd be any problems removing the 686 kernel by grubbooting the 386.  I've had to do that a few times back in my slackware days.

As for the nvidia binary installer, it installs a file "nvidia-installer" in /usr/sbin.  just nvidia-installer --uninstall if it doesn't work.  If you decide to give it a shot, try removing those two rc scripts I mentioned above (reinstalling the nvidia-glx pkg will reinstall them as well, and at worst it will make no difference after a reboot).  I'd really like to know if I'm the only person those scripts are slapping around.

And as for nvidia/hoary in general, I really have no idea.  My experience upgrading has just been one huge mess.  I followed the directions to a tee, as well;  but with all of the unsupported packages I've got installed, who knows where it went wrong.

---

### Post by ChrisTheGeek on 2005-04-14
Thanks for the reply Farnsworth.  I did grub load into the 386 kernel and then use symantic to remove the 686 kernel.  I then rebooted and it was gone no problem.

I then tried installing the nvidia drivers again and it actually installed!  This was a good thing (tm) until I decided to reboot Gnome and then the computer.  Now, once again my system is completely hosed. I can't even get to a command prompt!

AARRRGH!

The system seems to load up fine until the gdm starts to show then the screen just stays blank.  I have a knoppix CD so I was hoping I could remove the drivers manually?  Or I guess I could use apt if I could get to a command prompt....  My understanding is that I can change the run-level somehow so it won't load the gdm?   Think I'll have a look around google to see if I can get this to work  :roll:

---

### Post by sander marechal on 2005-04-14
AFAIK there's still a problem with Nvidia drivers under Hoary (more specifically: with Gnome 2.10). Nvidia needs to update their drivers to fix this. In the mean time:

- start Ubuntu in Recovery mode (any kernel you want)
- run sudo dpkg-reconfigure xserver-xorg
- go through the questionaire. When asking for the chipset, choose standard " nv"  and not "nvidia".

The above fixed it for me. At least... I get Ubuntu to run normally. No hardware 3D though, just 2D, so forget about running GL games for now and wait untill the next Nvidia drivers are out.

---

### Post by Casey on 2005-04-14
I have absolutely no problems with this.  Are you sure you remembered to install the linux-restricted-modules that goes with the 686 kernel?

---

### Post by ChrisTheGeek on 2005-04-15
Thanks for the replies.  I've recovered the system by loading into recovery mode from Grub and apt-get removing the NVidia packages.  I then restored my Xorg.conf from a backup I'd made.  The system is now back up and running in glorious 2D.

I looked on the NVidia website and they do seem to have released updated drivers that "fix installation problems on some 2.6 kernels".  I downloaded and tried to install these but the installer couldn't find a pre-built sommit or rather and told me I needed the kernel source header files to build one.  I'm afraid this is a bit beyond me at the moment!  ](*,) 

Will the hoary NVidia drivers be updated in the Ubuntu repository?  Is there some way I can get the new drivers via apt (which I understand!) or find out when they're released by Ubuntu?

Ps: Casey, I have installed all the necessary kernel files. I've had trouble with both 386 and 686 kernels now.  It does appear that most people have got it running without problems, lucky gits ;-)  Maybe it's because of my laptop?

---

### Post by jtopping on 2005-04-24
you need linux-restricted-modules-686 for nvidia drivers to work
it includes the nvidia kernel module.

---

