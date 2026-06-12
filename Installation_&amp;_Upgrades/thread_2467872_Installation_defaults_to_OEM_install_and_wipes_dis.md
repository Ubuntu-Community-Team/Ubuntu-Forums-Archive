---
title: "Installation defaults to OEM install and wipes disk"
date: 2021-10-10
forum: Installation &amp; Upgrades
---

### Post by jeanluc2 on 2021-10-10
Hi,

I just got a new Lenovo Thinkpad X1 Yoga Gen6.  I ordered it with Ubuntu installed, and it came with 20.04.2  But I wanted to do my own fresh install anyways, so I used the startup application (on my other laptop) to make a boot USB with the latest LTS image (20.04.3).

I booted the new laptop, interrupted startup to select the USB drive as the boot disk, and off it went.

Here's the problem: it defaulted to immediately reinstalling everything.  I was never given a chance to select the type of installation, or to press a key to interrupt or anything.  The install screen said "*OEM mode, manufacturers only*".

This seems **very** dangerous.  If it hadn't been a new laptop I would have lost everything.

So, two questions:

1) Is this normal?  Am I missing something?  I know OEM mode exists, but I wouldn't have though the "stock" Ubuntu image downloaded from their site would (file name: ubuntu-20.04.3-desktop-amd64.iso).

2) How can I do a non-OEM install?

Many thanks,

Jean-Luc

---

### Post by guiverc on 2021-10-10
I can't speak with authority here, but I'll provide my thoughts of what I know.

(I QA-test new ISOs so I'm somewhat aware of features, but as my hardware is old - I've no experience with some *newer* features like OEM)

Ubuntu's desktop installer `ubiquity` had OEM features added to it, and when it detects a device on it's list that it knows about (which works better with OEM kernel & packages/features), it has different functionality on the ISO enabled.  I've not seen it, so have no idea what it looks like. All I know is the ISOs behave normally [to me] on the hardware I use in QA-testing.

Did you verify the ISO as being valid?

I'd ensure the write to your installation media is valid (*if I have a suspect write, I tend to test it on a like & very different box; as if it behaves badly on other boxes - I tend to blame a bad write*). In my experience about 5-8% of ISO writes to thumb-drives fail; as I'm writing 350+ per annum I'm looking out for those failures.

I'd **assume** the alternate options exist in the same manner that FREE SOFTWARE ONLY installs are performed; ie. hitting a key early in the boot process to have grub options on the boot/install media to show.  On *~recent* releases I found that hard to *reliably* make the menu appear, so I stopped QA-testing those options; but a quick look at the ISO tracker ([http://iso.qa.ubuntu.com/qatracker/milestones/408/builds/238108/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/408/builds/238108/testcases)) and OEM setup implies a key needs to be pressed - thus I'd ensure your ISO was valid & write to media perfect.

(*the OEM changes I'm referring to relate to new kernel options (ie. packages installed) used for OEM installs.. ie. far more significant than the no-user settings of prior releases*; *Lubuntu doesn't provide these (using `calamares`) so I have no need to know of them in detail*)

---

### Post by grahammechanical on 2021-10-10
The OEM install is an option that suppliers can use when they pre-install Ubuntu on machines. The first reboot after installation which should be by the buyer of the machine would offer the buyer the option of setting a user name and password. This method prevents shop workers from knowing a username and password for your machine.

Just to be clear about things. Did you download the Ubuntu ISO image from Ubuntu.com or from a Lenovo web site? I have experimented with the OEM install and to do one we need to access a special screen and then press F4 and select OEM install (for manufacturers). Is that what you are doing?

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

Normally we do not see the first screen in that link I have provided. Even so, as you can see we do get a screen where we can select the type of installation. The installer should not go straight to Erase disk and install Ubuntu. The option may already be ticked ( as in the image) but nothing will happen until we click "Continue."

So, I have no idea what is happening to you.

Regards

P.S. Does the motherboard manual give any information about re-installing?

---

### Post by MAFoElffen on 2021-10-11
> **grahammechanical said:**
> Just to be clear about things. [COLOR=#ff0000]Did you download the Ubuntu ISO image[/COLOR] from Ubuntu.com or [COLOR=#ff0000]from a Lenovo web site?[/COLOR] I have experimented with the OEM install and to do one we need to access a special screen and then press F4 and select OEM install (for manufacturers). Is that what you are doing?

I just finished renewing my Lenovo Warranty Certs for Lenovo. (As well as for Dell and HP) "support.lenovo.com" does not have a download link for Ubuntu. (As they also do not have download links for Windows media.) Nor does it have driver downloads for anything except Windows 10 and Windows 11 for that model. To receive any recovery media from them, you have to contact them, and... it is a process. There are 9 submodels for that model- 5 prebuilt's and 2 build-your-own's. Only one submodel, one of the build-your-own's, comes with Ubuntu (Part Number:  20XYCTO1WWUS2) When I log into their Tech Portal as a Tech, I don't see anything else there for an Ubuntu download. Just lots of diagnostics and motherboard branding tools. All hardware related tools for Field and Depot. 
              
The User Manual has general hardware use and "get to know your device" directions. Nothing on software or OS. The only other manual is the HMM- the Hardware Maintenance Manual, which are amazing for detailed instructions on disassembly, repair, diagnostics, etc... That manual, or type of manual, would have the motherboard information. When I need answers as a Tech, that is the manual I look to. But again, it has nothing on software applications nor anything on operating systems, except for the UEFI system utilities. Even as an Onsite Service Tech, they don't do OS or software related problems. Those are referred for the customer to call technical support... Which then direct them to...

So, unless he called Lenovo Tech Support, and requested their OEM branded recovery media, I suspect he downloaded the ISO from Ubuntu.

When they started supporting Ubuntu as a pre-installed option, they did come out with an install guide, which did go into pre-install BIOS settings, the main installation and the specific driver installations... but it was for and said "Ubuntu 18.04 LTS and later." I haven't seen any update to that:
[https://download.lenovo.com/pccbbs/mobiles_pdf/tp_p1_gen2_ubuntu_18.04_lts_installation_v1.0.pdf](https://download.lenovo.com/pccbbs/mobiles_pdf/tp_p1_gen2_ubuntu_18.04_lts_installation_v1.0.pdf) 

Just saying...

---

### Post by jeanluc2 on 2021-10-11
Hi guiverc, yes, it definitely seems to me like the installer is somehow "recognizing" my Lenovo and going straight for some kind of default install.

I did not verify the ISO as being valid, no.  I'll go and doublecheck.

Thanks,

Jean-Luc

---

### Post by jeanluc2 on 2021-10-11
Hi Graham,

Yes, the image was downloaded directly from Canonical, not from Lenovo.  Latest version of 20.04.3 for desktop.

No selection screen appears whatsoever, even briefly.  It goes straight to overwriting mode.  I interrupted it early once and the computer wouldn't boot, so it does indeed immediately wreck things.

Manual: this is a Lenovo laptop.  Precious little documentation is provided.

Thanks,

Jean-Luc

---

### Post by jeanluc2 on 2021-10-11
Hi MAFoEfflen,

You're correct, the image came straight from Ubuntu, not from Lenovo.

The PDF manual you posted is interesting because it shows a Ubuntu menu, which is exactly what I don't get in my install.  So what I'm experiencing must be a recent change.

I wish I could document this better but now that I've set up the laptop (using the default OEM install I had no choice to do) I don't want to risk wiping it!

Many thanks,

Jean-Luc

---

