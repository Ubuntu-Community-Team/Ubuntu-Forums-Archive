---
title: "No GUI after upgrade"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by DaveM59 on 2012-10-22
Toshiba Satellite T235D dual boot with Win 7. Lucid 64 bit was installed on 2 partitions / (12 gig) and /home (35 gig). 

Trying to upgrade to Precise. First tried using Update Manager. During this upgrade got several "low disk space" warnings and had to skip installation of some software as a result. I know, I know, should have aborted at the first sign of trouble. But I did not, told it to go ahead and it got to the "Finished" stage and called for a reboot. Failure -- the old grub menu appeared -- not the new one I expected -- and I could not boot Ubuntu. Could boot Windows.

Next I made a live Precise 64 bit CD, booted from it, it worked fine, however it did not have the installation options I wanted (I wanted to save my old /home) so I made an Alternate install disk and used that. Booted from it, formatted / partition, kept /home and installed Precise. Ran into trouble at the "Installing software" step, at 85% the step failed. I tried 2 more times but each time it failed at that same point. Not knowing what else to do I had it skip to the next step and it finished installing. On reboot I now get the new grub menu but selecting Ubuntu puts me into a bash shell.

My first impulse is to re-run the Alternate installation but see no reason to expect a different result. Any suggestions would be welcome.

---

### Post by dino99 on 2012-10-22
try installing with acpi=off ( or noacpi)

google around "ubuntu boot option" to get the howto

---

### Post by DaveM59 on 2012-10-23
Thanks for the suggestion. I ran the Alternate install CD again and set the option to acpi=off. Unfortunately it made no difference, the "Select and Install Software" step still failed at the same point. It gives a message of "cleaning up" down below the progress bar for a second before it goes to the failure screen. 

Rather than start over, I decided to see whether the problem might be that the installer needed more drive space. I created a new 42 GB / partition, everything went smoothly, then went back through the "Install base system" step again -- successfully completed as before.  But when it got to the "select and install software" it failed again at exactly the same point.

Any further suggestions to troubleshoot this problem would be appreciated.

---

### Post by IWantFroyo on 2012-10-23
Maybe you should try installing Kubuntu or another variant of Ubuntu. It might work if the software being installed is different.

dino99: It's "noapic", not "noacpi"

---

### Post by DaveM59 on 2012-10-23
I may try that. Will I still be able to use my old Thunderbird  mailbox files on my /home partition?

apparently "noapic" and "noacpi" are both boot options, I have done a little checking but do not understand why they would make a difference during installation.

---

### Post by dino99 on 2012-10-23
> 
dino99: It's "noapic", not "noacpi"

to help you a bit, there is also nolapic, and many more, check the docs. :P

---

### Post by IWantFroyo on 2012-10-23
> **DaveM59 said:**
> I may try that. Will I still be able to use my old Thunderbird  mailbox files on my /home partition?

apparently "noapic" and "noacpi" are both boot options, I have done a little checking but do not understand why they would make a difference during installation.

Usually these options are to help you get to the installer. I don't use Thunderbird, so I can't help with that.

dino99: I see. Thank you! :)

---

### Post by DaveM59 on 2012-10-23
> Usually these options are to help you get to the installer.

Yes I see that makes sense, ACPI puts all the devices on a single IRQ which might confuse the installer.

I am actually trying to install from a USB flash drive.

Would a "real" DVD drive (external USB, my laptop has no optical drive built in) make any difference?

Well anyway disabling ACPI made no difference so I am going to try a Xubuntu install and see if that goes any better.

---

### Post by dino99 on 2012-10-23
you have to find which boot option works for your hardware. Lot of users have used nomodeset, that often works but removing "splash" from grub is a better solution (and let you know what is wrong while booting (verbose mode))

the "no gui" can be due to some graphic driver & abi conflicts, thats why before upgrading its always a good idea to deactivate the non genuine ubuntu sources and clean the cache to avoid such problems.

of course, nothing is better than a fresh clean install. Does booting the iso (without installing) works as it might?

---

### Post by DaveM59 on 2012-10-23
Yes the regular Live/install CD boots and runs just fine.

I am trying to do a clean install, *except* that I want to keep my old data in the /home partition.

The two installations I have attempted with the Alternate CD, both times I have formatted the / partition.

Thanks for your help.

---

### Post by DaveM59 on 2012-10-23
Update --

I downloaded and installed the 32-bit version of Xubuntu. It took its sweet time but installed correctly. On reboot all my bookmarks were there in Firefox, and Thunderbird opened with my mailboxes up. 

After 2 days of having to use Windows, I just wanted to get my Ununtu back, so I chose a version different enough that I thought it might work.

If anyone has further suggestions I would be willing to try another install with a 64 bit version. I have filed a bug report here: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1070483?comments=all]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1070483?comments=all")

Again thanks for the help.

---

