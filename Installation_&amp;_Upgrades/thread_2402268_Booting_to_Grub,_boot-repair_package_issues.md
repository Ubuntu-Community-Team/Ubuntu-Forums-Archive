---
title: "Booting to Grub, boot-repair package issues"
date: 2018-09-28
forum: Installation &amp; Upgrades
---

### Post by Velasquez on 2018-09-28
Hiya,

I have a new laptop which came with Windows 10. I would like Lubuntu or Xubuntu working on it. Windows has been removed. I've tried a few distros and Ubuntu Unity was working for a while. I tried to install some others and now I boot to GRUB>.

I tried reinstalling an OS (Lubuntu or Xubuntu, I forget which) and it still boots to GRUB>. One of these is still installed, I just can't get to it.

I've tried booting boot-repair from a USB, but the "Recommended repair" button displays two error messages:

Please enable a repository containing the [linux-generic] packages in the software sources of Ubuntu 18.04 LTS (mmcblk0p2). Then try again.

Followed by:

Please enable a repository containing the [grub-efi-amd64-signed] packages in the software sources of Ubuntu 18.04 LTS (mmcblk0p2). Then try again.

I have nothing of value on this laptop and a clean install would be fine.

Am I right in thinking grub is one of the first things to boot, but doesn't know what to boot after that? If this makes any difference, I couldn't see any grub.cfg file in /boot or /boot/grub.

I'm not sure where to go, any help is appreciated.

Thankyou.

---

### Post by yancek on 2018-09-28
If you have boot repair, try selecting the option to Create BootInfo Summary.  If that completes, it should give you a link which you can post here and members will be able to view information on your system and hopefully make suggestions to resolve the problem.

---

### Post by Velasquez on 2018-09-28
[http://paste.ubuntu.com/p/qGRwk7qm8n/](http://paste.ubuntu.com/p/qGRwk7qm8n/)

This is the output from boot-repair.

If there's any easy solution such as installing an OS that would reinstall/fix GRUB and then install my chosen OS I'd certainly give that a go.

Thankyou for your help.

---

### Post by oldfred on 2018-09-28
Script says you have no kernel and not connected to Internet?

You need to connect to Internet and in Boot-Repair's advanced mode, choose the full reinstall of grub and check install newest kernel.
Not sure if that will correct everything that is missing and if not, then you may need to reinstall.

Boot-Repair's report uses bootinfoscript for first third of report. But bootinfoscript has not been updated to support MMC & NVMe drives, yet. Author needs a user with those drives to test changes.
[https://github.com/arvidjaar/bootinfoscript/issues/5](https://github.com/arvidjaar/bootinfoscript/issues/5)

---

### Post by Velasquez on 2018-09-28
Here's a pastebin where I connected to the internet, it still has the same two problems as before with regards to the repos.

[http://paste.ubuntu.com/p/7FF9WMDPhM/](http://paste.ubuntu.com/p/7FF9WMDPhM/)

Thankyou again

---

### Post by Velasquez on 2018-09-28
I am guessing "install kernel" means "purge kernel and reinstall last kernel", otherwise I didn't see the option I'm afraid.

---

### Post by oldfred on 2018-09-28
I see mention of Zesty. You must be using versions that are current.
If install is Zesty 17.04, you must backup your data & reinstall. Both 17.04 & 17.10 are EOF - end of life.

If actually 16.04 or 18.04:
Boot-Repair seems to be offering to install grub.
But the default may not be a total reinstall, but just reconfiguring it into UEFI.
You want advanced mode & full reinstall & install of kernel.

If that does not work, you may need fsck on ext4 partition.

---

### Post by Velasquez on 2018-09-29
I tried the above to no avail, however I've installed regular 18.04 Ubuntu and that boots fine by itself, so for now that'll suit me while I work out how all this boot stuff works!

Thankyou to people who've helped so far!

---

