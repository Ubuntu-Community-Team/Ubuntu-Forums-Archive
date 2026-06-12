---
title: "/boot empty at startup"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by Mondhund on 2011-09-15
Hi,

I solved this problem, but I'd like to understand what went wrong.

I downloaded Ubuntu 11.04 on a stick and started the installation procedure on my Zotac box with default settings, first on another USB stick. This was all fine and the new stick was booting as expected. But after a while it no longer worked for some reason so I decided to go for an external USB HDD.

I used the same USB stick to install the system on the HDD, but alas -  the box didn't come up. All I got was a grub-rescue prompt.

I thought something's wrong with the MBR so I executed all sort of MBR/grub repair procedures that I could find, upgraded BIOS etc. but without success. When I plugged the same HDD in my laptop, I immediately got the boot screen from grub.

Then I dug deeper and found that in the grub-rescue prompt, I could ls  (hd0,0) and (hd0,msdos1). Other commands (normal, loading modules etc) did not work. 

When looking from the grub-rescue prompt into the directories, everything looked good except the /boot directory which was empty! When plugging the HDD into the laptop and mounting, all the files are there.

I then came across a hint that it might be a good idea to make a separate partition during installation for the /boot directory and - hurray - that worked and the box bootes now.

But why was that darn /boot empty while booting?

Ideas?

Thx,  Thomas

---

### Post by oldfred on 2011-09-15
Welcome to the forums.

I actually suggest not to use a /boot partition for normal desktops. The standard install is just / (root) & swap. Often a good idea to add a /home, but anything more thatn the defaults requires you to use manual install to choose which partition is used for which.

Often to see what is actually install where this is a good (but detailed) tool. I use it before & after every system change, since I have several drives & versions of Ubuntu installed.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Lots of detail on installs to second drives:
Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by xlogger on 2012-06-14
I ran into a similar problem, however, in different circumstances. As well, I was able to resolve it, but there was definitely a glitch during the boot.

Here's the story. I've used Ubuntu 10.04 LTS box for quite a while. During installation I used standard disk configuration with one exception: /boot directory was mounted to a separate (non-LVM) partition: /dev/sda1.

For quite a while the machine worked fine. One day the system failed to come up and I got grub-rescue prompt. I rebooted the box a number of times with the same result.

The error message stated that root device could not be mounted.
From the prompt I was able to manually mount both root and boot partitions - they look fine to me. It appeared that for some reason /boot directory could not be mounted during the boot.

Then, I looked into /etc/fstab on the root partition and found that /boot is mounted by UUID. I commented out this line, and typed in boot device name instead of UUID: /dev/sda1. After reboot the system came up with no problem.

I suspected that somehow UUID of my boot device was changed or could not be fetched, but "blkid" showed the same UUID for the boot device that appeared in /etc/fstab. So I reverted /etc/fstab to the original state, rebooted - and voila - it worked!

Of course, identifying devices by UUID gives more flexibility that using device names, but apparently in some circumstances it fails.

---

