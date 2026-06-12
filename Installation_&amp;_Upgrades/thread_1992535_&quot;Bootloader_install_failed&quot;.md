---
title: "&quot;Bootloader install failed&quot;"
date: 2012-05-31
forum: Installation &amp; Upgrades
---

### Post by MagicalMonkey on 2012-05-31
Hello Ubuntu community,
[INDENT]Today I attempted to install Ubuntu onto my hp laptop from a usb flash drive. I selected to have it dual boot along side with windows vista. Everything seemed to install correctly, but after it installed some files it got a "fatal error". Saying "grub-install /dev/sda" had failed. I pressed "ok" and received a prompt similar to the set up below.[/INDENT]

**Ubuntu Version:** 12.04

> [I][INDENT][INDENT]Sorry, an error occured and it was not possible to install the bootloader at the specified location.[/INDENT][/INDENT]

How would you like to proceed?

[INDENT] Choose a different device to install the bootloader on:
[INDENT]/dev/sdb[/INDENT]

 Continue without bootloader.

 Cancel installation.[/INDENT][/I]


So I proceeded with the first option. A pop-up came up and said the installation was complete and that you may now restart the device, bu the the Bootloader install failed window as seen above showed again. 

So my question is what should I do to fix this?

---

### Post by wilee-nilee on 2012-05-31
Use this tool, choose the bootinfo summary and post the http address, wait for us to look at the script before using any other functions in the tool.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by MagicalMonkey on 2012-05-31
> **wilee-nilee said:**
> Use this tool, choose the bootinfo summary and post the http address, wait for us to look at the script before using any other functions in the tool.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Ok after further investigation it turns out sdb is my flashdrive that I am trying to install it from. My flashdrive does not have the memory required to do this. So I would rather it download to my computers hard drive. It appears that the partitioning process worked and it created sda1 and sda2. By clicking the drop down menu I get these options.

/dev/sda ...           ATA SAMSUNG HM250JI (250.1 GB)
/dev/sda1 ...         Windows Vista (loader)
/dev/sda5 ... 
/dev/sda2 ...         Windows Vista (loader)

Now by taking into consideration that it would be a bad thing to put the bootloader on to sda and that I just simply cant put it on sda5, which one do I install it to.

I believe that sda1 is my larger partition where I want my Windows Vista to remain, but I am not sure. I don't want to make any mistakes when considering that many mess up a fresh installation onto a vista computer.

---

### Post by wilee-nilee on 2012-05-31
> **MagicalMonkey said:**
> Ok after further investigation it turns out sdb is my flashdrive that I am trying to install it from. My flashdrive does not have the memory required to do this. So I would rather it download to my computers hard drive. It appears that the partitioning process worked and it created sda1 and sda2. By clicking the drop down menu I get these options.

/dev/sda ...           ATA SAMSUNG HM250JI (250.1 GB)
/dev/sda1 ...         Windows Vista (loader)
/dev/sda5 ... 
/dev/sda2 ...         Windows Vista (loader)

Now by taking into consideration that it would be a bad thing to put the bootloader on to sda and that I just simply cant put it on sda5, which one do I install it to.

I believe that sda1 is my larger partition where I want my Windows Vista to remain, but I am not sure. I don't want to make any mistakes when considering that many mess up a fresh installation onto a vista computer.

I can't really help you without seeing the script.

---

### Post by oldfred on 2012-05-31
If it installed to your flash drive it just is in the MBR of the flash drive. When it says grub install, it is just the grub2 boot loader that is installed to the very first sector of the hard drive or MBR. It also uses some of the space between the MBR and the first partition for core.img or more of grub2.

You probably could boot hard drive by using BIOS to choose flash drive. If using boot repair you want to install to sda or the drive not any partitions. If you install to the Windows partitions it will corrupt Windows but it normally is repairable.

---

### Post by MagicalMonkey on 2012-05-31
> **wilee-nilee said:**
> I can't really help you without seeing the script.

Should I choose to "cancel the installation" and run "Boot-Repair" or should I select "Choose a different device to install bootloader" and select "/dev/sda" from the drop down menu?

Sorry if I seem as though I am not following you guidance, just want the easiest and safest solution. For all I know there is no problem except that it needs to install to sda instead of my flashdrive (sdb).

---

### Post by MagicalMonkey on 2012-05-31
> **oldfred said:**
> If it installed to your flash drive it just is in the MBR of the flash drive. When it says grub install, it is just the grub2 boot loader that is installed to the very first sector of the hard drive or MBR. It also uses some of the space between the MBR and the first partition for core.img or more of grub2.

You probably could boot hard drive by using BIOS to choose flash drive. If using boot repair you want to install to sda or the drive not any partitions. If you install to the Windows partitions it will corrupt Windows but it normally is repairable.

I dont want it to run from the flashdrive. I also have ubuntu installed onto the computer, I just need to put Bootloader on there. So after some more research I should tell this prompt to install boot loader to my first option, /dev/sda. Is this correct?

**Edit:** Sorry for double post. Could have sworn the first post didn't go through.

**Edit:**
I tried to use /dev/sda, but I got the same error.

---

### Post by wilee-nilee on 2012-05-31
Here is a picture, it can be confusing I understand. ;)

When you run this you will get a web address where the script is, so post that address.

[ATTACH]219030[/ATTACH]

This script is helpful as a debugging tool, we don't want to guess, and it will show what the problems may be to the other helpers that work in this general area.

On occasion with a flash boot, the hard drive and the flash get reversed so the flash is reading as sda. 

There also could be a non mbr partitioning set up like gpt or another, this script will tell us what is up.

---

### Post by MagicalMonkey on 2012-05-31
> **wilee-nilee said:**
> Here is a picture, it can be confusing I understand. ;)

When you run this you will get a web address where the script is, so post that address.

[ATTACH]219030[/ATTACH]

This script is helpful as a debugging tool, we don't want to guess, and it will show what the problems may be to the other helpers that work in this general area.

On occasion with a flash boot, the hard drive and the flash get reversed so the flash is reading as sda. 

There also could be a non mbr partitioning set up like gpt or another, this script will tell us what is up.

[http://paste.ubuntu.com/1017292/](http://paste.ubuntu.com/1017292/)


The script is to big to paste here.

---

### Post by wilee-nilee on 2012-05-31
Looks like you ran the boot-repair recommended repair this did not fix it, you have grub in the sda mbr?

You are also missing key boot files for vista, at least the script says so.

 Lets try a chroot to get the ubuntu to boot just run these commands as posted from a live cd.

```
sudo mount /dev/sda5 /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
``````
sudo chroot /mnt
``````
grub-install /dev/sda
``````
grub-install --recheck /dev/sda
``````
update-grub
``````
Exit chroot: CTRL-D on keyboard
``````
sudo reboot
```If this does not work grub may need a purge and reinstall hard to say. 

We will have to see if vista boots as well.

When you get into the Ubuntu install if you do, run this command, to see if vista is showing.

```
sudo update-grub
```

---

### Post by MagicalMonkey on 2012-05-31
> **wilee-nilee said:**
> Looks like you ran the boot-repair recommended repair this did not fix it, you have grub in the sda mbr?

You are also missing key boot files for vista, at least the script says so.

 Lets try a chroot to get the ubuntu to boot just run these commands as posted from a live cd.

```
sudo mount /dev/sda5 /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
``````
sudo chroot /mnt
``````
grub-install /dev/sda
``````
grub-install --recheck /dev/sda
``````
update-grub
``````
Exit chroot: CTRL-D on keyboard
``````
sudo reboot
```If this does not work grub may need a purge and reinstall hard to say. 

We will have to see if vista boots as well.

Noob question. What do I do so I can run these commands?

Also thanks for the help. :)

---

### Post by wilee-nilee on 2012-05-31
> **MagicalMonkey said:**
> Noob question. What do I do so I can run these commands?

Also thanks for the help. :)

Boot to a live cd/or flash and run this command to confirm the HD is being seen as sda still.

```
sudo fdisk -lu
```If still sda copy and paste each command from the last post to a terminal and run as is.

If the HD is seen as sdb instead substitute the b for an a in these commands in the list in the last post.

```
sudo mount /dev/sdb1 /mnt
``````
grub-install /dev/sdb
``````
grub-install --recheck /dev/sdb
```So I have isolated these out for change if the HD is being read as sdb. So you would change these commands in the last post to these.

Does that make sense it can be confusing, especially the way I explain it. :)

---

### Post by MagicalMonkey on 2012-05-31
> **wilee-nilee said:**
> Boot to a live cd/or flash and run this command to confirm the HD is being seen as sda still.

```
sudo fdisk -lu
```If still sda copy and paste each command from the last post to a terminal and run as is.

If the HD is seen as sdb instead substitute the b for an a in these commands in the list in the last post.

```
sudo mount /dev/sdb1 /mnt
``````
grub-install /dev/sdb
``````
grub-install --recheck /dev/sdb
```So I have isolated these out for change if the HD is being read as sdb. So you would change these commands in the last post to these.

Does that make sense it can be confusing, especially the way I explain it. :)

Ok I understand. Run it from my flash drive rather than from my hardrive. Thanks.

---

### Post by wilee-nilee on 2012-05-31
> **MagicalMonkey said:**
> Ok I understand. Run it from my flash drive rather than from my hardrive. Thanks.

Cool so I am assuming here that you cannot boot anything.

If it is that you can boot ubuntu but not vista, then these commands will not fix that.

Am I correct with my assumption?

Your mention of running the commands from the HD is confusing as far as what I have tried to understand in your situation.

---

### Post by MagicalMonkey on 2012-05-31
> **wilee-nilee said:**
> Cool so I am assuming here that you cannot boot anything.

If it is that you can boot ubuntu but not vista, then these commands will not fix that.

Am I correct with my assumption?

Your mention of running the commands from the HD is confusing as far as what I have tried to understand in your situation.

I can boot Vista. I can now boot from the flash drive after reformatting it and re installing ubuntu onto it. I think I might try to reinstall UBUNTU, but do I need to get rid of the previously installed items?

Edit: I think the problem was with the installation on to my flash drive. Just dont really know where to go from here.

---

### Post by wilee-nilee on 2012-05-31
> **MagicalMonkey said:**
> I can boot Vista. I can now boot from the flash drive after reformatting it and re installing ubuntu onto it. I think I might try to reinstall UBUNTU, but do I need to get rid of the previously installed items?

Edit: I think the problem was with the installation on to my flash drive. Just dont really know where to go from here.

To be honest I am just not understanding you at this point.

We are not on the same page, good luck. ;)

---

### Post by MagicalMonkey on 2012-05-31
> **wilee-nilee said:**
> To be honest I am just not understanding you at this point.

We are not on the same page, good luck. ;)

No wait! Your my security blanket! jk

What is happening now is this. Boot loader is installed onto my computer. I was able to get the trial UBUNTU to work. My question is this. Can I just go through the same process I did before? Or do I need to uninstall bootloader and any other stuff that managed its way onto my computer. BTW I am talking to you from my other computer, my desktop.

---

### Post by oldfred on 2012-05-31
If you used the auto install and do that again, it will shrink something and squeeze in another / (root) partition.  That will leave your old install as unused space.

You now need to use Something Else or manual install, so you can overwrite your existing install. You then have to choose the partition you installed to sda5? and select / and format it (reformat) to ext4. If you have swap it will auto find it.
 If you used manual install before and created a separate /home partition you need to mount it as part of the install but DO NOT format it.

At the bottom of the partitioning screen is a combo box. It should default to the drive or sda. Leave that as the default.

---

### Post by Nico156 on 2012-06-12
edit

---

### Post by YannBuntu on 2012-06-14
Hello

> **MagicalMonkey said:**
> [http://paste.ubuntu.com/1017292/](http://paste.ubuntu.com/1017292/)


- we can see that grub-setup returns an error.
- / is between 157GB and 235GB, and it is an ATA disk, so it may be this problem: [http://ubuntuforums.org/showthread.php?t=1998257](http://ubuntuforums.org/showthread.php?t=1998257)

---

