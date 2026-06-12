---
title: "Too large file on FAT32 truncated to 0 bytes."
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by Garyu on 2006-08-04
I must be the stupidest man alive. I didn't have that much to do so I figured hey, I'll reinstall ubuntu all over again. My system was installed with Breezy but upgraded to Dapper and the upgrade didn't make my splash into the fancy version and so on so I figured I would try to reinstall it and see how much would change. 

So I tar:ed /etc into a .tgz on my fat32 shared data drive with my old windows dual-boot (only reason I still got windows is games like HOMM5 are less twitchy there - though they work in dapper too). Anyways, so I did the same with home
```
tar cvpzf /FAT/Backup/2006-08-04/home.backup.tgz /home/
```
I didn't get any error messages so I figured that hey it seems fine. All of the files in my home directory was listed in the process so it looked very OK. 

Then I formatted my harddrive and installed dapper, but got an error message on boot. "dosfschk /FAT/Backup/2006-08-04/home.backup.tgz ... (don't remember exactly) ... file truncated to 0 bytes". And now when I look at my FAT32 drive the etc.backup.tgz is intact but my entire home.backup.tgz is empty and gone. 

My guess is that the fat32 file system can't handle big enough files or something like that? Anyway, is there ANY way I can recover this??? Reading the data from the harddisk without filesystem or something? I had lots of really important things on that home dir and no other source of backup... (I told you I was stupid) ](*,)

---

### Post by dtfinch on 2006-08-05
Bummer. You're unlikely to get a whole lot of it back, especially if dosfschk works well and the partition is pretty fragmented.

First, you could try the Windows chkdsk /f and tell it to convert any lost chains to files. If you're lucky enough to wind up with a 4gb lost chain, extract it to recover a portion of you home directory. Tar and gzip don't care if the end of the file is missing. But most likely dosfschk freed the clusters, zeroing out the file's linked list in the FAT, leaving you with more limited options.

You can also read partitions (like /dev/hda2) like normal files, as a last resort, if the information's that important. This'll only work to recover the however much of beginning of the file is contiguous, not fragmented. If you or a friend can program, you can try looking for the bytes 1F 8B 08 00 (first 4 bytes of any .tar file) on a 512 byte boundary, with following bytes not matching any other .tar.gz you have on that partition. You might find several unfortunately. Save the next 4gb or so to a file and try to untar it, or pipe it directly to tar.

Last last resort: [http://www.urbanophile.com/~arenn/hacking/gzrt/gzrt.html](http://www.urbanophile.com/~arenn/hacking/gzrt/gzrt.html)
Looks like there's a gzrecover that can handle a partially corrupted (read: fragmented?) .gz file. And supposedly cpio (but not tar itself) can handle partially corrupted .tar files.

Just hope it didn't wrap around and overwrite the header when it exceeded 4gb, or you might have nothing. If you're extremely lucky, it might have even kept writing after 4gb and managed not to fragment it (unlikely). I'm not familiar with the linux vfat implementation. And I've never found myself in a position where I've had to recover a lost file like this.

---

### Post by kstefan on 2006-08-12
Don't know if this helps you, but I can affirm that you are not the only one who ran into this trouble ;-(
I had the exact same situation yesterday when I installed kubuntu 6.06.1 Alternate and booted the new installation for the first time. The exact message from dosfsck was:

File size is 0 bytes, cluster chain length is > 0 bytes. Truncating file to 0 bytes.

Unfortunately I haven't found a way yet to restore the file (also home.tar.gz). I definitely won't make a chkdsk /f yet, since this would write lost clusters to the same partition, possibly complicating other restoration methods later on.

Any undeletion software doesn't help either, since the file wasn't deleted but "just" truncated.

So I'll be glad to hear any suggestions ...

---

