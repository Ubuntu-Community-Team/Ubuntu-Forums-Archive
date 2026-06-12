---
title: "Dual-boot: 9.10 + 9.04 = several issues"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by mailman1175 on 2009-12-27
First, a little more information:

I have successfully installed Karmic UNR on my Acer Aspire One 110L (ZG5, with the Intel SSD). The /home partition is on an 8GB SD card. I've been looking for a lightweight distro to dual-boot with, something fully functional, but with a small footprint, something I can use as a rescue distro if need be. With that in mind, I had a 2GB partition set aside on the SSD.

I settled on Cruchbang (#!) Lite, largely because I'm now more familiar with Ubuntu variants than with any other Linux distros or their forks. Additionally, Ubuntu's community is far more active and supportive than any other I've encountered.

Anyway, on to the problems: 

The latest #! release is based on Jaunty. I wanted to point #! at the same /home partition, and use the same 1GB swap. The installer handled that part well enough, though I wasn't expecting it to append all new home sub-directories to the /home partition. Localization was set to the UK by default, with no option to change that in the installer. Weird, but nothing I couldn't change once it was installed.

**Of note here is that I opted NOT to install a bootloader in the #! install, because I was afraid it would have overwritten my Karmic GRUB2 install, and I wanted to let GRUB2 find the #! install with update-grub. This may or may not have anything to do with my problems.**

The #! Aspire One wiki page suggests installing the Kuki/sickboy custom kernel for best hardware support (wifi, proper sound, SD cards, fan behavior, etc). I've heard enough about this kernel in AspireOne user circles, I finally decided to give it a shot, understanding the limitations of support for a custom kernel.

That's where I started to run into problems, but it seems to me that my problems weren't specific to the Kuki kernel, since I couldn't apt-get upgrade to new ***supported*** kernels/headers, either. [This thread]("http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=9608&hilit=kuki+kernel+install#p62018") (on the AspireOneUser forums) has a pretty good run-down of the errors I get when I try to upgrade any of the kernel modules. apt-get upgrade does it; synaptic; .deb installers for the Kuki kernel — they all return the same errors.

It's not as if the kernel install completely fails, though. I boot back into Karmic, update-grub, reboot again, and the grub screen shows different boot options for each of the kernel modules I attempted to install under #!. The machine will boot into each of those kernels just fine. uname -r returns the expected kernel module in each case. But I see those same errors every time I do a package upgrade, and I can't compile madwifi drivers for the machine without kernel headers.

I kind of figure the root of my problem has something to do with GRUB. I just don't know what to do about it. Do I go ahead and let #! create a menu.lst like it wants to? Do I install GRUB2 on the #! partition? Is there something else going on I've missed?

I know just enough to be dangerous, folks. Y'all are lots of help, and I appreciate it. Let me know if you need to see some more detailed info… I'd sure like to figure this out. FWIW, I've posted similar requests for assistance on the AspireOne user forum and the Crunchbang forums, as well as trying Kuki's forums and their IRC channel.

TIA

---

### Post by oldfred on 2009-12-27
I am not sure you have a boot problem if you can boot into crunchbag ok. I do not know crunchbag so I cannot help there.

If you think it is a boot problem you can try chainbooting. Not everyone here is a fan of that and now grub2 does not like to be installed into a partition boot record, but old grub is fine. So if crunchbag is still grub legacy you can add it to the PBR of the crunch bag install and add a chainboot entry to 40_custom to link to the menu.lst for crunchbag.

Note that the partition numbering is different between grub and grub2. grub starts at 0 and grub2 starts at 1.

sda1   grub (hd0,0)     grub2 (hd0,1)

Boot into cruchbag and install grub to the partition see note and be sure to use your drive,partition:
#reset grub boot
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,5)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition
setup (hd0)
# Or
6. Type "s[COLOR=DarkRed]etup (hd0,3)". This is key.[/COLOR] Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".
quit


Then in your 9.10 install:

/etc/grub.d/40_custom

Add this to 40_custom and adjust drive, partition (one higher than entry above or same number as sda[COLOR=DarkRed]y[/COLOR]) to your crunchbag partition.
menuentry "Chainload Other System on sd[COLOR=DarkRed]a1[/COLOR]" {
set root=(hd[COLOR=DarkRed]0,1[/COLOR])
chainloader +1
}

---

### Post by mailman1175 on 2009-12-27
> **oldfred said:**
> I am not sure you have a boot problem if you can boot into crunchbag ok. I do not know crunchbag so I cannot help there.

If you think it is a boot problem you can try chainbooting. Not everyone here is a fan of that and now grub2 does not like to be installed into a partition boot record, but old grub is fine. So if crunchbag is still grub legacy you can add it to the PBR of the crunch bag install and add a chainboot entry to 40_custom to link to the menu.lst for crunchbag.

Note that the partition numbering is different between grub and grub2. grub starts at 0 and grub2 starts at 1.

sda1   grub (hd0,0)     grub2 (hd0,1)

Boot into cruchbag and install grub to the partition see note and be sure to use your drive,partition:
[COLOR=Red][B]#reset grub boot
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,5)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition
setup (hd0)
# Or
6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".
quit[/B][/COLOR]


Then in your 9.10 install:

/etc/grub.d/40_custom

Add this to 40_custom and adjust drive, partition (one higher than entry above or same number as sda[COLOR=DarkRed]y[/COLOR]) to your crunchbag partition.
menuentry "Chainload Other System on sd[COLOR=DarkRed]a1[/COLOR]" {
set root=(hd[COLOR=DarkRed]0,1[/COLOR])
chainloader +1
}

@oldfred

Thanks. #! 9.04 does use legacy-grub.

It's kind of hard for me to make sense of the highlighted portion above without code tags applied. #! is installed to /dev/sda1. Is this what my CLI entries should look like in #!?

```
[COLOR=Black]$ sudo grub
 $ find /boot/grub/stage1
$ root (hd0,0)
$ setup (hd0,0)[/COLOR]
```[COLOR=Black]

Having done that, then, I'll need to get back into KarmicUNR and:

```
$ sudo gedit /etc/grub.d/40_custom
```and enter, for example:

[/COLOR]```
menuentry "Chainload #! 2.6.31-rc9 on sd[COLOR=Black]a1[/COLOR]" {
set root=(hd[COLOR=Black]0,1[/COLOR])
chainloader +1
}
```then:

```
update-grub
```and see what happens?

Like I said: I know just enough to be dangerous, not quite enough to read between the lines and know what you mean just yet.

Thanks!

---

### Post by oldfred on 2009-12-27
Your entries look good. I think you have to sudo the grub update

```
sudo update-grub
```

---

### Post by mailman1175 on 2009-12-27
Ok:

```
$ sudo grub
grub> find /boot/grub/stage1
Error 15: File not found
grub>
```

If you'll recall, I didn't install a bootloader when I put #! on sda1, as I didn't want grub-legacy to interfere with grub2. What happens if I reinstall, this time placing the bootloader on (hd0,1)? That shouldn't — theoretically — overwrite the grub2 config I've already got, am I right?

I don't mind fixing something that's broke (my #! install). I don't want to break something that's working right (my Karmic UNR install).

Thanks again!

---

### Post by oldfred on 2009-12-27
Did you run the sudo grub from inside crunchbag? It should find your grub. Perhaps crunchbag does not have stage1 (some do not) type stage2. But grub2 will not have any of the stages.

Grub2 is installed in sda so putting grub1 in sda1 will not interfere with grub2 in sda.

---

### Post by mailman1175 on 2009-12-28
> **oldfred said:**
> Did you run the sudo grub from inside crunchbag? It should find your grub. Perhaps crunchbag does not have stage1 (some do not) type stage2. But grub2 will not have any of the stages.

Grub2 is installed in sda so putting grub1 in sda1 will not interfere with grub2 in sda.
@oldfred

Yes, I ran sudo grub from inside #!. What I posted above were the results. Are you saying I should repeat that, replacing "stage1" with "stage2"? Or shall I just reinstall (not *that* big a deal), and this time see if the installer will let me put the bootloader in sda1?

---

### Post by oldfred on 2009-12-28
When you said you did not install the boot loader that usually means that grub is not put into the MBR, but it still is in your install. The error 15 seems to say you do not have a /boot/grub directory with the grub files?

In Ubuntu as part of the install is an advanced button that lets us choose to not install or install to a partition or different drive.

It may be easier to just reinstall. Even if you accidentally overwrite grub2 in the MBR it is not that difficult to reinstall it.

---

### Post by mailman1175 on 2009-12-28
> **oldfred said:**
> When you said you did not install the boot loader that usually means that grub is not put into the MBR, but it still is in your install. The error 15 seems to say you do not have a /boot/grub directory with the grub files?

In Ubuntu as part of the install is an advanced button that lets us choose to not install or install to a partition or different drive.

It may be easier to just reinstall. Even if you accidentally overwrite grub2 in the MBR it is not that difficult to reinstall it.
I reinstalled, and that seems to have cured the "won't install headers" issue. Now I'm off to try to get wifi working.

I never will understand why every distro's live CD has functioning wifi, but doesn't work when you actually install it.

---

