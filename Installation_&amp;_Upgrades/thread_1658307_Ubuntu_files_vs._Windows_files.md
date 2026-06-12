---
title: "Ubuntu files vs. Windows files"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by rmm64 on 2011-01-02
On a separate note from my main problem posted [COLOR=Red]**[here]("http://ubuntuforums.org/showthread.php?t=1656952")**[/COLOR].

I'm using PhotoRec to recover files off my lost C: drive, will I have any issues seeing/using the files that get recovered once I'm back in a Windows environment? I just wasn't sure if there'd be any differences in Windows accessing or recognizing the files created within an Ubuntu environment.

Also, if I end up having to reinstall Windows, I have a storage drive I'd like to reformat to use as the primary boot/install drive (so I'm not using the same install drive as before, start fresh - repartitioning/reformatting/installing Win7 to.) Would there be any issues accessing the files if I moved them from one drive to another (to consolidate everything)?

I'm using NTFS Config to access all my drives right now. Just want to be sure I can actually get to the files and use them once they're recovered and/or moved after I've got Win7 reinstalled again.

Thanks.

---

### Post by rmm64 on 2011-01-04
Still hoping for a response to this post for a little reassurance before reformatting. Anyone?

---

### Post by endotherm on 2011-01-04
well, first and foremost, make sure that you recover the files to a drive other than the one you are recovering them off of, but you prolly already know that.

most files are completely portable between windows and linux. jpeg files for instance as written in a format specified by a standard that is implemented on most platforms, so a jpeg is a jpeg is a jpeg. 

photorec is a datacarving utility, so it goes through the binary data on the disk, and tries to find a data sequence indicating the start and end of a file (of a known type; photorec can only recover files that have known standard headers and trailers). 

the other day i had a failing hdd with an very damaged ntfs partition. I used ddrescue to get a partial image of the drive, and then wrote it to another disk. then I used photorec to carve out the files it could find (the baby pics and some office documents) and copied them to an ext4 partition before placing them on an ntfs external drive for delivery to the client. once photorec had recovered them to the ext partition, all my portability concerns had been solved.

---

### Post by rmm64 on 2011-01-04
> **endotherm said:**
> well, first and foremost, make sure that you recover the files to a drive other than the one you are recovering them off of, but you prolly already know that.

most files are completely portable between windows and linux. jpeg files for instance as written in a format specified by a standard that is implemented on most platforms, so a jpeg is a jpeg is a jpeg. 

photorec is a datacarving utility, so it goes through the binary data on the disk, and tries to find a data sequence indicating the start and end of a file (of a known type; photorec can only recover files that have known standard headers and trailers). 

the other day i had a failing hdd with an very damaged ntfs partition. I used ddrescue to get a partial image of the drive, and then wrote it to another disk. then I used photorec to carve out the files it could find (the baby pics and some office documents) and copied them to an ext4 partition before placing them on an ntfs external drive for delivery to the client. once photorec had recovered them to the ext partition, all my portability concerns had been solved.

Thanks, that's kind of what I thought, Just needed some reassurance that Ubuntu didn't do anything to the files that may change them when back in a Windows environment. I know PhotoRec can only see a limited number of file types, which is okay. It was mainly jpgs (family photos) along with some tiffs, eps, and InDesign files (client files) that I needed to get. I think it's covered the main ones I needed to save, and yes, I saved them to a different internal drive in my system.

What was the point of making a partial image from the bad drive? Was it just to salvage the image before the drive was completely inaccessible? Or would it be possible to pull a image of the entire drive, reformat/repartition the original drive (or another) and reinstall or repair from the salvaged image? Mine seems to be either a bad partition or corrupt MBR, but the actual Win7 install with everything on the drive still seems intact. It'd be nice if that was an option so I could repair without the need of reinstalling from scratch again. Just curious.

Thanks for the reply.

---

### Post by endotherm on 2011-01-04
> **rmm64 said:**
> 
What was the point of making a partial image from the bad drive? Was it just to salvage the image before the drive was completely inaccessible? Or would it be possible to pull a image of the entire drive, reformat/repartition the original drive (or another) and reinstall or repair from the salvaged image? Mine seems to be either a bad partition or corrupt MBR, but the actual Win7 install with everything on the drive still seems intact. It'd be nice if that was an option so I could repair without the need of reinstalling from scratch again. Just curious.

Thanks for the reply.
exactly. the drive was in such an advanced state of mechanical failure, that I was only able to actually get 826MB of binary data off the 320GB partiton. I tried 3 sessions with ddrescue and after the third, the bios would not even recognize the hdd, and it no longer span up at power-on.

there is nothing wrong with recovering to another drive, then formatting the original and copying back to it, as long as teh drive is mechanically healthy. if it is however, and you still have a recognizable partition, I woudl recommend FS repair tools like fsck or chkdsk over recovery unless something is seriously wrong with your filesystem indexes. 

just make sure your drive reads as healthy to the Disk Utility before copying data to a drive. 

as for OSes installed on recovered partitions, it all depends on the state of the filesystem and the nature of the error. ddrescue for instance will attempt to repair data in bad sectors, so if the repair is sucessful and you write the new image off to a drive that doesn't have a bad block, then the issue is repaired. in short, the answer to that depends entirely on the exact cause of failure. keep in mind though, computers are surprisingly resilient, so it is likely that if your error had gotten bad enough for you to notice it, then the chances of repairing everything easily are probably low.

---

