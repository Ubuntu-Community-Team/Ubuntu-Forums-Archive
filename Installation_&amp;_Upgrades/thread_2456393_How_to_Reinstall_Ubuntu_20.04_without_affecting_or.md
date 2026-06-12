---
title: "How to Reinstall Ubuntu 20.04 without affecting original data"
date: 2021-01-10
forum: Installation &amp; Upgrades
---

### Post by mike430 on 2021-01-10
Hello Ubuntu community. Would like to reinstall Ubuntu 20.04 without affecting any data in my original installation. Well of course I would like to affect the annoying Nvidia driver situation that is driving me to madness. But honestly, I am interested in reinstalling, retaining all data in home file, configuration files in /etc, samba users, and various other settings. Not sure if this is possible.

I might add others have written in other forums that by using live usb when you get to the partition after choosing 'something else' simply install over root partition without formatting. In my opinion, this sounds too easy and too good to be true. 

Thanks in advance for any input. 

Kindly, -Mike

---

### Post by guiverc on 2021-01-11
Assuming you are talking about Ubuntu 20.04 LTS Desktop (or like *flavors*), you can re-install using *"Something else"*, then select existing partitions, and as long as you don't format any, the install will

- note your additional packages installed (those added post-install)
- erase system directories (as you mention /etc; contents there will be lost as it's a system directory)
- install new system
- add back additional packages (*noted earlier; if available in your 'new' release in Ubuntu repositories*)
- ask to reboot.

No user directory is touched, thus as desktop programs store their configuration files in $HOME or your user directory; they will survive (unless you ticked *format*)

If fonts were added in your user directory; they'll of course survive, but any fonts installed and placed in system directories (so all users can use them), they'll be lost unless they were installed via package tools from Ubuntu repositories; those will get restored.  Any global change/setting made via edits to system directories will be lost (the effect will depend on how you made changes; if you used user programs to make configuration changes; those changes tend to be stored in your $HOME directory thus survive, however  changes made to files in system  directories will get lost.

This can be used to re-install a different release; but note: going forward (possibly *hirsute*) the re-install of your additional packages may no longer occur (I read a message in bug report that indicated this; it still occurs last Lubuntu *hirsute* install were I specifically tested for this feature).

This behavior is trigged by the no-format selection  If you select to *format*, you'll get a clean install without regard for what was installed previously.

---

### Post by gdesilva on 2021-01-11
If all you are trying to do is to uninstall nVidia, why not simply uninstall all nVidia packages? This probably is the simplest and safest way to do what you are trying to achieve. Once nVidia packages are uninstalled the system will automatically use open source driver for your card.

If, however, you still want to re-install then the one possibility would be to;

1. create a new partition for your data
2. copy all files in /home to the newly created partition
3. re-install using the 'something else' option and specify that you want to use the newly created partition where your data now resides as the /home
4. Proceed with the re-installation

However, this will not save any of your config files in /etc or elsewhere like samba config files - so it is a lot of work for achieving very little.

---

### Post by yancek on 2021-01-11
> simply install over root partition without formatting 

I did this successfully on another Linux OS recently, all my data and apps I had previously installed were still available after the reinstall.  I would expect the same result with Ubuntu.  I would certainly make sure I had a backup of personal data before doing this.

---

### Post by agvantibo on 2021-01-11
Yes, I've had an experience reinstalling w/o formatting, and it fixes stuff. This most definitely keeps all apps and data. Be wary that stuff might break. For me it was just gnome-terminal, so if you run into problems, purge and reinstall the package like so:
```
sudo apt remove --purge broken-package
sudo apt install broken-package
```.
Your problem may be in the configs, and reinstalling keeps some.
So you can probably can do a quick rm -rf on /etc and .config (be sure to back them up though).
Hope this helps.

---

### Post by mike430 on 2021-01-11
how to delete this post?

---

### Post by mike430 on 2021-01-11
> **gdesilva said:**
> If all you are trying to do is to uninstall nVidia, why not simply uninstall all nVidia packages? This probably is the simplest and safest way to do what you are trying to achieve. Once nVidia packages are uninstalled the system will automatically use open source driver for your card.

If, however, you still want to re-install then the one possibility would be to;

1. create a new partition for your data
2. copy all files in /home to the newly created partition
3. re-install using the 'something else' option and specify that you want to use the newly created partition where your data now resides as the /home
4. Proceed with the re-installation

However, this will not save any of your config files in /etc or elsewhere like samba config files - so it is a lot of work for achieving very little.
[COLOR=#000000]GDESilva, to your point that is the core of my problem and ideally I would not like to have to reinstall. I cannot for the life of me get Nouveau to load my Desktop/Gnome. Nvidia has been purged in its entirety, and I get so far as to see Nouveau installed but hangs after top left hand corner reads 'some number blocks/ clean 'some number/blocks' or something to that affect. From here I can only access the terminal.[/COLOR]

[COLOR=#000000]If you want to help me troubleshoot I'm all for it. Let me know. thank Mike[/COLOR]

---

### Post by grahammechanical on 2021-01-11
I have done what has been described above and it does work. As I gain experienced I saw the wisdom of having a partition for root ( / ) and a separate partition for /home. You have to give both partitions a mount point in the Something Else section but you can format the root partition. Just do not format the /home partition. Later on I set up a separate partition for Data where I save my files on. Then I can do a full reinstall without loosing my working documents.

Regards.

---

### Post by gdesilva on 2021-01-11
> **mike430 said:**
> [COLOR=#000000] and I get so far as to see Nouveau installed but hangs after top left hand corner reads 'some number blocks/ clean 'some number/blocks' or something to that affect. From here I can only access the terminal.[/COLOR]

[COLOR=#000000]If you want to help me troubleshoot I'm all for it. Let me know. thank Mike[/COLOR]

The message you see on the top left hand corner is most likely saying that the OS has just checked the filesystem for errors. This would have nothing to do with your display issue unless it reports of any errors.

I suspect the problem is due to nouveau module is not getting loaded and hence you are being presented with the console login prompt. You can check if nouveau is getting loaded by running 

lsmod | grep nouveau  

This should give you a list of entries if nouveau is loaded. I suspect in your case this will return nothing as most likely, installing nVidia earlier may have blacklisted the nouveau driver.

Run the following to see whether nouveau driver is blacklisted during the nVidia installation

sudo find / -type f -name "blacklist*" -exec grep -l "nouveau" {} \;

This should scan any files with the name blacklist for the string  nouveau. If you find any entries disable the nouveau (ie remove from the blacklisted drivers) by commenting it off and reboot.

If you do not find any entries the following post will give you some suggestions.

[https://askubuntu.com/questions/1032357/how-to-switch-from-nvidia-to-nouveau-drivers-on-ubuntu-18-04](https://askubuntu.com/questions/1032357/how-to-switch-from-nvidia-to-nouveau-drivers-on-ubuntu-18-04) 

Hope this will help.

---

### Post by mike430 on 2021-01-11
> **gdesilva said:**
> The message you see on the top left hand corner is most likely saying that the OS has just checked the filesystem for errors. This would have nothing to do with your display issue unless it reports of any errors.

I suspect the problem is due to nouveau module is not getting loaded and hence you are being presented with the console login prompt. You can check if nouveau is getting loaded by running 

lsmod | grep nouveau  

This should give you a list of entries if nouveau is loaded. I suspect in your case this will return nothing as most likely, installing nVidia earlier may have blacklisted the nouveau driver.

Run the following to see whether nouveau driver is blacklisted during the nVidia installation

sudo find / -type f -name "blacklist*" -exec grep -l "nouveau" {} \;

This should scan any files with the name blacklist for the string  nouveau. If you find any entries disable the nouveau (ie remove from the blacklisted drivers) by commenting it off and reboot.

If you do not find any entries the following post will give you some suggestions.

[https://askubuntu.com/questions/1032357/how-to-switch-from-nvidia-to-nouveau-drivers-on-ubuntu-18-04](https://askubuntu.com/questions/1032357/how-to-switch-from-nvidia-to-nouveau-drivers-on-ubuntu-18-04) 

Hope this will help.
You are correct nouveau is currently not loaded. Also deleted the file that blacklisted loading Nouveau in the /etc/modprobe directory. I think I'm out of luck. I'll try one more time to load Nouveau. Thanks for the help.

---

### Post by gdesilva on 2021-01-12
Also worth trying purging the nouveau package, if it already installed, and then re-install the nouveau package before you give up on this.

---

