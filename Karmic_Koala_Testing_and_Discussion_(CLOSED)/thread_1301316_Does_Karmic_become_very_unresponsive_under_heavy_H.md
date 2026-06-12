---
title: "Does Karmic become very unresponsive under heavy HDD load for anyone else?"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by themusicalduck on 2009-10-25
Seems like since I upgraded to Karmic, copying large files or installing programs/updates can make my desktop very unresponsive. Copying files can sometimes cause the desktop to slow down to a complete freeze before eventually freeing itself up again. This is a problem I experienced a little in 8.04, but 8.10 was better, and 9.04 even better. Yet it seems to be back to worse than it was in 8.04 with Karmic.

---

### Post by andrewabc on 2009-10-25
Did you upgrade from 9.04 or before?

Or is this a fresh format/install of 9.10 (release candidate)?

If upgrade from 9.04 are you using ext3 or ext4?

What type of hard drive? 7200RPM? Laptop or desktop?

If an upgrade, you might be best off backing up important stuff and formatting and installing 9.10 final.

Could be a driver problem somewhere as well.

When doing these operations, open up terminal and type in
top
and see if anything is eating up the CPU. Maybe a problem when moving stuff that eats up CPU and causes slowdowns. Give computer specs so we know what you're using.

---

### Post by themusicalduck on 2009-10-25
It's an upgrade from 9.04. 9.04 was from a fresh install. My root is ext4, but home is ext3 and I'm often copying from my home to an NTFS drive. All my drives are SATA 7200RPM.

Looking at top, it looks like mount.ntfs-3g fluctuates quite a bit between 20% and up to 60%, which is quite high. Xorg also has occasional spikes up to 50%. Also chromium sometimes uses a lot of CPU, but I think that is down to flash.

I might give a fresh install a go, it could be related to my NVidia drivers not performing properly as well, since I am using the 190 beta version.

My specs are 2gHz AMD dual core, 1GB of ram, 3.4GB of swap.

I guess I have a couple of things to try, it's only interesting that the problem seems to have gotten progressively worse as Karmic has been updated. Also this same configuration worked so well on Jaunty and the Karmic beta.

---

### Post by andrewabc on 2009-10-25
Do you get slowdowns when moving stuff around just on your ext3/ext4? Or mostly when moving to another hard drive with the ntfs? Is it via external hard drive (usb?). Maybe the combination of moving something from hard drive over usb to ntfs causes problems. If something gets saturated (filled) enough then it causes other problems. I'm just guessing.

I did a little test on my computer from SSD ext4 ubuntu 9.04 drive to my 320gb hard drive. Cut/paste small 20mb file caused mount.ntfs-3g to spike to 20% for a second. Also browsing the hard drive (ntfs) causes nautilus to sometimes use CPU.
core2duo 1.8ghz ICH8 (SATA II), intel g965 x3000

I'd say combination of moving between different hard drives and different filesystems could slow things down on any system.

copying 700mb ubuntu 9.10 RC on one NTFS partition on hard drive to another NTFS on hard drive uses 30-40% CPU at start and 20% once going for mount.ntfs-3g, and 10% xorg. Although I'm on SSD (ubuntu 9.04) so no big slowdowns noticed (I have compiz enabled so that slows my computer down enough if lots of CPU usage). I don't do a lot of big file transfers often. But that could change when my internet gets faster soon.

So, the high spikes in CPU probably cause slowdowns. Are they quick slowdowns (lasting seconds), or big slowdowns for entire duration of copy/pasting file?

---

### Post by themusicalduck on 2009-10-26
It's only copying from ext3 to NTFS. I only use ext4 for my root so I rarely need to copy anything from or to there. It isn't over USB, everything is on internal SATA. I have three drives, but home and the NTFS partition are on the same drive, root on a seperate drive, but using the same controller. I have one other IDE drive I rarely use.

Seems like mount.ntfs-3g uses a lot more CPU for me than it does for you. It could be related to the latest kernel, since I didn't really notice it before it was updated from 13 to 14. I have an nforce4 chipset too, which I've heard a fair few bad things about.

The slowdowns are fairly quick, they last for around about 5 or 6 seconds before I can use the computer again, but then it'll only last another 5-6 seconds before it freezes up again. Doing anything becomes difficult, especially playing video.

Certainly if I'm not doing much else while copying the file the computer isn't too bad, but trying anything other than browsing html and things start to get nasty.

---

### Post by cariboo on 2009-10-26
I've had apparent lock ups doing some fairly cpu intensive operations. So far it has only happened twice, so I'm still investigating.

---

