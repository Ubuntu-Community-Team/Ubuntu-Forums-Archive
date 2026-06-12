---
title: "Unable to boot after dist-upgrade on 20.04"
date: 2021-04-09
forum: Installation &amp; Upgrades
---

### Post by spacecats on 2021-04-09
Hello,

I am using Ubuntu 20.04 and I am no longer able to boot into my computer. Ubuntu is the sole operating system. The OEM logo for the BIOS just shows up and it gets stuck there. Just before the issue, In order to resolve some issues of packages being held-back, I tried running a dist-upgrade which showed that a lot of packages were going to be deleted. I didn't look over them that closely, but I have a feeling that some of them may have been vital to be required to boot up. After the dist-upgrade (which succeeded), I noticed that the packages (it was 13, now it's 12) are still marked as held-back.

I can access all of my files via the LIveCD, but I am wondering if there is a standard procedure here for these kinds of issues where you can chroot in from the LiveCD and install the minimum set of packages required to boot back in. However, all of my google searches for these issues have mostly been about when dpkg is in an error state. AFAICT dpkg thinks everything is fine.

Would someone be able to provide some guidance, or point me in the right direction, of some ways to ensure that I have the necessary packages to boot? If there's a possibility of data-loss on /home etc. or if it's too involved, I'm fine with manually recovering my files and starting fresh with 20.04.

Thanks

---

### Post by drewhowden on 2021-04-09
In your situation, I would simply refresh your Ubuntu installation (this is not the same as a full re-installation, this approach will replace any missing/damaged packages, while leaving your personal data intact, though you may need to reinstall your applications on your own). I made a YouTube video that shows how to do this. It explains the process much better than I can explain it here. Click the link below to watch:
            [https://youtu.be/DhVBOfHLPEc](https://youtu.be/DhVBOfHLPEc)

---

### Post by guiverc on 2021-04-10
I would explore what you actually removed by looking in the logs (ie. properly read the messages you didn't take much notice of), a summary of which can be found in /var/log/apt/history.log

Details of what you removed are what I'd use as a basis for what to re-install.

You haven't said if you're talking about Ubuntu Desktop 20.04 LTS or Ubuntu Server 20.04 LTS, but what exactly do you mean it won't boot up?  If you switch to text terminal can you login?  (ie. do you mean only the GUI isn't booting up or you can't even login to a text terminal?)  Are you getting past `grub`? or what do you mean by doesn't boot up?

I would always try and fix an installation before I resorted to *fix by re-install*, if for no other reason than *learning experience* (*or even refresher as reminder to not make the same mistake again*). Yes *fix by re-install* is very quick for desktops, but you didn't say what 20.04 system you're actually using, and the results vary on your usage (*but are actually great for most desktop use; more recovery required for server type roles*).

---

### Post by grahammechanical on 2021-04-10
This is what the man page says about dist-upgrade

> dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. The dist-upgrade command may therefore remove some packages. The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general settings for individual packages.

Packages are held back because supporting/dependency packages are not yet available. Installing the held back packages might break the system. The dist-upgrade command forces the installation of packages and avoid package conflict by removing packages. It is called "smart" conflict resolution. It does not seem so smart to me when being "smart" breaks the operating system.

In this case the machine is not getting past the manufacturer's splash screen. It is not loading Grub. Has Grub been removed? Can you enter the UEFI/BIOS settings utility? If you have a UEFI motherboard then at the OEM splash screen press (perhaps several times) the escape key. That should bring up a Grub menu. If one still exists. If you have BIOS motherboard then at the OEM splash screen press & hold the shift key.

If you get a Grub menu then select Advanced options for Ubuntu and then select a Linux kernel with Recovery Mode. If you can get to a recovery menu it will possible to get to a root shell prompt where you can run some commands to correct things.

Regards

---

