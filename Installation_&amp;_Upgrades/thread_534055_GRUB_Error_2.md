---
title: "GRUB Error 2"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by Nakul Tiruviluamala on 2007-08-24
Hello, I apologize for making this post when there are other threads that have addressed this topic. However, I have tried  my hand at using these threads as well as others on other forums and have found that my problem is still not resolved.

I am a new Linux user and have tried installing Ubuntu about 10 times with no avail. I repeatedly receive this message when trying to boot. 

GRUB Loading stage1.5

GRUB loading, please wait...
Error 2

I clean reformatted the machine so Windows isn't installed anymore. I tried the automated install, as well as installing using manual partitions. On my last install, I used the automated install, but clicked "advanced" right before the partitions were created and tried setting (hd0,0) instead of (hd0).

I downloaded a GRUB boot loader CD, but have tried using the terminal after logging into the LiveCD, as recommended by the threads.

I am really looking forward to getting Ubuntu to boot. I refuse to give up!

Thank you,
Nakul

---

### Post by merlinus on 2007-08-24
You might post results of:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

-merlin

---

### Post by Pumalite on 2007-08-24
I think you better re-install and let Grub install to MBR by default.

---

### Post by Nakul Tiruviluamala on 2007-08-24
Merlin,
Here are the results of "sudo fdisk -l"

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table
```
```

ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
```

Pumalite,
I've tried letting Ubuntu automate my install without any interference. How do I let GRUB install to MBR by default?

---

### Post by merlinus on 2007-08-24
> **Pumalite said:**
> I think you better re-install and let Grub install to MBR by default.

This seems unnecessary, as supergrub will do this.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Main_Purposes_of_Super_Grub_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Main_Purposes_of_Super_Grub_Disk)

-merlin

---

### Post by Pumalite on 2007-08-24
Ok

---

### Post by Nakul Tiruviluamala on 2007-08-24
I already have the SuperGrub disk. I just booted into it. How should I use it to restore GRUB onto the MBR?
I also listed some specifications on an above post.

Thank you,
Nakul

---

### Post by merlinus on 2007-08-24
**Select the appropriate Super **[COLOR=#000000]**Grub**[/COLOR][B] Menu option
[/B]Super Grub Disk's English Menu has  four options plus the Quit menu.

The first two options are for those who like things quick and easy,
**Gnu/Linux** is for computers with a single hard disk and just one or two operating systems when you want to boot Linux or install your Linux's GRUB boot loader to MBR.

Fix boot of gnu/linux.

-merlin

---

### Post by Nakul Tiruviluamala on 2007-08-24
My Super Grub Disk loads differently than on the screenshots below.

[http://supergrub.forjamari.linex.org/?section=screenshots](http://supergrub.forjamari.linex.org/?section=screenshots)

The top line is the same, including the version number, but there is no graphical interface. The screen reads:

```
Super Grub Disk based on GNU GRUB version 0.97-os.1  (612K lower / 1046096K upper memory)
 [Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. 

grub>
```

Did I download the incorrect version?

---

### Post by merlinus on 2007-08-24
Enter these commands at the CLI, one at a time.
```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```Substitute results from find for (hdx,y) and setup (hdx).

-merlin

---

### Post by Nakul Tiruviluamala on 2007-08-24
"find /boot/grub/stage1" is not locating any files.
So I think I'll try a clean install once more without tampering without the "advanced" tab. And then I'll try your advice.

---

### Post by merlinus on 2007-08-24
OK.  It looks like grub never got installed, for whatever reason.

Good luck this time!

-merlin

---

### Post by Pumalite on 2007-08-24
What did I tell you? Ha,ha,ha

---

### Post by merlinus on 2007-08-24
Actually, if he had a supergrub disk that booted into a gui, it would have been very simple to install grub.

But it is far too esoteric from the CLI.

-merlin

---

### Post by Pumalite on 2007-08-24
It's just a joke, Merlin!

---

### Post by Nakul Tiruviluamala on 2007-08-24
Hi, I reinstalled Ubuntu using the automated install for a full hard drive partition. I didn't tamper with the install this time. But when I receive this message again.

```
grub>find /boot/grub/stage1

Error 15: File not found
```

I tried entering this command from the LiveCD terminal as well.
Is there a way to get a Super Grub Disk with a GUI? Would that solve the problem?

---

### Post by merlinus on 2007-08-24
It might.  What version of supergrub do you have?

Also, did you enter this in the live cd terminal (especially the first line -- sudo grub):

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```Substitute results from find for (hdx,y) and setup (hdx).

-merlin

---

### Post by merlinus on 2007-08-24
You might also try this:

```

sudo grub
root (hd0,0)
setup (hd0)
quit

```

-merlin

---

### Post by Nakul Tiruviluamala on 2007-08-24
Merlin, I did indeed forget to type in the "sudo grub" command. After completing this, I was able to complete the accompanying commands. I remember doing this procedure in the past, from this thread:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

However, when I restarted the machine, the original error message still shows up. 

As for the Super Grub Disk, I installed the main link (Download last Multilingual Super Grub Disk ISO) from this link: [http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

After burning the ISO, it still doesn't have  GUI. What should I do?

---

### Post by merlinus on 2007-08-24
[http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

Download [sgd_0.9598.iso.bz2]("http://forjamari.linex.org/frs/download.php/605/sgd_0.9598.iso.bz2")

-merlin

---

### Post by Nakul Tiruviluamala on 2007-08-24
Merlin, I used the second external link you gave me and burned the disk, but a GUI still doesn't register with my computer.

---

### Post by merlinus on 2007-08-24
I just booted my computer from the same version of supergrub.  It comes up with a colored menu from which I can use arrow keys and Enter to make choices.

What happens when you boot from the cd?

What do you see when you look at the contents of the cd?  I see three items -- boot, rr_moved and boot.catalog.

-merlin

---

### Post by Nakul Tiruviluamala on 2007-08-24
Merlin, I think progress is being made. I got suspicious of my CD drive when I was able to load the Super Grub Disk on my other computer. I tried putting the disk into my computer's other optical drive and the Super Grub Disk worked fine. I received some unusual errors, so I'm going to try and install Ubuntu one more time using the other optical drive, and then see if Super Grub is even necessary. I'm going to eat dinner and try this again in a little while. Thanks for all the help!

---

