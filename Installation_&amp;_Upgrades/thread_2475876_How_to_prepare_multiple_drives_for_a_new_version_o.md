---
title: "How to prepare multiple drives for a new version of Ubuntu"
date: 2022-06-10
forum: Installation &amp; Upgrades
---

### Post by couzin2000 on 2022-06-10
I currently am running 18.04 LTS. I tried running 20.04 but didn't work properly for me so I reverted back to 18 through a clean install. 

I'm starting to run into some problems with new software and I need to consider the fact that I will have to upgrade to 22.04 LTS. 
However, last time, upgrading didn't work just as I had planned... ran into [multiple problems with drives]("https://ubuntuforums.org/showthread.php?t=2471454"). I want to fix this.

How do I prepare a PC running Ubuntu to be wiped clean and run a new Ubuntu from scratch? I have 3 "storage" drives (storage1, storage2 and storage3) that are all formatted exFAT. Last time I wiped the system, all permissions for these drives reverted to 'read-only'. I could access the contents but not execute change ownership - [FONT=Courier New]chown [/FONT]was useless. I had to install a separate drive and copy the contents of my storge1 and storage2 to that extrenal USB drive which took forever. I don't want to have to deal with that again. I want to know how to "open up" these permissions for the drives so that when I install a new Ubuntu from scratch I will be able to take ownership of the files and use them as though they were always part of that install... if this is doable at all.

If not, then I'll just have to buy yet another drive and copy everything YET AGAIN.

Thanks for helping out!

---

### Post by oldfred on 2022-06-10
Ownership & permissions are only supported on Linux formatted partitions.
Your exFAT is Microsoft and does not support Linux ownership & permissions. Or you cannot change once mounted.
You have to set a default set of permissions when you mount a partition and with Microsoft formats they have to be a bit more permissive. And ownership always stays as root, but permissions let you use it. 
Much better to change to ext4 or other Linux format if using with Linux. 

External drives typically should not be mounted with fstab. I do use exFAT, but driver may now be included with new install, otherwise you have to manually install that driver.

---

### Post by GhX6GZMB on 2022-06-10
First, are you running Ubuntu or Lubuntu? Your signature opens questions.
Second: are your storage1...3 separate or even external drives? With ExFAT you're in a bad position and will probably need to backup/copy them.
Do you want to use your main drive completely for Linux?
Many things are unclear to me.

---

### Post by couzin2000 on 2022-06-10
> **oldfred said:**
> Ownership & permissions are only supported on Linux formatted partitions.
Your exFAT is Microsoft and does not support Linux ownership & permissions. Or you cannot change once mounted.
You have to set a default set of permissions when you mount a partition and with Microsoft formats they have to be a bit more permissive. And ownership always stays as root, but permissions let you use it. 
Much better to change to ext4 or other Linux format if using with Linux. 

External drives typically should not be mounted with fstab. I do use exFAT, but driver may now be included with new install, otherwise you have to manually install that driver.

Ok. I didn't know exFAT was MS. So what you're saying is that if these drives are all exFAT, permissions wouldn't work at all?
because I currently CAN set permissions. So I must have wrong, then. Maybe it's EXT4 after all. I'll double check.
EDIT: they're all EXT4.

> **ml9104 said:**
> First, are you running Ubuntu or Lubuntu? Your signature opens questions.
Second: are your storage1...3 separate or even external drives? With ExFAT you're in a bad position and will probably need to backup/copy them.
Do you want to use your main drive completely for Linux?
Many things are unclear to me.

Ubuntu 18.04 LTS. I don't see how my sig opens any questions.
Second... they are internal drives that I auto fstab into when booting up. 
My main drive is the issue, I set myself up with 2 SSDs running RAID1, and it's just been a nightmare since day one. I frequently have to fsck one of the drives back into the array because of drops or errors.

SO - if these drives are EXT4, I'm in good shape. How would I go about setting permissions and taking back ownership after having installed a fresh Ubuntu 22.04?

---

### Post by oldfred on 2022-06-10
I just installed 22.04 onmy SSD and used same user & id.
I had no issue mounting  using my data partition on HDD.

If issues then chown & chmod will work on ext4.
I sometimes incorrectly save data using sudo and then do run chown & chmod to correct settings. 

Do not know RAID, there are multiple types of RAID. Typically RAID used for servers to maintain uptime. Less used for desktops as RAID is not backup.
If RAID issues you need to start a new thread and post details of your current RAID configuration and what your issue is.

---

### Post by GhX6GZMB on 2022-06-10
"[COLOR=#000000]Ubuntu 18.04 LTS. I don't see how my sig opens any questions."
It shows Lubuntu 18.04
That's why.

[/COLOR]

---

### Post by scpatl4now on 2022-06-10
Let me see if I can help.  First I want to make sure what I think you are asking is what I think you are asking.  Are storage drives 1,2, and 3 drives where you keep all your data (I am guessing you would not want to delete your files)  Is there a separate drive that has your system files?  If this is the case, and reading your answers thus far it looks like your drives are all EXT4 so what I am thinking is you want to install 22.04 replacing 18.04.  If your storage drives are neither / or home they should not be affected.  Could you post the output of

sudo blkid

So we can verify what is what

---

### Post by couzin2000 on 2022-06-10
> **ml9104 said:**
> "[COLOR=#000000]Ubuntu 18.04 LTS. I don't see how my sig opens any questions."
It shows Lubuntu 18.04
That's why.

[/COLOR]


Sorry - totally didn't see that. Changed it now. Thanks for letting me know!

---

### Post by couzin2000 on 2022-06-10
> **scpatl4now said:**
> Let me see if I can help.  First I want to make sure what I think you are asking is what I think you are asking.  Are storage drives 1,2, and 3 drives where you keep all your data (I am guessing you would not want to delete your files)  Is there a separate drive that has your system files?  If this is the case, and reading your answers thus far it looks like your drives are all EXT4 so what I am thinking is you want to install 22.04 replacing 18.04.  If your storage drives are neither / or home they should not be affected.  Could you post the output of

sudo blkid

So we can verify what is what


Here is the output:
```
couzin2000@SebUBServer2:~$ sudo blkid
[sudo] password for couzin2000: 
/dev/sda4: UUID="8f35a9aa-c8ba-40ba-a12d-5a465d6dd81f" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="3fc5c086-a55f-489d-bcc5-0124e26f7bc5"
/dev/loop1: TYPE="squashfs"
/dev/sdb1: LABEL="storage3" UUID="564d76d6-cf0e-4a2d-b88d-e6385a36aef2" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="8ce58651-2260-461d-ab5d-8b96e553c16d"
/dev/loop6: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop0: TYPE="squashfs"
/dev/sde1: UUID="9114a501-fe7a-4377-8ab8-e92f449fbe12" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="5ed7d121-3e8c-1b4e-aa69-ae40ef484368"
/dev/sdc1: UUID="60d171fb-0717-40ba-b1fc-1d7f999eab9d" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="c212757d-fffd-2144-9630-6fd508fe21bb"
/dev/loop7: TYPE="squashfs"
/dev/sda2: UUID="8AB3-8CEB" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="31ebc6a6-84d0-44ea-b990-dfe62976f45f"
/dev/sda3: UUID="e3cdad36-eb43-4de4-aa40-1b30bd0b951b" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="abf1d076-5b3a-4283-b522-490e177679c1"
/dev/sda1: PARTUUID="51160457-7edc-4df0-a6e3-f1f1ab102d80"
/dev/loop5: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"

```

Although I'm not sure what you're getting out of it. I have 5 drives in there - 2 are SSDs, one of those is my boot drive for a brand new 22.04 install. (And I'm really having issues with this because I use to run all of this 'headless', where all I did was tunnel in with Teamviewer and it all worked. Now with this version, my Mac won't tunnel in at all, my Windows machine doesn't seem to output the proper keystrokes to the Ubuntu Teamviewer, so trying to input [FONT=Courier New]sudo blkid[/FONT] was a pain just because the password wasn't going in, so I'm here running in the house from downstairs to upstairs... anyhow, it's a real pain right now).
The other 3 drives are HDDs, they are for storage. You're right - I cannot afford to lose the files in there. I'm trying to get this back where my Plex server is back online, my Minecraft server is back online, and my file server actually works and makes samba less of a hassle.

---

### Post by couzin2000 on 2022-06-10
> **oldfred said:**
> I just installed 22.04 onmy SSD and used same user & id.
I had no issue mounting  using my data partition on HDD.

If issues then chown & chmod will work on ext4.
I sometimes incorrectly save data using sudo and then do run chown & chmod to correct settings. 

Do not know RAID, there are multiple types of RAID. Typically RAID used for servers to maintain uptime. Less used for desktops as RAID is not backup.
If RAID issues you need to start a new thread and post details of your current RAID configuration and what your issue is.

Yeah, I WAS using my 2 SSDs in RAID1, lesson learned. Not doing this again. It has been buggy from the get go because using the RAID controller built-in to the mobo instead of using software RAID. I'll be moving everything to Unraid eventually and using Ubuntu as a VM, but for now Ubuntu is my go-to. I think what you're saying is that everything should work fine this time around. I'll see how it comes out!

---

