---
title: "Grub rescue - Unknown file system - On booting"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by jvd on 2011-10-06
Hello,

I see this error on booting:
==================
Unknown file system
Grub Rescue>
==================
Saw a few resolved threads in this forums and tried sudo .. etc..
But my system does not recognize 'sudo'.
It does not recognize 'cd'

I can type 'ls'
It lists me some (hd0), (hd0, msdos1), .......... 
I tried rebooting with my ubuntu cd but that did not help, could be the disk is bad (Can't verify now)

It is just stuck at the prompt and no way out :P

Now whats my next step.
How do I fix this.

Thanks
Jes

---

### Post by westie457 on 2011-10-06
> **jvd said:**
> Hello,

I see this error on booting:
==================
Unknown file system
Grub Rescue>
==================
Saw a few resolved threads in this forums and tried sudo .. etc..
But my system does not recognize 'sudo'.
It does not recognize 'cd'

I can type 'ls'
It lists me some (hd0), (hd0, msdos1), .......... 
I tried rebooting with my ubuntu cd but that did not help, could be the disk is bad (Can't verify now)

It is just stuck at the prompt and no way out :P

Now whats my next step.
How do I fix this.

Thanks
Jes

Hello and welcome.

Probably a silly question. Did you boot the CD into TRY mode and try to use Disc Utility to check the SMART status of the drive?
Also did you remember to tell the BIOS to boot from the CD? I have made that mistake in the past.

Another thing to try at the Grub menu is either boot into recovery mode or boot into an earlier kernel version.

Are you dual-booting or are you using one OS?

---

### Post by jvd on 2011-10-06
I have Windows Vista and Ubuntu.
I changed my BIOS settings to look at the CD first.
As I am new to Ubuntu, would request a bit detailed instructions.

Many Thanks

---

### Post by westie457 on 2011-10-06
Trying to hunt down the problem so if you think I am being an idiot by asking what seem like silly questions they do serve a purpose.

At the moment you cannot boot Ubuntu because of the Grub error and the CD will not boot. Is that right? Do you get a Grub menu at all? Or does it go straight to that error message?
Are you able to boot into Windows?
If you can boot into Windows then either download and create another CD of the same version you are running now and use that to purge and reinstall Grub using this for guidance. [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You might have to repair your Windows first using either a recovery cd or install disc. Not a restore disc as everything on the hard drive will be lost - certainly the Windows partition will be wiped and reset to the day it left the factory.

If none of the above works for you don't panic as I am a relative newbie despite the number of posts made. These Forums are 24/7 and the more knowledgeable people than me are either not on-line or are looking at other things. We are all volunteers and are willing to help.

---

### Post by jvd on 2011-10-06
Thanks mate.
I will keep you posted on how I succeed with these options.

---

### Post by oldfred on 2011-10-06
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Someone posted that a full powerdown & reboot (cold boot) let him see CD again. Not sure why that would make a difference.

---

### Post by jvd on 2011-10-07
Thanks ppl.
I tried a live cd by downloading a newer version.
This worked.
Now, I am just exploring to see to how I can remove the old versions and more importanly Vista.
I could get hold of some info.

Many Thanks

---

### Post by oldfred on 2011-10-07
A new install of use entire disk will overwrite everything, just be sure to back up any data you want to keep.

I suggest partitioning in advance will will also erase drive or those partitions you want to change. By partitioning in advance you have a bit more control than using the installer version, but the newest versions of the installer offer a lot of flexibility.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by harry_r_s on 2011-10-09
Same Problem here!
Pls help me..
In my case i deleted some extended partition before reboot.
[ I have installed Ubuntu 11.04 in Win7. ]
And no operation works on drives while on live CD(11.04)...
Help me please! I dont want to loose my data.

---

### Post by oldfred on 2011-10-09
@harry_r_s
Please start your own thread.  And post as much info as you can. 

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

