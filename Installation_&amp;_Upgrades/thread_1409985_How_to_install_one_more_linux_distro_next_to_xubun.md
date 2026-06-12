---
title: "How to install one more linux distro next to xubuntu?"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by vickoxy on 2010-02-18
Hi,
i have xubuntu 9.10 and would like to install mint and crunchbang next to xubuntu.
1) Is it so simple as just to install every distro next to xubuntu partition (as suggested in install setup)?

2) How to choose at startup which distro to run?

Thanks

---

### Post by tommcd on 2010-02-18
> **vickoxy said:**
> 
i have xubuntu 9.10 and would like to install mint and crunchbang next to xubuntu.
1) Is it so simple as just to install every distro next to xubuntu partition (as suggested in install setup)?
You will need to create a new partition for each distro. I like to use a Parted Magic live CD for this:
[http://partedmagic.com/](http://partedmagic.com/)
or you should be able to use the GParted live CD, or the GParted from the Xubuntu live CD.
These new partitions will be used for the root directory of each distro that you install. All distros can share the same swap file that you are using for Xubuntu.
If you have a separate home partition, then all distros *can* share home. However, it is a good idea to use a different user name for each distro, so that all the hidden (i.e., that start with a period) configuration files and folders in your home directory for each distro do not conflict with each other.
I like to use a /data partition for my data. That way each distro's home directory resides in that distro's root partition so there is no chance of conflicts between different distro's config files. All distros can read and write to my /data partition.
> **vickoxy said:**
> 
2) How to choose at startup which distro to run?

You can use Xubuntu's grub2 to boot all distros you install. When you install Mint and Chrunchbang, either elect not install grub (if they give you that option) or install their grubs to their own root partition instead of the MBR. Then just boot up Xubuntu 9.10 and run:
```
sudo update-grub
```
and grub2 should automatically add entries for Mint and Chrunchbang and give you the option to boot them when you see the grub2 menu on boot up.
Or you could let Mint or Chrunchbang install grub to the MBR. Then either Mint or Chrunchbang's grub will control the MBR.

I currently boot WindowsXP, Ubuntu 9.10, Zenwalk 6.2, and Slackware 13 64bit on my desktop and this is how I do it.
Write back if you need more help.

---

### Post by presence1960 on 2010-02-18
> **vickoxy said:**
> Hi,
i have xubuntu 9.10 and would like to install mint and crunchbang next to xubuntu.
1) Is it so simple as just to install every distro next to xubuntu partition (as suggested in install setup)?

2) How to choose at startup which distro to run?

Thanks

it does not matter if the partitions are adjacent to ubuntu's partition, they can be anywhere on the hard disk. When you install the others make sure you install GRUB to the partition of that distro that you are installing. You can do this at the ready to install window by clicking the Advanced button (see attached pic) and choosing where to put GRUB. I.e. I am putting crunchbang on sda7 so I would choose from the drop down box to put GRUB on /dev/sda7. This will keep your ubuntu GRUB on MBR. After the distro is installed boot into ubuntu and run in terminal ```
sudo update-grub
```This will detect your new disto(s) and add it to the GRUB menu at boot.

---

### Post by presence1960 on 2010-02-18
> **tommcd said:**
> You will need to create a new partition for each distro. These new partitions will be used for the root directory of each distro that you install. All distros can share the same swap file that you are using for Xubuntu.
If you have a separate home partition, then all distros *can* share home. However, it is a good idea to use a different user name for each distro, so that all the hidden (i.e., that start with a period) configuration files and folders in your home directory for each distro do not conflict with each other.
**_*I like to use a /data partition for my data. That way each distro's home directory resides in that distro's root partition so there is no chance of conflicts between different distro's config files. All distros can read and write to my /data partition.*_**

You can use Xubuntu's grub2 to boot all distros you install. When you install Mint and Chrunchbang, either elect not install grub (if they give you that option) or install their grubs to their own root partition instead of the MBR. Then just boot up Xubuntu 9.10 and run:
```
sudo update-grub
```
and grub2 should automatically add entries for Mint and Chrunchbang and give you the option to boot them when you see the grub2 menu on boot up.

I currently boot WindowsXP, Ubuntu 9.10, Zenwalk 6.2, and Slackware 13 64bit on my desktop and this is how I do it.
Write back if you need more help.
That is exactly what I do also & works great for me with Karmic, mint 8 & sabayon.

It's funny that 2 of us from philly were typing a response at about the same time. :popcorn:

---

### Post by darkod on 2010-02-18
If you have unallocated unpartitioned space on that hdd (or any other hdd), yes, it's that simple. Just install it where ever you want.
The main thing is this: You already have grub2 with Xubuntu, and it can load any other linux or windows OS. So, when installing any future linux it's better to look carefully at Advanced option during the install (for different linux they are called differently) and select NOT to install a bootloader (grub).
When you reboot after the install, don't be surprised to see only Xubuntu in your list, or to boot directly into xubuntu. For grub2 just do in terminal:

sudo update-grub

and it will detect all new OSs and add them to the boot list.
You have to avoid the confusion which grub are you using from which linux. It helps later on.

---

### Post by vickoxy on 2010-02-18
Ok, just to summarize-i just plug into my computer usb live stick and make install-only have to choose in advanced options "not" install with the grub.

After that i should upgrade grub and after restart there should be visable all my linux distros?

---

### Post by darkod on 2010-02-18
> **vickoxy said:**
> Ok, just to summarize-i just plug into my computer usb live stick and make install-only have to choose in advanced options "not" install with the grub.

After that i should upgrade grub and after restart there should be visable all my linux distros?

Yes. :)

---

### Post by tommcd on 2010-02-18
> **vickoxy said:**
> Ok, just to summarize-i just plug into my computer usb live stick and make install-only have to choose in advanced options "not" install with the grub.
If you want Xubuntu's grub to control the MBR, then either elect not to install grub when installing Mint and Chrunchbang. Or install Mint and Chrunchbang's grub to their own root partitions. Then just run:
```
sudo update-grub
```
from Xubuntu and you should have options to boot all your ditros.
You could install Mint's or Chrunchbang's grub to the MBR and let those distro's grub control booting the system. It is really just a personal preference as to which distro controls the MBR.
One thing to consider is that Crunchbang is still based on Ubuntu 9.04 as far as I know. So Crunchbang will likely still use grub legacy. If it were me I would just let Xubuntu's grub control the MBR.
> **vickoxy said:**
> 
After that i should upgrade grub and after restart there should be visable all my linux distros?
Yes, just run "sudo-update grub" from Xubuntu and you should be good.

@Presence1960,
Hello from Philly!!

---

### Post by vickoxy on 2010-02-18
Thanks! :popcorn:
Now just to fix my gparted and we will see...

---

### Post by vickoxy on 2010-02-18
Hi,
had one problem-my ignorance... in which step should i determinate NOT to grub? I choose to install crunchbang next to Xubuntu in step 4-i added 10GB disk-now i have free space-should i go fort to choose NOT to grun, because in step 4 i found nothing?

Thanks

---

### Post by tommcd on 2010-02-19
> **vickoxy said:**
> Hi,
had one problem-my ignorance... in which step should i determinate NOT to grub? I choose to install crunchbang next to Xubuntu in step 4-i added 10GB disk-now i have free space-should i go fort to choose NOT to grun, because in step 4 i found nothing?

I have never installed Crunchbang. When you get to the step where Crunchbang wants to install grub to the MBR, there should (hopefully) be a key you can select for advanced options or something like that. This should allow you to either skip the grub install or to install grub to Crunchbang's root partition. Either option will work fine, since either option will preserve the grub from Xubuntu on the MBR.
BTW, When installing Crunchbang and Mint, be sure to choose manual partitioning. This will let you select the new partitions you have created for the root partitions of your new distros. It will also allow you to set your /home partition as the mount point for /home. This assumes that your home directory is on a separate partition. Is it?

---

### Post by vickoxy on 2010-02-19
In the last step i choose "grub not install"-well, about partitioning-i had some issues there-some free space-then i went to manual partitioning menu and tried to delete free space and then- i do not know how-i had option to use all available free space to make new partition-i made it and installed there crunchbang. By startup i have now several options and i can run crunchbang. Have though some problems with linux header configuring-made all available updates, but it reports error by configuring linux header. Don´t know what that is... 

> **tommcd said:**
> I have never installed Crunchbang. When you get to the step where Crunchbang wants to install grub to the MBR, there should (hopefully) be a key you can select for advanced options or something like that. This should allow you to either skip the grub install or to install grub to Crunchbang's root partition. Either option will work fine, since either option will preserve the grub from Xubuntu on the MBR.
BTW, When installing Crunchbang and Mint, be sure to choose manual partitioning. This will let you select the new partitions you have created for the root partitions of your new distros. It will also allow you to set your /home partition as the mount point for /home. This assumes that your home directory is on a separate partition. Is it?

---

### Post by tommcd on 2010-02-19
I'm not sure where to go with all of this ...
> **vickoxy said:**
> In the last step i choose "grub not install"-well,
So did you install grub from Crunchbang? And if so, where did you install grub, to the MBR or to Crunchbang's root partition?
> **vickoxy said:**
> 
 about partitioning-i had some issues there-some free space-then i went to manual partitioning menu and tried to delete free space and then- i do not know how-i had option to use all available free space to make new partition-i made it and installed there crunchbang. 
You do not need to delete free space. You can just choose manual partitioning. Then create a partition (10GB should be plenty) for Crunchbang. Then install Crunchbang to that partition.
> **vickoxy said:**
> 
By startup i have now several options and i can run crunchbang. Have though some problems with linux header configuring-made all available updates, but it reports error by configuring linux header. Don´t know what that is...
So can you still boot Xubuntu? I am not sure what you mean here.
If you are unable to run Xubuntu, then bootup the Xubuntu live CD and reinstall grub2 to the MBR like this:
From the live CD, open a terminal and run:
```
sudo mount /dev/sdaX /mnt
```
Where X = your Xubuntu root partition.
This will mount your ubuntu partition. Then run in terminal
```

sudo grub-install --root-directory=/mnt/ /dev/sda

```
This will put GRUB2 on MBR of your hard disk
Also, see these tutorials for reinstalling grub2:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

---

### Post by vickoxy on 2010-02-19
> So did you install grub from Crunchbang? And if so, where did you install grub, to the MBR or to Crunchbang's root partition? - no, i did not

So, i can run xubuntu and crunchbang whitout problems. Only, when i run crunchbang, and want something to install from synaptic/terminal-it reports some error with linux kernel and header-something like it leaves it unconfigured. Never mind that-xubuntu is my main system-i use crunchbang just to test it.

I will mark this thread as solved, because i followed the guides that was given to me, and i did  make installation of new linux system.

Other issues  i will report later if needed.

Thanks a lot :popcorn:

---

### Post by tommcd on 2010-02-20
At least now you know how to go about booting multiple linux distros.
I do not know whey Crunchbang would report those errors. Perhaps you could start a new thread about that if you are unable to solve it. Or ask over at the Crunchbang forums.

---

