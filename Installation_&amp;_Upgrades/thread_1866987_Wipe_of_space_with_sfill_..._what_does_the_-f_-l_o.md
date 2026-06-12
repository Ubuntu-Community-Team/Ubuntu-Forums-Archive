---
title: "Wipe of space with sfill ... what does the -f -l options?"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by alepila on 2011-10-22
Hello everyone, I would like to clean up my hard drive before selling it and I would like to know more about the package sfill; I found the man and readed the following instructions:
```
sfill (1)

Name
sfill - secure free disk and inode space wiper (secure_deletion toolkit)

Synopsis
sfill [-f] [-i] [-I] [-l] [-l] [-v] [-z] directory/mountpoint

Description
sfill is designed to delete data which lies on available diskspace on mediums in a secure manner which can not be recovered by thiefs, law enforcement or other threats. The wipe algorythm is based on the paper "Secure Deletion of Data from Magnetic and Solid-State Memory" presented at the 6th Usenix Security Symposium by Peter Gutmann, one of the leading civilian cryptographers.

The secure data deletion process of sfill goes like this:

*
    1 pass with 0xff 
*
    5 random passes. /dev/urandom is used for a secure RNG if available. 
*
    27 passes with special values defined by Peter Gutmann. 
*
    5 random passes. /dev/urandom is used for a secure RNG if available. 

afterwards as many temporary files as possible are generated to wipe the free inode space. After no more temporary files can be created, they are removed and sfill is finnished.

Commandline Options

-f
    fast (and insecure mode): no /dev/urandom, no synchronize mode. 
-i
    wipe only free inode space, not free disk space 
-I
    wipe only free disk space, not free inode space 
-l
    lessens the security. Only two passes are written: one mode with 0xff and a final mode with random values. 
-l
    -l for a second time lessons the security even more: only one random pass is written. 
-v
    verbose mode 
-z
    wipes the last write with zeros instead of random data 

directory/mountpoint this is the location of the file created in your filesystem. It should lie on the partition you want to write. 
```

I want to know what exactly does the options -f and -l

because I do not understand what ```
fast (and insecure mode): no /dev/urandom, no synchronize mode. 
``` means

 Thanks

  Cheers

---

