---
title: "[Ubuntu 20.04] Intermittent boot problem after installation"
date: 2022-06-01
forum: Installation &amp; Upgrades
---

### Post by ermann89 on 2022-06-01
Hello, I have recently installed *Ubuntu 20.04* (default installation, wiping the whole disk), I am now having transient issues booting, I am sent to the BIOS page and it looks like it does not find the Linux partition (I don't see it in the boot order). 

Some times I manage to boot successfully either by multiple retries, or by inserting a live USB stick (by this I mean that some times when I do it "recognizes" the Ubuntu partition, not that I boot into the live USB; the live USB is always recognized and I can always boot into it without issues), but in general it's not a regular pattern. 

Some other data:

[LIST]
[*]Laptop is Asus F556U (F556UJ-DM205T), I have updated the BIOS to the latest available version (Version 413 2019/06/06 retrieved from [https://www.asus.com/supportonly/F556UJ/HelpDesk_BIOS/](https://www.asus.com/supportonly/F556UJ/HelpDesk_BIOS/)) 
[*]*boot-repair* report: [https://paste.ubuntu.com/p/THrRPFwkbY/](https://paste.ubuntu.com/p/THrRPFwkbY/) 
[/LIST]

 I would greatly appreciate any help.

---

### Post by tea for one on 2022-06-01
[COLOR="#0000FF"]Line 49[/COLOR] - SecureBoot enabled but mokutil says: SecureBoot enabled

I would disable Secure Boot in the UEFI Set Up and see if the transient boot issues improve.

---

### Post by ermann89 on 2022-06-01
Thanks for the response! I disabled the *secure boot*, however it did not help the situation.

I also reinstalled the operating system, continuing to experience the same issue (managed to log in a two times, installed the updates, etc., but the intermittent boot issue persists, writing this from a live USB). I have pasted the updated *boot-repair* post in the post above (link is [https://paste.ubuntu.com/p/THrRPFwkbY/](https://paste.ubuntu.com/p/THrRPFwkbY/)), now I see:
>  
* SecureBoot disabled - SecureBoot disabled - Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL].*

but I still can't consistently boot into the operating system.

---

### Post by tea for one on 2022-06-01
Some vendors' UEFI settings have a plethora of boot and security options:-
PTT (Platform Trust Technology)
TPM (Trusted Platform Module)
Etc....Etc....

It may be worth double checking the options.

Also, you mentioned that the laptop always recognises and boots the live USB - can you set your hard drive to boot before the external USB?

---

### Post by ermann89 on 2022-06-02
Thanks for the response! The issue is that the hard drive is not shown in the boot options when the problem occurs (otherwise I could select it from the BIOS page and log onto the system). 

For example, by pressing ESC and pulling up the list of bootable mediums at startup, I see only the live USB and the Setup page (the BIOS page) when the problem occurs, and from the BIOS page I see only the live USB. 

When the problem does not occur I also see the disk with my Ubuntu installation, and in terms of order it indeed comes before the live USB.

I was starting to wonder whether it could be a hardware issue with the SSD, however at times it works without a hitch. The intermittent and seeminly random pattern is what I find confusing.

---

### Post by tea for one on 2022-06-02
> **ermann89 said:**
> I was starting to wonder whether it could be a hardware issue with the SSD, however at times it works without a hitch. The intermittent and seemingly random pattern is what I find confusing.
I would also be confused with this lack of consistency. It could certainly be hardware related.
A diagnosis would involve lots of trial and error such as:-
Checking all the internal connections.
Swapping the drive with a known working one.
Using the drive in another PC
Etc.

I wonder if another bootloader may help.
There is a utility [COLOR="#0000FF"]rEFInd[/COLOR] which can be put on a USB stick (i.e. it will not permanently interfere with Grub unless you install it)
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/) > Getting rEFInd > A USB flashdrive image file

May be worth a shot?

---

### Post by ermann89 on 2022-06-02
Thanks, I will try out rEFind.

---

### Post by oldfred on 2022-06-02
I would think this would be fixed by now, but may be worth a test.

How to install Ubuntu on ASUS F556U, JournalError error?  add pci=nomsi 
[https://askubuntu.com/questions/1079540/how-to-install-ubuntu-on-asus-f556u-journalerror-error/1081221#1081221](https://askubuntu.com/questions/1079540/how-to-install-ubuntu-on-asus-f556u-journalerror-error/1081221#1081221)

---

### Post by ermann89 on 2022-06-04
I had already taken a look at that ASUS F556U post and tried the *pci=nomsi* change without success (in one of the attempts at re-installing Ubuntu). That's also when I decided to update the BIOS to the latest available version as suggested by the accepted answer. Unfortunately, neither change fixed my issue. At the moment, I seem to be able to get it to boot after 2/3 retries (crossing fingers), but there is no pattern (sometimes it boots immediately, other times after one retry, etc.).

One thing I'll note is that i never go to the GRUB menu, even in case of successful boot, it just boots directly into Ubuntu and I arrive at the login screen. I remember that in previous Ubuntu versions I arrived at the GRUB screen first and could select which kernel to boot, and whether to boot in recovery mode, etc. Not sure whether this is expected behavior (a change in Ubuntu 20.04?).

---

### Post by sudodus on 2022-06-04
- Is there a difference between cold boot and reboot? I'm asking because the problem might be that the SSD hardware or the UEFI/BIOS system may have some data left from previous operations in some locations, that are not properly reset.

- Would it work (as a workaround) to always have a USB pendrive connected when booting, or does it only work when you change from no pendrive connected? (You could use a small, slow and cheap one, that does not get too hot for example the smallest available Sandisk Cruzer blade.)

- Have you tested that the SSD is working correctly? See for example [this link](https://askubuntu.com/questions/972978/fsck-reports-that-filesystem-still-has-errors/972983#972983).

- Have you tested that the RAM is working correctly? You can run memtest (from an Ubuntu *live* drive when booted in BIOS mode (alias CSM alias legacy mode). You can run memtest overnight and there should be no error at all in the morning.

---

### Post by oldfred on 2022-06-04
If you only have one install, the grub menu is not shown by default & it just continues to boot.
You have to press escape between UEFI/BIOS screen and when grub menu normally shown. May have to try several times or press escape more than once to hit the correct timing.

---

### Post by ermann89 on 2022-06-05
- I don't think there is a difference between cold boot and reboot, I have experienced the issue in both contexts.
- Unfortunately, the Ubuntu installation is not always recognized when I insert a live USB (in other words, inserting a live USB does not always trigger the recognition of the installed Ubuntu system). I am usually able to boot it after various retries.
- Thanks for the information on how to test SSD and RAM, I tried the SMART self test (extended) and the disk was identified as "OK".

---

### Post by ermann89 on 2022-06-05
The following are the *s**martctl -a *and *udiskctl* results:
- *sudo smartctl -a /dev/sda1* output: [https://paste.ubuntu.com/p/yXqZXfDBPY/](https://paste.ubuntu.com/p/yXqZXfDBPY/)
- *sudo udisksctl dump | cat* output: [https://paste.ubuntu.com/p/MSmMtFK8RZ/](https://paste.ubuntu.com/p/MSmMtFK8RZ/)

---

### Post by sudodus on 2022-06-05
I have no good idea how to continue right now. Maybe after a night's sleep ...

---

### Post by tea for one on 2022-06-05
> **sudodus said:**
> I have no good idea how to continue right now. Maybe after a night's sleep ...
Me too - this is quite a rare problem.

Did you try [COLOR="#0000FF"]rEFInd[/COLOR] on a USB stick?

---

### Post by ermann89 on 2022-06-07
Was trying to install rEFInd on a USB stick, while I was formatting it with the Disks utility I saw a very strange occurrence: the Ubuntu disk disppeared, and the system seemed to degrade, I could not launch other applications, plus see the issue with the icons in the attached pictures). Will try to post a picture, but I am writing from my cellphone.

---

### Post by ermann89 on 2022-06-07
I have posted the output of *sudo fdisk -l* in [https://paste.ubuntu.com/p/S7P34xQdsC/](https://paste.ubuntu.com/p/S7P34xQdsC/)

Note that I don't have a *sda1 (EFI) + sda2 (Linux filesystem)* entry, which was there right before and then disappeared (contextually, I saw it disappear from the *Disks* application). Note that this is not the last *sdb** entry, that disk is my live USB. 

So it appears that the Ubuntu disk is randomly disappearing (in this case, it happened right under my nose while I was using the live USB, and as I was not logged into the Ubuntu system I had installed on disk, I did not experience degradation as in the post above, and was able to post this entry to the forum).

---

### Post by sudodus on 2022-06-07
It is possible that your motherboard is malfunctioning, or maybe there is a loose connection to the internal drive. Maybe you can 'wiggle' the connection a few times to remove oxidation (if that is the problem).

---

### Post by ermann89 on 2022-06-07
I think that it might be a hard drive problem, after it "disappeared" while I was using the live USB this morning, it is no longer visible (i.e. from the live USB environment, the *gnome-disks* application does not show it, and if I go forward with the installation Ubuntu does not find any disk).

---

### Post by sudodus on 2022-06-07
At some point you had better try with a new internal drive.

---

### Post by ermann89 on 2022-06-08
I have updates. I discovered that there was an issue with the way the disk was attached to the motherboard, that was the root cause of the issue. I will resolve the ticket.

---

