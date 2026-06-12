---
title: "Help/advice regarding new dual boot alongside windows 10 on desktop computer please."
date: 2023-03-13
forum: Installation &amp; Upgrades
---

### Post by reptilean on 2023-03-13
Hi, I have an oldish but still very functional windows 10 desktop.  It uses UEFI rather than bios.  It has a 1tb ssd hard drive where windows 10 is installed, a 3tb sata hard drive with a 2tb ntsc partition and 1tb unpartitioned space and it will soon also have a 2tb sata hard drive, unpartitioned.  It has a 64 bit pentium and 16 gb or ram, and a dvd drive.

a few days ago, I tried to install a dual boot system with the current version of Ubuntu desktop, 5 year support, on a usb stick.  At that time, the magnetic drives were not clear but I freed up a 500gb partitionless space.  I don’t think I was paying sufficient attention because the install freed up space on the ssd drive and installed there.  There were a lot of error and fail messages scrolling by throughout the install.  I ended up with a not very functional installation: no wifi, no wireless keyboard (I plugged one in) not much software.  I was surprised because I’ve done this before with Centos and Fedora, some years ago, and it was really easy.  

To cut a very long story short, I tried to remove the installation and remove the dual boot facility.  I broke everything….  I’ve cleaned up the discs from a windows boot disc using Diskpart and clean, re-installed windows 10, restored data from backup and would like to try again…

Is it possible to install Linux on one of my clean discs and not mess with the windows 10 ssd?
What version of Ubuntu should I use for the best and “fattest" desktop experience?
Should I be doing this with Ubuntu or with Fedora or some other distro?

Any suggestions or advice before I try again, not limited to the above questions, would be much appreciated.

Many thanks in advance,

kind regards,

Mark

---

### Post by MAFoElffen on 2023-03-13
You want the fastest, safest method? Then unplug your Windows disk (completely) during the install.

Install and configfure it how you want. When you are finished, go to the /etc/default/grub file, edit it with sudo permissions and add this line to it:
```

GRUB_DISABLE_OS_PROBER=false

```
Save and shutdown...

Plug in the SSD with Windows, but set the BIOS to boot the Ubuntu installed disk first. Boot into Ubuntu... Open a terminal and do
```

sudo update-grub

```
Grub OS Prober will find your Windows Installation and add it to the Grub2 Menu. 

Done. (without touching anything on your Windows Installation. See? The safest and fastest way to be dual boot with Windows. And in a manner that you had explained what you wanted (Being located on a different disk).

---

### Post by reptilean on 2023-03-13
Blimey! I&#8217;m really glad I asked the question.  That really sounds like the way to go.

Id quite like to improve my knowledge of grub once I&#8217;ve got myself sorted out.  Can you recommend some good, clear documentation with examples please?

Many thanks for your help.  I&#8217;m sure this will make a big difference.

kind regards,

Mark.

---

### Post by ubfan1 on 2023-03-13
A good start would be the man page, man grub-install (or xman if you prefer).  Then having gone through the dance of the Disconnect the Disk, add yourself to the "Does this affect me?" launchpad bug 1396379 -- Grub installs to wrong disk.  Not really a grub bug, grub just does what you tell it, but the usual installer simply ignores your "bootloader location", and uses the first location it finds (usually on the Windows disk).

---

### Post by MAFoElffen on 2023-03-14
The Ubuntu Wiki:
[Grub2 - Community Help Wiki - Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2")
[Grub2/Setup - Community Help Wiki]("https://help.ubuntu.com/community/Grub2/Setup")
[Grub2/Troubleshooting - Community Help Wiki]("https://help.ubuntu.com/community/Grub2/Troubleshooting")
[Grub2/Installing - Community Help Wiki - Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2/Installing")
[Grub2/Displays - Community Help Wiki ]("https://help.ubuntu.com/community/Grub2/Displays")
[Grub2/ISO Boot - Community Help Wiki]("https://help.ubuntu.com/community/Grub2/ISOBoot")
[Grub2/Passwords - Community Help Wiki]("https://help.ubuntu.com/community/Grub2/Passwords")


The GNU Documentation:
[GNU GRUB Manual 2.06]("https://www.gnu.org/software/grub/manual/grub/grub.html")

---

### Post by reptilean on 2023-03-14
I had a successful day with this approach but the result wasn&#8217;t quite as expected.  The Ubuntu install with the windows disc removed went well.  I had a network cable plugged in and noticed packages being downloaded and later was prompted and accepted a software upgrade. I modified grub and ran the command line as sudo after restarting with the windows disc reconnected.  The Linux installation was detected but not the windows installation and the message remarked that no other os would be detected.  However, I discovered that I can easily boot either the windows disc or the Linux disc by switching the boot order.  I&#8217;ve never seen this before but it serves my purpose very well.  I&#8217;ve switched back and forth a good half dozen times now without problems.  I&#8217;m happy to consider this &#8216;job done&#8217; unless you can see trouble ahead and advise against it.  Should I go back and delete the line I added to grub or perhaps comment it out now?  I photographed the result of running grub and would be happy to send it to you or post it here if that is allowed.

Many thanks for your help.  I know have a working Ubuntu desktop sitting alongside windows 10.  Still have to sort out wifi, printer, scanner etc&#8230;.

kind regards,

Mark

---

### Post by reptilean on 2023-03-14
Many thanks for your suggestions.

kind regards,

Mark

---

### Post by tea for one on 2023-03-14
> **reptilean said:**
> The Linux installation was detected but not the windows installation and the message remarked that no other os would be detected. 
Three possible reasons why Grub did not detect Windows 10:-
[LIST]
[*]Windows is hibernating.
[*]Mixed mode installations - one OS in UEFI mode and the other OS in Legacy mode
[*]Grub not configured correctly
[*]
[/LIST]
Here is some info about mixed modes [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Is your Grub similar to this?
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false
```

Anyway, booting from the PC one-time boot menu is more than sufficient and it may be better to leave things as they are until your experience affords you more "tinkering" time ;)

---

### Post by MAFoElffen on 2023-03-14
Oh dang... I had a typo in Post #2, Sorry. I should have checked my own machines! Doh! (Embarrassed.)

Went back and corrected Post #2... Thank at "tea for one".

---

### Post by reptilean on 2023-03-14
> **MAFoElffen said:**
> Oh dang... I had a typo in Post #2, Sorry. I should have checked my own machines! Doh! (Embarrassed.)

Went back and corrected Post #2... Thank at "tea for one".

Many thanks for the additional information.  I&#8217;ve edited the change you advise into my grub file and commented it out.  I&#8217;ve also commented the subsequent command directly below this line so I won&#8217;t have to look it up in future if I want to run it.

unless you advise that it is a very bad idea, I&#8217;m planning to keep this config which seems to give me the best of all worlds.  Also (I&#8217;m sure this won&#8217;t happen) if I want to remove Ubuntu and return to windows 10, I don&#8217;t have any boot loader complications.

Thank you so much.  You have been a tremendous help.

Thanks also to "tea for one".

Best wishes,

Mark.

---

### Post by reptilean on 2023-03-20
Thought I&#8217;d provide some feedback onto where I got to with this so that others don&#8217;t follow my process.

The computer started behaving oddly and wouldn&#8217;t boot with all my hard drives connected (windows partitioned and formatted).  I tried running the recommended and amended command but got the same error message and couldn&#8217;t see any difference.  In the end, I connected only the cleaned and re-installed ssd on which I had done a clean windows 10 install but it wouldn&#8217;t boot to windows, only Ubuntu&#8230;. This was a real puzzle.  There were no other discs connected, no dvd in the drawer and no usb drives connected.  I decided to boot from a windows repair dvd delete the partition and re-install from scratch again.  This worked ok, the computer booted to windows and the ubuntu option was gone from the boot menu in bios.  

If I connected my other hard drives, they were not recognised.  The Ubuntu option had also returned to the bios start up options.  DiskPart from a windows repair disk with clean command made no difference. But clean all eventually brought them back and I now have a working system.  The Ubuntu option is still there in the bios boot options but I daren&#8217;t try it.  I bought a new drive for my wife&#8217;s laptop and successfully installed Ubuntu on that (single boot).

Very time consuming and stressful,and still not sure if I&#8217;m in the clear.

---

### Post by yancek on 2023-03-21
> I connected only the cleaned and re-installed ssd on which I had done a  clean windows 10 install but it wouldn’t boot to windows, only Ubuntu 

Had you set the SSD with windows to first boot priority in the BIOS firmware boot options?  

>  If I connected my other hard drives, they were not recognised.

Was this while booted into Ubuntu?  Were the other drives windows drives?  If so, as stated in an earlier post this may be due to the default setting of hibernation in windows.

>  The Ubuntu option is still there in the bios boot options but I daren’t try it.

If Ubuntu is not installed on any of the drives on the computer, it obviously won't boot but will still show in the BIOS as this information is on the system board not the drive.  You should be able to use sudo efibootmgr to delete that option or do it by going into the BIOS firmware setting to delete it.  The link below gives a simple explanation on how to do this with efibootmgr.

[https://digitalrobin.net/2020/07/11/how-to-remove-old-efi-boot-entries-in-linux/](https://digitalrobin.net/2020/07/11/how-to-remove-old-efi-boot-entries-in-linux/)

---

### Post by TheFu on 2023-03-21
I'm going to disagree with dual booting.  Use a virtual machine and run one of the OSes inside it.  This way, only 1 system will screw with the boot process. The other will be 100% separate, running from virtual storage, controlled and managed by they hostOS.  There are reasons for the hostOS to be Linux and there are reasons for the hostOS to be Windows. Only you can decide.

Having 2 different OSes try to share boot settings and responsibilities is asking for problems.  Not every week or every month, but perhaps once every other year, when is it completely convenient NOT to have a booting computer. NOT!  Boot issues tend to happen when we don't have any time to deal with them.  Avoid it completely by using a hypervisor and setting up the VM to share resources between the host OS and the guest VM.  

Back when my LUG had installfests at the local University, we'd push for people to use virtual machines, since we knew they needed Windows for classwork.  Using VMs also eliminates hardware problems, since the VM host emulates extremely compatible hardware for Linux.  You'll never need to worry about some wifi driver or GPU driver for a VM system.  Also, the storage provided to each VM is self-contained, so there's no chance of an accidental wipe for the other OS happening. It just doesn't happen.

---

### Post by reptilean on 2023-03-21
Thanks, TheFu, I completely agree.  I&#8217;ve used VMware for multiple os&#8217;s on a windows computers in the past with no problems.  I was just hoping to save myself a few bob as it&#8217;s quite expensive.  Much cheaper to buy an extra drive for my wife&#8217;s hardly used laptop and only takes a minute to swap back.  I _think_ my windows desktop is working correctly now but would love to get rid of the Ubuntu boot option in bios.  I can&#8217;t find a delete option in the menus.

with the amount of time expended, I could have learned to play the piano&#8230;

Many thanks for the well considered advice and patience from all those who contributed to the thread.

---

### Post by MAFoElffen on 2023-03-22
VMware Player and VirtualBox are both free for personal use... Then, if you have Windows Pro, you could use Hyper-V...

---

### Post by TheFu on 2023-03-22
> **reptilean said:**
> Thanks, TheFu, I completely agree.  I’ve used VMware for multiple os’s on a windows computers in the past with no problems.

"VMware" makes 6 different hypervisor products.  Some are expensive (ESXi+vsphere), some cost some money (Workstation), and some are free for home users (Player).  All are proprietary.  VMware isn't the only company in this race.

There are other options.  On MS-Windows, for a home user, probably the least "bad", but capable choice is Oracle's VirtualBox. The core of virtualbox can be F/LOSS.  Where Oracle gets companies, is with their Guest Additions license which isn't F/LOSS, but does allow for home users to use it without cost ... but it will be phoning home to report that you are using it to Oracle. I think they call the license PEULA - personal use end-user license agreement.

Of course, if the host computer were running Linux, then there are many, many, other choices for hypervisors - most aren't just free, but F/LOSS, if that matters to you.  In these forums, we tend to see people using VirtualBox or KVM+virt-manager.  VirtualBox runs on Windows, but it also has a native Linux version.

When it comes to what works on MS-Windows, MAFoElffen works in that realm and is quite knowledgeable, while also knowing the Linux options extremely well too.

---

### Post by reptilean on 2023-03-25
It&#8217;s a few years since I used VMware workstation but it worked very well indeed.  As you point out, there are other alternatives though my hardware doesn&#8217;t support Windows own product. I didn&#8217;t know/had forgotten that VMware player is free.

I&#8217;ve got Ubuntu up and running properly on a spare laptop with a dedicated drive.  It&#8217;s a good solution for me.  It will be great to start using it.

once again, many thanks to everyone who has given freely from their considerable knowledge and experience.  Much greater than my own.  I really appreciate it.

Thanks

---

