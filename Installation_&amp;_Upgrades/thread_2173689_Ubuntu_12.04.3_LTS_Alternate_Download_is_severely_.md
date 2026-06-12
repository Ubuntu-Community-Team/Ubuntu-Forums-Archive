---
title: "Ubuntu 12.04.3 LTS Alternate Download is severely broken.."
date: 2013-09-10
forum: Installation &amp; Upgrades
---

### Post by Fatal Force Sam on 2013-09-10
Hi,

A bit of background - my desire was to set up a RAID 1 setup with an Ubuntu install. Shouldn't be too bad, unfortunately they stripped that support for the desktop version in the Ubuntu 13 release, at least to my knowledge I couldn't find anything that would enable me to get it. So no big, I settled for the 12.04 alternate download that would allow me to set up the RAID 1. 

Or so I thought, after downloading the iso from: [http://releases.ubuntu.com/precise/ubuntu-12.04.3-alternate-amd64.iso](http://releases.ubuntu.com/precise/ubuntu-12.04.3-alternate-amd64.iso), I made a bootable USB flash drive using unetbootin and universal usb installer (at a later time, both resulted in the same issue). I booted up the machine and was able to boot off the flash drive. At this point, everything seemed great. I went ahead and chose my keyboard configuration and got a few of the initial steps out of the way. 

Then I ran into an error screen with the following message: [IMG]http://i.stack.imgur.com/bHUSS.jpg[/IMG]

Sorry, if the image shows up really large (or if it's not allowed)... new to the forum. The error message was: "There was a problem reading data from the CD-ROM. Please make sure it is in the drive. If retrying does not work, you should check the integrity of your CD-ROM. Failed to copy file from CD-ROM. Retry?"

After some searching around, I found quite a few posts that seemed to indicate this was very much so a problem with trying to boot off of a USB stick, instead of a CD. Overwhelmingly people recommended adding the following option to the boot command, "[FONT=Ubuntu Mono]cdrom-detect/try-usb=true"[/FONT]

This however was not the issue, as by default this option was already in the boot command! I stumbled upon this solution, [http://www.answeredubuntu.com/127398/usb_drive_install_of_ubuntu_12_04_server_fails_can_t_find_components_from_cd_rom#sthash.8VZeGPxz.dpbs](http://www.answeredubuntu.com/127398/usb_drive_install_of_ubuntu_12_04_server_fails_can_t_find_components_from_cd_rom#sthash.8VZeGPxz.dpbs), and it got me going on the correct path towards the eventual solution.

After reading that, it got me to thinking that maybe the download was corrupt. So I ran the checksum on the download that was provided, and everything checked out. Well, thanks to the post above, I ALSO ran the checksum from the install, and viola! It came up with a mistakenly named file. I compared what it was complaining that it should have, and compared it to what was there. Sure enough, they were different. So I changed it, and reran the checksum. Again, another file had an issue, so I fixed it, and repeated, again, and again, and again. I can't tell you how many times I did this, but it was at in the ball park of 50-100 files that I had to change!

The names should have been in this format (most of the time): <.....>precise1_amd64.deb, instead what I wound up seeing was crap like <.....>prec_amd64.deb, <.....>precise1_.deb, <......>precise_am6.deb, and on and on. 

What I can't understand is how something that is clearly, and absolutely broken - released. Or how this hasn't been documented more. Am I truly the only person that's come across this issue? The one post touched on it, but they had to change 1 file, and it apparently was fixed. I had to change it time and time again. Also, I'm confused as to how the download on my Windows machine passed the checksum, but the actual installations checksum caught the issue. 

~Sam

---

### Post by oldfred on 2013-09-11
I think part of the issue is that they assumed that few desktops used RAID. But now with Intel SRT on Windows 8 systems everyone of those have RAID. When they did away with the alternative installer they were promising to have encrypted & RAID supported in the Desktop. So far only encryption is supported.

       Elimination of Alternative installer for 12.10 and no RAID support directly for Desktop.
[http://ubuntuforums.org/showthread.php?t=2049021](http://ubuntuforums.org/showthread.php?t=2049021)

You can report bugs.

 bug reports info on how to do:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)


 Grub does not loopmount alternate
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/914926](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/914926)

Same issue on server in trying to loopmount ISO directly with loopmount. 

This ISO also had name issues.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1172065](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1172065)

---

