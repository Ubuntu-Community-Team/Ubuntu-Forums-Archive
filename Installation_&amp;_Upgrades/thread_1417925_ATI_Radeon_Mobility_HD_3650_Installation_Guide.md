---
title: "ATI Radeon Mobility HD 3650 Installation Guide"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by honkeypatrolfbi on 2010-02-27
Hey everyone. I bought a Toshiba Satellite A355-S6935 with some help from my family on Christmas. This laptop uses the ATI Mobility Radeon HD 3650 graphics card which causes the black screen from the Ubuntu LiveCD. After about a month of frustration, running VESA (low-graphics) I finally figured out how to successfully install Ubuntu 9.10 with the proper graphics configuration. There are many threads that are not very newbie-friendly and took me a long time to figure out how to do this. With that said, I am brand new to Linux and I now LOVE it. Gnome+Compiz+GLX-Dock is my personal favorite environment. If you prefer KDE, check out Kubuntu. Mint also looks pretty decent. There are many clips on youtube that show different linux installations.

Here are the proper steps to properly install it on a 64-bit (3+ GB RAM) laptop with Mobility HD 3650 graphics card.

1) Download a 64-bit version of Ubuntu Desktop. I had the latest version &#8220;Karmic Koala&#8221; or 9.10. Go to [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download) and select the Alternative download options. Chose the Ubuntu 9.10 installer with 64-bit architecture. Save the ISO to a place you will remember. The file is almost 700 MB so it could take a while on slower connections.

2) Burn the ISO to a CD-R. Ubuntu's installer is a LiveCD which means that you can boot the CD up from the BIOS. Make sure you burn the ISO without opening it and playing with the files or you may risk the ISO to be nonbootable. You can use Ubuntu without installing it on your hard drive. Pretty cool. For newer laptops, which you most likely have, look for the Boot Selection function during the startup with your computer. It should show up as soon as you turn it on. Mine happens to be F12. Hit that key and select your CD/DVD drive to boot from it.--If you can't find the Boot Selection, go into the Setup (usually F2, delete, or F10) and look for boot options. Set the CD-ROM to be the first bootable option, save, and restart.

3) Okay here's the important part. Apparently this particular graphics card fails to get properly allocated into the Kernel. So here's what you've got to do. Add pci=use_crs to the boot options. Do this by selecting your language with the arrow keys and enter. Then hit F6 and it will show you a menu. Close the menu out with Escape. Then type pci=use_crs directly after quiet splash --. It should look like &#8220;.seed boot=casper initrd=/casper/initrd.lz quiet splash -&#8211; pci=use_crs&#8221;. Hit enter to enter the Ubuntu environment. This should bypass the black screen problem with those having issues.

4) Okay you should be in the Ubuntu environment at this point in your monitor&#8217;s native display resolution (mine happens to be widescreen 1366x768 16:9). Double click the Install Ubuntu 9.10 icon and install away! For those with Windows, dual-booting is fine but Grub loader will run before Windows which some people don&#8217;t like. I dual-booted but set up the advanced boot option to install grub on a USB flash drive so I didn&#8217;t mess at all with my Windows boot environment. N00bz/Newbies/whatever: Grub is a bootloader which is a menu of operating systems and memory tests etc. which loads up directly after the bios.

5) Okay once the install is complete it will tell you to pop out the CD and restart. Now make sure you boot from the hard drive you installed onto (Reconfigure your Setup in BIOS to boot from IDE/Hard Drive if you changed the setup). Grub's main menu should appear. Make sure your selection is over Ubuntu 9.10 (NOT RECOVERY) Hit E to edit the boot options. Now scroll to the second last line after quiet splash and, just like before, add pci=use_crs after that. It should look SIMILAR to &#8220;46a-a2bcale93d ro   quiet splash pci=use_crs&#8221;. Just make sure you have pci=use_crs at the end of the line after splash. Then hit control+x to boot into Ubuntu,

6) Set up your network. I wont go into this because it's all different. Once you have internet connection, update your machine with System &#8211; Admin &#8211; Update manager. Hit the check button and install all updates that are available. Chose to use the new Grub loader if it asks you to. Okay, now you need to restart. You must boot up the same way as before by adding the pci=use_crs option. This will be the last time before you can manually add it to grub.

7) Okay after booting using the pci=use_crs option, edit your grub configuration by Applications &#8211; Accessories &#8211; Terminal. Type in the following into the console.

sudo gedit /etc/default/grub

hit enter, type your password and hit enter. Now your grub config will show up in gedit. Scroll to the option

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash&#8221;
and change it to  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=use_crs"

Save the document and close out. Now in terminal type

sudo update-grub

And now you wont have to worry about typing in pci=use_crs again. This will add it automatically to the boot options for you so you don't have to manually add it.

8) Download the hardware drivers with Applications &#8211; Ubuntu Software Center &#8211; Get Free software. Type in fglrx in the search box and download jockey-gtk, ati binary X.Org driver, and ATI Catalyst Control Center. Install all of those, then select system &#8211; admin &#8211; hardware drivers. I got ATI/AMD Proprietary FGLRX on mine, I guess you can install a couple different ones for the same gfx card, but that's what I use. Hit activate, and restart. You should now be able to use Extra Animations and Compiz etc.

I hope I helped out those who are having trouble getting Ubuntu installed on their Toshiba and Acer laptops! I am no Linux expert, in fact, this is the only time I could understand Linux after trying SuSe many years ago. Please be patient, and if you have any questions please make sure to research before asking. :D

One question I have is, is there any way the developers can implement the pci=use_crs option to the F6 command during the LiveCD boot options? That could save massive headaches to new users of Ubuntu who have the same GFX card I have and don't understand what they're doing yet. I almost gave up with Ubuntu, despite how much I loved it. Windows will always be a my last resort now.

---

### Post by naderb on 2010-04-20
Hello There, 
thanks for the post, its really good and works to activate ATI HD 3xxx series on any Ubuntu Based PC.

i had it fixed longtime ago. and works fine but its little laggy for me i have no idea why. i removed the driver reinstalled it from ATI Driver support page also same problem 
its laggy.. when i removed the with older versions of Ubuntu use to work Much faster...

is there anything i can do to get it back to as fast as it should be ?


Thanks,
Nader.B

---

### Post by honkeypatrolfbi on 2010-04-23
Hey sorry for the delayed response. Honestly, the driver is a little sluggish no matter what build you get for it. Unfortunetly, I've tried multiple installs of it and found best results with the ATI official site (with 3d effects enables). I have not come across any solutions that actually provide no lag. I have problems especially with maximizing and full screening streaming videos. Hopefully in newer builds of Ubuntu they may provide fixes. Unfortunetly these drivers do not have much support because they are considered out-of-date despite that the HD Mobility 36xx drivers have come out recently. If anyone knows an easy solution, feel free to provide information. But sorry for now I'm not sure how to answer your question.

---

### Post by afab on 2010-06-22
I have same PC and thankfully to your guides I managed ti install it but after installation it does not start graphic interface. I mean it loads ubuntu in command line and asking for login/password. After entering l/p I have command line and nothing going. Which command I have to execute? How to start Ubuntu command line?

---

### Post by EagleTG on 2010-08-01
Thank you very much!  This worked perfectly on my Toshiba A355-S6935.  The only thing different I needed to do was copy the xorg.conf.failsafe I had in /etc/X11 to xorg.conf.  I was receiving a prompt:
> Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid
... when I was trying to enable the proprietary drivers using System/Administration/Hardware Drivers.

Thanks again, I had been struggling with this.  I had given up long ago, and decided to retry when 10.04 was released.  I ran into the same issues as I did in prior Ubuntu on this laptop (black screen, etc)...  Then I found your post.  Worked like a champ.

---

### Post by honkeypatrolfbi on 2010-08-03
No problem! I tried to make it as easy as possible to follow. Any unanswered questions, I do not know how to respond. Sorry!

---

### Post by Erafo on 2010-08-18
I looks like Ubuntu 10.10 Maverick Meercat fixed this. At least the alpha 3 did. But i can't say it for sure because i didn't tried it yet, u just opened it in the live CD and was fine.

---

### Post by tanasis on 2010-10-31
Hello.
I just installed ubuntu 10.10 32-bit and I installed the all the drivers for my ati radeon hd3650.However, although the fglrx driver is "installed and currently in use", none of the effects work. Neither the effects of Compiz nor the normal or extra effects of the 'Change desktop background'.

My laptop has an intel core2duo @ 2.4 ghz, 3gb ram memory and a 500gb hdd.

Any ideas?

---

### Post by yannoo on 2010-12-29
Hi Tanasis,

Haven't tested it yet, but it seems this tutorial is detailed enough:
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

---

