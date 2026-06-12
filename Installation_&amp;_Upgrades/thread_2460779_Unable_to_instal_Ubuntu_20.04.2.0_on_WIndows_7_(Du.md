---
title: "Unable to instal Ubuntu 20.04.2.0 on WIndows 7 (Dual Boot)"
date: 2021-04-18
forum: Installation &amp; Upgrades
---

### Post by luke486 on 2021-04-18
I'm new to linux so bear with me.
I wanted to install Ubuntu alongside windows 7 on my laptop. The problem is that the computer doesn't see any of the windows partitions (I also created one just for linux). It offers to erease the whole disk.
Attached is the printscreen.
Any ideas how to fix it?

P.S. I tried WUBI but it doesn't work as well. It won't find the iso file in the dvd drive.

Thanks,
Lukasz.

---

### Post by CelticWarrior on 2021-04-18
Welcome.

First of all, Windows 7 is out of support and shouldn't be used online under NO CIRCUMSTANCE.
So, you may consider replacing it instead of a dual-boot.

If you still want to do a dual-boot after all this warnings please check whether or not you're using: 1) RAID or Intel RST modes in BIOS/UEFI -> It must be AHCI but if you change this mode without installing the corresponding support in Windows, it won't boot; or 2) Dynamic partitions in Windows -> This are Microsoft proprietary and incompatible with Linux, there's no solution other than format.

Now, it's up to you.

---

### Post by DuckHook on 2021-04-18
Welcome to the forums, luke486

There are others here who are far better at helping you with your dual boot question, so I will leave the technical aspects to them.

I just wanted to comment on your larger picture. Please feel free to ignore me if my advice is not suitable to your needs:

[list=1]
[*]I'm sure you realize that Win 7 has been EoL for a long time now and running it on its own separate partition is a bad idea due to the extreme security risk that it now represents.
[*]Hence, you may wish to run it within a Virtual Machine instead. This can be done quite nicely if you install Ubuntu as your sole OS, then install a VM like VirtualBox or VMWare or Linux's native hypervisor, KVM.
[*]WUBI has been dead for years. It is no longer under active development, is no longer maintained, and always was a terrible kludge that rendered installs exceedingly brittle. Not at all recommended.
[*]If you wish to run Windows in a dual boot with Ubuntu, at least move to Win 10 which is up to date and continues to be patched.
[/list]

---

### Post by tea for one on 2021-04-18
Yes, as already mentioned by CelticWarrior and DuckHook, Windows 7 is unsupported and should be removed or, alternatively, upgraded to Windows 10.

This website may also help you [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by ajgreeny on 2021-04-18
Wubi is now dead and just about buried so forget that, though I believe there is a version of it totally unsupported by Ubuntu or Caninical.
Wubi was never intended to be used as a means of a full dual boot system as it was more like running a huge program (Ubuntu) in Windows, rather than a "real" dual boot.

Your screenshot looks like it is from Windows; is that correct, and is the one disk shown the correct size for your hard disk?
How did you attempt to install Ubuntu?  How did you create the install medium, and was that a DVD or USB?

Some USB installation disk creation programs available for Windows, eg Rufus will I believe create a UEFI boot disk only, but Windows 7 was always installed in BIOS mode so that may be the problem you have seen.  Windows 7 is now EOL so you shpould not be using it any more, certainly not as an internet facing system.

Give us as much detailed information as you can and we will try to assist but at present there is not enough to help you much further.

---

### Post by grahammechanical on 2021-04-18
Please remember to use Windows tools to create/delete/move/resize Windows partitions and always run Windows defrag afterward. Use Linux/Ubuntu tools to create/delete/move/resize Linux partitions.

This is confusing me.

> The problem is that the computer doesn't see any of the windows  partitions (I also created one just for linux). It offers to erease the  whole disk.

Instead of "computer" do you mean the Ubuntu installer? If the hard drive does not have enough unallocated space to create a partition or two to install Ubuntu in it will most likely only offer to Erase Disc and Install Ubuntu. The installer should have offered you the option of  Something Else. That option will allow you to choose which partition to install Ubuntu in.

This is some useful information about dual booting Windows 7 and Ubuntu. It is from the Windows 7 time period.

[https://ubuntu.com/blog/how-to-upgrade-from-windows-7-to-ubuntu-installation](https://ubuntu.com/blog/how-to-upgrade-from-windows-7-to-ubuntu-installation)

Do not install Ubuntu 18.04. The Ubuntu you should be installing is Ubuntu 20.04.

Regards

---

### Post by luke486 on 2021-04-19
Windows 7 isn't supported anymore that's true, however security is not my concern. The laptop on which it's installed is used just for "experiments". No worries there. I will take a look at what you wrote about dynamic partitions and all. At this point It's hard for me to refer to these methods as I lack knowledge.
Thanks for your reply.

---

### Post by luke486 on 2021-04-19
[COLOR=#000000]Windows 7 isn't supported anymore that's true, however security is not my concern. The laptop on which it's installed is used just for "experiments". No worries there. I will take a look at what you wrote about dynamic partitions and all. At this point It's hard for me to refer to these methods as I lack knowledge.[/COLOR]
[COLOR=#000000]Thanks for your reply.[/COLOR]

---

### Post by luke486 on 2021-04-19
Thanks for your reply. I do use Windows 10 on every day basis. The Windows 7 and the laptop on which it is installed isn't used for any sensitive work. I have no experience with Virtal boxes, I'll read about it, though. Thanks again.

---

### Post by luke486 on 2021-04-19
The screenshot is from the Ubuntu installer. I downloaded ISO image and burned it onto DVD. So then I put the DVD into the drive, rebooted the computer and the installation began smoothly. At some point the installation process reaches the partitioning part and what pops up is the screenshot. And yes, the disk size is correct, but it shows as the whole disk instead of windows partitions and one partition which I created for linux (EXt4 I think).
It's very strange beacause I have an old PC Desktop with Windows 7 as well and I managed to install Ubunto alongside Windows with no problem (using the same steps as descrived above).
What other specific information would be helpful for you?

Thanks,
Lukasz.

---

### Post by luke486 on 2021-04-19
Yes, I mean the installer. The unallocated space is not a problem. I had created a whole separate partition for linux (Ext4 I think). Even if there was no space, the installer usually gives me an option to shrink partiition C with Windows on it. But not this time...strange.
I was able to install Ubuntu on an old Desktop computer with Windows 7 on it as well. But the laptop is problematic.

---

### Post by CelticWarrior on 2021-04-19
> [COLOR=#000000]I had created a whole separate partition for linux (Ext4 I think)[/COLOR]
No, you couldn't have created an EXT4 partition from Windows.
And no partition is needed, unallocated space is and unallocated space isn't a partition. The installer should detect the unallocated space and use it in the "install alongside" option. It can also offer to shrink other partitions to have unallocated space where then to create its own required partitions for the Ubuntu installation. That, however, won't happen is MBR ("msdos") drives with 4 primary partitions already, a limitation of the old partitioning table, not the installer's or Ubuntu's.

But again, DON'T USE WINDOWS 7!!!!
Simply choose "Erase and install..." and problem solved.

---

### Post by Impavidus on 2021-04-19
Having nothing sensitive or valuable on that computer isn't enough to stop worrying about hackers on Windows 7 (or any other system). They may be interested in other things than stealing your files or taking them hostage. For example, sending spam, routing (or hosting) questionable content, mining bitcoins, cracking other people's passwords, running ddos attacks, whatever. So best to simply wipe Windows 7. If you continue using it, make sure it isn't connected to the web.

If you want to know what's going on now, let us have a look at your current partitioning. That screenshot isn't very clear. Try this in a terminal:```
sudo parted -l
```(that's a lower case ell)

---

### Post by DuckHook on 2021-04-19
> **Impavidus said:**
> Having nothing sensitive or valuable on that computer isn't enough to stop worrying about hackers on Windows 7 (or any other system). They may be interested in other things than stealing your files or taking them hostage. For example, sending spam, routing (or hosting) questionable content, mining bitcoins, cracking other people's passwords, running ddos attacks, whatever. So best to simply wipe Windows 7. If you continue using it, make sure it isn't connected to the web.
@OP

As per Impavidus's warning, your machine getting pwned isn't just about you but is about the rest of us. The drones of the various botnets that infest the internet are comprised of pwned machines with exactly such dead OSes as yours.

Furthermore, a pwned machine serves as a wide open gateway into your LAN, which the scumbags then leverage to infect the rest of your private network. In fact, it is the classical method to bypass router firewalls. Once in, the rest of your LAN is wide open to them, especially given the fact that such a cavalier approach to the most highly compromised OS ever developed means you're unlikely to have implemented any defence in depth.

---

### Post by rsteinmetz70112 on 2021-04-19
You can still upgrade Windows 7 to Windows 10 if you wish to. Simply go to  Windows Media Creation Tool  website.

---

### Post by luke486 on 2021-04-26
Thanks about your advice on Windows 7, I'll keep that in mind. As far as EXT4, actually I was able to create it on Windows. I used the program called Partition Magic. It allows for creating any partition you want, including partitions devoted to linux.
I get the idea of unalloctaed space but since I am a bit cautios about partitioning during the linux instllation - I've always don it this way: I would create linux partition (EXT , Riser or whatever else linuex can run on), run the installation DVD, the installer would show all the partitions available (windows partitions AND the linux one that I had created), next I would choose the EXT4 and install linux on it. There was ususally the second option that came with the installer - I could choose to shrink Windows on the C partition and install linux alongside it. All done automatically, of course. Sadly, none of the mentioned options work now. The command line you gave me wouldn't really help much at this point since I the only OS on my laptop is Windows 7. I can try and use it on on my PC (on which I have WIndows 7 and Ubuntu installed) and see what it tells me (I had no problems with installing Ubuntu on this machine)

---

### Post by luke486 on 2021-04-26
Again, thanks for your concern but that's not the issue I turned to you guys about.

---

### Post by ActionParsnip on 2021-04-26
Resize the NTFS in Windows, then install Ubuntu to the freed space. NTFS is proprietary to Microsoft so only they know how it really works.

---

### Post by oldfred on 2021-04-26
If NTFS is hibernated or corrupted (needing chkdsk), then Linux NTFS driver will not see it.
If drive converted to proprietary dynamic partitions, Linux NTFS driver will not see it.

Post these from live installer in live mode, to see partitions:
sudo parted -l
sudo fdisk -lu

---

### Post by luke486 on 2021-04-27
OK, I'll try these commands in live mode and make a printscreen; I'll also try to resize the NTFS partition like you suggested before trying to install Ubuntu. One thing bothers me though. Let's say the NTFS partition (converted to EXT4) is corrupted and Linux NTFS driver doesn't see it, but why wouldn't the linux installer offer me to shrink the C partition with Windows 7 on? Is the C partition also corrupted? If so, WIndows doesn't mind it, I guess :).

---

### Post by yancek on 2021-04-27
>   Let's say the NTFS partition (converted to EXT4) is corrupted and Linux  NTFS driver doesn't see it, but why wouldn't the linux installer offer  me to shrink the C partition with Windows 7 on? 

That  is the reason for the manual install option (Somethiing Else).  If you want a non-standard installation you need to tell the installer what you want.  Generally, the first option is to Erase disk and install whichever OS you are booting from (Ubuntu).  I've not used the Install Alongside option but my understanding is that you should have that option if you have unallocated space and should also be offered if you have a valid Linux filesystem on a partition.  The installer isn't telepathic so it doesn't know if you want to shrink your primary windows partition.  Most users do that with Disk Management in windows, then reboot to test it and probably run chkdsk  before trying to install LInux to verify that windows boots.  That's a non-standard install and you are always better off using windows tools to manage windows and Linux tools to manage LInux.

---

### Post by tea for one on 2021-04-28
> **yancek said:**
> The installer isn't telepathic so it doesn't know if you want to shrink your primary windows partition.  Most users do that with [COLOR="#0000FF"]Disk Management in windows[/COLOR], then [COLOR="#0000FF"]reboot to test it and probably run chkdsk[/COLOR]  before trying to install LInux to verify that windows boots.  That's a non-standard install and you are always better off [COLOR="#0000FF"]using windows tools to manage windows[/COLOR] and [COLOR="#FF0000"]Linux tools to manage LInux.[/COLOR]

This is the best bit of advice to try and avoid any difficulty with Windows partitions.

---

### Post by luke486 on 2021-05-01
I haven't resized the partitions yet but I deleted the "linux" partition that I had previously created for the sake of installing Ubuntu onto it. So now, apart from regular windows ntfs partitions, there is around 10GB of unallocated space.
I unsuccessfully tried to instal Ubuntu alongside Windows again. I did some printscreens illustrating the process. I put the in the google document to make it clear.

[https://docs.google.com/document/d/1aXSom6yxk12k-WdBqYT-SFmu-1KGezIfEToOvFPkBAI/edit?usp=sharing](https://docs.google.com/document/d/1aXSom6yxk12k-WdBqYT-SFmu-1KGezIfEToOvFPkBAI/edit?usp=sharing)

Any ideas?

Thanks,
Luaksz.

---

### Post by luke486 on 2021-05-01
Sorry for double posting. The format of the forum is somewhat confusing. I was trying to reply to some other user in this thread.

---

### Post by oldfred on 2021-05-01
10GB is really too small to do much.
I have about 8GB used of 30GB in my Ubuntu install, but all data in over 150GB on data partition.
And I aggressively houseclean. Just deleting an ISO I downloaded made my / 2GB larger temporarily.

---

### Post by ubfan1 on 2021-05-01
As oldfred had previously mentioned, the old MSDOS partitioning is limited to four primary partitions.  You already have the 4 (the extended counts as a primary), so shrinking the C primary will not allow you to make another primary.  Only logical partitions may be added, and all of those must be inside the extended partition.  so shrink one of those logical partitions, and the Ubuntu installer should find the room it needs.

---

### Post by luke486 on 2021-05-02
It doesn't work. I shrank the logical partition D which gave me 20GB of unallocated space, but the Ubuntu installer still isn't able to detect that. Again, it only offers to erase the whole disk (it doesn't see ANY other partitions, inluding the C with Win7 on it). 
Basically it looks identical to what I presented in my google doc. Any ideas?

---

### Post by tea for one on 2021-05-02
Did you run chkdsk (Windows tool) on all your Windows partitions?

Is Windows in hibernation?

---

### Post by Impavidus on 2021-05-02
I've been looking at your google drive document (I think it's easier to copy text from the terminal to your forum posts and attatch screenshots), and there's something very weird about your partitioning. You've got 3 primary partitions, 1 extended partition with 2 logical partitions inside and a bit of unallocated space at the end. Nothing strange about that. But the third primary partition (sda3) sits in the middle of the extended partition (sda4). It's positioned on an unallocated part of the extended partition, between sda5 and sda6, so it doesn't directly lead to data corruption, but I doubt this is according to standards and I'm quite sure this will confuse many partitioning tools.

---

### Post by luke486 on 2021-05-02
I checked C (no errors). I forgot to check the remaining partitions (I'm doing it now). As for hibernation I'm a bit confused what it means as far as Windows goes. I mean when I turn on my laptop it, Windows 7 boots and it works ...like a regular OS. I've never tried putting it in hibernation  (I can't even imagine if it's possible while installation of Ubuntu). I'll run chkdisk and let you know.

---

### Post by luke486 on 2021-05-02
Impavidus, the partitions may be screwed up. Hard to tell (although Ihad been using this laptop for the past 10 years and no problems occured). Thing is what to do about it? Any ideas? And remember..I'm a layman when it comes to partitions and stuff. So if you have any ideas, let me know.

---

### Post by oldfred on 2021-05-02
The other thing that Windows does is convert to a proprietary dynamic partitioning scheme that Linux does not normally work with. Shown as SFS or LDM.

Post these:
sudo parted -l
sudo fdisk -lu

---

### Post by Impavidus on 2021-05-03
Chances are this problem appeared recently, when you attempted to create a partition for Ubuntu. Your partitioning tool tried to be clever by creating non-adjacent logical partitions. Sufficiently naïve tools don't even notice that there's a primary partition overlapping your logical partition, so it works most of the time, but other partitioning tools may not be able to handle this. Maybe the partitioning tool you used to create this layout can undo it. Else, it is shuffling things around manually (and I'm not confident enough I can tell you how to do it exactly) or wiping the drive and starting fresh.

---

### Post by Geoff_Lane on 2021-05-03
> **luke486 said:**
> I'm new to linux so bear with me.
I wanted to install Ubuntu alongside windows 7 on my laptop. The problem is that the computer doesn't see any of the windows partitions (I also created one just for linux). It offers to erease the whole disk.
Attached is the printscreen.
Any ideas how to fix it?

P.S. I tried WUBI but it doesn't work as well. It won't find the iso file in the dvd drive.

Thanks,
Lukasz.

Thee Ubuntu installation procedure usually states another Operating System has been detected then asks if you want to install Ubuntu (not sure of exact wording) beside current Operating System, Use the entire disk or Advanced Options where you should be able to install it to the partition you created for it.

Geoff

---

### Post by luke486 on 2021-05-03
I used Acronis Disk Director 12 to create the partitions (not Partition Magic like I mentioned earlier). This program has always worked for me. Well, anyways, thanks for your reply.

---

### Post by luke486 on 2021-05-12
I do know that this is what normally happens during the installation. It's not happening in this case, hence my posts here.

---

### Post by rickticktock on 2021-05-13
I say chaps,
    I installed Ubuntu onto my Samsung Series9 laptop which is pretty old now. It came with W8, but worked better with W7 - until it got some malware so I formatted its disk and did Ubuntu. My point is that Ubuntu 18 works just fine, and I'm totally happy with it, but it refuses to upgrade to 20. I assume that the laptop can't cope with 20. So anyone with an older computer (which came with W7) shouldn't be too ambitious for the latest version.
TTFN
Rickticktock

---

### Post by ubfan1 on 2021-05-13
My Lenovo W520 (UEFI but pre secure boot) came with Windows 7, and runs Ubuntu 20.04 just fine.  Didn't Samsung have limited nvram problems early on?  I know at some point, grub(?) got enthusiastic  about adding boot entries, and jumped from six or so boot entries to 24 -- everything you could image, on disks that didn't even exist.  Maybe try a legacy install, or maybe just a legacy grub (strange, but  the legacy grub.cfg does not prevent Ubuntu from booting UEFI-- wont work for Windows however).

---

### Post by oldfred on 2021-05-13
Full Ubuntu may be an issue.

I used to install standard Ubuntu and then when Ubuntu went to Unity installed the fallback/flashback gui which was lighter weight. I used this on my old laptop, but for consistency used it also on desktops.
Recently converted to 20.04 Kubuntu as main working install on desktops, and decided to try it on old laptop. It worked and is ok, even though one of the lighter weight flavors may be better.
Old laptop would not install standard Ubuntu 20.04, originally had to install 20.04 server & then fallback which was a bit of a hassle. 
Kubuntu just installed & worked. That laptop only has 1.5GB of RAM so is now very limited.

Older systems:
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

---

