---
title: "How do I boot to a different partition?"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by Grafeit on 2012-02-09
Dell OptiPlex - 380 - 3 GB RAM - 2.93 GHz

I installed Ubuntu 11.10 on my Dell with Windows 7 and now I can't boot to the windows partition. I can't seem to figure how to specify what partition the computer boots to. I know how to get to the bios and tell the computer what order to boot in, and how to get to the boot manager to select a device, but it only shows the HDD, it doesn't show the various partitions.

---

### Post by lisati on 2012-02-09
When you boot your computer, you can get a menu by pressing a key. In newer releases of Ubuntu, it's usually by holding down the shift key while your system is booting.

---

### Post by Grafeit on 2012-02-09
> **lisati said:**
> When you boot your computer, you can get a menu by pressing a key. In newer releases of Ubuntu, it's usually by holding down the shift key while your system is booting.

I can get to the boot manager by holding esc. That just lets me select the device I want to boot to. I will hold down shift and see of that works when I get home. Thanks, hopefully that works!

---

### Post by oldfred on 2012-02-09
If it finds two systems to boot, it should be showing the menu.

Have you run this from the terminal and when you do does it show that it found Windows?
```

sudo update-grub
```

---

### Post by raja.genupula on 2012-02-09
now set boot time to 10 sec .
 small suggestion to you that install Grub Customizer to set your primary boot OS .It can handle with all grub operations . you can set your primary boot also . 

[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)

that will help you .

All the best .

---

### Post by Grafeit on 2012-02-11
Ok, so I tried a shift boo, that didn't work...I am having Internet troubles...I can't download updates, and I wasn't able to get that Grub Customizer...

Can I manually DL the Customizer to a flash drive anywhere? or Can I manually download all updates for Ubuntu 11.10 somewhere?

---

### Post by darkod on 2012-02-11
So, what is the situation right now actually? Does it boot ubuntu directly or not booting at all?

If the win7 system files are not discovered correctly, grub2 will not create a dual boot menu, which makes sense since it can't discover any other OS.

These days win7 usually comes with separate System Reserved partition with the boot files on it. If it gets deleted by mistake, it can't boot and can't be discovered by ubuntu.

Also, about the internet, did you try a wired connection? Most of wired connections work. Connect it temporary by cable, sort out the boot issue and then the internet connectivity.

If getting internet is impossible, you can download the boot info script from the link in my signature, move it with a usb stick to the broken system, run it there and post the results as explained in the link.

---

### Post by Grafeit on 2012-02-11
> **darkod said:**
> So, what is the situation right now actually? Does it boot ubuntu directly or not booting at all?

If the win7 system files are not discovered correctly, grub2 will not create a dual boot menu, which makes sense since it can't discover any other OS.

These days win7 usually comes with separate System Reserved partition with the boot files on it. If it gets deleted by mistake, it can't boot and can't be discovered by ubuntu.

Also, about the internet, did you try a wired connection? Most of wired connections work. Connect it temporary by cable, sort out the boot issue and then the internet connectivity.

If getting internet is impossible, you can download the boot info script from the link in my signature, move it with a usb stick to the broken system, run it there and post the results as explained in the link.

The current situation is:

The computer boots to Ubuntu by default, I can see my Windows Partition when I am browsing the home folder in Ubuntu. I can see all of my Windows System Files, I can see all of my Windows User Files and such too. I am wanting to boot to my Windows partition but I can't figure out how to do so.

For some reason when the computer boots, it goes to a blue dell screen that lets me select the bios or boot manager, then it goes to a black screen with a floating window that says the screen resolution is incorrect, then lastly it shows the Ubuntu login window. Those are the exact steps and order it works in.

The internet issue isn't in regards to my computer. My ISP is Comcast and currently either my Modem is fried or they just have crappy service. (I haven't called yet because I've been working a lot and dealing with school).

---

### Post by darkod on 2012-02-11
Have you tried lowering the resolution in ubuntu? Just to see if it works with some low, basic one.

The message about the resolution might be showing up at the same time as the boot menu, and since ubuntu is default OS by the time the screen comes on, you already have the login page shown up.

Does it say what is the resolution that it has problems with?

---

### Post by Grafeit on 2012-02-11
> **darkod said:**
> Have you tried lowering the resolution in ubuntu? Just to see if it works with some low, basic one.

The message about the resolution might be showing up at the same time as the boot menu, and since ubuntu is default OS by the time the screen comes on, you already have the login page shown up.

Does it say what is the resolution that it has problems with?

It does, it has a problem with 1980x800

I will change it to a lower res and see if that helps, although it does boot up to 1980x800, so I know it works with that res.

---

### Post by darkod on 2012-02-11
That might be fine for working (that's why the login page shows), but the grub2 boot menu might not support it.

There is a setting in /etc/default/grub for resolution just for the boot menu, but I have never touched those settings. If you change anything in that file, you need to run sudo update-grub to recreate a new grub.cfg file.

Google around for setting that option in the grub configuration, it might help.

---

### Post by Grafeit on 2012-02-15
Sorry for the delays...I have an update though...I made a tiny little mistake...

I booted up holding shift and when the window came up telling me that my resolution was wrong I used the arrow keys and managed to get to windows just fine without any problems, all of my stuff was still there.

So that's the good news, however...

While in Windows I went to the Disk Manage and deleted the Ubuntu Partition...turns out that deleting the primary partition is bad...So now when I boot, I don't even get the chance to hold down shift, it just says: "error: partition not found grub>" it seems to be a sort of command prompt but none of the MS DOS commands work, anyone have any suggestions?

p.s. I was thinking maybe if I reinstall Ubuntu then I would be able to boot back into Ubuntu and I would also get to manipulate the boot manager to get back into Windows. Would this work? Also, if so, how do I make the Windows partition the primary partition?

(Sorry for the delayed response, I spend a lot of time away from home so I can't always get back very quickly)

---

### Post by oldfred on 2012-02-15
The MBR has just a bit of code to start booting. It just loads enough to know where on the hard drive to find additional code to continue to boot. You should install the Windows boot loader before deleting the rest of grub that the grub boot loader wants to find in the Ubuntu partition.

Use a Windows repairCD or USB to run fixMBR (XP) or BootRec.exe /fixMBR (Vista/7).

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Grafeit on 2012-02-15
Looks like I am in trouble...I'm not paying $10 for a recovery CD...Yes, I am that cheap. :/

---

### Post by oldfred on 2012-02-15
If you have an Ubuntu liveCD. New versions may also have to install synaptic.
sudo apt-get install synaptic

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by Grafeit on 2012-02-15
> **oldfred said:**
> If you have an Ubuntu liveCD. New versions may also have to install synaptic.
sudo apt-get install synaptic

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.


Haha! That was very confusing for me. synaptic? lilo? Am I to reinstall Ubuntu first, then install Synaptic or Lilo? Then run commands?

---

### Post by oldfred on 2012-02-16
You do all of that from liveCD, but liveCD only has one Cd's worth of programs. So you have to download a couple of additional packages to make it work.

Some Linux repair liveCD come with Lilo already installed, so all you have to do is run the commands to install lilo's boot loader to the MBR, and then it will boot Windows (if Windows is bootable).

---

### Post by Grafeit on 2012-02-16
> **oldfred said:**
> You do all of that from liveCD, but liveCD only has one Cd's worth of programs. So you have to download a couple of additional packages to make it work.

Some Linux repair liveCD come with Lilo already installed, so all you have to do is run the commands to install lilo's boot loader to the MBR, and then it will boot Windows (if Windows is bootable).


So how do I make a live CD? I have a bootable DVD and a flash drive both with Ubuntu 11.10 on them, is that not the same as a live CD?

---

### Post by oldfred on 2012-02-16
Yes

---

### Post by YannBuntu on 2012-02-16
Hello
you can also try this:
boot into a Ubuntu session, run Boot-Repair, click "Advanced options", tick the ["Uncomment GRUB_GFXMODE" option]("https://help.ubuntu.com/community/Boot-Repair#Advanced_options") and apply.

 Indicate us the Boot-Info summary that will appear.
Then reboot and check if the GRUB menu appears.

---

### Post by Grafeit on 2012-02-17
> **YannBuntu said:**
> Hello
you can also try this:
boot into a Ubuntu session, run Boot-Repair, click "Advanced options", tick the ["Uncomment GRUB_GFXMODE" option]("https://help.ubuntu.com/community/Boot-Repair#Advanced_options") and apply.

 Indicate us the Boot-Info summary that will appear.
Then reboot and check if the GRUB menu appears.

I was able to reinstall Ubuntu and now I am back to square 1. The computer boots natively to Ubuntu, I can't see the grub boot manager menu, I can boot to windows by guessing how many times to press the down arrow key and then pressing return. (press the down arrow 4 times and return gets me to windows 7, 5 times gets me to windows 7 safe boot, 6 times gets me to windows recovery)

Is there a way to safely make the windows 7 partition the primary partition? I enjoy Ubuntu, I do, but I am kind of sick of this mess lol, I just want to go back to windows and stop trying to guess when I should press enter. I'd be ok if I was seeing the windows boot manager, but this grub resolution stuff sucks! (IMO)

---

### Post by darkod on 2012-02-17
Do you want to keep ubuntu or you want to have windows as only OS?

---

### Post by Grafeit on 2012-02-17
> **darkod said:**
> Do you want to keep ubuntu or you want to have windows as only OS?

At this point, I'd rather just go back to Windows as my primary and only OS. Keeping in mind that I do not have a recovery CD. I don't want to lose anything on the windows partition. (I won't be able to reinstall windows either)

---

### Post by darkod on 2012-02-17
If you want to make windows boot directly, boot ubuntu and in terminal do:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

There will be a warning about lilo configuration, but ignore it and continue. You will be only using small part of it anyway.

After you reboot your windows should boot directly as if ubuntu is not there. You can decide whether to delete the ubuntu partitions and use that space for ntfs partition so you can use it in windows.

If you decide, you can keep both OSs, and we can configure grub to boot windows by default, and ubuntu when you decide. That should help you with the problem of not showing the menu at boot, if you use windows more often.

Up to you...

---

### Post by Grafeit on 2012-02-17
> **darkod said:**
> If you want to make windows boot directly, boot ubuntu and in terminal do:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

There will be a warning about lilo configuration, but ignore it and continue. You will be only using small part of it anyway.

After you reboot your windows should boot directly as if ubuntu is not there. You can decide whether to delete the ubuntu partitions and use that space for ntfs partition so you can use it in windows.

If you decide, you can keep both OSs, and we can configure grub to boot windows by default, and ubuntu when you decide. That should help you with the problem of not showing the menu at boot, if you use windows more often.

Up to you...

So if I run that command, then I should boot to windows from then on? It will use the MS Bootloader? If so, I can just use the MS Bootloader to choose to boot to Ubuntu if I want, right?

---

### Post by darkod on 2012-02-18
No, windows bootloader doesn't boot linux by default. It can't even see it.

If you run the lilo mbr install, it will just install a generic mbr which passes the boot to the partition that has the boot flag, that is the windows partition. And the windows bootloader will boot windows directly, without any boot menu.

If you still want to keep both, we can do some tweaks of grub so that you have windows as default OS to boot, and ubuntu if you select it. But the selection can be much easier than what you are doing now since your grub boot menu is not showing.

On another note, did you ever try to set a smaller resolution for gtub? You never replied to that, you simply deleted the ubuntu partition.

---

### Post by Grafeit on 2012-02-18
> **darkod said:**
> No, windows bootloader doesn't boot linux by default. It can't even see it.

If you run the lilo mbr install, it will just install a generic mbr which passes the boot to the partition that has the boot flag, that is the windows partition. And the windows bootloader will boot windows directly, without any boot menu.

If you still want to keep both, we can do some tweaks of grub so that you have windows as default OS to boot, and ubuntu if you select it. But the selection can be much easier than what you are doing now since your grub boot menu is not showing.

On another note, did you ever try to set a smaller resolution for gtub? You never replied to that, you simply deleted the ubuntu partition.

Yea, sorry, I tried to set a smaller res, but I don't know how to save the changes I made. I was following a walkthrough that told me how to change the settings, it just didn't tell me how to save my changes.So I attempted to change them, I just didn't have a whole lot of luck...

I'm fine to boot to windows only, if that is going to be easier than thats what I'll do.

---

### Post by darkod on 2012-02-18
Saving the changes for the new grub2 is very easy.

First step: You open the /etc/default/grub file and change the settings you want to change. You save and close that file.

Second step: For the changes to be applied to the grub.cfg configuration file that grub2 uses, you just need to open terminal and run:
sudo update-grub

That will update the grub.cfg and it will start using the new config until you decide to make more changes, etc.

---

### Post by Grafeit on 2012-02-18
> **darkod said:**
> Saving the changes for the new grub2 is very easy.

First step: You open the /etc/default/grub file and change the settings you want to change. You save and close that file.

Second step: For the changes to be applied to the grub.cfg configuration file that grub2 uses, you just need to open terminal and run:
sudo update-grub

That will update the grub.cfg and it will start using the new config until you decide to make more changes, etc.

I was editing Grub through Terminal. Basically I ran a command that showed me all of the Grub defaults, I changed a value, then there was no "save" option and I couldn't file save either...I closed the Terminal and run the sudo update, but that didn't help.

---

### Post by darkod on 2012-02-18
It's easier to edit with the gedit editor. To open the file in gedit, in terminal type:

gksu gedit /etc/default/grub

In the toolbar of gedit you have the standard Save icon, looking like floppy disk. When it opens, it will ask you for your password, same like it does in terminal when using sudo in front of a command. The gksu is the same but it is used for programs that have a GUI, like gedit.

---

