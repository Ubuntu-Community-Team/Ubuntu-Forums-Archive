---
title: "Installing Ubuntu boot loader on a differend hard drive"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by EugeneS on 2009-11-21
Hi folks!

I've been trying to find some posts related to my problem but couldn't find exactly same scenario so I decided to post a new thread.

I have the following problem:

1. I have 2 hard drives installed.
2. On one of them I have Windows XP installed and running normally.
3. The second hard drive is divided to 3 partitions: ext3 partition, swap partition and NTFS partition.
4. I have Ubuntu installed on the ext3 partition of the second drive.
5. During the Ubuntu installation I choose to install the boot loader (GRUB) to the second drive (with 3 partitions).

So when I start the computer, Windows XP is booting correctly just as if I never had installed Ubuntu.
My problem is creating a dual boot menu.
What I tried to do is to extract the first 512 bytes from the second hard drive (which is supposedly the MBR), save it in a file, for example: bootsect.lnx and then create following reference in Windows boot.ini file:
c:\bootsect.lnx="Linux"

Now as a result - it didn't work for me.
When I done the above, I do get a windows boot menu which gives the "Linux" option but when I choose it I just get back to the same boot menu. So I can boot only Windows.

If I switch the hard drives in the BIOS menu I can't boot neither Windows XP nor Ubuntu. I mean if I choose Ubuntu, I get some GRUb error related to the missing system and if I choose Windows, I get the " Missing NTLDR" message. So I had to switch the hard drives back and continue with Windows only.


P.S. I extracted the MBR using following command:
dd if=/dev/sdb(x) of=/tmp/ubuntu.mbr bs=512 count=1



If someone could help me with this issue, I will be more than thankful!!

Thanks in advance.
Eugene

---

### Post by darkod on 2009-11-21
Have you considered installing grub on the first hdd, the one with windows on it?
I agree changing the selection in BIOS should have worked but out of whatever reason it didn't.
Another option is to make the ubuntu drive first choice in BIOS, and with that setup to reinstall grub on it. Maybe it makes a difference during grub installation whether disk1 or disk2 is first boot option in BIOS. Just guessing here.

---

### Post by presence1960 on 2009-11-21
> **darkod said:**
> Have you considered installing grub on the first hdd, the one with windows on it?
I agree changing the selection in BIOS should have worked but out of whatever reason it didn't.
Another option is to make the ubuntu drive first choice in BIOS, and with that setup to reinstall grub on it. Maybe it makes a difference during grub installation whether disk1 or disk2 is first boot option in BIOS. Just guessing here.

Just go in BIOS and switch the boot order of the hard disks so the disk with Ubuntu boots first.

GRUB needs to be on the MBR of the first disk that boots in the BIOS hard disk boot order..

---

### Post by lmarmisa on 2009-11-21
I agree with darkod.

Don't waste your time trying to start Ubuntu from a Windows loader. Ubuntu loader (grub) is able to manage dual boots, but not Microsoft.

If, by any reasons, you do not want to install grub in your Windows disk, you could try to switch the two disks (IDE or SATA) interfaces, in such a way that Ubuntu disk would be the first device in the disk boot chain (some little adjustments in the grub configuration would be neccesary in this case).

If your BIOS supports boots from USB, you could try to install grub in a pendrive and configure it to start Ubuntu from it.

---

### Post by alexfish on 2009-11-21
any one thought about going back to lilo

added link for reading about lilo 

[http://en.wikipedia.org/wiki/LILO_%28boot_loader%29](http://en.wikipedia.org/wiki/LILO_%28boot_loader%29)

---

### Post by darkod on 2009-11-21
The reason I think the OP should set the option in BIOS first and then install grub is because I am not sure how disks are marked when you have more than one.
For example, as he explained, the windows disk was still first in boot order when he was installing ubuntu. In that case, would sda be windows disk and sdb ubuntu disk? Grub is making the appropriate menu.lst (on 9.04 it's grub1).
Then you switch the boot disk order in BIOS, does that make the windows disk sdb and ubuntu disk sda?
If that turns out true, it is perfectly normal that grub can't boot both ubuntu and windows because it's looking at the opposed disks.
Just my theory. :)
Otherwise with single drive situation or when you do not switch the boot order I find grub very reliable and it seems to work "out of the box".

PS. I expressed myself wrong. sda and sdb would remain the same but hd0 and hd1 that grub uses might change. And that will make grub configured wrongly, depending which drive had first boot order when installing grub, and which after you change settings in BIOS.

---

### Post by presence1960 on 2009-11-21
> **darkod said:**
> The reason I think the OP should set the option in BIOS first and then install grub is because I am not sure how disks are marked when you have more than one.
For example, as he explained, the windows disk was still first in boot order when he was installing ubuntu. In that case, would sda be windows disk and sdb ubuntu disk? Grub is making the appropriate menu.lst (on 9.04 it's grub1).
Then you switch the boot disk order in BIOS, does that make the windows disk sdb and ubuntu disk sda?
If that turns out true, it is perfectly normal that grub can't boot both ubuntu and windows because it's looking at the opposed disks.
Just my theory. :)
Otherwise with single drive situation or when you do not switch the boot order I find grub very reliable and it seems to work "out of the box".

PS. I expressed myself wrong. sda and sdb would remain the same but hd0 and hd1 that grub uses might change. And that will make grub configured wrongly, depending which drive had first boot order when installing grub, and which after you change settings in BIOS.

You are absolutely correct! BIOS controls the hard disk boot order irregardless of Ubuntu disk labeling and output from fdisk. Even though a disk is labeled sda it is not necessarily the first disk to boot. That is determined by BIOS.

I agree- switch the order of booting in BIOS so the disk with Ubuntu boots first. You may not have to install GRUB it may still be on MBR from the original install. If not restore it.

---

### Post by darkod on 2009-11-21
Thanks for the pat on the back. :) I'm new here and it means a lot.
I always had single drive but now I am beginning to understand why and when you need those strange map (hd0) (hd1) map (hd1) (hd0) entries in grub.
In this situation it seems just making ubuntu disk first doesn't help. If I understand correctly the OP already tried that and couldn't boot neither OS. Grub is there but looking at the wrong disk because when he installed ubuntu and grub the windows disk was hd0 and now the ubuntu disk is hd0.
I still don't understand why would people like to keep windows bootloader on one drive. I've seen lots of threads similar to this one and the rule is: you get into trouble by keeping windows bootloader and installing grub on another drive which is NOT your first choice boot drive WHEN INSTALLING ubuntu. That is the key. From that point onwards, grub is configured wrongly and setting the other disk as first boot choice won't help you.
Once you decide to dual boot, forget about windows bootloader, just keep the drive as first boot choice as it was, and install grub over windows MBR. IMHO...
This might even deserve a sticky, some short direct explanation what not to do because they complain on ubuntu later.

---

### Post by oldfred on 2009-11-21
I agree with presence1960. Switch Hard drives and do whatever it takes to get ubuntu working, it should at worst cast be a reinstall of grub.

I like the idea of having the operating system in the drive setup in the MBR of that drive. That way you can switch drives in BIOS and still boot incase of hard drive issues. 

Also for right now there is a known bug in grub2, slow grub loading.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc

---

### Post by presence1960 on 2009-11-21
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.35 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Then we will be able to see your setup & tell you what exactly to do.

---

### Post by EugeneS on 2009-11-23
Hi guys.

Thanks a lot for your replies!

First of all I am totally agree that GRUB is much more usable and versatile tool than NTLDR. 
But the reason I am trying to configure the boot process using NTLDR, is that my goal was to make a minimal impact on my windows system since at the moment the majority of my work is concentrated on windows.

I already tried to switch the boot order of the hard disks so the disk with Ubuntu boots first but when I done that I couldn't boot neither Ubuntu nor Windows. So I just switched the hard disks back to the initial state.

In fact I was in a rush regarding the Ubuntu installation (I needed it urgently for some kind of project). As a result I just installed the Linux boot loader on the Windows partition and now I have a GRUB loader through which I can access my Windows system also.

Nevertheless I still would like my computer be configured too load using NTLDR.
Is there any way to "Uninstall" Linux? Then I could run the script presence1960 provided and analyze its output.


Thanks!

---

### Post by darkod on 2009-11-23
But that's exactly the point, IMHO. With all the additional steps that you would need to chainload Ubuntu into windows bootloader, and the possibility that it won't even work (there are threads like that here too), are you making less or more impact to your system, then letting grub do what it's doing good anyway? You seem to have no problems booting trough grub so why all the hassle and the chance to break things when they are working?

Otherwise, no need to uninstall anything. Just delete the ubuntu partitions (be careful not to delete a partition you use for windows), format that space as NTFS and use it trough windows. Use windows cd/dvd to restore windows bootloader on the MBR in case you have grub and that's it.

If you still feel like learning new things and having windows on one hdd with it's own bootloader, and ubuntu on another one with grub, I think I figured out what you did wrong last time. You see, except for the linux reference of the drives and partition like sda, sdb, sda1, sda2, sdb1, etc, there are references for grub hd0 (first disk), hd1 (second), etc.

You had your windows disk and that was the first option in BIOS right? When you started installing ubuntu, your windows disk was still first in the boot order, so the BIOS together with grub assigned hd0 for the windows disk and hd1 for the disk where you instaled ubuntu.

After ubuntu was installed, and grub on the same disk, you switched the disk order in BIOS (but too late), and hd0 is assigned to ubuntu disk, while hd1 to windows disk. That is why grub is not booting neither windows or ubuntu if you switch the order.

You should have done it BEFORE starting to install ubuntu. You tell grub to install on the ubuntu disk but because the BIOS is correctly set up already, the hd0 and hd1 are assigned as they should be. If you do not make the switch in BIOS before installing ubuntu, then as a result grub will look for windows on the ubuntu disk, and for ubuntu on the windows disk, and nothing can boot.

I haven't dealt with multi drive systems a lot but I believe what I said above is correct. Grub is not to blame if you told it to switch the drives but only after it was already installed and set up.

---

### Post by EugeneS on 2009-11-23
I agree that there is no need to fix something that ain't broken, but you have to agree that it is always better to let the system work in a "natural" way. And the configuration I wanted to achieve lets each system work in its natural way.

With current setup, when GRUB is installed over the NTLDR, if something happen to the Ubuntu disk, it will reflect on the boot process of both systems.

Moreover, it seemed like pretty easy configuration to be done.

Now regarding your recommendation to switch the disks order in BIOS, in fact I didn't intend to make this switch at all. My plan was to leave the disks as they are.

The windows loader only had to refer to the second disk(the one with Ubuntu installed on it) MBR.

P.S. I already had a similar configuration(GRUB over NTLDR) in my past. One day the GRUB just died, after it was working correctly for few weeks. The result was that I couldn't log on any system.

Could you please explain how can use the Windows start up disk in order to restore the MBR?

---

### Post by presence1960 on 2009-11-23
> **EugeneS said:**
> 

Could you please explain how can use the Windows start up disk in order to restore the MBR?

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) - if you have windows 7 use instructions for vista

---

