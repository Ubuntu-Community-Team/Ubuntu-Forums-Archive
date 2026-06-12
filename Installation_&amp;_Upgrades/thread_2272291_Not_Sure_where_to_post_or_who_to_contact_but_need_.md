---
title: "Not Sure where to post or who to contact but need massive help"
date: 2015-04-05
forum: Installation &amp; Upgrades
---

### Post by bluealchemy17 on 2015-04-05
[http://paste.ubuntu.com/10744509/](http://paste.ubuntu.com/10744509/)

Above is the Paste Bin from Boot Info. I have also attached my Plymouth Log and Kern Log (for AppArmor).

Here are the issues I can Identify.

Installed (and trying to get working) a Dual Boot with Ubuntu 14.04 Trusty and Windows 8.1. Always have had issues doing dual boot with Windows 8/8.1, never had issues with Windows 7. My computer is an Alienware M17xR3 (Late 2011?). Originally shipped with Windows 7 Home Premium x64. BIOS is NOT EFI as far as I can tell. Has a Hardware RAID controller. Originally shipped with 2x 500GB Hybrid HDD in a RAID 0 configuration. Had a lot less problems setting up dual boot with that. One of the Hard Drives ended up failing, was able to recover the data with Ubuntu and some Forensics programs (TestDisk I think). After that replaced both drives with Non Hybrid HDD both 1 TB setup NOT in RAID.

Plymouth doesn't boot graphically and will only boot in Verbose mode. Also it stops when it tries to Auto-mount my drives. This connects to all the other issues.

When I initially setup the system, I put Ubuntu on the first drive and Windows on the second drive. Very stupidly did this with my 2 external drives plugged in (didn't think it would matter). This connects to the Plymouth problem because the prompt with the Auto-Mounting is because it has problems mounting my external drives at boot, as far as I can tell.

Another Issue I noticed is that the mount points for the drives are screwed up. My external drives are mounted as sda and sdb and also identified as internal drives and not as external. Problem I think, Including with booting. Since the externals were mounted first (A and B), my actual internal drives are Auto-Mounted as sdc and sdd (Ubuntu as C and Windows as D). Every time I run Boot-Repair or Boot-Info it assumes that my externals (A and B) are internal and prompts me asking if sdc is external or not, which is actually my primary drive.

So far GRUB works, not sure if Boot-Repair installed GRUB or GRUB2. Primary drive (Ubuntu (sdc)) is partitioned as Extended Partition with 2 Logical Partitions within (Root and Swap); I did this because I was under the impression that Extended/Logical partitions were more stable than Primary partitions. Second drive (Windows (sdd)) is partitioned as a system reserved partition (identified as the boot partition) and the main Windows partition (assumed the equivalent of Root partition). Incorrect mount points of drives results in Boot-Repair installing GRUB on all 4 drives instead of just the internal drives, also I can't find the option to stop Boot-Repair from installing GRUB on the 2 external drives (or identifying them as external). Further I'm confused as to which Windows partition (sdd1 (System Reserved) or sdd2 (Windows Root?)) to have GRUB installed on and which one to place the boot flag onto. If I select to have GRUB boot to sdd1, the menu goes away and you just see the background of GRUB (like it's transitioning normally) but it just stays there, no progress. If I indicate to boot to sdd2, GRUB will transition to the drive and sometimes I reach the Windows equivalent of Plymouth (Windows logo and progress indicator), but it just sits there, no further progress.

Also, Having a lot of AppArmor issues and getting a lot of system crashes and program crashes. And Messages Indicator will not load. Tried reinstalling any programs I could Identify from the Log file. Additionally, having compatibility issues with Desktop Environments (Unity, Gnome3, Gnome Fallback (Compiz & Metacity), and Cinnamon), assumed that I shouldn't since all are Gnome Based.

Have no idea who to contact for help or all of what logs to send you. I hope you can help some.

PS- If there are any other log files you need please contact me and ask.

Have the log files for Plymouth and Kern.log but theyre too big to attach and I don't know how to make a PasteBin Link.

---

### Post by QIII on 2015-04-05
The place to contact someone is right where you posted.

Please use the open forums for support rather than asking for private help.  If a private message conversation occurs, any solution will be unavailable for the rest of the community to benefit from.  A basic tenet of this forum is that others in the community can learn from solutions given here.

Thanks.

---

### Post by grahammechanical on 2015-04-05
It is best to identify one problem at a time and get that solved. Also, what happened in the past if it is no longer relevant because the situation has changed then it is best left as history. 

So, why don't start from the beginning again. Back up any data. Run the Ubuntu Try/live session to test that everything works on your hardware and then re-install. Find out for definite if the boot system is BIOS or UEFI.

I am of the opinion that I install Ubuntu with Unity and if I want to run Ubuntu with Gnome 3 shell, then I install Ubuntu Gnome. I dual or triple boot different flavours of Ubuntu as it avoids complications that are caused by adding alternative desktops (as you have discovered). 

And from 14.04 onwards I think that it is better to use Gnome Session Flashback than Gnome Fallback. I have gnome session flashback on my 15.04 installation and I do not have any complications. But be careful changes we make in one desktop session have an effect in the other desktop sessions as well. We should make a note of what settings we change then we know what to revert to default if problems arise. Make on change at a time and test to see that there are no side effects before making other changes.

Regards

EDIT: A simple thing that you can try is to disconnect those external USB drives. Load into Ubuntu and run

```
sudo update-grub
```

And see if that makes the Grub boot menu clearer.

---

