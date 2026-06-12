---
title: "unmet dependencies after failed update to lts enablement stack"
date: 2013-03-06
forum: Installation &amp; Upgrades
---

### Post by SirWeazel on 2013-03-06
In short, i messed up. I tried to update ubuntu 12.04 to the latest hardware enablement stack, but it fails to install the 3.5 kernel and now i have unmet dependencies.  The problem is because i have ubuntu 12.04 installed on non pae hardware when i foolishly ran ```
[COLOR=#333333][FONT=monospace]sudo apt-get install linux-generic-lts-quantal xserver-xorg-lts-quantal[/FONT][/COLOR]
```
So now i get the following error when trying to install or update anything. Thanks for you help. I don't remember exactly how i installed ubuntu 12.04 on this non pae laptop, the only reason i tried updating is because i've had some minor hardware issue and i thought there might be some added support in the newer kernal. I've tried to apt-get remove the same code, but it keeps complaining of dependecy issues when trying to remove. Thanks again for any help.
```
chris@HPDV1000:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-lts-quantal : Depends: linux-image-3.5.0-25-generic but it is not installed
E: Unmet dependencies. Try using -f.
chris@HPDV1000:~$ 

``````
chris@HPDV1000:~$ sudo apt-get -f install
[sudo] password for chris: 
Sorry, try again.
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-24 linux-headers-3.2.0-24-generic
  linux-headers-3.2.0-24-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.5.0-25-generic
Suggested packages:
  fdutils linux-lts-quantal-doc-3.5.0 linux-lts-quantal-source-3.5.0
  linux-lts-quantal-tools
The following NEW packages will be installed:
  linux-image-3.5.0-25-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/40.1 MB of archives.
After this operation, 118 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 660337 files and directories currently installed.)
Unpacking linux-image-3.5.0-25-generic (from .../linux-image-3.5.0-25-generic_3.5.0-25.39~precise1_i386.deb) ...
This kernel does not support a non-PAE CPU.
dpkg: error processing /var/cache/apt/archives/linux-image-3.5.0-25-generic_3.5.0-25.39~precise1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.5.0-25-generic_3.5.0-25.39~precise1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
chris@HPDV1000:~$


```

---

### Post by carl4926 on 2013-03-06
You can chroot the installed system with the original 12.04 install media
Ensure your sources are for 12.04 only and do
```
sudo apt-get clean
```
```
sudo apt-get update && dist-upgrade
```

---

### Post by SirWeazel on 2013-03-06
I'm not sure how to chroot the whole system. My sources should be for 12.04 only, i've only added a couple extra ppas (for chrome, opear, java). They system is bootable, in fact i am using it now.  So if you need screenshots or additional info then please let me know and i will try my best to provide additional information.

---

### Post by carl4926 on 2013-03-06
If it's bootable then no need to chroot
It should be possible then to undo the mess
Synaptic is quite useful ....

---

### Post by SirWeazel on 2013-03-06
I thought i had synaptic installed, but i don't and now because of the unmet dependencies i can't install it.

---

### Post by carl4926 on 2013-03-06
Boot the 12.04 cd
> * Open a terminal and type

$ sudo fdisk -l


    * Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt


$ sudo mount /dev/sda1 /mnt


    * Now mount the rest of your devices


$ sudo mount --bind /dev /mnt/dev


    * Now chroot into your system


$ sudo chroot /mnt

Now use apt-get

```
apt-get install synaptic
```

Now either carry on as chroot or reboot

---

### Post by SirWeazel on 2013-03-07
carl4926, thanks for taking the time to reply back to my questions.  The way i installed ubuntu 12.04 on this computer was from the mini iso and used this to install the non pae version of ubuntu.  I don't think i can boot from the regular ubuntu live cd because the live cd contains the normal pae kernel.  My system is currently bootable, thats how i provided the copy paste from my first post. Is there not a way to undo from the command line or force install syanptic to help reverse what i've done. I've tried the apt-get remove, but then it complains of unmet dependencies or it says package not installed.  If i've completely messed myself, i can just back up and reinstall.... but would prefer not to go that route if there is a simpler approach/fix.

---

### Post by carl4926 on 2013-03-07
Sorry but ATM I too much work on to give this the attention it needs/deserves.
I will check bask ASAP, probably tomorrow early AM (UK)

---

### Post by SirWeazel on 2013-03-12
I was able to fix my issue. The command i was unfamiliar with, and ended up using was "dpkg". To remove the packages i used "sudo dpkg --remove" and filled in whatever package it was complaining about. The exact commands i ran:
```
[FONT=Ubuntu Mono][COLOR=#000000]sudo dpkg --remove linux-image-generic-lts-quantal
sudo dpkg --remove linux-generic-lts-quantal[/COLOR][/FONT]
```

I was pretty sure the new kernel would work with my cpu, but my early version of the pentium M was missing the pae flag. So i found "fake-pae" which adds the pae code to /proc/cpuinfo. After i fixed my unmet dependencies with dpkg --remove i was able to install fake-pae with their ppa.
```
sudo apt-add-repository ppa:prof7bit/fake-pae
sudo apt-get update
sudo apt-get install fake-pae

```
Then i re-installed the enablement stack by using: 
```
sudo apt-get install linux-generic-lts-quantal xserver-xorg-lts-quantal
```

Everything now works... and i do get better video support with the new kernel. For anyone else reading this, my main problem was i didn't know that i could dpkg --remove the broken packages and dependencies. I just needed to get to the point where i could apt-get install stuff. I could have then removed everything and reverted to my original kernel and xorg, but i forged forward and tried the fake-pae with my CPU. I'm providing links to the 3 sources of info that helped me in this problem.

[http://askubuntu.com/questions/211476/intel-pentium-m-with-ubuntu-12-10-ppa-needed](http://askubuntu.com/questions/211476/intel-pentium-m-with-ubuntu-12-10-ppa-needed)
[http://ubuntuforums.org/showthread.php?t=2113826](http://ubuntuforums.org/showthread.php?t=2113826)
[https://launchpad.net/~prof7bit/+archive/fake-pae](https://launchpad.net/~prof7bit/+archive/fake-pae)

---

### Post by SirWeazel on 2013-03-12
I want to mark this as solved, but i do not have that option under thread tools?

---

### Post by sudodus on 2013-03-12
> **SirWeazel said:**
> I want to mark this as solved, but i do not have that option under thread tools?

Welcome to the fake-pae club :-)

Try to mark it as solved according to this link [URL="http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730"][COLOR=#ff0000]http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730

[/COLOR][/URL]> Go to the first post in your thread. Click on "Edit Post". Now click on  the orange "Go Advanced" button. In the advanced editor change the  prefix to "SOLVED". Now click on the orange "Save Changes" button.

Please note that there is a 60-day limit on being able to edit posts, and this would include changing the prefix.

---

