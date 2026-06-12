---
title: "No option for installing alongside."
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by Vibins on 2011-03-01
Hi,I'm trying to dual boot windows 7 (x64) and unbuntu 10.10 (x64) on my laptop (msi gx660r).

I have the unbuntu 10.10 desktop file burned to cd and I am able to start the installation. The problem comes when I try to select the option to install unbuntu along side my current operating system, because that option isn't there.

I currently have 300 GB of unallocated space on my hard drive.

I think the problem may be that my hard drive is actually a RAID 0 array of 2 500 GB hard drives. This is not a hardware RAID it is Intel RAID (Intel rapid storage technology) which I think is technically called a firmware RAID.

If anyone can offer some help I would greatly appreciate it.

---

### Post by Hakunka-Matata on 2011-03-01
I'd like to alert you to a bug in 10.10's installer.  Data Loss can occur when using the side by side option.  It's important enough that I wanted to alert you now, before you proceed, because if you already have a Windows installation on your disk, you have to be careful.  I'll come back in a minute with some links that explain it well.

---

### Post by Hakunka-Matata on 2011-03-01
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install]("https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install")

First pagagraph, bug (655950)

---

### Post by Hippytaff on 2011-03-01
> **Hakunka-Matata said:**
> I'd like to alert you to a bug in 10.10's installer.  Data Loss can occur when using the side by side option.  It's important enough that I wanted to alert you now, before you proceed, because if you already have a Windows installation on your disk, you have to be careful.  I'll come back in a minute with some links that explain it well.
I think that's if you choose to manually over-ride the side by side option by choosing entire disc, but good point.

If there is no option to install side by side it means that windows is taking up the entire disc, so it needs to be shrunk which is a risky business, so back up anything you can't live without (the general advice is to back up whenever you partition anyway).

Welcome to the forums - by the way

---

### Post by Hakunka-Matata on 2011-03-01
[http://www.gtlib.gatech.edu/pub/ubuntu-releases//10.10/]("http://www.gtlib.gatech.edu/pub/ubuntu-releases//10.10/")

ubuntu-10.10-alternate-amd64.iso 

The alternate installer is what you need to install to RAID0

---

### Post by Hakunka-Matata on 2011-03-01
> **Vibins said:**
> Hi,I'm trying to dual boot windows 7 (x64) and unbuntu 10.10 (x64) on my laptop (msi gx660r).

I have the unbuntu 10.10 desktop file burned to cd and I am able to start the installation. The problem comes when I try to select the option to install unbuntu along side my current operating system, because that option isn't there.

[COLOR="Red"]I currently have 300 GB of unallocated space on my hard drive.[/COLOR]

I think the problem may be that my hard drive is actually a RAID 0 array of 2 500 GB hard drives. This is not a hardware RAID it is Intel RAID (Intel rapid storage technology) which I think is technically called a firmware RAID.

If anyone can offer some help I would greatly appreciate it.

OP says he has 300 GB unallocated.  And with RAID 0 array, he needs the alternate installer, no?  

Also, I'd love to see some clarification/information on the alternate installer's procedure vis-a-vis the 'side by side partitioning problem' that exists in the 10.10 Desktop installer.  Is this also extant in the alternate install procedure?

---

### Post by Hakunka-Matata on 2011-03-01
> **Hippytaff said:**
> [COLOR="Magenta"][COLOR="Blue"]I think that's if you choose to manually over-ride the side by side option by choosing entire disc,[/COLOR][/COLOR] but good point.

If there is no option to install side by side it means that windows is taking up the entire disc, so it needs to be shrunk which is a risky business, so back up anything you can't live without (the general advice is to back up whenever you partition anyway).

Welcome to the forums - by the way

@Hippytaff, thanks, and I believe you are right, that is how I understand the bug also, and that is the problem IMHO.  If you've already chosen 'side by side', the options to use entire partition or entire disc should not be offered, because if a new user doesn't quite understand and *does indeed* choose one of those options, his existing installed partitions go bye-bye.  Once 'side by side' is chosen, the correct thing to do is Continue, period.  Or so I see it, anyone see a problem with that logic?

---

### Post by Hippytaff on 2011-03-01
> **Hakunka-Matata said:**
> @Hippytaff, thanks, and I believe you are right, that is how I understand the bug also, and that is the problem IMHO.  If you've already chosen 'side by side', the options to use entire partition or entire disc should not be offered, because if a new user doesn't quite understand and *does indeed* choose one of those options, his existing installed partitions go bye-bye.  Once 'side by side' is chosen, the correct thing to do is Continue, period.  Or so I see it, anyone see a problem with that logic?

Makes sense :-)

---

### Post by Vibins on 2011-03-01
Thanks for the help, I'll try the alternate installer and get back to you.

Ps, i backed up my entire computer and created a recovery disk before attempting to install but thanks for the link Hakunka.

---

### Post by Vibins on 2011-03-01
Still not working unfortunately, has anybody tried to dual boot windows 7 and unbuntu on an Intel RAID?

---

### Post by Hakunka-Matata on 2011-03-01
Can you do this for us?  And by the way, the following text and code is plagiarised, from Rubi1200 I think, it's good. 

From the LiveCD, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the Desktop folder.
3. Open a terminal and run the command

```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Vibins on 2011-03-02
> **Hakunka-Matata said:**
> Can you do this for us?  And by the way, the following text and code is plagiarised, from Rubi1200 I think, it's good. 

From the LiveCD, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```

sudo bash ~/Desktop/boot_info_script*.sh
```This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

sorry that didn't work. It said no such file or directory.

---

### Post by ronparent on 2011-03-02
Yes it can be a cinch depending on which version of Ubuntu you are trying to install.

The problem is that there was originally a bug affecting the initial releases of both 10.04 and 10.10. That bug did not allow the installer to properly see the raid drive during installation. It should have been fixed by now. But if not there is a work around.

You may also want to shrink the win 7 install from within windows prior to beginning. Leave enough unallocated space for the Ubuntu install. Also, if windows already has created two primary partitions you may want to create an extended partition to install Ubuntu to. You are limited to four primary partition on the drive but may have as many extended (logical) partitions as you want.

1)Boot to a live cd and open a terminal window to install kpartx to the live cd session **(sudo apt-get install kpartx**, or, thru software center or synaptics)
2) without leaving the session optionally start gparted to create an unallocated extended partition.

3) Continue the session to install -everything should work fine now. If you elect to manually create the install partition, don't for get to designate a '/' for the install. Also to create a swap partition.

Post if you have additional problems.

edit: Refering to post #10 - installing to a fakeraid

---

