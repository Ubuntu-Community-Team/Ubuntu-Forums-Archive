---
title: "grub, again"
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by LMHmedchem on 2012-08-15
I had some issues with my motherboard a bit ago and had to move some of my drives to a sata card. I also re-installed XP.  My grub screen no longer appears, since I guess the XP did its thing and ignored everything else, but I need to get it back. I can use supergrub2 to get  into ubuntu, but the command update-grub just returns, "grub not found". Super grub2 can also load the grub2 conf from which I can boot into ubuntu. It would appear the the conf is still there and still works.

I tried these steps from an earlier thread, using sda1 instead of sdc1.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sdc1 and want grub2's bootloader in drive sdc's MBR:
#Find linux partition, change sdc1 if not correct:
sudo fdisk -l
#confirm that linux is sdc1
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sdc
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdc

This completed without errors, but does not fix the issue and I stil get grub not found. I also tried the boot repair disk, which has worked from me in the past. It gives me some command line arguments to paste in to a terminal to un-install grub, but the terminal gives an error about something not found and I can't get past that point.

I have attached the results file from the boot info script. It seems like I should un-install all my grub and start again, but I'm not sure how to go about that or if it's the best option.

It seems like grub should be installed to the MBR of sdb where XP is, since that disk is the first in the boot order, but at the moment, I would be happy with a functional version anywhere it will work.

Thanks for the advice,


**[color="#000090"]LMHmedchem[/COLOR]**

---

### Post by darkod on 2012-08-15
So just go into BIOS and set sdc to be the first disk to boot from.

As long as you are booting from the wrong disk you can't expect to see the correct grub2 menu. The installation to sdc seems to have finished successfully according to you, now you only need to boot from sdc.

---

### Post by drs305 on 2012-08-15
Make sure the BIOS is booting from your 150GB drive. The drive letters may be different than what you are expecting, but it's the 150GB drive which you want BIOS to boot first.

Edit: A bit slow ... what *darkod* said...

---

### Post by LMHmedchem on 2012-08-15
All right, that makes sense and I will try that, but why do I get "grub not found" when I run update-grub from ubuntu? Which grub gives me nothing either.

**[color="#000090"]LMHmedchem[/COLOR]**

---

### Post by LMHmedchem on 2012-08-15
Switching the bios to boot from the 150GB drive does get me the grub menu back, so that is a start.

There are two additional problems however.

My usb2 wireless keyboard (verbatium) does not appear to be supported. I cannot use the arrow keys to select an option other than the default. After the timeout, I am booted into ubuntu.

I still get "grub not found" in ubuntu when I run sudo update-grub. This would appear to imply that there is still something wrong with the setup.

I still need to use supergrub2 if I want to boot into any os other then the defualt.

**[color="#000090"]LMHmedchem[/COLOR]**

---

### Post by drs305 on 2012-08-15
I'm not sure about the keyboard, but I recommend purging and reinstalling GRUB. As long as you have a steady Internet connection it poses very little risk.

The Ubuntu Community documentation provides the details on how to do it:
[_Installing# Purging & Reinstalling GRUB 2_]("https://help.ubuntu.com/community/Grub2/Installing#Purging_.26_Reinstalling_GRUB_2")

It could be that the keyboard modules are not being loaded and reinstalling may solve that issue as well.

---

### Post by |{urse on 2012-08-15
Procure a bios-supported keyboard. You're stuck until you do that. Once you've set your bios to correctly support usb peripherals and to boot from the correct disk then everyone can assist you further.

---

### Post by LMHmedchem on 2012-08-15
> **drs305 said:**
> I'm not sure about the keyboard, but I recommend purging and reinstalling GRUB. As long as you have a steady Internet connection it poses very little risk.


I think that makes the most sense. I know I have used this keyboard with a grub2 setup before, so it doesn't make much sense that it doesn't work now. I had a ps2 keyboard installed (along with the usb) because I needed it to select the session type with the boot repair disk. I have never understood why such a thing would not support a certain keyboard type for the start screen, but would support it later on in the app. That keyboard was probably still connected when I re-installed grub from the live cd, so possibly the installer thought that it only needed ps2 support.

I will follow the instructions at the link and let you know how it goes.

**[color="#000090"]LMHmedchem[/COLOR]**

---

### Post by LMHmedchem on 2012-08-15
> **|{urse said:**
> Procure a bios-supported keyboard. You're stuck until you do that. Once you've set your bios to correctly support usb peripherals and to boot from the correct disk then everyone can assist you further.As far as I know, my bois is set up right, at least I can access my bios and make changes using my wireless keyboard. I just used this wireless keyboard to change the boot order. Is there some other legacy keyboard support in the bios that I may have forgot to enable or something like that?

My ps2 keyboard and mouse are never further away than the drawer underneath my computer. There are still absolutely necessary from time to time. I would use them full time, but my computer is not on my desk any more and wireless is the only thing the will work with my current setup.

**[color="#000090"]LMHmedchem[/COLOR]**

---

### Post by |{urse on 2012-08-15
Depends on which bios you have, yes, enable legacy usb if you see that. You may need to search around the bios to find it.

---

### Post by LMHmedchem on 2012-08-15
> **|{urse said:**
> Depends on which bios you have, yes, enable legacy usb if you see that. You may need to search around the bios to find it.Looking around in the bios, I say that usb keyboard and usb mouse were not enabled, nor was legacy usb. I changed my memory a little while ago and I think I reset the bios to optimized defaults to get it to post. I'm not sure how I could get into the bios in the first place. Changing those options did allow me to navigate the grub menu, but when I select windows, I get an error message that the device does not exist.

I am back in live and am starting the process of purging and reinstalling.

**LMHmedchem**

---

### Post by LMHmedchem on 2012-08-15
Well I moved through the first steps without any error messages.
sudo apt-get update
sudo apt-get purge grub-common

When I go to reinstall grub, I get a "GRUB installation failed" I tried installing grup to all 4 drives, and then just to the linux drive, but I get the failure message in both cases.

This is the output from the terminal,
```

Setting up grub-pc (1.98-1ubuntu13) ...

Creating config file /etc/default/grub with new version
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```

I'm guessing that I didn't mount the drives in dev. I didn't realize that I could do this from inside my ubuntu install and didn't need the live cd. I will go back and read through the tutorial to see if it covers mounting drives. I can probably get into ubuntu using supergrub if it would be easier to fix that way, but for now I am staying in the live cd.

**[B][color="#000090"]LMHmedchem[/COLOR]**[/B]

---

### Post by drs305 on 2012-08-15
It's a fairly simple matter from within the operating Ubuntu OS. If you were trying this from the LiveCD and didn't mount the Ubuntu partition purging grub shouldn't have touched your actual OS.

If it's still possible, just boot your normal OS and purge/reinstall. 

If you have to do it from the LiveCD, it's a bit more complicated since you have to 'chroot' first. Rather than doing it manually in that case I'd recommend installing Boot Repair in the LiveCD and it can assist you with the process.

---

### Post by LMHmedchem on 2012-08-15
After booting back into ubuntu, when I run,

apt-get purge grub-common

I get the following,

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-common is not installed, so not removed
The following packages were automatically installed and are no longer required:
  firefox-branding os-prober
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 215 not upgraded.

The apt-get install grub-pc command seemed to go fine and I decided to install grub to the MBR of the 150GB linux drive as well as to my windows drive. I did update-grub and that worked as well. I will now see if I can boot in to everything.

**[color="#000090"]LMHmedchem[/COLOR]**

---

### Post by LMHmedchem on 2012-08-15
Well everything works now, I can boot into xp, ubuntu, and suse. Since I installed grub on both the 150GB linux drive and the xp drive, am I right in assuming that I should be able to have either drive as the first drive in the boot order and still get the grub menu?

As an aside, if I restore a partition from an image, that should not affect grub since it was installed to the MBR and not to a partition, right?

LMHmedchem

---

### Post by drs305 on 2012-08-16
Yes to both.

As to the first, you can leave Grub set up to boot from either drive. The other option would be to restore the Windows bootloader to the Windows drive. That way if you lose Grub you would still be able to boot into Windows by changing the BIOS boot order.

Of course, you can also do that IF Grub fails in the future as well, as long as you have a LiveCD. It just takes a few simple commands if you are interested. 

For now or future reference, you install an alternate bootloader called lilo. You run the following two commands, replacing X with the drive letter of the Windows (1000GB) drive. The system will complain about not being fully configured, but you only have to run these 2 commands and you should get your Windows bootloader back on that drive. Just change the BIOS boot order to boot the Windows drive first.

From either a running Ubuntu or LiveCD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sd[COLOR="Red"]X[/COLOR] mbr  # Replace X with the Windows drive letter sda, sdb, etc.

```

To put Grub back on from a running normal installation of Ubuntu:```

sudo grub-install /dev/sd[COLOR="Red"]X[/COLOR]  # Same letter as used above
```

---

### Post by LMHmedchem on 2012-08-20
Thanks, that's good to know. It would really be nice to have an easy way to get back into windows if there is a problem. The 150GB drive is a V-Raptor and is getting old. I'm sure it will go one of these days. Is it now considered best practice to install grub on the MBR of all drives? What about data drives that don't have an OS?

I have always been mystified about how complex setting up a multi boot system can get. In theory, it's straightforward, but I have had a number of issues that would have been a challenge for many users to take care of.

It seems like there should be a CD/usb app that you could run that would find all the OSs on your drives and set up all the necessary files (deleting old ones, etc), let you configure a menu, and all of that. I heard that Acronis has a boot manager that they sell with their backup software and have heard good things about it. I haven't checked to see if they sell it separately or not. I would think it would be in the best interest of the linux community to make it as easy as possible to set up dual/multi boot systems. Not a complaint really, I have just often been surprised that this has not been worked on more.

Thanks again, there are many days when I don't know what I would do without these forums.

**[color="#000090"]LMHmedchem[/color]**

---

