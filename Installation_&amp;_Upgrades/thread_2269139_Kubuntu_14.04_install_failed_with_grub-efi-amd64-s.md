---
title: "Kubuntu 14.04 install failed with grub-efi-amd64-signed not installed"
date: 2015-03-13
forum: Installation &amp; Upgrades
---

### Post by Kay. on 2015-03-13
I had successfully installed Kubuntu 14.10 alongside windows 8.1 which came factory installed on the computer (dell xps13 9343). Everything was working, except sound. I then tried to install 14.04, and the installer crashed out at the grub-efi-amd64-signed package. Now I end up at grub prompt on boot.

After some reading on these forums, I found I could boot both the Kubuntu and the Windows manually from the grub command line, so both of the boot partitions seems to be fine.

How can I now fix the grub so I get the menu of choices (one for ubuntu, one for windows) that I had the first time round with 14.10? Is that what boot-repair is for? or is it some other method?

---

### Post by oldfred on 2015-03-13
Is that Dell the very new Broadwell based computer?

You may do better with very newest Ubuntu. 
And I do not normally suggest a beta - 15.04, it also have even more updates for newest hardware.

 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

      
 Dell XPS13 - New Broadwell, not yet fully supported Feb 2015
[http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/](http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/)
[http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly](http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly)

---

### Post by Kay. on 2015-03-13
Yes it is the Broadwell version.  That major.io link is very good reference thanks! I had the touchpad freeze-up problem too, but at least there was a quick work-around for it. On the plus side, the two finger scrolling worked better than I'd been led to believe it would from reviews. That just leaves sound and now that I see what a problem it is for everyone, yes I guess I'll go back to 14.10 and watch for a fix in the near future.

---

### Post by Kay. on 2015-03-14
OK went back to 14.10, and like the first time everything installed successfully. Not sure how the grub part got messed up with the attempted 14.04 install, but it may have had something to do with the fact that I had not selected the re-format checkbox option for the linux partitions as I had originally, and again now, with 14.10. From what I've read the digital sound output on this hardware will work, just don't have a displayport adapter for it yet.

---

