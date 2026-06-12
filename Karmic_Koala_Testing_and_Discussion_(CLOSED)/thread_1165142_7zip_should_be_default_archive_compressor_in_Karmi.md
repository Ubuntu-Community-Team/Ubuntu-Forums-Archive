---
title: "7zip should be default archive compressor in Karmic."
date: 2009-05-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Col-1023 on 2009-05-20
I've created a video file greater than 4GB, so when I archive this file onto some external drives, some of which are FAT32, I'll have to use an archiving method that supports file splitting.

Apparently in the repos there are 2 compressors that do this, rar and 7zip.

From what I've read rar is protected by patents, but 7zip is completely free.

So I suggest that 7zip be included in Karmic by default, so people who have to archive huge files to fat32 drives can do so and split the files into chunks under $GB.  Apparently winrar can read 7zip files as well so windows users who use winrar can access the archive.

On post #30 Psyke mention that he had filed a bug request on this issue and also mention another bug report, below is the quote.

I've filed this proposal as bug #379236. I recommend everyone who is interested to voice their opinions on that report.

A bug was already filed for inclusion into the default installation: bug #261117. Please comment there as well.

---

### Post by steeleyuk on 2009-05-20
It was included early in the Jaunty development but taken out again. Considering the size of the p7zip-full (or one of the other ones), it would probably be very useful to include it by default.

---

### Post by davideotape on 2009-05-20
> **Col-1023 said:**
> I've created a video file greater than 4GB, so when I archive this file onto some external drives, some of which are FAT32, I'll have to use an archiving method that supports file splitting.

Apparently in the repos there are 2 compressors that do this, rar and 7zip.

From what I've read rar is protected by patents, but 7zip is completely free.

So I suggest that 7zip be included in Karmic by default, so people who have to archive huge files to fat32 drives can do so and split the files into chunks under $GB.  Apparently winrar can read 7zip files as well so windows users who use winrar can access the archive.


Nothing against you or anythin, but a. How many everyday users actually use file compression software, b. Of them how many users are just decompressing files from the web, and c. Of those left, how many have 4gb files they want to split up. If that is the only reason to change the default archive tool, then I don't think it's worth it, but if 7-zip has more advantages over file-roller then I'd be interested to hear them :D

---

### Post by MaX on 2009-05-20
> **davideotape said:**
> Nothing against you or anythin, but a. How many everyday users actually use file compression software, b. Of them how many users are just decompressing files from the web, and c. Of those left, how many have 4gb files they want to split up. If that is the only reason to change the default archive tool, then I don't think it's worth it, but if 7-zip has more advantages over file-roller then I'd be interested to hear them :D

File-roller is just a client, it uses whatever compression you decide, including 7zip.

---

### Post by coutts99 on 2009-05-20
> **davideotape said:**
> Nothing against you or anythin, but a. How many everyday users actually use file compression software, b. Of them how many users are just decompressing files from the web, and c. Of those left, how many have 4gb files they want to split up. If that is the only reason to change the default archive tool, then I don't think it's worth it, but if 7-zip has more advantages over file-roller then I'd be interested to hear them :D

Any disadvantages to changing?

---

### Post by davideotape on 2009-05-20
> **MaX said:**
> File-roller is just a client, it uses whatever compression you decide, including 7zip.

Ah, sorry I didn't know that. What compression tool comes installed by default then? And does that mean 7-zip would still be used using the same GUI that already exests? If that's true then I think the only reason it isn't default might be size issues with the livecd.

---

### Post by psyke83 on 2009-05-20
> **davideotape said:**
> Ah, sorry I didn't know that. What compression tool comes installed by default then? And does that mean 7-zip would still be used using the same GUI that already exests? If that's true then I think the only reason it isn't default might be size issues with the livecd.

Tar, gzip and bzip are included. The 7z archive format uses LZMA compression (which is a much superior deflate algorithm to gzip and bzip), and dpkg already supports LZMA for packing .deb archives. I think a few extra kb devoted to p7zip on the Live CD would definitely be worthwhile...

---

### Post by psyke83 on 2009-05-20
> **coutts99 said:**
> Any disadvantages to changing?

No "changing" is necessary. Having the p7zip or p7zip-full package installed simply adds the command-line tools to your system. File Roller will then detect these command-line tools and enable support for .7z and .tar.lz archives in its interface.

---

### Post by psyke83 on 2009-05-20
Another idea (if space is too tight on the Live CD) would be to add p7zip-full (which includes rar support?) to the ubuntu-restricted-extras metapackage...

---

### Post by davideotape on 2009-05-20
> **psyke83 said:**
> Tar, gzip and bzip are included. The 7z archive format uses LZMA compression (which is a much superior deflate algorithm to gzip and bzip), and dpkg already supports LZMA for packing .deb archives. I think a few extra kb devoted to p7zip on the Live CD would definitely be worthwhile...

But what new features do you actually get with 7-zip, apart from 7z support and archive splitting. If 7-zip also handles tar, gzip and bzip, then you could get rid of them for just 7zip, thus potentially saving space on the cd. If it doesn't though, it doesn't offer a great deal of extra functionallity, and it has to be remembered that every kilobyte counts on the livecd.

---

### Post by psyke83 on 2009-05-20
> **davideotape said:**
> But what new features do you actually get with 7-zip, apart from 7z support and archive splitting. If 7-zip also handles tar, gzip and bzip, then you could get rid of them for just 7zip, thus potentially saving space on the cd. If it doesn't though, it doesn't offer a great deal of extra functionallity, and it has to be remembered that every kilobyte counts on the livecd.

You can't possibly remove gzip or bzip2, they're too ubiquitous on the Linux platform (and no, it doesn't matter if p7zip supports compression/decompression of those formats). It would introduce far too much breakage (e.g. packaging scripts).

Adding 7z support is an advantage for those who want better compression, simple as that. It's also cross-platform (there's a 7-Zip GUI for Windows and the most popular archiving program, WinRAR, also supports 7z archives).

Maybe this specification should also be revived: [https://blueprints.launchpad.net/ubuntu/+spec/dpkg-lzma](https://blueprints.launchpad.net/ubuntu/+spec/dpkg-lzma)

---

### Post by steeleyuk on 2009-05-20
The best way to think of it is the p7zip (or one of the variants) is a plugin which file-roller uses. It doesn't replace any GUI nor mess with bz2, gz, etc.

I'd like p7zip-full to be included, with a download size of 1195kB its not exactly excessive. Though there *may* be some patent issues, not looked but adding .rar support (works for most versions of rar) would be nice, to say the least. :)

---

### Post by Reiger on 2009-05-20
Anyone is free to implement de-compression and archive-reading support for RAR files. However _creating_ archive in RAR formats is another story.

EDIT: Altough RAR support can be delivered by simply adding unrar to the ISO if it hasn't been already. (Incidentally, source code for unrar is available from the winrar website.)

---

### Post by BwackNinja on 2009-05-20
Though less convenient, you could always just use the split command to make it smaller files, and to unzip, just cat file1 file2 file3 | gunzip or however you feel like it. Not very useful to non-*nix platforms though :P. Also not something I'd expect most people to be able to do at all either.

---

### Post by Reiger on 2009-05-20
Wouldn't that sort of give you rubbish at the 'seams' since what used to be file-headers is now treated as file-payload?

For me this makes more sense:
To compress: split, then compress, then tar up.
To decompress: untar in a fresh directory, unzip all files, then cat the results... ?

---

### Post by psyke83 on 2009-05-20
> **Reiger said:**
> Wouldn't that sort of give you rubbish at the 'seams' since what used to be file-headers is now treated as file-payload?

For me this makes more sense:
To compress: split, then compress, then tar up.
To decompress: untar in a fresh directory, unzip all files, then cat the results... ?

Splitting first and compressing later means that you cannot anticipate the resulting filesize for each part. Not exactly useful when you want to archive onto statically-sized media (CD/DVD, etc)...

---

### Post by Nullack on 2009-05-20
My tests show unrar free doesnt work properly. unrar works, but instead I just install all the P7Zip packages so I also have the 7zip format support.

---

### Post by Col-1023 on 2009-05-20
Thanks everyone for your replies.

My maine use for 7zip is to allow huge video (or other files) to be archived to fat32 external drives.

Since some of the users of these drives are windows, then fat32 is necessary for easy cross platform support.

If you encode video to high quality, it's not that hard to get a mkv file over 4GB, and fat32 won't handle files over 4GB.

I know that space on the CD is limited, but since many more people are doing video encoding and archiving, from HDTV for example, then 7zip would be useful.

---

### Post by davideotape on 2009-05-21
> I'd like p7zip-full to be included, with a download size of 1195kB its not exactly excessive.

I think even with a size of around a megabyte, it would be hard to squeeze it on to the live-cd. But, if it has better compression methods than those that are already used on the cd, it could in fact save space. Anyone know if it would take a lot of time and effort to use .7z to compress files on the cd instead of what is already being used?

> Adding 7z support is an advantage for those who want better compression, simple as that. It's also cross-platform (there's a 7-Zip GUI for Windows and the most popular archiving program, WinRAR, also supports 7z archives).

Fair enough, but in my experience the most widely used compression format on windows is .zip. Personally I have used 7-zip on windows from the right click menu, and it is a way better than win-rar.

---

### Post by Slug71 on 2009-05-21
> **davideotape said:**
> But what new features do you actually get with 7-zip, apart from 7z support and archive splitting. If 7-zip also handles tar, gzip and bzip, then you could get rid of them for just 7zip, thus potentially saving space on the cd. If it doesn't though, it doesn't offer a great deal of extra functionallity, and it has to be remembered that every kilobyte counts on the livecd.

Good point. Less bloat.

> **psyke83 said:**
> You can't possibly remove gzip or bzip2, they're too ubiquitous on the Linux platform (and no, it doesn't matter if p7zip supports compression/decompression of those formats). It would introduce far too much breakage (e.g. packaging scripts).

Adding 7z support is an advantage for those who want better compression, simple as that. It's also cross-platform (there's a 7-Zip GUI for Windows and the most popular archiving program, WinRAR, also supports 7z archives).

Maybe this specification should also be revived: [https://blueprints.launchpad.net/ubuntu/+spec/dpkg-lzma](https://blueprints.launchpad.net/ubuntu/+spec/dpkg-lzma)


So wouldnt it make sense to include 7z and over a number of releases work on getting it to work well enough(so we dont get said breakage) so that gzip and bzip2 can be replaced by it.

Perhaps by 11.10 or 12.04-LTS 7z could exist without gzip & bzip2.

I dont see the point of having multiple of the same type of tool installed if youre not working towards a goal of having 1 superior tool and creating less bloat. I really dont want to see Linux go down the same road as MS.

---

### Post by HavocXphere on 2009-05-21
> **davideotape said:**
> Of those left, how many have 4gb files they want to split up.
Ooo...pick me, pick me.\\:D/

This also applies to DVDs with the 4.5gb limit on them, so I think it actually applies to quite a few people.

Its unfortunate that Rar (all of it) isn't open sourced.:-|

---

### Post by psyke83 on 2009-05-21
> **Slug71 said:**
> Good point. Less bloat.




So wouldnt it make sense to include 7z and over a number of releases work on getting it to work well enough(so we dont get said breakage) so that gzip and bzip2 can be replaced by it.

Perhaps by 11.10 or 12.04-LTS 7z could exist without gzip & bzip2.

I dont see the point of having multiple of the same type of tool installed if youre not working towards a goal of having 1 superior tool and creating less bloat. I really dont want to see Linux go down the same road as MS.

Sorry, but it doesn't make sense at all. The p7zip tool specializes with LZMA compression - let it do what it was designed to do. Do you think the author would - or should - ever think "gee, I should make it 100% compatible with bzip2 and gzip so the Ubuntu folks can fit it on their Live CD"?

The bzip2 and gzip compressors are absolutely vital for everyone, even if they don't realize why - for example, Debian archives use these formats for (de)compression.

If the dpkg-lzma blueprint was implemented, the alternative CD would have space for many more packages (175mb according to the [wiki]("https://wiki.ubuntu.com/dpkg-lzma")), which would also mean smaller download sizes for updates. Although the Live CD may not benefit from space savings (as it uses a casper image which may not capable of being compressed, I'm not clear on this point), otherwise there are many benefits worth considering from including p7zip.

---

### Post by psyke83 on 2009-05-21
> **davideotape said:**
> I think even with a size of around a megabyte, it would be hard to squeeze it on to the live-cd. But, if it has better compression methods than those that are already used on the cd, it could in fact save space. Anyone know if it would take a lot of time and effort to use .7z to compress files on the cd instead of what is already being used?

See the [dpkg-lzma]("https://wiki.ubuntu.com/dpkg-lzma") wiki and associated blueprint. Basically, it would save around 175mb for the alternate CD image, though I'm not sure if we can get space savings for the Live CD. Having smaller .deb package seems very appealing to me, though (having spent time in Brazil with a 256k connection, trying to download updates for a freshly installed Intrepid installation).

> Fair enough, but in my experience the most widely used compression format on windows is .zip. Personally I have used 7-zip on windows from the right click menu, and it is a way better than win-rar.

That's true (and unzip support is built into Windows Explorer since XP), but I meant the most ubiquitous third-party archiver that a Windows users will inevitably find themselves using - WinRAR.

WinRAR has native 7z support, so (indirectly) the 7z format has good cross-platform support if you ever find yourself wanting to send a large file to a friend using Windows over the internet, etc.

---

### Post by davideotape on 2009-05-21
Very good points Psyke.

However, going back to the origional question, is there much of a problem with just downloading and installing the 7z support manually? I'm fairly sure that anyone needing the features knows what to install and how to install it.

---

### Post by psyke83 on 2009-05-21
> **davideotape said:**
> Very good points Psyke.

However, going back to the origional question, is there much of a problem with just downloading and installing the 7z support manually? I'm fairly sure that anyone needing the features knows what to install and how to install it.

Well, the point of discussion was arguments for or against the default inclusion of p7zip, correct?

I may have gone off on a tangent, but I felt it was a good opportunity to discuss the dpkg-lzma specification. There are distinct advantages towards implementing a more efficient compression scheme for Ubuntu's .deb packages - and having p7zip included by default would be a pleasant side-effect.

The above is probably not going to happen for Karmic, but I would love to see p7zip-full included in ubuntu-restricted-extras (as I disagree that users would necessarily "know" what to install to get better archiving support in Ubuntu). I'm going to file a bug to see if this is possible.

---

### Post by Bios Element on 2009-05-21
> **psyke83 said:**
> The above is probably not going to happen for Karmic, but I would love to see p7zip-full included in ubuntu-restricted-extras (as I disagree that users would necessarily "know" what to install to get better archiving support in Ubuntu). I'm going to file a bug to see if this is possible.

Sums it up. People use what is handed to them. If you hand them rar support they'll use that. zip, they'll use that. Same for p7. Add it and people wil use it and not really care and the more people who use it, the more people will go outta their way to use it and so on.

---

### Post by davideotape on 2009-05-21
> **Bios Element said:**
> Sums it up. People use what is handed to them. If you hand them rar support they'll use that. zip, they'll use that. Same for p7. Add it and people wil use it and not really care and the more people who use it, the more people will go outta their way to use it and so on.

That's a very good point I hadn't thought about. And is 7zip not even in the repos? If not, then i'm all for trying to get it included :D

---

### Post by dudude on 2009-05-21
Since dpkg-lzma has been brought up, I think it may be worth adding that the Ubuntu live cd uses SquashFS.

The normal version of SquashFS only supports gzip compression, but there is another version of it that supports lzma compression, called SquashFS LZMA.

I don't believe that dpkg-lzma will be implemented any time soon, but it shouldn't be too difficult to implement SquashFS LZMA. With this, it would mean that there would be lzma support in Ubuntu and there would be more free space on the live cd.

The main issue I see is that lzma is slower, albeit with a better compression ratio, than gzip or bzip2, which could be an issue for older hardware.

[SquashFS]("http://squashfs.sourceforge.net/")

[SquashFS LZMA]("http://www.squashfs-lzma.org/")

---

### Post by amano on 2009-05-21
> **psyke83 said:**
> Another idea (if space is too tight on the Live CD) would be to add p7zip-full (which includes rar support?) to the ubuntu-restricted-extras metapackage...

+1
That would be the minimum. 7z is such a great tool. Big thanks to Igor Pavlov for giving this to the world.):P

---

### Post by psyke83 on 2009-05-21
> **amano said:**
> +1
That would be the minimum. 7z is such a great tool. Big thanks to Igor Pavlov for giving this to the world.):P

I've filed this proposal as [bug #379236]("https://bugs.launchpad.net/bugs/379236"). I recommend everyone who is interested to voice their opinions on that report.

A bug was already filed for inclusion into the default installation: [bug #261117]("https://bugs.launchpad.net/bugs/261117"). Please comment there as well.

Col-1023, perhaps you can edit post #1 and provide these bug reports for first-time readers of this thread? I realize you were asking for p7zip as the default in Ubuntu, but getting p7zip-full in ubuntu-restricted-extras is also a worthy cause (the -full package supports unpacking of RAR archives, so different needs are served).

I'll also file a bug to propose that p7zip be included on the CD (which will probably get rejected, but it's understandable).

---

### Post by BoyOfDestiny on 2009-05-21
7zip is Free Software, it doesn't belong in restricted IMHO.
Just install it and it works with file roller as was said, perhaps there is something not needed on the Ubuntu ISO, i.e. software packaged for Windows (if memory serves there was a copy OOo on there... I've been dist-upgrading for a while now...)

As for the use case, storing on FAT32, come on and use a file system that can handle files larger than 4 gigabytes. It's nearly the year 2010.

Give your Windows using pals this
[www.fs-driver.org/](www.fs-driver.org/)

It will let them read/write to ext3 drives.

Compressing an already heavily compressed Video into multiple zip archives will have to be extracted, requiring more space, and more hard drive thrashing for both the storage hard drive and your user's hard drive. 

Just seems silly and unnecessary all around.

If the files after compression, i.e. 4 gig, end up being like 3.99gb you should just use split and cat. 

Of course Windows doesn't have cat out of the box...

Summation of rant: Don't use FAT32 for anything.

---

### Post by psyke83 on 2009-05-21
> **BoyOfDestiny said:**
> 7zip is Free Software, it doesn't belong in restricted IMHO.
Just install it and it works with file roller as was said, perhaps there is something not needed on the Ubuntu ISO, i.e. software packaged for Windows (if memory serves there was a copy OOo on there... I've been dist-upgrading for a while now...)

Let's not muddy the waters here. The p7zip software uses the LZMA algorithm which is not patent-encumbered and according to its license it is "Free Software". It is not restricted, but it's in the "universe" repository, presumably because it lacks a maintainer with enough time to scrutinize the software to a high enough degree to keep it in the "main" repository.

There is a version of the p7zip package (p7zip-full) which includes support for patent-encumbered archive formats (RAR). This package will never make it into "main" because of patent concerns, so it is "restricted" in a certain sense.

I propose we put p7zip on the CD for the default install (i.e., get it accepted into "main"), and we have p7zip-full included with the ubuntu-restricted-extras metapackage. See the difference?

> As for the use case, storing on FAT32, come on and use a file system that can handle files larger than 4 gigabytes. It's nearly the year 2010.

Give your Windows using pals this
[www.fs-driver.org/](www.fs-driver.org/)

It will let them read/write to ext3 drives.

I have two removable drives. One uses ext3, another uses a small bootable Ubuntu partition and large NTFS partition.

The ext3 drive has compatibility issues with Windows - sometimes files will not save or be read correctly while using the ext3 ifs driver that you mentioned.

Logically speaking, NTFS is the ideal cross-platform filesystem. A stock Ubuntu (or modern Linux distro) install and a stock Windows install can both read an NTFS partition without extra software. However, the NTFS driver (ntfs-3g) is based in userspace, and performance is not ideal compared to a native in-kernel filesystem (and I don't care how many people insist that ntfs-3g is now much more optimized, it is still less efficient in my experience).

While I personally think that FAT32 should die a horrible death, there is something to be said about the performance benefits over NTFS via ntfs-3g, especially if working with large files regularly.

> Compressing an already heavily compressed Video into multiple zip archives will have to be extracted, requiring more space, and more hard drive thrashing for both the storage hard drive and your user's hard drive. 

Just seems silly and unnecessary all around.

If the files after compression, i.e. 4 gig, end up being like 3.99gb you should just use split and cat. 

Of course Windows doesn't have cat out of the box...

Summation of rant: Don't use FAT32 for anything.

Yes, compressing lossy content (video) using a lossless archiver is a bit silly. However, unless I'm mistaken, I would assume the OP would want to "compress" to a multipart .7z archive with the compression level set to "none" - in other words, simply use the multipart functionality of the 7z container format.

Let's look at the inclusion of p7zip and/or p7zip-full from a wider perspective than the original intent of this post, though. There are many advantages beyond splitting large files.

---

### Post by gaspard.leon on 2009-05-21
the usual answer would be:
"Just use a ZIP file."

however given this:
[http://en.wikipedia.org/wiki/Zip_file#Technical_information](http://en.wikipedia.org/wiki/Zip_file#Technical_information)
> The original ZIP format had a 4.2gb limit on various things (uncompressed size of a file, compressed size of a file and total size of the archive), as well as a limit of 65535 entries in a zip archive. In version 4.5 of the specification (which is not the same as v4.5 of any particular tool), PKWARE introduced the "ZIP64" format extensions to get around these limitations. Zip64 support is emerging. For example, the File Explorer in Windows XP does not support ZIP64, but the Explorer in Windows Vista does. Likewise - some libraries, such as IO::Compress::Zip in Perl, have new support for ZIP64, while others, such as Java's built-in java.util.zip, still lack it.

I have encountered this problem personally, so now I generally prefer to use 7-Zip for most things when large file support or proper splitting are required.

So to summarize, ZIP supports max 4GB for contained and container files...

RE: the use case: I agree that the NTFS disk solution sounds great, and works fine, but FUSE is one slow mutha when you have a large amount of data to copy... (can't believe the Linux kernel maintainers and the NTFS-3G guys can't organise getting it into the kernel, it's only _the most common filesystem_)

so yeah transparently splitting files using 7-Zip (with 0% for already compressed files) is the best solution...

Gaspard

---

### Post by seeker5528 on 2009-05-22
If all you are worried about is splitting and joining large files, lxsplit is in the repository.

Hjsplit seems to be not so uncommon for this type of use and readily available to Windows users and unlike with lxsplit, Windows users are provided with a GUI. :p

There is an hjsplit for linux that has a GUI, but it requires some Kylix crap and it looks like the GTK front end for lxsplit is a dead project.  

Later, Seeker

---

### Post by psyke83 on 2009-05-22
> **seeker5528 said:**
> If all you are worried about is splitting and joining large files, lxsplit is in the repository.

Hjsplit seems to be not so uncommon for this type of use and readily available to Windows users and unlike with lxsplit, Windows users are provided with a GUI. :p

There is an hjsplit for linux that has a GUI, but it requires some Kylix crap and it looks like the GTK front end for lxsplit is a dead project.  

Later, Seeker

Shhh, don't ruin everything ;)

The "p7zip" package is a 337kb download and once it's installed, file-roller will give the option to split into volumes. The only problem is that file-roller doesn't display any options to change the compression level for any archive types, unfortunately.

---

### Post by BoyOfDestiny on 2009-05-22
> **psyke83 said:**
> Let's not muddy the waters here. The p7zip software uses the LZMA algorithm which is not patent-encumbered and according to its license it is "Free Software". It is not restricted, but it's in the "universe" repository, presumably because it lacks a maintainer with enough time to scrutinize the software to a high enough degree to keep it in the "main" repository.

There is a version of the p7zip package (p7zip-full) which includes support for patent-encumbered archive formats (RAR). This package will never make it into "main" because of patent concerns, so it is "restricted" in a certain sense.

I propose we put p7zip on the CD for the default install (i.e., get it accepted into "main"), and we have p7zip-full included with the ubuntu-restricted-extras metapackage. See the difference?

Thanks, I see that now.


> 
I have two removable drives. One uses ext3, another uses a small bootable Ubuntu partition and large NTFS partition.

The ext3 drive has compatibility issues with Windows - sometimes files will not save or be read correctly while using the ext3 ifs driver that you mentioned.

Logically speaking, NTFS is the ideal cross-platform filesystem. A stock Ubuntu (or modern Linux distro) install and a stock Windows install can both read an NTFS partition without extra software. However, the NTFS driver (ntfs-3g) is based in userspace, and performance is not ideal compared to a native in-kernel filesystem (and I don't care how many people insist that ntfs-3g is now much more optimized, it is still less efficient in my experience).

While I personally think that FAT32 should die a horrible death, there is something to be said about the performance benefits over NTFS via ntfs-3g, especially if working with large files regularly.


Excellent suggestion, I hadn't run into issues with that driver (but I've used it sparingly, mostly to migrate data from systems that will be "retired".) As for the ntfs-3g driver, it went final long after I had use for it, good to hear that it works nicely.

> 
Yes, compressing lossy content (video) using a lossless archiver is a bit silly. However, unless I'm mistaken, I would assume the OP would want to "compress" to a multipart .7z archive with the compression level set to "none" - in other words, simply use the multipart functionality of the 7z container format.

Wrong tool for the wrong job. I could use ghex to work on standard txt files rather than gedit...

> Let's look at the inclusion of p7zip and/or p7zip-full from a wider perspective than the original intent of this post, though. There are many advantages beyond splitting large files.

Fair enough, definitely support for creating/extracting 7z files out of the box would be a boon.

Thank you for the detailed responses.

---

### Post by Reiger on 2009-05-22
> **psyke83 said:**
> The ext3 drive has compatibility issues with Windows - sometimes files will not save or be read correctly while using the ext3 ifs driver that you mentioned.

That's because it is an ext2 driver, and AFAIK isn't aware of how permissions are set in the context of the 'original' environment (the system which created & uses the partition). This means that breaking an existing Linux installation can be as simple as writing to it using that driver (file system/permission corruption).

> Logically speaking, NTFS is the ideal cross-platform filesystem. A stock Ubuntu (or modern Linux distro) install and a stock Windows install can both read an NTFS partition without extra software. However, the NTFS driver (ntfs-3g) is based in userspace, and performance is not ideal compared to a native in-kernel filesystem (and I don't care how many people insist that ntfs-3g is now much more optimized, it is still less efficient in my experience).

Definitely not. Similar issues exist with ntfs-3g not the least of which is that no NTFS permissions are enforced (everything is mounted with permissions set to 700 and owner & group to the current user). This means that if the partition concerned is not intended as a shared partition you present a very real security risk (anything running as the current user can totally destroy it). At the same time dumb-users can't use the partition: you can't use it for a WWW server because the WWW server runs as a dumb-user and can't read from the partition. You can't use it for a FTP or media server because of the same either...

Finally the fact that while NTFS is case-sensitive its typical 'original environment' (Windows) is not means that you can have real fun when you have a file called 'CASE' and then create another file called 'case'. Oh and you will regularly corrupt the contents of the trash can (because trash cans work different under the Windows environment than they do under Linux DE's) meaning that you might as well not have one [the 'solution' is to empty the recycle bin/trash can] if you change between environment frequently.

---

### Post by yelo3 on 2009-05-22
I also use 7 zip to send compressed contents via email.
I remember this thing: I had to send a monodevelop project to a windows user, so I used zip. The result was a 12MB archive, which I could not send due to the maximum attachment limit.
Then I used 7z and I got a 4MB archive :D

---

### Post by qamelian on 2009-05-22
> **seeker5528 said:**
> If all you are worried about is splitting and joining large files, lxsplit is in the repository.

Hjsplit seems to be not so uncommon for this type of use and readily available to Windows users and unlike with lxsplit, Windows users are provided with a GUI. :p

There is an hjsplit for linux that has a GUI, but it requires some Kylix crap and it looks like the GTK front end for lxsplit is a dead project.  

Later, Seeker
HJSplit also has a java version that works quite well.

---

### Post by psyke83 on 2009-05-22
> **Reiger said:**
> That's because it is an ext2 driver, and AFAIK isn't aware of how permissions are set in the context of the 'original' environment (the system which created & uses the partition). This means that breaking an existing Linux installation can be as simple as writing to it using that driver (file system/permission corruption).

Actually, my issues were with Latin characters in filenames, not permissions. The open-source [ext2fsd]("http://ext2fsd.sourceforge.net/") seemed more unstable, unfortunately.

> Definitely not. Similar issues exist with ntfs-3g not the least of which is that no NTFS permissions are enforced (everything is mounted with permissions set to 700 and owner & group to the current user). This means that if the partition concerned is not intended as a shared partition you present a very real security risk (anything running as the current user can totally destroy it). At the same time dumb-users can't use the partition: you can't use it for a WWW server because the WWW server runs as a dumb-user and can't read from the partition. You can't use it for a FTP or media server because of the same either...

Come on. Enforcing permissions is completely unnecessary for an NTFS partition intended to be shared across computers. It is highly unlikely that anyone will rely on the "security" of this feature due to how trivial it is to override permissions - even in Windows itself.

> Finally the fact that while NTFS is case-sensitive its typical 'original environment' (Windows) is not means that you can have real fun when you have a file called 'CASE' and then create another file called 'case'. Oh and you will regularly corrupt the contents of the trash can (because trash cans work different under the Windows environment than they do under Linux DE's) meaning that you might as well not have one [the 'solution' is to empty the recycle bin/trash can] if you change between environment frequently.

The case issue is important, but not a big deal for the use case I was talking about. As for the trash can issue, it's slightly annoying, but how is it different to using a FAT32 partition, or using a ext partition in Windows and seeing the .Trash folder in the root of the drive?

The main issue with the ntfs-3g driver is that it will never have good performance as long as it's in user-space.

---

### Post by Reiger on 2009-05-22
> **psyke83 said:**
> Actually, my issues were with Latin characters in filenames, not permissions. The open-source [ext2fsd]("http://ext2fsd.sourceforge.net/") seemed more unstable, unfortunately.

Oh, well I've had slightly different issues with it ... :P

> 
Come on. Enforcing permissions is completely unnecessary for an NTFS partition intended to be shared across computers. It is highly unlikely that anyone will rely on the "security" of this feature due to how trivial it is to override permissions - even in Windows itself.

The security risk is when someone logs on to the computer but `accidentally' invokes rm -rf on the partition. Or rewrites the contents with junk. Sounds like `unusual' and `uncommon' behaviour? The post/thread on 'malicious commands' already devotes an entire section to these `use case scenarios'. Things which can largely be prevented by enforcing file permissions.

However you must have missed my second part: the permissions with which the partition is mounted *also* make it useless for sharing: again, 700 means 0 permissions for anyone who isn't logged on. And that means you cannot remotely read or execute anything via a dumb-user.. So in your use case [to be shared accross computers] you would want to have the partition used as the data for a WWW server or FTP server or media server (MPD)... But you can't because none of those services will be able to read the files [they all run as a dumb-user].

Only things which run over SSH (or otherwise make use of real user accounts on the server system) will be able to access the files; but they will be able to do *everything* including those things forbidden by the Gods of Common Sense. Heck they will have *more* permissions set on the NTFS share than they will have on their *home folder*...

As for the other issues these are to point out that NTFS as used by Windows is not actually inter-operable with other OS'es like Ubuntu: the concept of recycle bin is simply handled differently as is deleting a file.

---

### Post by Col-1023 on 2009-05-23
OK, thanks Psyke83 for the bug reports and links, I edited the original post, but since I'm a noob or casual user when it comes to editing forums, I cut and pasted the quote and only the numbers came out, the links didn't get pasted, but with the numbers people can find the bug reports.

Will file-roller ever get the option to set the compression, since as mention earlier in this thread you can set a password and split a file in file-roller, but there is no option to set the compression ratio.

---

### Post by steeleyuk on 2009-05-23
You can set the compression ratio using Gconf but not via the GUI... you'd have to speak to the maintainer for their reasons for that.

Use the string '/apps/file-roller/general/compression_level'. The settings can be either very_fast, fast, normal or maximum.

---

### Post by psyke83 on 2009-05-23
> **steeleyuk said:**
> You can set the compression ratio using Gconf but not via the GUI... you'd have to speak to the maintainer for their reasons for that.

Use the string '/apps/file-roller/general/compression_level'. The settings can be either very_fast, fast, normal or maximum.

Yes, unfortunately it doesn't have a "store" option, though.

---

### Post by taavikko on 2009-05-23
Anyone tried creating .tar.7z archive with file-roller, or via nautilus menu
ends up segfaulting...

---

