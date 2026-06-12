---
title: "Boot and BIOS"
date: 2021-08-13
forum: Installation &amp; Upgrades
---

### Post by davidbelow on 2021-08-13
[COLOR=#0C0D0E][FONT=&quot]I have a windows laptop that is getting a little old so I installed a dual boot system using GRUB and UBUNTU so that I could use a quicker running system when required. This worked fine for months however Ubuntu opened yesterday and said it needed to update, I installed the update and it prompted a restart… upon restarting all I get is a black screen indefinitely! GRUB won’t load up, I cant choose an operating system to open or run, the BIOS and UEFI doesn’t appear to be there any more and won’t allow me to access it to try and boot from a usb or anything, a simple update appears to have rendered my laptop completely useless and I have work documents on there that need to be recovered. What on earth has an update done to remove both grub and access to the computer bios??[/FONT][/COLOR]

---

### Post by tea for one on 2021-08-13
When you power on, do you know the dedicated key(s) to reach:-

The UEFI setup
The UEFI boot menu

For example, Intel uses F2 for UEFI setup and F10 for UEFI boot menu.

---

### Post by davidbelow on 2021-08-13
Using f2 does nothing, if I use f12 I can access what it calls the &#8216;boot menu&#8217; but still am unable to access the full bios or uefi to select the device to boot from or change the boot order or boot in to safe mode etc, regardless of what i select it continues to take me to the blank black screen with the exception of the &#8216;hdd recovery&#8217; option which I haven&#8217;t tried and am reluctant to do so as I dont know if it will work and I also can&#8217;t afford to lose the documents and files I have saved on it.

---

### Post by tea for one on 2021-08-13
> **davidbelow said:**
>  if I use f12 I can access what it calls the ‘boot menu’ 
What is displayed there?
> **davidbelow said:**
> I also can’t afford to lose the documents and files I have saved on it.
Boot into a [COLOR="#0000FF"]live[/COLOR] session and back up your documents before doing anything else

When you have completed your backup, while still in a live session, try this via a terminal:-
```
sudo systemctl reboot --firmware-setup
```
It should allow you to reach the UEFI setup.

---

### Post by yancek on 2021-08-13
You should always indicate the version of windows and Ubuntu you are using when you post a problem.  I would also suggest that you specifically define "old" as it has different meanings for some of us.  What year was it purchased if you bought it new.  You should also post the manufacturer if you have a computer purchased from one of them and the specific model.  Some problems are specific to certain manufacturers and specific models  Also, accessing the BIOS firmware uses different keys on different models which is why posting that info is useful.

You indicate this machine is older but then mention UEFI.  Do you know if your machine is using UEFI?  Do you not know the keys you used to access the BIOS previously?

You could try the suggestions at the link below which dea with 20.04 so may not apply.  You haven't indicated which release of Ubuntu you are using so....?  

[https://askubuntu.com/questions/1243134/black-screen-on-startup-ubuntu-20-04](https://askubuntu.com/questions/1243134/black-screen-on-startup-ubuntu-20-04)
.  
I would suggest that you use an external drive for backup and only have it attached when you are doing the backup.  Having important data on your system without a backup is a bad idea and tells everyone it really isn't that important.

Linux systems don't generally access the BIOS firmware on an EFI machine except to create a boot entry.

---

### Post by TheFu on 2021-08-13
HDDs fail all the time.

BTW, to me, old could mean from 2005 - 2010, before UEFI booting existed. It depends on perspective.  I know people who get new computers every 18 months because it is their job and faster means they can make more money, easily paying for the new computer. They give the old computer to family and there is a hand-me-down priority list.  The kids usually want a "new-to-them" computer in August, before school starts, but not again for a year, since that would mean setting up programs and applications when they are busy.  Because they reload all the OSes, that removes some problems caused by 'lazy bits', which Windows seems to have after 3 yrs, especially for computers that don't have proper, weekly, complete, backups.  

Backups aren't just about the data, they also exercise the read-checking in the drive hardware to force refreshing the bits BEFORE they become weak.  Oddly, this means that systems with regular backups are less likely to actually need to restore those backups.

BTW, the boot areas of dual/tri/quad/+ boot systems are shared by all the OSes in UEFI.  The last OS to touch it could be any of those.

Depending on which Ubuntu release is being used and the hardware involved, there are more likely issues that arise due to firmware updates and GPU issues.

The great thing about Linux is that a flash drive with Try Ubuntu environment can be used for days/weeks if necessary.  I ran a media server for almost a week last year when the 4TB boot HDD died and I was waiting for a replacement to arrive.  Gotta keep the family happy, right? When the replacement arrived, a quick restore - the base OS and settings for all programs were working in 30 minutes, but getting all that data copied took some time.

---

