---
title: "Verbatim USB 3.0 Flash Drive Cannot Be Formatted 14.04"
date: 2016-04-03
forum: Installation &amp; Upgrades
---

### Post by grace3 on 2016-04-03
Hello,

I am currently travelling in Central America and purchased a Verbatim Secure Pro USB 3.0 Stick. I wanted to install a linux distro on it. It turns out that this device is designed to be used as a storage only device; and has built in encryption software. It has two partitions; a 34MB part that contains the encryption and mounting software and a 57GB data part that I believe is using exfat; and will only mount in Windows. What a useless hot mess. Has anyone figured out what to do with these, or am I stuck pleading with Vebatim to give me a refund. BTW, nowhere on the labeling was there any information about these issues. Caveat Emptor, ouch.........

Thanks

---

### Post by kansasnoob on 2016-04-03
I'd think dd would overwrite anything but dd earned it's monikers data destroyer and disc destroyer honestly :(

I won't provide any random commands without knowing you have a good understanding of Ubuntu device designations, eg; /dev/sdXY (where X is the drive designation and Y is the partition designation). It's very doubtful that Verbatim would accept a return after taking dd to that drive. And using the proper dd command with an improper device designation can have perilous consequences.

---

### Post by grace3 on 2016-04-03
> **kansasnoob said:**
> I'd think dd would overwrite anything but dd earned it's monikers data destroyer and disc destroyer honestly :(

I won't provide any random commands without knowing you have a good understanding of Ubuntu device designations, eg; /dev/sdXY (where X is the drive designation and Y is the partition designation). It's very doubtful that Verbatim would accept a return after taking dd to that drive. And using the proper dd command with an improper device designation can have perilous consequences.

In disk utility the 34MB partition, which appears as CD/DVD Drive, is labeled /dev/sr1 (read only). Contents UDF mounted at /media/me/Verbatim.

The 57GB Partition, which appears as Drive, is labeled /dev/sdb. This partition is not mounted for reasons already discussed.

If I can get rid of both of these partitions, and combine them, I'd like to proceed. If I'm going to be stuck with the read only partition, then it's going to be a waste of time.

Your thoughts.

"I have become dd, the destroyer of data." Unix Proverb

---

### Post by X-RED_Tech on 2016-04-03
GParted or even Disk should allow the removal of any partition provided that none is mounted. Then you can format it as you need.

---

### Post by sudodus on 2016-04-04
If you are brave enough and have backed up all important data, you can try dd. But I would recommend using dd with a safety belt: 

Using the mkusb method, you can install most linux distros directly (without wiping it, because the method used will overwrite the existing partition table and file system(s) anyway).

See the [main mkusb help page](https://help.ubuntu.com/community/mkusb)

Wipe the USB drive and/or create a new partition table and file system with mkusb. This way you can restore the USB drive to a storage device (but it won't restore the special encryption of your Secure Pro drive).

See this link: [mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by grace3 on 2016-04-06
> **sudodus said:**
> If you are brave enough and have backed up all important data, you can try dd. But I would recommend using dd with a safety belt: 

Using the mkusb method, you can install most linux distros directly (without wiping it, because the method used will overwrite the existing partition table and file system(s) anyway).

See the [main mkusb help page]("https://help.ubuntu.com/community/mkusb")

Wipe the USB drive and/or create a new partition table and file system with mkusb. This way you can restore the USB drive to a storage device (but it won't restore the special encryption of your Secure Pro drive).

See this link: [mkusb/wipe]("https://help.ubuntu.com/community/mkusb/wipe")

Thanks for the reply. I have installed mkusb. It does indeed look like an execellent tool; and your recommendation of using dd with a safety belt is indeed sage advice, for the following reasons: dd should but does not require authentication. It will wipe a drive clean, without asking for the root password, which I consider reckless if not insane. I would therefore recommend the following caveats when using this command. Never copy and paste dd code directly into the terminal; and never edit this command in the terminal. If you must copy and paste, open gedit and edit the command there before entering it onto the command line, as it will launch without pressing the return key, when copied this way, Ouch.................:(

BTW, is it possible to request a code change for this "MONSTER," to require authentication and to wait for a carriage-return press; or is there a way to set these safeguards up on my box?

Anyway, while disk could read the device designations, the device would not mount; and I did use dd if=/dev/zer@ of=/dev/sr1 and I got a read-only message. Perhaps, this device uses a hardware filesystem  for sr1.

---

### Post by sudodus on 2016-04-06
Yes, I think /dev/sr1 might be a hardware filesystem, that is not available for any editing or write operations. But the rest of the pendrive should be available for your purposes.

dd has been around since the beginning of computers according to this link, [dd (Unix)](https://en.wikipedia.org/wiki/Dd_%28Unix%29)

> The name dd is an allusion to the DD statement found in IBM's Job Control Language (JCL),[3][4] in which the initials stand for "Data Description"

I think dd is so well established, that nobody will be allowed to modify it. But we should keep warning beginners :-P

-o-

If you paste a command line without the line feed at the end (into a terminal window), you have to press Enter to execute it.

---

### Post by oldfred on 2016-04-06
Sometimes when I copy commands into terminal they run, and other times they do not.
I have always assumed that I copied a hidden end of line or return on those that immediately run. 
Or it may depend on where copied from. 
Linux & Windows (and forum or Internet) use different line endings which may also be an issue.

---

### Post by yoshii on 2016-04-06
I think your USB drive is one of those "U3" USB drives.  There's some windows freeware that can erase them and make them like normal USB drives again, but I forget what it's called and I don't know what the Linux equivalent would be.  Next time you buy a USB drive, check the packaging for U3 and make sure you don't buy it if it has that written on it.

---

