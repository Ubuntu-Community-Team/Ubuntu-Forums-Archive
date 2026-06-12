---
title: "Configuration errors appearred."
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by AndyRic on 2010-08-12
Hello.

Recently my beloved ubuntu setup died and I'm struggling to fix it.  One day I turned it on and I received the following message:

"Your screen graphics card and input device settings could not be detected correctly'

Attempting to continue with the recommended lower graphics settings does not work and I am not sure where to go from here. Sometimes it will advance at the lower graphics setting until an error regarding the configuration defaults for the GNOME power manager that have apparently not been installed properly.

I didn't change anything and my windoze partition works well.  Running Lucid Lynx with nvidia graphics card and ndiswrapper.

Other error messages are:
(EE) [drm] failed to open device
(EE) Failed to initialise GLX extension (Compatible NVIDIA X driver not found)

If I reinstall ubuntu will I lose all my programs and data?

Any help much appreciated.

---

### Post by tommcd on 2010-08-12
> **AndyRic said:**
>  Running Lucid Lynx with nvidia graphics card and ndiswrapper.
Is this a real install of Ubuntu? Or is this a wubi (inside Windows) install?

What nvidia card do you have? Did you install the nvidia driver? If so, is it the driver from the Ubuntu repos? Or is it the driver from nvidia.com?
What are you using ndiswrapper for?
> **AndyRic said:**
> 
If I reinstall ubuntu will I lose all my programs and data?

If you reinstall Ubuntu, you will need to reinstall all programs that you have that are not included on the Ubuntu install CD.
If you have a separate home partition, your data and settings are safe. If you only have one Ubuntu partition for root that includes your home directory, then you will need to back up your data before reinstalling.

---

### Post by whitefort on 2010-08-12
This same error has suddenly appeared on my system.  It's a dedicated Ubuntu setup (no windows partition)

I turned the machine on and now can't get past the login screen.

Could this be related to any recent updates?

I'd be really grateful if anyone could tell me how to get into my system again!

---

### Post by AndyRic on 2010-08-13
Thanks tommscd,

The install is a full Ubuntu install that's been running beautifully since lucid first came out.  I use grub and W7 for itunes because I have too.

Ndiswapper was the only way I could my old wifi card to work.  Support for my card ceased with karmic and I could not get it to work with MadWiFi so I had to resort to ndis.

The Nvidia drivers came from nvidia direct.

Most of my data is safe through backups but it'll be a real nuisance to have to reinstall and reconfigure.  I might have to look into a type of ghost backup of the essential system files in the future.

Thanks again for your reply.

---

### Post by tommcd on 2010-08-13
> **AndyRic said:**
> 
The Nvidia drivers came from nvidia direct.

If you installed the nvidia driver from nvidia.com you should know that this driver will have to be *reinstalled* whenever there is a kernel update for Ubuntu. The nvidia driver from the Ubuntu repos will be automatically reinstalled whenever there is a kernel update. When you go outside the Ubuntu repos, you are responsible for maintaining the system yourself.
So, since there are fairly frequent kernel updates for Ubuntu, you probably need to reinstall the driver from nvidia.com. Just stop X in Ubuntu and reinstall the driver the way you did before. Then reboot and you should be good.

---

### Post by tommcd on 2010-08-13
> **whitefort said:**
> This same error has suddenly appeared on my system.  It's a dedicated Ubuntu setup (no windows partition)
I turned the machine on and now can't get past the login screen.
Could this be related to any recent updates?

If you too installed the driver from nvidia.com, see my post right above this.
If you have the driver from the Ubuntu repos, write back and state what nvidia card you have, and exactly how you installed the nvidia driver.

---

### Post by AndyRic on 2010-08-16
Problem solved!!!!

Thanks for your help Tommcd.  For the sake of anybody else having similar problems this is how I fixed it.  Essentially I just followed tommcd's advice and reinstalled the driver.

Download the driver from nvidias website, for me it was NVIDIA-Linux-x86-256.44.run and put it in your home directory (at least that's where I put it).  I used another computer to do this.

Use the recovery mode in grub or some other way to get a prompt (command line).

execute the following commands:

su -c 'telinit 3'
(This was done because the installation program told me to quit out and run this and then run the installation program again)

cd whatever directory has the install program in it.
sudo sh NVIDIA-Linux-x86-256.44.run

reboot.
 
Works but I am going to try using the drivers from the ubuntu repositories so I don't have to repeat the process every kernel release.

Thanks again for your help Tommcd.  Much appreciated.

---

### Post by tommcd on 2010-08-16
> **AndyRic said:**
> 
Use the recovery mode in grub or some other way to get a prompt (command line).
execute the following commands:
su -c 'telinit 3'
(This was done because the installation program told me to quit out and run this and then run the installation program again)
cd whatever directory has the install program in it.
sudo sh NVIDIA-Linux-x86-256.44.run

If you boot directly to recovery mode, X should not be running. If you boot Ubuntu normally and then hit: ctrl + alt + F1-6 to get to a virual terminal, you will need to stop X with:
```
sudo service gdm stop
```
Then to restart X just replace *stop* with *start* in that command.
> **AndyRic said:**
> 
Works but I am going to try using the drivers from the ubuntu repositories so I don't have to repeat the process every kernel release.
If you want to install the nvidia driver from the Ubuntu repos after you have installed the driver from nvidia.com, you will need to *completely remove* the driver from nvidia.com first.
So stop X:
ctrl + alt + F2
```

sudo service gdm stop

```
Uninstall the nvidia driver:
```
sudo sh NVIDIA-xxx.run --uninstall
```
Replace xxx with the version of the nvidia driver that you installed.
Then reboot.

---

