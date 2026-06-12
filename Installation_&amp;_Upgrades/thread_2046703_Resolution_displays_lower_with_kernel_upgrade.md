---
title: "Resolution displays lower with kernel upgrade"
date: 2012-08-23
forum: Installation &amp; Upgrades
---

### Post by wa1d0rf on 2012-08-23
I have Ubuntu 12.04 installed since April 2012 but the kernel upgraded from 3.2.0-27-generic-pae to 3.2.0-29-generic-pae and now my resolution is 1024x768 compared to 1360x768 before the upgrade.

I have an NVIDIA GeForce GT520 SILENT installed and everything was working fine until the upgrade to the new kernel happened.

The NVIDIA X Server Settings showed the recommended driver is installed and activated and it detected my Sony KDL-40S2010 LCD TV as the primary (only) display device but only when I boot using the 3.2.0-27-generic-pae kernel.  With the newer kernel, it somehow doesn't recognize the NVIDIA driver is installed and the display settings app shows 1024x768 "Laptop" as the display device.  The detect device button doesn't work.

I don't understand why this happens!  Help! :(

---

### Post by TheFu on 2012-08-23
The nvidia drivers are kernel extensions. Whenever the kernel is changed, the drivers need to be relinked. In theory, this should happen automatically, but if you installed any drivers outside APT, then that same install process needs to happen again to reconnect the new kernel with the drivers.  Uninstall following the procedure from the installation instructions, then ...

The easiest way is to force a reinstall using APT.
```
 sudo apt-get  --reinstall nvidia-current
```If you did install using APT (software center, aptitude, Synaptic, or apt-get), then just do that command and it should be fine.

---

### Post by wa1d0rf on 2012-08-23
I have done this:

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```

but when I reboot, it automatically selects 3.2.0-29-generic-pae and the I get the lower resolution.  This is not "fine".  I have to select 3.2.0-27 from grub or I don't get the correct resolution.

---

### Post by TheFu on 2012-08-23
Sorry, I forgot to tell you to run these to configure the nvidia settings.
```
sudo nvidia-settings
sudo nvidia-xconfig
```I'm confused. Who said to load that PPA?  I've never used a PPA for nvidia stuff.  I've been burned using direct-from-nvidia drivers more than once. I always wait until Canonical puts them into their repos.

---

### Post by wa1d0rf on 2012-08-24
> **TheFu said:**
> I'm confused. Who said to load that PPA?  I've never used a PPA for nvidia stuff.  I've been burned using direct-from-nvidia drivers more than once. I always wait until Canonical puts them into their repos.

When I did the nvidia-settings from the console, the display device now shows Sony KDL-40S2010 as the model and the correct resolution.

I've been trying to figure out how to fix this for a while and found this online:
[http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html)

Thanks for your help.

---

### Post by TheFu on 2012-08-24
**There is no explanation of the PPA there. You do not need it.**
I doubt this PPA is harmful, but your system doesn't need it.

Always remember that "**new**" is the enemy of "**stable**."

---

### Post by wa1d0rf on 2012-08-24
OK, so I don't "need" that PPA.  I did the things you suggested.   I still have the same issue when I boot to the newest kernel.  How do I get the NVIDIA drivers to be recognized?  

You say this will happen with every kernel release, but what is the recommended way to fix this when a new kernel is released?

On top of all that, I don't get my mouse support when I reboot into the current kernel now either.  Jeez!

---

### Post by TheFu on 2012-08-24
You need to be using the newer kernel when you reinstall the nvidia drivers.
Steps:

[LIST=1]
[*] Boot into the new kernel.
[*]reinstall the nvidia drivers (if you do it running a different kernel, the module won't be linked to the new kernel)
[*]reboot to get the newest nvidia drivers active.
[*]rerun nvidia-xconfig as root/sudo
[*]rerun nvidia-settings as root/sudo - be certain you **SAVE** the settings.
[*]reboot.
[/LIST]
If you don't save the settings, then nothing will be remembered.

In theory, none of this should be required provided you use kernels and modules from APT sources.  In theory, newer kernels would relink the latest available video drivers automatically using the dependency facilities. If you've installed modules outside APT or directly from nvidia, I don't think it works.

Do you see where you might have gone wrong previously?

---

### Post by wa1d0rf on 2012-08-24
OK, I rebooted into the newest kernel (3.2.0-29-generic-pae) and when I try to do this:

```
sudo apt-get --reinstall nvidia-current
```It says it is invalid.  Do I need to uninstall (somehow) then install it fresh to get it to link to the new kernel?

Thank-you so much for your patience with me.

---

### Post by wa1d0rf on 2012-08-24
So I searched web for instructions on how to uninstall the drivers and I found this:

```
sudo apt-get purge nvidia-current
sudo apt-get install nvidia-current
```

I assumed this satisfied your step #2.

When I tried to do step #3 (reboot), I got a weird error saying something about a "broken pipe" and not being able to mount a CIFS drive.  Never saw this before!

This is going from bad to worse quickly!

---

### Post by TheFu on 2012-08-24
Did you get to step 6 or not?  Is the display working or not? What, exactly, are the issues?

You've never said whether you were using Ubuntu nvidia drivers or you got them somewhere else.  How they were installed previously **matters tremendously.**  Did you always use official ubuntu packages or something else?  I'm worried about that added PPA - non-Ubuntu released drivers could be inside there.

Before you do any package installation, **always** do an 
```
sudo apt-get update
sudo apt-get upgrade
```first. If there are any errors shown, those need to be fixed.

Video drivers don't have anything to do with mounting a remote network CIFS drive. Unrelated issue IMHO.  A broken pipe can be anything. During a reboot, lots of "pipes" could be broken, especially network pipes. Was anything being downloaded or transferred when you typed reboot? Something could have been interrupted.

In the future, showing the exact error messages is extremely helpful.  Often we (people in general) leave out important details when reporting issues.  Googling the exact error message will often find the solution.  
Using the "man pages" to learn how a command works means you don't have to wait for a response.  For example, 
```
$ man apt-get
```will teach everything.

---

### Post by wa1d0rf on 2012-08-24
No, I didn't get to step 6.  I wrote previously, I did step 2 then tried to reboot (step 3) and I got the following COMPLETE error:

```
Could not write bytes: Broken pipe
mountall: Disconnected from Plymouth
[      30.748091] CIFS VFS: Error connecting to socket.  Aborting operation
[      30.748222] CIFS VFS: cifs_mount failed w/return code = -113
Unable to find suitable address.
mountall: mount /NAS [1420] terminated with status 2
```

That is with 3.2.0-29-generic-pae kernel.

I then had to do a hard reboot (on/off switch on case) then I tried 3.2.0-29-generic kernel and it booted up perfectly including the correct screen resolution with the nvidia driver activated.  The nvidia-settings app shows the correct resolution and detected my TV make and model correctly.

The only way I ever installed any drivers were through that PPA attempt or through the nvidia additional drivers app.

So, something is horribly wrong with the installed pae kernel.  Maybe this kernel just doesn't work with my video card.  If I have less that 4GB of RAM, I don't really need the pae kernel anyway, correct?

---

### Post by TheFu on 2012-08-24
That error is definitely an unrelated issue.  I take it you have a NAS device some where on the network named Plymouth that you mount via CIFS?  During the reboot, the network appears to be shutdown - perhaps before the remote storage is unmounted.  Anyway, that is an issue for a different thread.

Perhaps "horribly wrong" is an overstatement about that minor issue?  90% of the time I think something was a bug, it turned out to be my mistake.  
Under 12.04 the PAE kernel seems to be the default. It is installed here and I didn't do anything special.  Sadly, I don't have pure 12.04 Desktop installed on any desktop machines with an nvidia card, so I can't reproduce this issue.  I have it on a few servers, without video cards. Sorry.

PAE is useful when you have over 3.5G of RAM. Besides that, you are correct, but I suspect the package manager will keep trying to install it.

Did you remember to remove that PPA from your /etc/apt/ directories and go through the entire update, upgrade, reinstall, .... stuff?

---

### Post by wa1d0rf on 2012-08-25
How is it unrelated?  It only started when I started messing around with these drivers and different kernels.  I don't have anything named "Plymouth" and I don't know where that comes from.  I do have a CIFS device with a mount point of /NAS however.  That device has been powered off for a while and never caused this error to appear before.

While searching for solutions to my issue, I read many posts about getting a black screen and no GUI appearing.   Maybe the error was hidden before because the kernel kicked in and displayed the GUI.

I read that Ubuntu is moving toward only supporting the PAE kernels, so I better figure this out or I'm stuck.  I currently have 3.9GB of RAM.

When you say "remove that PPA from your /etc/apt/ directories" do you mean remove the PPA listing from the sources.list file?  I looked in there and didn't actually see the PPA listed.

---

### Post by TheFu on 2012-08-25
> **wa1d0rf said:**
> When you say "remove that PPA from your /etc/apt/ directories" do you mean remove the PPA listing from the sources.list file?  I looked in there and didn't actually see the PPA listed.

You typed this previously:
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
That added a repository to somewhere under /etc/apt/ ... there are subdirectories down there too.  You should find where that is located and ***do the right thing to remove that PPA***.  That could be deleting a few lines from a file or it could be deleting a file completely. I don't know what it is on your machine.

Check inside /etc/apt/sources.list.d/ for a file or two.

---

### Post by wa1d0rf on 2012-08-25
I did the following to remove the PPA:

```
sudo add-apt-repository --remove ppa:ubuntu-x-swat/x-updates
```

I also commented out the line in the fstab relating to the /NAS mount point.

Then I rebooted allowing GRUB to select the latest kernel on the list (3.2.0-29-generic-pae) and when it boots up I get a black screen with just the following now:

```
Could not write bytes: Broken pipe
```

It won't do anything after this.

If I Ctrl-Alt-Del and select the 3.2.0-27-generic-pae it boots fine (still).  I really don't know what to do with this at this point.  I know that it will mess me up when 12.10 comes out, again.

---

### Post by TheFu on 2012-08-25
X/Windows isn't starting.  To figure out that issue look at a few log files.
* What does the /var/log/Xorg.0.log file show for errors and warnings?
 * What does '**dmesg**' show for errors and warnings?
* Is there anything interesting in the syslog?

You might need to switch to a different console to see anything after the reboot into the latest PAE kernel.  <alt>F2 ... <alt>F4 will switch login consoles. After boot can you remote in from a different box via ssh?

Are there any "held back" packages when you do an **apt-get update**?

---

### Post by wa1d0rf on 2012-08-25
/var/log/Xorg.0.log doesn't show any errors (EE codes), some warnings but doesn't look like any show-stoppers.

dmesg displays a huge listing of stuff but only the following looks interesting:

```

[   22.364426] nvidia: module license 'NVIDIA' taints kernel.
[   22.364431] Disabling lock debugging due to kernel taint
...
[   22.830290] nvidia 0000:03:00.0: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16
[   22.830298] nvidia 0000:03:00.0: setting latency timer to 64
[   22.830303] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   22.830549] NVRM: loading NVIDIA UNIX x86 Kernel Module  295.49  Mon Apr 30 23:30:07 PDT 2012


```

the syslog has these interesting entries:

```
rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]

kernel: [   22.830549] NVRM: loading NVIDIA UNIX x86 Kernel Module  295.49  Mon Apr 30 23:30:07 PDT 2012
```

nothing else seems out of the ordinary or different between the 27 kernel and the 29 kernel log entries.

> You might need to switch to a different console to see anything after  the reboot into the latest PAE kernel.  <alt>F2 ... <alt>F4  will switch login consoles. After boot can you remote in from a  different box via ssh?

I don't know what all that means in the above quote.

> Are there any "held back" packages when you do an **apt-get update**? 	

I assume you want me to try that on the 27 kernel as it is the one I can get X to start. The following is what apt-get update produces:
```

Ign http://extras.ubuntu.com precise InRelease
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://ca.archive.ubuntu.com precise InRelease                             
Ign http://ca.archive.ubuntu.com precise-updates InRelease                     
Ign http://ca.archive.ubuntu.com precise-backports InRelease                   
Hit http://packages.medibuntu.org precise InRelease                            
Ign http://archive.canonical.com precise InRelease                             
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://ca.archive.ubuntu.com precise Release.gpg                           
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://extras.ubuntu.com precise Release                                   
Get:1 http://ca.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://security.ubuntu.com precise-security Release                        
Hit http://archive.canonical.com precise Release                               
Hit http://ca.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://security.ubuntu.com precise-security/main Sources                   
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://ca.archive.ubuntu.com precise Release                               
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://security.ubuntu.com precise-security/restricted Sources             
Hit http://security.ubuntu.com precise-security/universe Sources               
Hit http://security.ubuntu.com precise-security/multiverse Sources             
Hit http://security.ubuntu.com precise-security/main i386 Packages             
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Hit http://security.ubuntu.com precise-security/universe i386 Packages         
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Get:2 http://ca.archive.ubuntu.com precise-updates Release [49.6 kB]           
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://ca.archive.ubuntu.com precise-backports Release                     
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Hit http://ca.archive.ubuntu.com precise/main Sources                          
Hit http://ca.archive.ubuntu.com precise/restricted Sources                    
Hit http://ca.archive.ubuntu.com precise/universe Sources                      
Hit http://ca.archive.ubuntu.com precise/multiverse Sources                    
Hit http://ca.archive.ubuntu.com precise/main i386 Packages                    
Hit http://ca.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://ca.archive.ubuntu.com precise/universe i386 Packages                
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Hit http://ca.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://ca.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://ca.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://ca.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://ca.archive.ubuntu.com precise/universe TranslationIndex             
Get:3 http://ca.archive.ubuntu.com precise-updates/main Sources [158 kB]       
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Get:4 http://ca.archive.ubuntu.com precise-updates/restricted Sources [3,285 B]
Get:5 http://ca.archive.ubuntu.com precise-updates/universe Sources [50.1 kB]  
Ign http://extras.ubuntu.com precise/main Translation-en_CA                    
Get:6 http://ca.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:7 http://ca.archive.ubuntu.com precise-updates/main i386 Packages [378 kB] 
Ign http://archive.canonical.com precise/partner Translation-en_CA             
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en                
Get:8 http://ca.archive.ubuntu.com precise-updates/restricted i386 Packages [6,732 B]
Get:9 http://ca.archive.ubuntu.com precise-updates/universe i386 Packages [127 kB]
Get:10 http://ca.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,672 B]
Hit http://ca.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://ca.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://ca.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://ca.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://ca.archive.ubuntu.com precise-backports/main Sources                
Hit http://ca.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://ca.archive.ubuntu.com precise-backports/universe Sources            
Hit http://ca.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://ca.archive.ubuntu.com precise-backports/main i386 Packages       
Hit http://ca.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://ca.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://ca.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://ca.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://ca.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://ca.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://ca.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://ca.archive.ubuntu.com precise/main Translation-en_CA                
Hit http://ca.archive.ubuntu.com precise/main Translation-en                   
Hit http://ca.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://ca.archive.ubuntu.com precise/restricted Translation-en             
Hit http://ca.archive.ubuntu.com precise/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com precise/universe Translation-en
Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en_CA
Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en
Hit http://ca.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://ca.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://ca.archive.ubuntu.com precise-backports/main Translation-en
Hit http://ca.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://ca.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://ca.archive.ubuntu.com precise-backports/universe Translation-en
Ign http://packages.medibuntu.org precise/free Translation-en_CA
Ign http://packages.medibuntu.org precise/free Translation-en
Ign http://packages.medibuntu.org precise/non-free Translation-en_CA
Ign http://packages.medibuntu.org precise/non-free Translation-en
Fetched 786 kB in 5s (133 kB/s)
Reading package lists... Done
```

---

### Post by TheFu on 2012-08-25
The issue is with the new kernel, not the old one.  Doing anything with the older kernel booted does not help with a solution. Sorry I wasn't clear about that.

Your nvidia version did not revert back to that which is officially in the Ubuntu Repos.
My fully updated 12.04 has nvidia-current at version "295.40-0ubuntu1.1".  You appear to be using newer, untested-by-Canonical video drivers.  I suspect you got them from that PPA.

The package "update" output is not important, it is the package "upgrade" output that matters. Sorry I wasn't clear about that.

BTW, DKMS is what should have relinked the nvidia drivers to the new kernel. Learn more about it '**man dkms**'

---

### Post by wa1d0rf on 2012-08-25
I tried the following:

```
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
```

and when I rebooted into the newest kernel, I get the 1024x768 res again.

As far as DKMS goes, is this the kind of thing I need to do?
[http://ubuntuforums.org/showthread.php?t=1036788](http://ubuntuforums.org/showthread.php?t=1036788)

---

### Post by TheFu on 2012-08-26
That DKMS thread is for getting on the bleeding edge of nvidia drivers using the source. I've done that, but not in years.  On my nvidia hardware, it wasn't necessary.

Removing and reinstalling the drivers was a very reasonable idea. I hope you did it from the new kernel.  Doing it from the older kernel doesn't help.  Kernel modules are built and stored per-kernel in /lib/modules/`uname -r` - that's why it is so important that you do all this work running the kernel you are trying to fix.

There should be a 800x600 VESA mode that can be forced during the grub boot to get into the new kernel with a minimal GUI. Or just disable the GUI completely and get a non-X/Windows login.  I believe it really is easier to ssh in from a different machine to run the commands.

Just because the PC doesn't have a GUI, that doesn't mean you can't ssh in and install stuff.  Are you familiar with that?

---

### Post by wa1d0rf on 2012-08-26
As I wrote in my last post, I was able to get the X windows to start again by purging all the nvidia drivers and reinstalling the nvidia-current.  After the reboot, I still have 1024x768 resolution.  I tried the nvidia-settings again and it still says I don't have a nvidia driver active.

I tried to boot into recover mode but it wouldn't let me do any apt-get stuff.  I didn't recognize nvidia-current.  No, I haven't used ssh before.  Is that sort of like a vpn kind of thing to gain access to another system?  I've used vpn and rdp in the windoze environment.

So I (once again) booted into the newest kernel, and tried to purge and install the driver and this is what the install shows:

```
sudo apt-get install nvidia-current

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  nvidia-settings
The following NEW packages will be installed:
  nvidia-current nvidia-settings
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/34.4 MB of archives.
After this operation, 100 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package nvidia-current.
(Reading database ... 302866 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_295.40-0ubuntu1.1_i386.deb) ...
Selecting previously unselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_295.33-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current (295.40-0ubuntu1.1) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libOpenCL.so because associated file /usr/lib32/nvidia-current/libOpenCL.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/nvidia-current/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic-pae
Loading new nvidia-current-295.40 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-29-generic-pae
Building for architecture i686
Building initial module for 3.2.0-29-generic-pae
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-29-generic-pae/updates/dkms/

depmod.....

DKMS: install completed.
Setting up nvidia-settings (295.33-0ubuntu1) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic-pae
```Notice the stuff where it says it skipped installation of some files because some other files/folders didn't exist.  What's that about?

Anyway, I rebooted again into the newest kernel and the screen resolution is finally correct!  "displays" app shows as "Laptop" but correct res.  It used to detect my device and show "Sony KDL-40S2010".

"additional drivers" shows nvidia-current as active and "nvidia-settings" shows everything the way I want it FINALLY!!

So, I'm hoping that next time (12.10?) there is a new kernel, all I have to do is purge nvidia*, install nvidia-current, reboot and I will be fine.  I will keep my fingers crossed!

Thank-you Fu for all your patience and support!

---

### Post by TheFu on 2012-08-26
> **wa1d0rf said:**
> "additional drivers" shows nvidia-current as active and "nvidia-settings" shows everything the way I want it FINALLY!!

So, I'm hoping that next time (12.10?) there is a new kernel, all I have to do is purge nvidia*, install nvidia-current, reboot and I will be fine.  I will keep my fingers crossed!

Thank-you Fu for all your patience and support!

** Glad we finally got it working.**  We definitely went the long way around.  I think 
a) DKMS **should** have rebuilt the video drivers** automatically** when the new kernel was installed. Don't know what happened.
b) I believe all that was really necessary was:
```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get purge nvidia-current*
sudo apt-get install nvidia-current*
[B]sudo nvidia-xconfig
sudo nvidia-settings[/B] - SAVE

```That's it.

In theory, **just the last 2 nvidia-* commands should have been needed.** The purge/install could be a single --reinstall instead, if the DKMS didn't work.
Adding that extra PPA complicated things.  If you need it, that is probably fine, but mixing the kernel that you boot was confusing for both of us.

On Ubuntu systems, **dist-upgrade** will install any new kernel available and keep the system current with all patches.  I run this weekly to keep my systems up-to-date. Since 8.04 with a Xen kernel, I've never had any issues.  Getting the latest kernel is usually a smart idea for security. It will not upgrade to a new distribution unless the /etc/apt/sources.list has been manually changed to the new distro-codename. Completely safe.

I am not much of a GUI user. I can't imagine sharing point-n-click instructions to explain how to accomplish all this.

**ssh - OT rant**
ssh is fantastic.  The greatest inventions of all time are:
* fire
* wheel
* UNIX
* ssh
* rsync
I'm joking, but you get the point. ;)  Right now, I'm ssh'd into 5 other systems doing administrative stuff. No GUI.  I use ssh from  Android devices to manage system when on travel. Key-based ssh is safe from all over the world and from almost any network. It is that secure.  Once it is setup (2 steps), it is more convenient AND more secure than any other remote access method too. It is well worth your time to setup ssh servers on all your machines, so if the GUI locks up, you have a way in and can kill X/Windows, regain access and fix any issues. 

ssh connection security is easy [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) - this is from my blog.
ssh primer: [http://systemoverlord.com/sites/default/files/presentations/Keys-of-SSH.pdf](http://systemoverlord.com/sites/default/files/presentations/Keys-of-SSH.pdf) from a friend of mine. Even after using ssh 15+ yrs, I learned something.

On Windows (cough), Putty is the best ssh client.

BTW, I've written about nvidia setups on my blog:
* [http://blog.jdpfu.com/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver](http://blog.jdpfu.com/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver)
* [http://blog.jdpfu.com/2011/03/11/nvidia-gt-430-install](http://blog.jdpfu.com/2011/03/11/nvidia-gt-430-install)

---

### Post by carusoswi on 2012-09-02
TheFu
I was having the same problem. Copied/pasted the commands you listed from purge on down, and that fixed it for me.

I do not know what went wrong on this update, but I thank you for sharing your knowledge so that I could fix this problem.

My Nvidia driver would not download and install from that proprietary additional drivers screen for some reason.

Anyhow, thanks again.

Caruso

---

