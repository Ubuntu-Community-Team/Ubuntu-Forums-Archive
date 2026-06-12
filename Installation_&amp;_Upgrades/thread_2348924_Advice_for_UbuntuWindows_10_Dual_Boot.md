---
title: "Advice for Ubuntu/Windows 10 Dual Boot"
date: 2017-01-09
forum: Installation &amp; Upgrades
---

### Post by jmichael111 on 2017-01-09
[Too long; didn't read version] I'm looking to setup Ubuntu and Windows 10 on a new build and wanted any general advice and recommendations. 

Hello wonderful wizards of Linux. My name is John; I've been using Ubuntu for a little while now, so I have some experience, but I'm definitely no expert. I just built a new desktop (specs below) and I've been running Ubuntu on it. One of my purposes for it is gaming, but I've hit enough snags with Wine and PlayOnLinux that I decided it was time to bite the bullet and make it a Windows dual boot (I know, I know, I don't like it either, but I'm in college and some of the required programs need Windows). Before I go further, here are the specs for my desktop.

[Motherboard] Asus Maximus VIII Hero (Republic of Gamers version)
[CPU] Intel 6th Gen i7 Quad-Core 6700k (with water cooling)
[GPU] Geforce GTX 1060 with 6 gb cache
[RAM] 64 gb DDR4 (it was cheaper in bulk)
[Storage] 250 gb Samsung SSD & 2 tb HDD (Seagate I think)

What I'm going to do is install Ubuntu on the 2 tb HDD and Windows 10 on the SSD. I'm good on the installation; there's other sources on how to do that. I'm mainly looking for power user stuff: ultimate driver packs for Ubuntu, files to add or remove to make Ubuntu less likely to break, things to avoid doing, etc. I'm installing on a clean build (I'll format the drive before I start) and I want to do everything *perfectly*. Any advice, comments, or well written, polite, witty remarks would be welcome.

The only real questions I have are: which to install first, and how do I make sure Ubuntu stays in charge?

I'll be installing the OS's on the Jan. 16th. Thanks in advance!

---

### Post by craige2 on 2017-01-09
Hello,

I have a similar set up. I installed the windows first, then the Ubuntu and everything was smooth after. Since you are installing them in different disks, you shouldn't expect any major issues and as you are good with installations the process should be straightforward.

My only advise would be "do not do it in one day". Install Windows and let it update... for a couple of days. They have this anniversary version these days. Install windows, set to update and let it on for a couple of days to finish off the updates (no sleep after x minutes, no turn off disk etc.). Way too many updates in windows... Every now and then give it a restart and let it check for updates again, sometimes doesn't notify for updates if not restarted. Always install the updates and then check for new ones.

Then install your Ubuntu and you are good to go.

It would help to have a check for potential issues with dual boot before you do it, so you know what to expect.

I just did like that last week. That's an advice someone else passed to me and I follow it with no issues. Since it seems to work flawless for me I always do it this way.

Hope it helped.

Have fun.
Craige

---

### Post by oldfred on 2017-01-09
That will be new UEFI hardware.
So just be sure to boot both Windows installer & Ubuntu installer in UEFI mode.
And then both drives need to be gpt partitioned. Windows in UEFI mode has a bunch of extra required partitions, so often best to let it do its thing on installing.
Be sure to include ESP - efi system partition on sdb when partitioning in advance, but grub will only install to ESP on drive seen as sda.
Be sure to install drives in SATA port order starting with SATA0.

You probably need to change multiple UEFI settings, do not overclock at least until finished installing.
And with Ubuntu may need nomodeset to install and until you get nVidia driver installed. You probably will want the ppa to get the very newest nVidia driver as default in Ubuntu's repository is a bit older.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]https://wiki.ubuntu.com/Kernel/KernelBootParameters
[/URL]
 Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices 

      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    [URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]

[/URL]

---

### Post by jmichael111 on 2017-01-09
Thanks Craige and oldfred!

oldfred, I looked at the "Thread Tools" tab and the only options are Printable Version, Unsubscribe, and Poll. I don't have a specific question to answer; I was planning on deleting the thread once I had the OS's installed. If I'm not actually waiting for an answer, should I remove it now? I don't want to gum up the website.

Thanks! John

---

### Post by coffeecat on 2017-01-10
*Thread moved to **Installation & Upgrades***, since this is a technical support question, not a Cafe subject.

> **jmichael111 said:**
> I was planning on deleting the thread once I had the OS's installed. If I'm not actually waiting for an answer, should I remove it now? I don't want to gum up the website.


We don't delete threads, and you won't be "gumming up the website." You posed a useful general set of questions and the replies may be of value to others in a similar situation. That is partly why we retain all threads in public view, except for those that are problematic in terms of the forum rules. 

Good luck with your installation, and do please start a new thread if you have a specific problem you need help with.

---

