---
title: "Ubuntu won't boot from freshly burned cd"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by jimmys_ on 2011-01-08
I just downloaded the Ubuntu 10.10 64-bit and burned it to a cd. The problem is that Ubuntu never boots. It stays in that Ubuntu loading screen forever. When I press a button a get these errors:

(process:319): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

and then

the following error again and again

/scripts/casper-bottom/10adduser: line 26: db_set: not found

What's going on?

---

### Post by jimmys_ on 2011-01-09
Does it have something to do with the 64-bit edition? From the errors I understand that is something with the users, but which users since I try to boot for the first time in order to install Ubuntu?

---

### Post by Rubi1200 on 2011-01-09
Did you check the MD5SUM before burning?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Did you burn at the lowest speed?

What graphics card do you have?

---

### Post by jroa on 2011-01-09
+1 to what Rubi1200 said.  I have not had any problems as long as I check the checksum to make sure that the iso is ok and use the slowest burning speed possible.

---

### Post by jimmys_ on 2011-01-09
> **Rubi1200 said:**
> Did you check the MD5SUM before burning?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Did you burn at the lowest speed?

What graphics card do you have?

Thanks for your reply

I'll check it now and let you know.

I actually formatted my hard disk and wanted to dual boot win7 with ubuntu and since I had just installed win7 I burned it with the burner that comes with win7. There's no selection of burn speed.

I have an onboard Intel GMA3000

---

### Post by jimmys_ on 2011-01-09
Okay, I checked the MD5 hash and they are the same. I'll try to burn the image again and see if that makes any difference.

---

### Post by jimmys_ on 2011-01-09
After burning the image again, the first error message for process:319 is still shown but at least the others don't appear and it boots normally. I hope there isn't a problem.

---

### Post by Rubi1200 on 2011-01-09
> **jimmys_ said:**
> After burning the image again, the first error message for process:319 is still shown but at least the others don't appear and it boots normally. I hope there isn't a problem.

In other words, you are at the graphical desktop?

What do you want to do exactly?

Go to Applications > Accessories > Terminal and copy/paste the following command:
```
sudo parted -l
```

Copy/paste the results back here and please use the # tag on the menu to generate code tags. Paste the results between the tags and submit.

The command will give us a quick overview of your current drive setup and will make offering advice on partitioning/installing easier.

Thanks.

---

### Post by jimmys_ on 2011-01-09
I think I finally installed it. The problem now is that during installation, the ethernet was working and downloading updates which took an hour or so, and now after rebooting the ethernet is not working and the graphics drivers are not recognized. This is so annoying. What's wrong now?

Here's the code Rubi1200 asked for
```
Model: ATA SAMSUNG HD321KJ (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      106MB   269GB  268GB   primary   ntfs
 3      269GB   320GB  51.5GB  extended
 5      269GB   271GB  2047MB  logical   linux-swap(v1)
 6      271GB   320GB  49.5GB  logical   ext4




```

---

### Post by Rubi1200 on 2011-01-09
As far as I know, the graphics card should not be a problem. What troubles are you experiencing with it?

For connection information, post the output of the following commands please.

Go to Applications > Accessories > Terminal:

```
ifconfig

sudo lshw -C network
```

---

