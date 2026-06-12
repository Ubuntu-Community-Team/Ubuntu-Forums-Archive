---
title: "Bad blocks on install"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by heatmizuh on 2006-10-02
Hi --

First time around installing Ubuntu -- the LiveCD I got is incredibly awesome, so I decided to install it to an older HD I had laying around the house.

The install would fail at various parts numerous times, and I realized I had some hardware failures... I dropped down to the shell and ran 'badblocks' and a number of them showed up.

My question is, now that I know I have them, how do I mark them as 'bad' so the installer works around them?  The shell doesn't have mke2fs or e3fsck installed, so I am assuming the installer just tries to use the bad blocks...

For the most part, the hard drive is in pretty good shape...I just need to mark those blocks as unusable.

Any help would be greatly appreciated!  Thanks!

---

### Post by az on 2006-10-02
I read the badblocks manpage and it says that the -o parameter passes the badblocks to a file that can be used by mke2fs using the -l parameter.

However, the mke2fs manpage says:
 -l filename
              Read the bad blocks list from filename.   Note  that  the  block
              numbers  in  the bad block list must be generated using the same
              block size as used by mke2fs.  As a result,  the  -c  option  to
              mke2fs is a much simpler and less error-prone method of checking
              a disk for bad blocks before formatting it, as mke2fs will auto&#8208;
              matically  pass the correct parameters to the badblocks program.


So forget about using badblocks, just make the filesystem using the -c parameter and you are good to go.

---

### Post by heatmizuh on 2006-10-02
Yeah, I read that too --

The only thing is, installing with the text installer via CD, where is the mke2fs executable and how to I tell the installer to use the -c parameter?

I'm a little n00bish when it comes to Ubuntu, and Linux in general, so any help would be appreciated.

Thanks!

---

### Post by az on 2006-10-02
> **heatmizuh said:**
> Yeah, I read that too --

The only thing is, installing with the text installer via CD, where is the mke2fs executable and how to I tell the installer to use the -c parameter?

I'm a little n00bish when it comes to Ubuntu, and Linux in general, so any help would be appreciated.

Thanks!

Do it beforehand and then set it up using manual partitioning and not formatting it.

---

