---
title: "Triple Boot"
date: 2014-01-18
forum: Installation &amp; Upgrades
---

### Post by JonthueM on 2014-01-18
I am doing a factory reset with the intent of freshing up for the year and getting not only ubuntu but also 
[h=2]Fedora and grub2 graphic with windows as well on the system.[/h]How would you do it without causing havoc for a newbie like me. I want fedora for the full gnome3 experience unless you have something better.

---

### Post by Bucky Ball on 2014-01-19
Make a partitioning plan. You are looking at an involved one.

Install Windows first, first partition, first drive (sda1). There are factors which are going to effect how you go about this. Are you installing in EFI or legacy? Which Win are you using? 

I know nothing about Fedora, but once Win is installed, install Ubuntu so you have Win and Ubuntu installed and operational, then perhaps you can hunt around the Fedora forums for how you go about installing that. You might have more luck (and discussion of installing Fedora should be in a new thread in ***Other OS/Distro Support*** here).

Good luck. ;)

---

### Post by 1clue on 2014-01-19
Um.

Virtual machines?

Dual/triple boot is a deliberate handicap of functionality.

If it's virtual machines, you can copy/paste between VMs, share apps and services or any other type of collaboration.  You don't have to close any apps to switch operating systems, it's just selecting a window and doing whatever, then coming back.

---

### Post by Bucky Ball on 2014-01-19
If you have the RAM and suitable hardware, that is. ;)

---

### Post by jp734 on 2014-01-19
The thing with VM is you don't get the full screen as well.

Triple boot is ok and you should be fine. I've had triple boot for years now and have tried fedora and Ubuntu combo with no problem. But now I'm a die hard Lubuntu and Crunchbang fanatic (low resource OSes)

Good luck to you

---

### Post by 1clue on 2014-01-19
@Bucky Ball.  Yes, of course.

@jp734 why not?  Don't bother using 'console' on the VM, that sucks no matter if it's KVM or VMware or whatever.  Just connect to the box using whatever would be appropriate for a remote computer and go full screen with that.

@JontheuM, Look at your hardware of course, but also map out all the advantages of using these systems when they run simultaneously, and then compare that to advantages and disadvantages of having to shut one down before starting the other.

---

### Post by oldfred on 2014-01-19
Some have posted that Fedora installs with separate /boot and LVM. LMV is a logical partition structure overlaying the physical partitions. Fine for full drive installs but not best with multiple boot as then it really has none of its advantages and all of its disadvantages.

If possible change from default LVM to just a more standard ext4s partition if dual booting with Fedora.

---

### Post by JonthueM on 2014-01-19
Win 7 I got win 7 up just thinking about which to do first.

---

### Post by JonthueM on 2014-01-19
I choose fedora because Gnome 3 I heard is better then on ubuntu

---

### Post by JonthueM on 2014-01-19
What distro would you suggest for full gnome experience?

---

### Post by JonthueM on 2014-01-21
What about this instruction?
[http://www.linuxbsdos.com/2013/03/05/triple-boot-windows-7-ubuntu-12-10-and-fedora-18-on-one-hdd/](http://www.linuxbsdos.com/2013/03/05/triple-boot-windows-7-ubuntu-12-10-and-fedora-18-on-one-hdd/)

---

### Post by JonthueM on 2014-01-21
@Oldfred how do you do that?

---

### Post by oldfred on 2014-01-21
I have not installed Fedora, so do not know. Others have posted that the do install to an ext4 partition, so it must be a manual install.

You can still use the LVM, but then in Ubuntu have to add the lvm2 driver and mount the Fedora partition for grub2's os-prober to find the Fedora install.

The Ubuntu installer has the lvm2 drivers, but if  you do not choose LVM in Ubuntu (which is full drive unless you use manual install), you can see it un-install the lvm2 driver during the cleanup at the end of the install process.

---

### Post by JonthueM on 2014-01-23
Okay I been to AskUbuntu, one reply was 
             My steps would be: 
  
[LIST=1]
[*]Boot to Fedora flash drive
[*]Shrink Windows partition using installer
[*]Create a root partition for Fedora following the Windows partition (leave room for Ubuntu!)
[*]Create a swap partition at the end of the disk (4-8GB should be enough)
[*]Install Fedora on its partition
[*]Reboot to Ubuntu flash drive
[*]Create Ubuntu root partition in the remaining space
[*]Use the swap partition you created earlier for Ubuntu swap as well, by selecting the "Use as" option, and selecting "swap"
[*]Install Ubuntu on its root partition
[*]Reboot! Ubuntu should have detected Fedora and Windows and set up GRUB accordingly.
[/LIST]
  You should end up with the following partitions in this order:
  
[LIST]
[*]Windows partitions
[*]Fedora root partition
[*]Ubuntu root partition
[*]Swap partition
[/LIST]
      

But because I already had a separation partition for it and ubuntu which is just 62 GB, I just pop in the flash drive trying to do a manual install when... error basically cant do anything because my drive is full. How?! No Idea. this is not a live disc sooo!!!! what should I do? dose it matter I start with fedora then ubuntu?

---

### Post by oldfred on 2014-01-23
Did you use all 4 primary partitions?

Post this from Ubuntu installer's terminal.
sudo parted -l

Not sure how to do above from Fedora, it that is version you have running.

---

### Post by JonthueM on 2014-01-23
I did not started with ubuntu I tried to do it with fedora rather then ubuntu first. Do you suggest I do from that way and then get grub2 afterwards? it was fedora that was giving me problems.

---

