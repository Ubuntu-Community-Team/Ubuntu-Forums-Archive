---
title: "Kernel panic at boot: not syncing. No init found"
date: 2014-06-07
forum: Installation &amp; Upgrades
---

### Post by SBFree on 2014-06-07
I did a clean install ( actually several attempts ) of 14.04 to my laptop and still cannot get it to boot. I tried [boot-repair]("http://askubuntu.com/questions/226061/how-to-install-the-boot-repair-tool-in-an-ubuntu-live-disc") from a live-USB and used the recommended repair but get the message: Kernel panic at boot: not syncing. No init found .
The boot-repair url it generated is : [http://paste.ubuntu.com/7607882/](http://paste.ubuntu.com/7607882/)
Any suggestions on how to debug this would be appreciated.
Thanks,
Scott

---

### Post by oldfred on 2014-06-07
I do not see anything really wrong with BootInfo report.
I thought it showed the newer grub in the MBR with 14.04, but may not?

Mine shows this for new install:
Grub2 (v2.00)

Where my 12.04 on a different drive is like yours:
Grub2 (v1.99)

I might try the full uninstall & reinstall of grub2 that Boot-Repair can do.

---

### Post by aqk on 2014-06-08
I have the same "not syncing. No init found" on my laptop.
I just upgraded my Ubuntu to 14.04  on a laptop and on my desktop.
Both systems were dual-booting Ubuntu and Windows-8.

Everything ran without a hitch on the desktop- Both Ubuntu and Win8 show on the GRUB and both boot sucessfully.
 Bu the install onto my laptop from the same USB thumbdrive resulted in this Kernel Panic error. 
At least my laptop's Win8 still boots OK from the new Grub.

This is the AMD64 ubuntu install file.
My desktop has an AMD64 processor and 8 Gb, whereas my laptop is a Pentium dual-core T4400, with 3 Gb of RAM.

Will this 64-bit Ubuntu run on the above Pentium T4400? Or should I try the 32-bit version?

---

### Post by LastDino on 2014-06-08
> **aqk said:**
> I have the same "not syncing. No init found" on my laptop.
I just upgraded my Ubuntu to 14.04  on a laptop and on my desktop.
Both systems were dual-booting Ubuntu and Windows-8.

Everything ran without a hitch on the desktop, but the install from the same USB thumbdrive resulted in this Kernel Panic eror.
This is the AMD64 ubuntu install.
My desktop has an AMD64 processor and 8 Gb, whereas my laptop is a Pentium dual-core T4400, with 3 Gb of RAM.

Will this 64-bit Ubuntu run on the above Pentium T4400? Or should I try the 32-bit version?

You should probably post your own thread, but yeah, x64 bit will work on Dual core, it works on my P4 which belongs to early start point where Intel started using x64 architecture and your CPU is far more advanced than mine.

---

### Post by SBFree on 2014-06-08
I purged Grub and reinstalled using boot-repair booted from a usb drive.
It still fails to boot with the same error as the title of this thread.

I generated a different pastebin record [http://paste.ubuntu.com/7614698/]("http://paste.ubuntu.com/7614698/")

There was one line of the boot-repair instructions that did not run, it was:
apt-get install -y --force-yes grub-pc linux
This told me that it was unable to locate package linux. Instead I ran:
apt-get install -y --force-yes grub-pc
and got screens that seemed to be anticipated by boot-repair.

It looks like someone else has a similar set of errors.

Thanks in advance for any help.
Scott

---

### Post by oldfred on 2014-06-08
I do not see anything really wrong with BootInfo report.

Just to test can you boot with Supergrub?

       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by SBFree on 2014-06-08
Thanks for this suggestion 'oldfred'. I spent an hour trying to make a bootable USB with either Supergrub or Rescatux and failed. I'll have to see if I can make a bootable CD and attach an external drive. The machine has not optical drive. Not sure why Pendrive or YUMI would not make a bootable USB.
Thanks again for the replies. I'll have to work more on this in a couple of days.
Scott

---

### Post by SBFree on 2014-06-09
Got Supergrub ( runs GRUB 2.00.22 ) working. Cannot boot either the standard or rescue images of Ubuntu.

From Grub opening menu I selected 'Everything', then this lists two Linux /boot/vmlinuz-3.13.0-24 images [hd1, msdos1] or [(single) (hd1,msdos1)]
Selecting either gets to:
Failed to execute /init
Kernel panic - not syncing : No init found

Scott

---

### Post by mörgæs on 2014-06-09
The report from Boot-repair tells that you have a 40 GB hard disk which could indicate that rest of the hardware is weak. 

Have you tried a fresh install of Lubuntu?

---

### Post by SBFree on 2014-06-09
The machine ran the 12.04 LTS version until I got it into my head to try to move to the next LTS version. Loading the kernel should take almost no resources. The drive is an SSD, the machine has 8G of RAM. Not sure what else I would want.

---

### Post by oldfred on 2014-06-09
I checked synaptic as I did not recognize the linux that you said it did not install. That was a new kernel. 

Did you have any ppa's or other proprietary software that causes a hang up as it does not have a trusty version now and then update crashes?

I would chroot in and try a full update/

 #Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

---

### Post by SBFree on 2014-06-09
Just to clarify. Are you suggesting I boot 14.04 from a USB, perform the updates on the live version, then use the install to HD link?
Thank you for continuing to work with me on this.
Scott

---

### Post by oldfred on 2014-06-09
You boot the live installer, but chroot or CHange ROOT, so you actually are working in your install on the hard drive.
Boot-Repair does that when you do a full uninstall/reinstall of grub2.

Some other ways to chroot:
 UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by SBFree on 2014-06-13
So sorry to ask a command questions, I have not had reason to use CHROOT. After I mount the HD with the install that won't boot should I CHROOT  the entire file system or just the root folder?

I do not understand how "cat /etc/issue" will help reassure me that I have chrooted correctly if both the live an HD versions are the same.

Thank you for your patience.
Scott

---

### Post by oldfred on 2014-06-13
With the chroot process you are in the entire system, but using the kernel from the system you boot.
Not sure about cat /etc/issue to confirm you are in your install.

If a new install so there is nothing to save, sometimes a new reinstall is easier. But use Something else and select the same partition for /. If you have /home separate select it also but DO NOT tick the format box. It will find swap if it exists.

---

### Post by SBFree on 2014-06-16
Thank you OldFred, 14.04 amd64 installs and boots now. This thread is solved. As a summary for others that might read this far or jump to the end of a resolved thread:
**Problem:**
I did a new install of ubuntu-14.04-desktop-amd64.iso from a USB drive made with [YUMI]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/") . The live distro booted ok and I did a HD install by choosing the *Install Ubuntu* rather than *Try Ubuntu* option on the live distro start up screen. HD Install would not boot generating error *Kernel panic at boot: not syncing. No init found*.

**Steps to resolve:**
In the post above OldFred suggested **using chroot**. I did mkdir HDInstall then mounted my HD partition to that directory, then did chroot to HDInstall follow by:
[INDENT]
#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a
[/INDENT]

This did generate messages that were : *Failed to fetch ...... Could not resolve 'us.archive.ubuntu.com'* many times.

I then used the Install to HD link that was on the live desktop and the install boots.
Kudos to OldFred

---

### Post by LastDino on 2014-06-16
You can safely ignore ''failed to fetch'' message as this generally means that; that particular mirror is slow and download process automatically tries it again from where it was cut offed.

However, when doing update in installed desktop, its usually advisable to update resource and mirror list. It can be done from ''software and update'' manager in system settings.

Welcome to Ubuntu!

---

### Post by BillyBarty on 2014-08-18
> **SBFree said:**
> 
This did generate messages that were : *Failed to fetch ...... Could not resolve 'us.archive.ubuntu.com'* many times.

I then used the Install to HD link that was on the live desktop and the install boots.
Kudos to OldFred

Hello. My first post!

I was able to solve this issue from information in your post. Thank you and “oldfred” for that. And I know this one has been marked SOLVED, but I did run across some things that I had to add in order to be successful. Furthermore, I was able to avoid receiving any "Failed to fetch ...... " messages and found that the step where you used the "Install to HD link" that was on the live desktop to be unnecessary. Therefore, I thought others may benefit from some detail about what I had to do. So here is what I did (after the initial installation that left me with the "Kernel panic at boot: not syncing. No init found" error) - stealing text from your post where applicable:

1) I booted up into the “Live CD” (actually a USB thumb drive), and changed the root (chroot) to HD install. Following are the details of how I did the chroot (I include this detail because, at least for me, a “chroot” command by itself was insufficient). I derived these commands from [http://ubuntuforums.org/showthread.php?t=2036730](http://ubuntuforums.org/showthread.php?t=2036730) (second post):

# Make directory for and then mount root partition (my root partition was on sda1 and I did not have a separate boot partition - might be different for you):
sudo mkdir /HDInstall
sudo mount /dev/sda1 /HDInstall

# Mount virtual file systems:
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /HDInstall$i; done

# Chroot
sudo chroot /HDInstall

2) In order to get the apt-get update/upgrade/install commands to work, I added proxy information to my /etc/environment (now same as /HDInstall/etc/environment due to doing the change root). For example:

http_proxy="http://proxy-chain.acmewidgets.com:8080/"
https_proxy="https://proxy-chain.acmewidgets.com:8080/"
ftp_proxy="ftp://proxy-chain.acmewidgets.com:8080/"
socks_proxy="socks://proxy-chain.acmewidgets.com:8080/"

Actually, in my case (booted into the Live CD), the O/S was not able to resolve “proxy-chain.acmewidgets.com” and I had to go to another computer on our network, ping “proxy-chain.acmewidgets.com”, get the IP address that came back, and put that in my /etc/environment file like so:

http_proxy="http://<IP Address>:8080/"
https_proxy="https://<IP Address>:8080/"
ftp_proxy="ftp://<IP Address>:8080/"
socks_proxy="socks://<IP Address>:8080/"

Then, and this was important for my setup (not sure why), I had to enter super user mode in order to get apt-get update/upgrade/install to work. Like I said, I’m not sure why, but simply prefacing those apt-get commands with “sudo” did not work for me.  What worked was entering “su” at the command line and then running the apt-get commands WITHOUT prefacing with “sudo”. I noticed I had to do this even if I was working in a super user terminal (opened by executing “sudo gnome-terminal”). Until I issued that “su” command at the prompt, the proxy settings in /etc/environment were not seen. I checked this by doing “echo $http_proxy” before and after the “su”; before: nothing came back, after: what was set in etc/environment came back.

3) At this point, I am back to your (and oldfred’s) directions:

apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f
apt-get -f install
dpkg --configure –a

Note: I did NOT get any “Failed to fetch ......” messages or any other error messages from the above commands.

4) I then rebooted (thus, I skipped the step where you used the “Install to HD link” that was on the live desktop), and the O/S came up without a hitch.

Given my above chronicled experience, and due to your mention that you received “Failed to fetch ......” messages and also performed an extra step that I that I did not (namely, execute the “Install to HD link” that was on the live desktop), I am not sure what actually fixed the issue for you. 

Hope this might help someone else!

---

### Post by Gergely_Fodor on 2015-06-12
Thank you very much OldFred and[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1939759") BillyBarty, solved my "*Kernel panic at boot: not syncing. No init found*" problem on my HP ProBook430.

---

### Post by pgoodchild on 2016-04-21
[COLOR=#000000]Thank you very much OldFred and BillyBarty. This also solved my "[/COLOR]*Kernel panic at boot: not syncing. No init found" on an asus gene 6 motherboard system. *

---

### Post by Dooley_Labs on 2017-01-13
[COLOR=#ffffff].
[/COLOR]I understand that I'm bumping quite an old thread, however, there's a much more simple way to restore network access without proxying to an external machine. Once you've completed the quoted steps below, you need to run the command following the quote **before **entering the chrooted hard drive.
> **BillyBarty said:**
> # Make directory for and then mount root partition (my root partition was on sda1 and I did not have a separate boot partition - might be different for you):
sudo mkdir /HDInstall
sudo mount /dev/sda1 /HDInstall

# Mount virtual file systems:
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /HDInstall$i; done

```
cp /etc/resolv.conf /HDInstall/etc/
```

Once you've copied the resolv.conf file, you can enter the chrooted system with full network access.

[HR][/HR]
Another note is that you needn't create the directory /HDInstall; instead, mount the disk to /mnt instead, like so:
```
mount /dev/sda1 /mnt
for i in /sys /proc /run /dev /dev/pts; do mount --bind "$i" "/mnt$i"; done
cp /etc/resolv.conf /mnt/etc/
chroot /mnt
```
Once you've repaired your system, exit the chroot with a command, like "exit", run the following code to safely unmount your drive, and reboot your system.
```
umount /mnt
```
[RIGHT][SIZE=1]**SOURCE:** [http://www.webupd8.org/2014/01/how-to-fix-non-bootable-ubuntu-system.html](http://www.webupd8.org/2014/01/how-to-fix-non-bootable-ubuntu-system.html)[/SIZE][FONT=Verdana]
[/FONT][/RIGHT]

---

### Post by howefield on 2017-01-13
Thread closed.

---

