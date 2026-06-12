---
title: "Resizing existing XP partition for use in vmware"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by larsbjo on 2008-10-10
Hi 

I need some advice for how to re-size my existing XP partition and give more space for my Ubuntu. I run my native XP as a virtual machine under vmware and I want to move my documents from XP to Ubuntu so I need more space.

This is my disk today:

 dev/sda1 (NTFS) 125 GB
 dev/sda2 (extended) 65 GB
    dev/sda5 (ext3) 59 GB
    dev/sda6 (linux-swap) 2.5 GB

I want to "move" 60 GB from the sda1 to sda5. 
Is this possible? 
I was considering creating a new FAT32 or NTFS partition that I could share between both XP and Ubuntu. It would preferable be invisible for XP when XP runs as a virtual machine and visible when I boot into XP. Does anyone know how to do this or do you have a better solution. 
I'm trying my best to leave the Windows world but my company is still stuck with windows so I need to maintain my XP for some tasks.

---

### Post by caljohnsmith on 2008-10-10
> **larsbjo said:**
> 
I want to "move" 60 GB from the sda1 to sda5. 
Is this possible? 
Since sda5 physically comes immediately after sda1, you should be able to resize sda1 and add the extra 60 GB to sda5 without any problems. I would recommend using Ubuntu's partition editor gparted, which you will have to use from a Live CD so that your HDD is not in use when you work on it. If you have a Ubuntu Live CD, you can open gparted by pressing ALT + F2 while you are in the Ubuntu desktop, and then type:
```
gksudo gparted 

```
Also note that the Live CD will often use any swap partition it finds on the HDD, so you may have to select your swap partition on the HDD from gparted, right-click, and choose "swapoff" in order to work on the HDD. Once you shrink sda1, you'll need to enlarge sda2 first (the extended partition that contains sda5), and then you can enlarge sda5.

You might have to run a "chkdsk /r" and possibly some other things on your Windows partition to make it fully functional after the resize, so it would be good if you have your Windows Install CD handy. But if you run into any problems with Windows after the resize, usually it's not a big deal at all to get it working again, and I can help you with that if you want.
> **larsbjo said:**
> 
I was considering creating a new FAT32 or NTFS partition that I could share between both XP and Ubuntu. It would preferable be invisible for XP when XP runs as a virtual machine and visible when I boot into XP. Does anyone know how to do this or do you have a better solution. 
I'm trying my best to leave the Windows world but my company is still stuck with windows so I need to maintain my XP for some tasks.
I don't know anything about VMware (I only have some experience with VirtualBox), but I bet there is a way within VMware to restrict access to certain drives/partitions. Sorry I can't be of much help with this, maybe someone else who knows VMware can help you with that. :)

---

### Post by larsbjo on 2008-10-10
Thanks caljohnsmith!

This was the last step in a long process turning my Windows XP environment into a seamless Ubuntu/Windows environment.

I post my findings so far in case someone else is looking for a similar solution. I need to to be able to do the following:

- Run my native Windows as a virtual machine under Ubuntu
- Access my documents from both windows and Ubuntu
- Store all documents encrypted because of company policy (i use truecrypt for this) : [http://www.truecrypt.org/](http://www.truecrypt.org/)
- Boot into a windows for heavy 3D CAD work, or
- Boot into Ubuntu and from there to windows (to read my outlook mail and use VPN)

What i did (before I discovered that i needed another partition was this: 
[http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/](http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/)

To add the "missing" partition do this:
 
1) Download gParted live CD from here : [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and create the CD
2) Boot into the live cd and did a resize the dev/sda1 (NTFS) partition.
3) Formate the empty space as FAT32 (this might have to change due to file size limitations)
4) Boot into Windows using the "native" hardware profile and let windows discover the change in disksize.
5) Boot into Ubuntu, start vmware and click "edit" on the virtual machine. Wmware will complain that the disk has changed. Delete the disks and follow the guide to add it again. Add the same disks as before and leave the new partition out.
6) Mount the truecrypt image (that you store on the new FAT32 disk) in ubuntu.
7) Set the trucrypt disk as a shared folder in vmware.
8) Boot into your virtual windows and choose the "wmvare" hardware profile. 
That's it.

When I boot into windows i mount the trucrypt image in windows and access my files from there. 
When I boot into Ubuntu i mount the trucrypt image in Ubuntu and set it as a shared folder for my vmware windows XP installation. In that way i can reach my files from both windows and Ubuntu. I this way I have only one windows installation, one Linux and no duplicated documents.

I might create a how-to without the extra steps. I guess this might be a relevant problem for anyone wanting to use Linux in a company where everyone else is using windows. 

I'm also happy to hear from anyone having a better solution. :)

---

