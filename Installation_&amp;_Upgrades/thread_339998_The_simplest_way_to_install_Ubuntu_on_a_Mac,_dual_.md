---
title: "The simplest way to install Ubuntu on a Mac, dual or triple boot."
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by Didden on 2007-01-16
This is a new technique, born out of frustration with existing techniques I found posted around the internet, and a technique I “stumbled” upon, through trial and error after being inspired by William Sowerbutts, who considered it might be possible.

I believe that it is incredibly simple in-comparison to existing techniques because it does not require any work in a shell to get the boot working and only takes another 5 minutes to implement.

My sincere thanks go to **Kebes** and **Rccharles** on the Ubuntu forums for their help along the way and their patient explanations and creativity in trying to find solutions to help me.

[SIZE="4"]The principle behind this new technique:[/SIZE]

Installing Ubuntu on any Intel Mac is problematic because Apple Macintosh’s use EFI BIOS. This isn’t a problem for Linux normally because it recognizes EFI BIOS, but is problematic because Ubuntu wasn’t designed with Mac’s architecture in mind.

As a result, Ubuntu’s normal Live CD install fails because it cannot install Grub.

This isn’t so bad, because there are several workarounds, but all the techniques I found require some knowledge of Linux and are quite technical.

This technique installs Ubuntu slightly differently, using the Ubuntu DVD’s “Install in Text Mode” because it offers more flexibility than the normal installer and bypasses a problem in the normal installer when used on Macs.

Lastly, it requires that the installer is run twice to get around the boot loader and partition problem. Don’t worry, the second install is not a complete re-install, it is done to allow the successful installation of Lilo boot loader over the first install successfully.

The real bonus is that it requires no shell configuration to make it work, although all Mac’s require some configuration of Linux once installed.

[SIZE="4"]Who is this guide for?[/SIZE]

Intel Macintosh Owners.

I created this install technique on a Mac Mini, Duo Core 2 with 512mb RAM. There are slight differences between different Mac Mini’s and of course the other Apple Intel platforms, although this technique should work on any Intel Mac.

[SIZE="4"]Double or triple boot?[/SIZE]

Whether you want to double or triple boot your Macintosh into OS X, Ubuntu or Windows is up to you.

Know that this install technique is identical regardless. The only difference will be how many partitions you create at the start of the process.

You can choose to use the simplified Apple Boot Camp program to create two partitions using the “drag and drop” interface in the Boot Camp Assistant and instead of installing Windows on the second partition, install Ubuntu.

Download Boot Camp at:

[www.apple.com/bootcamp](www.apple.com/bootcamp)

To create three partitions for a “triple boot” you have to use the DiskUtil command in OS X’s terminal, although this is not particularly difficult and is only one carefully written line. 
Further details on both of these techniques can be found at the following sites:

[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)

[http://www.mactel-linux.org/wiki/HOWTO](http://www.mactel-linux.org/wiki/HOWTO)

I went with a triple boot because I wanted to run Windows natively. If you do go for a triple boot, you do not have to install Windows first; the choice is yours, because rEFIt gives you the choice to boot from a Windows install CD.

If you do install Windows after Ubuntu, Windows install will moan about disabling a boot flag on the MBR, although this has made no difference to any of my final operating systems, and they all boot as expected.

[SIZE="4"]What you will need:[/SIZE]

An Intel Mac

OS X Updated to at least 10.4.7 (Current version is 10.4.8 at time of writing).

Ubuntu 6.10 DVD (Both earlier versions and newer versions of Ubuntu may work just as well using this technique.)

Alternatively you may also install Ubuntu Server CD using this technique.

The Ubuntu CD-ROM cannot perform this technique, as it does not offer the “Install in Text Mode” option on the CD menu. I recommend finding the DVD online and living with the extra download time. Took me about 2 hours to download it.

[SIZE="4"]Disclaimer[/SIZE]

Macintoshes come with OS X already installed. PLEASE ENSURE YOU BACKUP ALL FILES BEFORE PROCEEDING.

Be prepared that this process may fail or that you may make mistakes that result in it’s failure.

Any mistakes could mean you have to start a clean fresh OS X install and may lose files as a result. Anything that involves partitioning your drives naturally requires great care and thought on your part.

[SIZE="4"]STAGE 1[/SIZE]

The rest of this guide assumes you’ve made your choice when it comes to double or triple booting and that you have already created the separate partitions using the information on the links I provided above and backed up your data.

The following technique is identical whether you have opted for a Dual or Triple boot.

After you’ve partitioned the drives, you need to reboot into OS X again.

Download rEFIt at:

[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

This is a simple, but effective boot tool that you need. Apple does not provide the ability to see Linux drives at startup. rEFIt provides this.

Run the rEFIt installer and please ensure that you customize the options so that you include drivers for ext3 file format (This is the third option and is normally off, tick it on!).
If you don’t install these extra drivers, none of the following guide will work, because we’re using ext3 to format the Ubuntu partition, and without these extra drivers, rEFIt can’t see this drive.

After you’ve installed rEFIt insert the Ubuntu DVD.

Then reboot the system.

[COLOR="YellowGreen"]Tip: Using OS X’s built in ability to choose a startup drive actually disables rEFIt and you will need to reinstall it if you ever do this.[/COLOR]

[SIZE="4"]STAGE 2[/SIZE]

When you reboot, you are presented with the rEFIt menu. You should see an Apple for OS X and a Penguin CD symbol for the Ubuntu DVD. Select the Penguin before rEFIt auto boots into OS X.

From the Ubuntu DVD menu select “Install in Text Mode” do not run the installer from the Live DVD startup (The first option).

Step through the setup that appears. It’s pretty straightforward, but it is very important that the settings you choose, such as your computers name, your login and password are noted down.

The reason for this is that we actually need to run the installer twice, and you have to enter the same settings the second time around to ensure consistency.

[COLOR="YellowGreen"]Tip: The first screens on the text install ask you about the language you’d like to use, and then it offers to Auto Detect the keyboard - I skipped this, as I found that it is easier to select it from the menu manually.[/COLOR]

Setup networking.

[COLOR="YellowGreen"]Tip: I found that on occasion, Auto DHCP would fail, just step back and try again, and it works a second time normally.[/COLOR]

Then you get to choose the Disk / Partition to install Ubuntu on.

There are a few options displayed here, but you must select “Manually edit partition table” this is very important.

Whether you opted for a, dual and triple boot, your Linux Partition will be sda3. Enter this partition to select the configuration options for the install.

Set the “Use as” to Ext3 Journaling file system

Format the partition set to: “Yes, format it”

Set the “Mount point” to be /

Change the “Bootable flag” to On by selecting it and pressing enter

Do not resize the partition.

Exit changes, by going to “Done Setting up the Partition”. The installer then asks if this is all OK, confirm that it is.

Then a warning comes up about having no swap file. Select No, do not step back to set one up. It is not essential for the installer to work and has be added after the install has been successful from within Ubuntu itself. The reason for this is that the installer will always attempt to format a swap partition whatever you set it as, and this breaks the GPT and MBR sync.

At this point, you are asked for the Time Zone, choose and select yes for the following UTC option.

Then enter your full name, your login and finally your password. Again, note these down for next time, and enter them identically on the second install.

The system will then go ahead and install the contents of the DVD. Typically takes about 15 minutes or so.

Sadly, at the end of this process you will get an error installing Grub. Don’t panic, this is normal for Intel Mac’s. They can’t handle Grub on the install.

[COLOR="Red"]Note: If you have already installed Windows, you will also get an option to install Grub onto Windows the MBR. I suggest that you do not do this, because firstly, Grub will fail anyway, and secondly because rEFIt allows you to make a choice instead and their is no need for Grub on a Mac with rEFIt. If you have to enter a setting type /dev/sda3 for the location, this will fail with no side affects. Do not let Grub install onto /dev/sda - the first partition.[/COLOR]

Because of this error, you can “Go Back or Continue”, either option provides you with a screen with several different options, each option is basically a stage in the installation.

It’s very important that you choose to end the installer by choosing “Finish install”.

Despite the problem with Grub, this finishes the install properly and reboots elegantly.

Do **not** choose the abort the install or any of the other bootloader options including LILO or GRUB again at this stage (Both will repeatedly fail).

You will see a  warning about the lack of boot loader, which can be ignored. It pushes out the DVD. Push this back into the drive as we still need it and then hit enter. The installer will then automatically reset the computer.

At the end of stage 2, what you have done is format the partition correctly, and installed Ubuntu onto it. Sadly, without a boot loader, you can’t boot it, but thats what we fix in the next stage.

[SIZE="4"]STAGE 3[/SIZE]

When the rEFIt menu appears, select the Partitioning Tool using the arrow keys.
You will get a warning that rEFIt want’s to fix the GPT and MBR records. Press Y to agree.
This is actually quite important. When you format the Linux Drive you effectively reset the the GPT and MBR records on the Linux partition, because Ubuntu isn’t really designed to recognize the Mac’s architecture, it doesn’t do this properly. rEFIt fixes the partition for the Mac to see the new Linux partition properly.

rEFIt returns you to the menu. Instead of rebooting at this point, I actually suggest you actually power down your machine completely for a few seconds and then turn it back on. I found problems if I just rebooted. Sometimes when I rebooted, I would get the rEFIt screen, but when I selected an option (Like the install DVD), the screen went blank. As a result, I was forced to manually power down again, when I turned the mac back on, everything was fine. By ignoring the reboot option on rEFIt and just powering down in the first place you shouldn’t get blank screens at all.

When rEFIt returns, you can now see an extra drive - your Linux drive!

At this point however, the drive has no boot loader (because GRUB failed), so booting from it will fail.

Thats why we still need the Ubuntu DVD installer again. We will repeat the install, but this time with a few changes to make sure that the Boot loader will install.

Choose the “Install in Text Mode” from the DVD menu again.

Go through the same settings as the first time, setting up the keyboard, ensuring to use the same settings you applied the first time are repeated.

You will have to go through quite a few steps, including networking. Eventually you are asked to choose a partition again.

As before, choose to manually configure the partitions.

When you see the different partitions, go into sda3 again.

Because on the first install we formatted sda3, we specifically don’t want to reformat it this time around - formatting it is what breaks it on a Mac, and what rEFIt fixes!

This is the reason for choosing the Text Mode Installer, as it allows you to skip reformatting the drive and essentially allows you to “overwrite” the existing install.

This time around however, the ONLY option we need to change on sda3 is the “Mount Point”. This needs to be set back to /

Again, this little option is quite important, because all the files you installed last time are already sitting at this / mount point.

When you exit and confirm the changes, the installer actually tells you that nothing is going to be changed (Even though you set the mount point to /). This is good news!

Yet again, you get the warning about the swap file, select No to continue, effectively ignoring it.

The next option you have is the time zone. This is actually our first chance to “break out” of the normal install steps and manually pick an option which is exactly what we want to do this time. You do this by selecting “go back”.

Instead of going back to the partition menu, you actually get the complete menu again.
We need to do this, because we don’t actually want to reinstall everything, we want to stop the normal install process and skip to installing the boot loader, the time zone is the first chance we get to do this.

Select the “Install the LILO Boot loader”

You get a warning about it being an “unclean target”, which is actually what we want. Hit yes!

The installer will now install the “core” linux files again, which is no biggie, and in the end, you get an option to put LILO on the partition of your choice.

Because our linux is on sda3, choose to install LILO onto “/dev/sda3: new Ubuntu partition.”

Choose to make this partition active - yes!

LILO then completes the configuration - LILO is now installed alongside your existing Ubuntu install and the DVD pops out and your computer reboots. You’re done.

You can quit the installer and reboot. Again though, I suggest you power down your mac for a few seconds when you get to the rEFIt menu.

Turning your Mac back on, rEFIt will show the new Linux hard drive, choosing it, boots you into your new OS.


[SIZE="4"]What’s next?[/SIZE]

Well you now have Ubuntu installed and booting, I chose to install Windows next, then used Ubuntu to divide the Windows Fat 32 partition up for a swap file from the Live DVD/CD. This went smoothly, but has drawbacks you need to consider. Then you have to configure Ubuntu for your environment (Adding drivers etc). This technique is discussed here:

[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)

Alternatively, you can setup a swap file on your existing sda3 drive.

Read the guides on the links I used earlier, which detail how to do this, and setup Ubuntu for the Mac environment.

[SIZE="4"]What if it failed?[/SIZE]

The only reason I found this technique didn’t work, was if you in some way alter the sda3 partition or you use a swap partition on the second install. Changing the mount point to / is the only acceptable change the second time around.

Just remember, any other alteration to your partition within the installer breaks the GPT and MBR tables which is fixed with the rEFIt partition tool.

Thats the reason why the Live CD install fails, and why I recommend the DVD Text Install instead.

Any comments or feedback welcome.

- Stephen :cool:

---

