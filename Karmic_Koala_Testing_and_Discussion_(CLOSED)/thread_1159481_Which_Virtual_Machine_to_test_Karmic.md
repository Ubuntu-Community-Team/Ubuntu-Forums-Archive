---
title: "Which Virtual Machine to test Karmic?"
date: 2009-05-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by QwUo173Hy on 2009-05-14
I want to start testing alpha 1 but I don't have a machine to install on at the moment. Which virtual machine can I get up and running fastest? I've seen QEmu and VirtualBox but this note put me off VirtualBox:
> The virtualbox-ose-source package is also required in order to compile the kernel modules needed for virtualbox-ose.

---

### Post by fifth on 2009-05-14
> **jarlath said:**
> I want to start testing alpha 1 but I don't have a machine to install on at the moment. Which virtual machine can I get up and running fastest? I've seen QEmu and VirtualBox but this note put me off VirtualBox:

Don't let the compiling put you off. Its a pretty automatic procedure when you install VirtualBox from the repo's. You dont have to worry about compiling anything yourself, it very much like installing anything else.

---

### Post by QwUo173Hy on 2009-05-14
Ah, thanks fifth. I'm installing virtualbox now. I was dreading a night of fuddling around with command-line argument syntax.

I have buddies in Glasgow by the way, I see you're near there. 

Thanks again,
Jarlath

---

### Post by Starks on 2009-05-14
I tend to discourage Virtualbox OSE. Use the regular version available at virtualbox.org. It has more features, namely USB support.

---

### Post by Gina on 2009-05-15
Thanks for that info - it may save me a lot of time.  :)

I'm not running Karmic in VB (I have separate testing machines) but want to set VB up to run my weather station software which needs Windows and USB - I've failed to find suitable Linux software.

---

### Post by cszikszoy on 2009-05-15
Maybe a little off topic, but Virtualbox + USB works exceptionally well.  I highly recommend it.  I have yet to try karmic in a VM, maybe that's a project for this weekend!

---

### Post by PGHammer on 2009-05-15
i'm currently running Karmic in a VM (VirtualBox inside Windows 7).  While the video works fine, the sound does not (even with the Guest Additions installed); but this *is* Alpha 1, so there are bound to be bugs (no idea yet whether this is a VB or 'Buntu Bug at this point)....

---

### Post by jerrylamos on 2009-05-15
Dual or triple or even quad boot works for me most of the time.  An early Fiesty did wipe out both hard drives on one of my test machines, however that hasn't repeated.  

Some people share the home directory.  That fouls up for me if sharing between Ubuntu levels.  I have a separate partition with all my common stuff and just go thru Places to access the stuff I want to save.

If there's a bootable desktop CD, then there's a way to make a 1 mb partition and boot it "CD" Live however karmic only has running alternate and server images now.

Jerry

---

### Post by QwUo173Hy on 2009-05-15
Well as far as running Karmic on VB - it's a no go for me. It installs fine until after partitioning. Then it gives an error saying that the step: select and install software failed.

I tried backing up to the 'configure the package manager' step - but that failed too. Pity, because the bootloader can't even be installed now.

If any of you do run Alpha1 successfully in a VM, please share the light!

---

### Post by Gina on 2009-05-15
I might give it a try. I'll report back if I do.  I'll be using VirtualBox.

---

### Post by miwaypet on 2009-05-15
I am running karmic in VB. I had zero problems with it until the latest upgrades and updates. Video is chopping, again. And no sound. As for install, I started with jaunty cd and then changed the sources to karmic in /etc/apt/sources.list, except the line for the cd. Just left it commented out. So far, I still cannot open some gui front ends like software sources. But I work around it. Just wish sound would work again.

---

### Post by QwUo173Hy on 2009-05-15
Thanks Gina, I'm surprised that miwaypet got it working - wonder what the problem could be.

Miwaypet - I have questions for you :)
Did you use all the default installation options? (ext3 for example)
How big was your virtual disk?
Was it dynamic or static in size?

Emm.. that's all I can think of.

---

### Post by Gina on 2009-05-15
Well, here I am in Firefox running in KK in VB hosted by Jaunty 9.04 :) :)

Everything fine except that I need to sort out the VB window size - I'm currently in 800x600 which is a bit small in a 1680x1050 screen :lol: But it's usable :)

The installation used the downloaded Alternate AMD64 ISO directly so was a lot faster at reading files than the usual install even from USB stick.  Everything went entirely according to plan.

I haven't run the updates yet - so I'm at the Alpha 1 stage ATM and only tried Firefox so far but it's looking good :)

For reference :- 
Processor - Athlon 64 X2 Dual Core 4200 +
Mobo - ECS 6100SM-M2
Graphics - On board nvidia GeForce 6100 nForce 405
RAM - 1GB DDR2 667MHz

---

### Post by Gina on 2009-05-15
Just added over a hundred updates and still OK :)

---

### Post by miwaypet on 2009-05-15
I used the default installation. I make my disk to be 10GB. I give it 28mb for video. I use ext 3. I use ext 4 when I put Karmic on metal. I don't used a burned disk. I install directly from the downloaded iso. Disk is dynamic. Network is bridged. Make sure you are checked off as a member of vboxusers. Create a usbusers group and make your self a member (not root).Add the usbfs to your /etc/fstab.

---

### Post by PGHammer on 2009-05-15
> **miwaypet said:**
> I used the default installation. I make my disk to be 10GB. I give it 28mb for video. I use ext 3. I use ext 4 when I put Karmic on metal. I don't used a burned disk. I install directly from the downloaded iso. Disk is dynamic. Network is bridged. Make sure you are checked off as a member of vboxusers. Create a usbusers group and make your self a member (not root).Add the usbfs to your /etc/fstab.

I've created a second Karmic test VM (still using VB on Windows 7 RC); this one for Kubuntu.  I've gone with a modified default VM (384 MB system RAM, 64 MB accelerated video, 8 GB dynamic HD (formatted ext4), AMD PCFast III networking (NAT), AC97 onboard sound).

I found out what the problem was with the first Karmic VM; I used the wrong ISO image (in short, it was an IBK error, not a bug).  I had downloaded/installed from the *server* image of Karmic (which does not install X or audio support by design/default), as opposed to the desktop image (GNOME).  I did install GNOME; however, there is no audio support (not typically needed for a server).  I will create a third Karmic VM (GNOME) over the weekend; I'll leave the first one up as a debug VM (and as a reminder that I don't know everything).

---

### Post by whitefort on 2009-05-16
I haven't noticed any problems yet with VirtualBox OSE and Koala - it installed without any hassle, and has been running just fine, even with all the updates.  I can't get resolution better than 800X600, but I think that's just a driver thing, and I seem to remember that it always happens on this machine when I install a new Ubuntu.

---

### Post by tacantara on 2009-05-16
I recently installed Karmic in VirtualBox (guest additions pending). I'm not sure if I didn't answer a prompt correctly during the Karmic setup or if something else went wrong, but I can't enable Wi-Fi. When I look at the Network Manager, the Wi-Fi options are grayed out. Has anyone else experienced this, and is this something that can be fixed?

---

### Post by miwaypet on 2009-05-16
Close down the machine. Open the setting tab. Open networking. Make sure that it is NAT or Bridged. If Bridged, select wlan0 from the drop down list.

---

### Post by vishalrao on 2009-05-16
Folks, how would I go about enabling better-than-800x600 resolution under virt-viewer/virt-manager/kvm on Jaunty? I'm running Karmic in KVM/virt under Jaunty :) Im able to get it working in VirtualBox after installing the guest additions...but cant figure out KVM...

edit: posted too soon, vbox guest additions does not install with "unknown xserver version"...

---

### Post by vishalrao on 2009-05-16
OK managed to get better resolution with VB. I'd earlier tried to install guest additions via the VB menu which downloads an ISO but the ISO doesnt work due to unknown X version.

So the following steps worked for me, Im running the very Kool Kubuntu Karmic Koala with Kde, so if you're running GNOME replace kdm with gdm:

Inside the karmic VM in a terminal do:

```
sudo /etc/init.d/kdm stop
```

Login to shell then you need to install the following 2 packages in order and separately, they didn't seem to work if I tried them together:

```
sudo apt-get install virtualbox-ose-guest-utils
```

Then when it completes, hopefully without errors, then do:

```
sudo apt-get install virtualbox-ose-guest-source
```

Then to restart X and get back KDE in higher screen size:

```
sudo /etc/init.d/kdm start
```

---

### Post by Gina on 2009-05-16
I can't get USB working in VB.  VB recognises the devices but the guest OS doesn't see them.  KB, mouse and network are OK.

Any ideas, please?  Am I missing something simple?

---

### Post by vishalrao on 2009-05-16
Not sure but what if you add yourself to the vboxusers group and also try the above "guest" package installation steps?

---

### Post by miwaypet on 2009-05-16
@Gina
Shutdown the VBmachine. Go into settings. Select USB. Insert, one at a time the usb sticks you want the machine to see. Forgot, make sure the machine you want to 'see' the usb sticks is selected. 

When you insert the usb stick, let Ubuntu see it, and open the sticks files. Close the file window. Select to add a usb stick. Choose the stick from the list. It appears in the USB box as added.

Caution, do not add keyboard, mouse, or cordless mouse. Client will see them as usb sticks instead of what they are, and they will not work.

In windows, same thing. 

Now start machine. When you finish start up, go and insert your stick, and choose it from Devices drop down list under USB.

---

### Post by QwUo173Hy on 2009-05-16
> **miwaypet said:**
> I used the default installation. I make my disk to be 10GB. I give it 28mb for video. I use ext 3. I use ext 4 when I put Karmic on metal. I don't used a burned disk. I install directly from the downloaded iso. Disk is dynamic. Network is bridged. Make sure you are checked off as a member of vboxusers. Create a usbusers group and make your self a member (not root).Add the usbfs to your /etc/fstab.

Thanks miwaypet. I'm using the alternative download, ext3 and booting from the downloaded iso, just like you. I've only just checked off myself as a member of vboxusers and created usbusers. Thanks for that info, I didn't know I had to do that.

The only step I haven't taken is adding usbfs to /etc/fstab. Is that really necessary? I don't know how to do it but when I searched the forums it was adviced not to do it.

---

### Post by miwaypet on 2009-05-16
Go [here]("http://writingoutloudblog.blogspot.com/2009/05/virtualbox-in-ubuntu-904.html").

Read through the instructions. I include pics with my tutorials.

Let me know how you get on.

---

### Post by Gina on 2009-05-17
Thank you ***miwaypet***, that looks very helpful :) :)  I'll have another go at it - bit more complicated that it first looks :lol:

---

### Post by vishalrao on 2009-05-17
well, 4.2.85 packages seem to be in much better shape now :) no air theme though, had to get it from svn, much better than the black oxygen theme... even some bare desktop effects work under virtualbox with xrender option! slide effect is decent. looking forward to a more stable feature filled kde 4.3 when karmic ships...

---

### Post by tacantara on 2009-05-17
I've been trying to install the Guest Additions in VirtualBox (not the OSE version, the new version from the website), but when I select the .iso image from the CD list, and click on >Devices >Install Guest Additions, nothing happens.  Has anyone else experienced this, and is there a solution to that problem?

---

### Post by miwaypet on 2009-05-17
Why not from **Devices** in the menu above your machine. It is the last entry in the drop down list. Select it, and  the cd shows on the desktop in a Linux machine, or the selection list appears in the Windows client.

Are you installing to Linux, or Windows?

---

### Post by tacantara on 2009-05-17
I am installing the Alpha version of Karmic on a VirtualBox.  The host OS is Kubuntu Jaunty.  I also have an XP machine in the VirtualBox.  When I mount the ISO image, the Device Notifier applet recognizes the image.  However, when I click on the Instal Guest Image on the Devices menu above the machine, nothing happens.  I've tried click and wait, up to five minutes of waiting, but nothing happens.  I've even installed all available updates for the Alpha, and still nothing.  From the other posts in this thread, it appears that installing Guest Additions hasn't been a problem, and that's why I'm particularly baffled on this.  Could this have anything to do with installing a Linux guest on a Linux host, as I'm attempting to do here?

---

### Post by tacantara on 2009-05-17
Looks like I figured out the problem with the Guest Additions.  I had to enable root user privileges in order to make it work.  I now have the full range of VirtualBox "goodies" available to me (larger screen size, mouse integration, et.al.).

---

### Post by QwUo173Hy on 2009-05-18
miwaypet, thank you. I noticed that my disk was set to 2GB - embarassing! Perhaps this was the problem all along.

Karmic is running fine. I haven't tried audio but obviously at this early stage there's nothing obviously different from Jaunty.

It's nice to be on the testing bandwagon so early in a release, thanks again to all.

---

### Post by Gina on 2009-05-18
Followed miwaypet's tutorial and sucessfully set up VB on both my AMD64 and P4 in Jaunty and installed Windows XP.  Everything working in the AMD including USB connection to my weather station - it's running the Cumulus Windows software and reading data and uploading now.  The P4 I'm still setting up antivirus etc.

One little point on your tutorial miwaypet, I think you are adding the repository for VB twice - once by adding to sources.list file directly and then by adding the URL in the Software Sources dialog in the Third Party section.  The second time I used the tutorial I skipped the direct editing of sources.list.  Seemed OK - maybe I'm missing something?

---

### Post by wsonar on 2009-05-18
I really like the sun virtual BOX

---

### Post by miwaypet on 2009-05-18
@Gina
I see what your talking about. I put the line in bold as an indicator of where to look on the download page. I did not relize it would cause confusion, and I apologize.

I only add the repo through the software sources gui, not the list. I feel that directing people that are not yet familiar with editing the list might cause some problems. Again i am sorry for the confusion, and I will rectify the situation, post haste.

I am glad your install is working, and I hope you will tune in from time to time, as I will continue to try and place useful tutorials as regularly as possible.

---

### Post by Gina on 2009-05-19
No need to apologise :) I'm glad I could help improve your tutorial :)  Yes, I'll certainly tune in and report back.

Thanks again for your tutorial - very helpful indeed :) :)

---

### Post by iamhugeinjapan on 2009-05-19
I'm so far having no luck booting the Alpha 1 iso on my Mac.

Under VMWare Fusion it locks up with a black screen after choosing to Install Ubuntu.

Under Virtualbox 2.2.2 it hard rebooted my Mac when I powered on the machine to start installing.

---

### Post by jerrylamos on 2009-05-20
Tried rsync of today's daily build .iso which at 715 mb is a bit large yet.  I haven't seen that the daily builds would boot, and it didn't, no surprise.  It got to "initramfs" and stopped.

I make a 1 gb Ext3 partition, in this case sda7 which is (hd0,6) to Grub, on the hard drive and then load the .iso onto it to run as a "live" image using an executable file such as:

mkdir /tmp/install_cd
sudo mount karmic-desktop-i386.iso -o loop /tmp/install_cd
sudo mkdir /mnt/installer
sudo mount /dev/sda7 /mnt/installer
sudo cp -rv /tmp/install_cd/* /mnt/installer
sudo cp -rv /tmp/install_cd/.disk /mnt/installer
sudo umount /tmp/install_cd

Then make an entry into menu.lst:

title           karmic Live7
root            (hd0,6)
kernel          /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=524288 rw quiet splash 
initrd          /casper/initrd.gz

# Adjust ramdisk_size to something reasonable for your memory.  I have run in 384K and I suppose 256K might work (maybe).

# As usual precautions apply when making partition table changes & menu.lst changes, an accidental boo-boo and you had better have backup of anything useful.

That setup is just a "CD Live".  Recovery mode boot replace the "quiet splash" with "single", add "persistent" if there is another suitable formatted partition labelled "casper-rw".

The setup runs fairly quickly to do an rsync, which is easy on internet traffic, run live install, and boot to see if it works.  Not today.

It's also handy for playing with different releases such as hardy, intrepid, jaunty, ... for checking xorg video problems and gtkperf performance results without having to do an install and without having to make CD's, just the .iso's will do.

Some releases ago it was possible to actually do an install from this 1 gb partition but no more.  Ubiquity gets upset about running from one  partition on a hard drive and formatting another, no reason I can think of.  Gparted has no such trouble.

Oh, by the way, this setup runs "full speed" since there is no virtual mode involved.  I think it will use a swap file on the hard drive as well if desired.

Cheers, Jerry

---

