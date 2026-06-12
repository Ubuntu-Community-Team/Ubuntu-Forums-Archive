---
title: "Can't boot Linux Live DVDs from USB or DVD with HP Z400 Workstation"
date: 2020-06-15
forum: Installation &amp; Upgrades
---

### Post by Randymanme on 2020-06-15
I recently purchased a second-hand HP Z400 Workstation: Xenon 3680 Hexcore 3.33 GHz, 24 GB ram 2 TB hdd, with Windows 10 installed. My intentions are to Tri-boot Windows 10, Ubuntu 18.04, and Deepin 20/beta; however, the computer will not boot the Linux OSes, nor any Linux live DVD from DVD drive or USB -- (so far, I've tried Ubuntu, 18.04 and 20.04, Linux Mint 19.3, RescueSystemCD, and Deepin 20/beta).

I've googled this problem every day for over a week and have gotten either no usable advice or suggestions that I don't have the technical expertise to try to implement. (And, by the way, the gentleman whom I bought the HP Z400 from doesn&#8217;t have the technical expertise to help me either &#8211; he did tell me that should I decide the put it back on Craigslist, I shouldn&#8217;t have any problems finding a buyer as he&#8217;s gotten plenty of calls from prospective buyers even after I bought it).

At this point, I strongly suspect that this problem may be rooted in a RAID configuration. I want to include some photos and screenshots from my monitor. Regarding changes I thought I could possibly I make in the BIOS, I found directions to disable SecureBoot and enable Legacy Boot, but the BIOS on this particular Z400 doesn&#8217;t include those options. So I thought about updating the BIOS, but found at [https://support.hp.com/us-en/warrant...69?sku=FM080UT]("https://support.hp.com/us-en/warrantyresult/hp-z400-workstation/3718668/model/3718669?sku=FM080UT") that the End-Of-Life for support for my computer has already happened. Someone at HP Customer Forum says that even though it&#8217;s past E-o-L the Z400&#8217;s BIOS can still be upgraded, but don&#8217;t try it with Windows 10 because Windows 10 didn&#8217;t come out until after the Z400&#8217;s E-o-L.

I&#8217;ve noted that HP did support RHEL and SLED for the Z400, but in both cases, that support required special installer disks that did not include the actual RHEL or SLED operating systems. (I presume I can still download the installer disks from HP; and as far as the actual operating systems go, I wonder if Fedora or CentOS will do instead of RHEL and/or if OpenSuse or Tumbleweed would suffice instead of SLED?) And I&#8217;m only assuming that if I could get any Linux operating system installed on my Z400, then others could follow without ado.

Perhaps the photos and screenshots bear some explaining.

At some point, it occurred to me that maybe this might be a PBKC situation; therefore maybe a viable solution might be for me to get up and do something. So I turned off the computer, got up and switched harddrives between my new computer: HP Z400 Workstation, Xeon 3680 hexcore 3.33 GHz, 2TB hdd; Windows 10; and my old computer: Optiplex 960, Intel Core2 Duo, 3.0 GHz, 6 GB ram; Ultimate Edition Oz Unity Star Sapphire (discontinued Ubuntu 14.04 remix upgraded to a 16.04 base); Linux Mint 19.3 Tricia/Mate. So now, my current setup is reflected in my signature (see below). ROM messages that displayed on the monitor during boot up, I took pictures of with my smartphone.

Since the 2TB hdd does boot on the Optiplex 960, I installed Ubuntu 18.04/Mate onto it using the installer option to install alongside of Windows 10; and then from there, used Ubuntu&#8217;s Gparted (Gnome Partition Editor) package to resize the Windows partition for space to install Deepin 20/beta. With the 160 GB hdd that I took out of the Optiplex 960 now in the Z400, while Linux Mint 19.3 doesn&#8217;t boot, Ultimate Edition Oz Unity Star Sapphire does.

So Let my sum up my question. How can I get the HP Z400 to boot the Linux operating systems after I put the 2TB hdd back in?

---

### Post by TheFu on 2020-06-15
i don't have any HP computers anymore.  Learned my lesson around 2000 not to buy those things.  To each their own.

There are BiOS setting specific for Windows that need to be disabled to boot other OSes since UEFi came out.  Definitely have to disable those.  On a new-to-me computer, i work through all the bios screens and look for any setting that say "Windows" and disable those - usually "Legacy" is the option.  Beware, changing these settings will often break an installed Windows so be ready to reinstall.

Also, have to set the HDD settings for AHCi, not raid.

if you cannot get linux booting, have you considered running those OSes inside a VM?  i've been doing that about 15 yrs. Works great for non-heavy-GPU stuff.

---

### Post by dbtech2 on 2020-10-15
I have experienced a similar failure when I tried to boot Ubuntu 20.04.1 live DVD on my 12 years old HP Z400. As a matter of fact I have had no problem booting a Ubuntu 18.04.5 live DVD. I agree with [COLOR=#000000]Randymanme: this must be related with the RAID configuration in the BIOS. Eventually I have succeeded using the following procedure.
- Press F10 (BIOS setup) during boot
- In the setup menu navigate to Advanced -> Device Options. Make sure that "SATA RAID Option ROM Download" is disabled if this item is available.
- In the setup menu navigate to Storage -> Storage Options. Make sure that "IDE" is selected.
- Save the configuration. It will try to re-enumerate the hard drives. This is the key of the solution.
Subsequently I was able to boot and install Ubuntu from the live DVD. Once the installation is completed, you should revert the changes in the BIOS because IDE emulation is awfully slow. Set Storage Options to RAID+AHCI and try to reboot while keeping your fingers crossed.

[/COLOR]

---

