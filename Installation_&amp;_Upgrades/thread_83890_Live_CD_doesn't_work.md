---
title: "Live CD doesn't work"
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by ross0201 on 2005-10-29
I have never used any sort of linux before, but thought I would give this live cd a try. I downloaded the iso and burned it, I get through picking language and keyborad and such, it looks like it is starting, I see lots of system messages, then the screen just goes black. I have a  Gateway Tablet M275E, 1.4 GHz processor and 768 mb DDR SDRAM. All the specs are online at [http://www.winona.edu/its/Laptop/Models/gwTabletM275E.htm](http://www.winona.edu/its/Laptop/Models/gwTabletM275E.htm) Any help would be appreciated

---

### Post by aysiu on 2005-10-30
Totally black or just a DOS-like command prompt?

---

### Post by giggss on 2005-10-30
I have the same problem.. live cd hangs when booting up.

**1st try:** 
Hangs at Loading GNOME (the screen with Ubuntu logo in the middle, where it loads the system clock, LVM Volume Groups, etc)

**Subsequent tries:**
Hangs at same screen but sometimes at the hotplug subsystem or Enterprise Volume Management System.
Sometimes it hangs there for awhile, then a black screen with lots of text scrolling quickly.. and finally stop there after a while.
Now I just tried again, it hanged at Setting Up Alsa Card 0...

It always hangs at the same screen but at different loading points... please help!

---

### Post by xmastree on 2005-10-30
The first thing I would do, if you made the CDs yourselves, is to check them with md5sum to make sure they're ok.
There are plenty of md5sum programs available for Windows (assuming that's what you used to make the CD). I've used [this one]("http://www.etree.org/md5com.html") myself, it's command-line based but that's not a bad thing as you'll need to get used to that for linux. :)
If there's a problem, then either yout ISO is corrupt or it's a bad burn. The ISO can also be checked with md5sum, the checksum is on the download page somewhere. If that's ok but the disc isn't, burn another at a slower speed. CDRW is useful here, as mistakes only cost time not money.

---

### Post by giggss on 2005-10-30
The MD5 checksum is correct... I burnt the disc with nero 6 at 8x... 
**How I burned it:**
Go to Nero -> Recorder -> Burn Image 
Then I select the Ubuntu Live CD iso file... and burn at 8x...

Is there anything wrong here? I've tried 3 CDs...

If I use a CDRW, I must uncheck the 'finialise cd' so that the disc can be written to again right? If not the disc will not be able to be written anymore..

---

### Post by giggss on 2005-10-30
or is it due to any unsupported driver?

---

### Post by xmastree on 2005-10-30
[QUOTE=giggss]Go to Nero -> Recorder -> Burn Image[/quote]That's correct. [See this]("http://www.xmastree.34sp.com/ubuntu/burn/") for more info, although I suspect you got it right.

> If I use a CDRW, I must uncheck the 'finialise cd' so that the disc can be written to again right?Wrong... In fact, I don't think it's possible to uncheck  the finalise option when burning an ISO, as that information is contained in the ISO itself. Finalised or not, a CDRW can still be erased and reused.
For CDR, finalising means no more data can be written to the disc, leaving it open allows further sessions to be written.

Sounds like you're burning it correctly if the md5 checks out.

---

### Post by giggss on 2005-10-30
ok thanks, now i understand about the CDRW and finalise option for burning cds. Right now, any other suggestion can you advise?

Strangely after many attempts, I am able to load up to ubuntu command prompt.. I suppose this means that the live cd is working already? But there's no GUI (maybe because I entered "boot: nolapi acpi=off" when booting up from the Live CD... so can I do what I want to do with the command prompt without the GUI ? I know it's going to be difficult..

---

### Post by giggss on 2005-10-30
actually what I want to do is to access my current HD (which i suspect is corrupted)... I want to access some files and backup those files before I format the whole HDD. How can I access the files in the current HD.. in NTFS file format... on Win XP

---

### Post by xmastree on 2005-10-30
If you've booted to a command prompt, typing **startx** should start the x graphical desktop. However, I suspect it won't or it would have come up automatically. :( 
See [this thread]("http://www.ubuntuforums.org/showthread.php?t=79827") for a similar problem, and possible solution.

However, if you just need to get at your hard disk, and you're comfortable using the command line, you don't need the desktop.

First you need to mount the disk.
[http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs) shows you how to mount a ntfs partition. It will be read-only since linux can't write to ntfs.

Where do you want to backup the files to? You'll need to mount that too, unless it's something like a flash disk which should mount itself.

Then you simply find your files and copy them to the new location. :rolleyes:


Edit: I probably shouldn't say this on the ubuntu forum, but [knoppix]("www.knoppix.com") is the weapon of choice for most people trying to recover files. I believe it automatically mounts your hard disks and puts them on the desktop, making things easier.

---

### Post by ross0201 on 2005-10-30
I just have a black screen, no command prompt

---

### Post by xmastree on 2005-10-30
[QUOTE=ross0201]I just have a black screen, no command prompt[/QUOTE]I just looked at the link in your post, I see it's a laptop. I suggest asking in the [laptop forum]("http://ubuntuforums.org/search.php?searchid=2312854") if no one here can help. There may be more experts there.

---

