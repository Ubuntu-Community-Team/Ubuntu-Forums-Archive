---
title: "[SOLVED] Boot Ubuntu with Media Direct Button"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by burgerearl on 2007-12-15
I just purchased a refurbished Inspiron 1520. After reading about a wide variety of issues with Media Direct, I've decided that I'd like to set things up so the power button boots windows and the Media Direct button boots Ubuntu.

Using Gparted to examine my current partitioning shows the following:

```
/dev/sda1	fat16		78.41 MB
/dev/sda2	ntfs		106.21 GB
/dev/sda3	extended	2.50 GB
  /dev/sda5	fat32		2.50 GB
/dev/sda4	fat32		3.00 GB
```

Windows Disk Manager shows that the 2.5 GB partition is labeled Media Direct. I believe the sda1 partition is Dell utility (a choice when you enter Dell's boot options). I have no idea what the 3 GB partition is, although I've seen some posts suggesting that Dell stores an image of a clean install of Windows.

Anyway, my plan is to use Gparted to expand and then format the Mediadirect Partition, and then install Ubuntu onto this space.

Dell's custom bootloader is already configured to boot that partition (sda5) when the mediadirect button is pushed, so as far as I can tell, this plan should give me the setup I want.

Can anyone comment on this plan and let me know if there's anything I should do differently or watch out for?

Thanks!

---

### Post by burgerearl on 2007-12-17
Curiosity and experimentation got the better of me. I went ahead and tried this. Fortunately, success!

I ended up with the following partitioning

```
Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  82.3MB  82.2MB  primary   fat16             
 2      82.3MB  32.3GB  32.2GB  primary   ntfs              
 3      32.3GB  117GB   84.5GB  extended               boot 
 7      32.3GB  84.0GB  51.7GB  logical   fat32             
 6      84.0GB  115GB   30.7GB  logical   ext3              
 5      115GB   117GB   2048MB  logical   linux-swap        
 4      117GB   120GB   3224MB  primary   fat32
```

The 51 GB partition is for shared data between Ubuntu and Windows.

Note: Gathering from what I've read, this will only work with newer versions of Media Direct where it is NOT installed on a Host Protected Area. I was able to see my Media Direct partition with both Windows disk utility and GParted.

The steps I used to achieve this:

1. Using the [System Rescue CD]("http://www.sysresccd.org/"), I used GParted to shrink my NTFS partition, grow my extended partition (sda3 above) and delete the logical partition for media direct within the extended partition. 

1b. I also added the Fat32 partition for data, but AFAIK this is completely unnecessary

2. Installed Ubuntu. I used the manual partitioning and ended up with 8 MB unpartitioned between two of my partitions. Figured there was nothing I could do about it

3. Screwed up once, but I won't go into detail.

4. Installed GRUB to the boot sector of my extended partition (instructions [here]("http://ubuntuforums.org/showpost.php?p=3113451&postcount=8"))

5. In a windows command prompt, ran the following command from the MD repair cd
```
cd dellkit
rmbr DELL 2 3
```

There's numerous explanations out there about the usage of RMBR

6. Shut down Windows, booted with MD button

7. Got a weird error, followed by an XP BSOD

8. Hard shutdown w/ power button, tried booting from MD Button again

9. Success!

Notes: I only included #6-#8 in case anyone else tries this and runs in to the same error. I guess don't get worried?

I decided to keep the Dell utilities and the Dell restore image on the disk, you could avoid installing GRUB to the extended partition boot sector if you had less partitions, but it wasn't really an issue.

Haven't tried booting XP yet... we'll see.

---

