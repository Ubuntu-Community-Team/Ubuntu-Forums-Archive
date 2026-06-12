---
title: "Unable to install alongside XP or resize partition"
date: 2019-02-13
forum: Installation &amp; Upgrades
---

### Post by davidforrest57 on 2019-02-13
I am new to Ubuntu and have just started looking at Xubuntu 18.04 on a live USB, with a view to installing it as a dual-boot on an old Dell Latitude D600. The D600 has a single 40GB partition installed with Win XP.

   
  When I try to install Xubuntu there is no option to install alongside XP. This dual boot option is available if I go through the installation procedure on another (Win 7) laptop, but I want to install on the D600. There seems to be some issue with the D600, not the Live USB.

   
  Furthermore, I am unable to shrink the ntfs partition with GParted (so I guess this is being thwarted by the same issue affecting the dual boot install of Xubuntu). GParted doesn’t have any such problems with the other laptop; once again, it’s only a problem with the D600. I get the same results with a dedicated GParted Live USB. Here are a couple of screenshots:

[ATTACH=CONFIG]282500[/ATTACH][ATTACH=CONFIG]282499[/ATTACH]

   
  In my search for a solution, I have found an old thread in the Ubuntu Forums that describes an issue just like mine:
   
  **[SOLVED] why can't gparted resize win xp partition on my toshiba laptop?** [https://ubuntuforums.org/showthread.php?t=1572176](https://ubuntuforums.org/showthread.php?t=1572176)
   
  So I have followed the advice in this thread and carried out the following on the D600:
   
  I have disabled virtual memory.
  I have defragmented the drive.
  I have run chkdsk /p from the Recovery Console (and also from within Windows).
   
  Unfortunately, none of these has solved my problem. Chkdsk finds 4kb in bad sectors (which has been present for many years), so I’m wondering if this is the source of the problem.
   
  Can anybody help, please?
   

  One curious thing: in the old thread the poster’s screenshot shows exactly the same amount of unallocated space (7.84 MB) at the end of the drive as mine. Coincidence?

   
  Thanks in advance.

---

### Post by Impavidus on 2019-02-13
It's indeed possible that the bad sectors cause this. I don't know every detail about chkdsk, maybe the bad sectors prevent it from marking the partition as clean.

You could try and shrink the partition using Windows tools instead of gparted. It's usually better anyway, although gparted and the installer usually do a good job with WinXP – it worked when I first installed Ubuntu back in 2006 and that computer is still running as dual boot. If after resizing and another run of chkdsk Ubuntu can access the Windows partition, all may be well. Ubuntu needs access to the Windows partition, or grub, the bootloader, will not be able to boot Windows. Now, if you manage to get those bad sectors in an unallocated part of the hard drive, they can be ignored.

Note that modern hard drives are supposed to just swap in some spare sectors in the place of those bad sectors. When they can't, it's usually a sign that the hard drive is dying. If it has been like this for years you may be OK, but I'd run a self-test on the hard drive anyway:[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools). You can run that from the Ubuntu live disk, try the long test.

---

### Post by davidforrest57 on 2019-02-13
Thanks, Impavidus. I wasn't able to run the disk check as you suggested. The installation stuck at a Postfix Configuration window that I could not proceed beyond.

I too had thought of using a Windows program to shrink the partition, e.g. Minitool's Partition Wizard, but I've no way of knowing just where the bad sectors are. I assume from your comments that if the bad sectors lie in the Windows partition after shrinking that dual boot still won't be possible?

Any more suggestions as to how I can test the drive?

---

### Post by Impavidus on 2019-02-14
Now I wonder why you can't install smartmontools. Can you show the complete output up to the point where it gets stuck? And can you show the specs of your computer? RAM, CPU etc.

Maybe you can replace the (probably) damaged harddrive by an old, but still healthy hard drive. That computer isn't worth a completely new drive. That won't give you dual boot, but it may be possible to install a light Linux flavour.

---

### Post by davidforrest57 on 2019-02-14
Here is the Terminal output:

```
xubuntu@xubuntu:~$ sudo apt-get install smartmontools
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
xubuntu@xubuntu:~$ sudo dpkg --configure -a
xubuntu@xubuntu:~$ sudo apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  mailutils postfix
Suggested packages:
  mailutils-mh mailutils-doc procmail postfix-mysql postfix-pgsql postfix-ldap
  postfix-pcre postfix-lmdb postfix-sqlite sasl2-bin dovecot-common resolvconf
  postfix-cdb postfix-doc gsmartcontrol smart-notifier
The following NEW packages will be installed:
  mailutils smartmontools
The following packages will be upgraded:
  postfix
1 upgraded, 2 newly installed, 0 to remove and 350 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1764 kB of archives.
After this operation, 6460 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
```

After I press Y there is a bit more output that I couldn't capture, and the the Terminal window becomes:
[ATTACH=CONFIG]282515[/ATTACH]
Pressing enter does nothing. Closing the window presents:
[ATTACH=CONFIG]282514[/ATTACH]
This is where things get stuck.

Computer specs: CPU: Pentium M 1400 MHz; RAM: 2GB. HDD: 40GB ATA (as per Image 1 in my original post); OS: Windows XP Pro (SP3)

I doubt I would be able to get a replacement drive that doesn't have any bad sectors, but 4kb  (4096 bytes in each allocation unit) that hasn't changed in 5 years, or more, doesn't seem too bad (but I'm no expert on these matters). Is this even a SMART HDD? Would Smartmontools be a suitable tool for such an old HDD?

In any case the PC works just fine. Boots up fully in just over a minute and no reports of errors or other signs of malfunction. It's my backup PC which can run some legacy apps that my Win 7 pc can't. I don't use it on the internet or any network, so I'm looking at a dual-boot set-up with Xubuntu so that I can familiarise myself with this OS and so that I can use it for internet work.

And while I've been typing all this, that Postfix Configuration dialog is still waiting! Can you advise what I'm supposed to do next?

Thanks for your patience.

---

### Post by alphaniner2 on 2019-02-14
Having just installed smartmontools, I can tell you you're not seeing the entirety of the 'Postfix Configuration' menu screen in that screenshot. See if you can scroll down, at the bottom you need to select one of the configuration options.

Aside from that, I've never tried to resize a Windows filesystem from Linux. Googling 'linux resize ntfs' I see there's the command line program 'ntfsresize' you could try. Generally though I'd go out of my way to connect the drive to a Win7 machine before I'd try that, unless I had a full backup.

If you do try 'ntfsresize', keep in mind it only resizes the filesystem; you then have to resize the partition to match.

---

### Post by davidforrest57 on 2019-02-14
Whilst waiting for your reply I did manage to install Gnome Disk, which also came up with some references to Postfix, but which I could (blindly) progress through. Anyhow, it eventually installed. I have not run any tests, but here is a snapshot:
[ATTACH=CONFIG]282516[/ATTACH]
Assessment is that the disk is OK, with 1 bad sector.

Do you have any recommendations or suggestions?

---

### Post by davidforrest57 on 2019-02-14
Sometimes, if you bang your head against a brick wall enough times, you'll break through...

Smartmontools eventually installed. Don't ask me how!

I ran a check to see if the drive had SMART capability, as per instructions:
[ATTACH=CONFIG]282517[/ATTACH]
To my surprise I got:

```
xubuntu@xubuntu:~$ sudo smartctl -i /dev/sda
smartctl 6.6 2016-05-31 r4324 [i686-linux-4.15.0-29-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Travelstar 5K80
Device Model:     HTS548040M9AT00
Serial Number:    MRL222L2HG12YB
Firmware Version: MG2OA53A
User Capacity:    40,007,761,920 bytes [40.0 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA/ATAPI-6 T13/1410D revision 3a
Local Time is:    Thu Feb 14 19:27:10 2019 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
```

So, what now, please?

---

### Post by alphaniner2 on 2019-02-14
I'd say first run some tests. I don't use Gnome Disk, so you'll have to figure out how to use it to run the tests.

Looking back at your first post though, the second image (dialog window "Information about /dev/sda1") indicates he ntfs-3g package is not installed. It contains 'ntfsresize', which is probably used by GParted, so the fact you don't have it may ultimately be the problem.

-----

**Edit: Test with smartctl**

I'd run a 'short' test first:

sudo smartctl -t short /dev/sda

You should see some output including "Test will complete after ...". You can just wait until the time indicated, or use

sudo smartctl -c /dev/sda

to watch the progress:

```
sudo smartctl -c /dev/sda
...
Self-test execution status:      ( 249)    Self-test routine in progress...
                    90% of test remaining.
...
```

When the test is complete, that line will indicate whether the test passed or failed:

```
sudo smartctl -c /dev/sda
...
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
...
```

If the short test passes, run a 'long' test:

sudo smartctl -t long /dev/sda

As with the short test, you can wait until the time indicated or use the command indicated earlier to watch the progress.

---

### Post by davidforrest57 on 2019-02-14
Thanks, alphaniner2.

I've come across numerous posts about the message concerning "ntfs-3g package is not installed", but the general consensus is that this is included in GParted.

As you suggested, I tried running the short test first, but no results were returned:

```
xubuntu@xubuntu:~$ sudo smartctl -t short /dev/sda
smartctl 6.6 2016-05-31 r4324 [i686-linux-4.15.0-29-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 2 minutes for test to complete.
Test will complete after Thu Feb 14 20:23:57 2019

Use smartctl -X to abort test.
xubuntu@xubuntu:~$
```

Valentine's Day duties call, so I'll have to sign off just now!

---

### Post by alphaniner2 on 2019-02-14
It's normal for the command to return immediately. Just use 'smartctl -c /dev/sda' to track the progress.

---

### Post by deadflowr on 2019-02-14
Please place terminal output in code tags as that will help retain the proper formatting:
See: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")
for a quick howdy-do on code tags.

---

### Post by Impavidus on 2019-02-14
That's weird. ntfs-3g is supposed to be available by default on the live disk. It has been like that forever. And why would postfix be installed? Smartmontools doesn't need it. Did you install it before?

---

### Post by alphaniner2 on 2019-02-14
I don't know what's going on with ntfs-3g, I just pointed out what was indicated in the screenshot.

As for postfix, smartmontools has "Recommends: mailx | mailutils" presumably it has something to do with that.

---

### Post by davidforrest57 on 2019-02-15
Just to catch up with the last few posts…

 Thanks to deadflwr for advice on code tags.

 Regarding ntfs-3g, as Impavidus says, it is supposed to be included with Gparted; having trawled a large number of posts, I’ve seen this stated elsewhere. Also, as I mentioned in my first post, when I ran GParted on my other (Win 7) pc I didn’t get any warnings at all, which perhaps implies that ntfs-3g is present. The yellow warning sign appears with the D600 only, and I’m trying to establish why this is.

 As for Postfix, I haven’t installed this; I too pondered why this should crop up in connection with a disk utility. Through sheer stubbornness I bludgeoned my way through installing Smartmontools and tried running some checks before Valentine’s Day duties called. However, when I tried running some disk checks I didn’t seem to be getting any results, but I now think that was my lack of experience using this utility.

 So today is another day; let’s try again…

 Here is an attempt to run a short test using “sudo smartctl -t short /dev/sda”:

 After waiting for 2 minutes I got:

```
 sudo smartctl -c /dev/sda
 …
 Self-test execution status:      (   0)    The previous self-test routine completed
                     without error or no self-test has ever  
                     been run.
 ...
```
  

 Following success with that, I ran the long test using “sudo smartctl -t long /dev/sda”.

 After 30 minutes I got:


```
 Self-test execution status:      ( 118)    The previous self-test completed having
                     the read element of the test failed.
```


 This finding doesn’t convey much information about the extent of the problem reported. It seems only to confirm what Chkdsk has found (this week and back in 2013): there is one bad sector on the disk. Plus, there is the Gnome Disk screenshot I posted, which tallies with Chkdsk; I haven’t actively run any of the Gnome Disks tests yet, but it has somehow reported “disk ok, one bad sector”.

 Is there any way of digging out more information? Or does this explain GParted's reluctance to make changes to the disk partitions?

---

### Post by davidforrest57 on 2019-02-15
Hmmm... why didn't the code tags work?

---

### Post by deadflowr on 2019-02-15
Wrong slash 
yours
[noparse]```
 [\code][/noparse]
and the correct way
[noparse][code] 
```[/noparse]

---

### Post by davidforrest57 on 2019-02-15
Doh!

---

### Post by davidforrest57 on 2019-02-18
I finally got Xubuntu installed as a dual-boot with Win XP.

After researching how to access SMART disk information, I used GNOME Disks to check the results of short and extended tests and concluded that the only thing wrong with the disk was a single bad sector. All the other tests were fine.

Nevertheless, nothing I tried would get Gparted to partition the drive, and Xubuntu would not install alongside Windows. The reason why remains a mystery. So I decided to see what I could do from within Windows.

Since XP has no capability to shrink volumes I looked for third-party tools and found free versions of Minitool Partition Magic 11 and EaseUS Partition Master 13.

Partition Magic failed to shrink the ntfs partition; on rebooting a message appeared to say “Failed to lock memory at 0x280048 size:153740, error:1453...Failed to launch Partition Wizard! … Press any key to exit...” Then XP booted normally.

I then tried EaseUS Partition Master, fully expecting a similar result. But NO!!! I ended up with 10GB of unallocated space.

After checking XP was alive and healthy I was able to manually create the Ext4 and swap partitions and install Xubuntu. I'm now a happy bunny! 

So, my advice is, if at first you don’t succeed, try something else; you may eventually succeed.

---

